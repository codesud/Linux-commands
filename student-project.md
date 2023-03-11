# Application Anatomy


An educational institution want to transform their process of admissions from manual paperwork to an application they can use online.


So for their requirement they have contacted IT Director (Bob) to make this application created and get it done as per their requirements. Bob recruited couple of developers (John and Jim) to start work on these requirements. John and Jim collaboratively understood the business requirements and they wanted to start the application development and they have chosen Java is best for this and they chosen Maven as Project Build tool and started the development using Agile Methodology.


First version of application has been delivered by Jim and John to Bob and they had some reviews modifications and finally they are ready with product. Now Bob want to run this application 24/7. He has calculated that running servers in his company environment is not viable and wanted to go with any cloud vendor to reduce the burden which has to avoid recruiting some more people to run infrastructure. 

Bob went to different cloud vendors and their quotations , he decided to go with Amazon Web Services as it suits more of his requirements in terms of cost and management. He signed with AWS and he got the required capacity to run the infrastructure for the application. Bob want an engineer who wants to can take care the cloud based automation as well as continuous delivery of the application. So he choose to recruit a DevOps engineer.

So now you as a DevOps engineer you need to take care of the efforts.


*  Supporting Agile Development and make necessary automation to deliver the application in CD/CD manner.
*  Ensure running the application 24/7 and also application met the capacity requirements (TPS).
*  Bob has given you free hand to use the tools of your choice to get this complete process standardized.
*  You need to review the complete requirements and finalize what are the tools can be used to standardized automation for this complete requirements.


Firstly you approached Jim and John and tried to understand the architecture of application.

As per their view the application looks like as follows.

![](images/01.PNG)

Following are the observations of yourself from the application architecture

*  It is just a three layered application. Typically have three layers.
*  Developer already running the application in AWS environment in test account.
*  Developer choose the application to be written in Java as they want to use Tomcat Application Server.
*  Developer wanted to proxy this application through the web server as they have some static content to be delivered and also they want to make some redirect rules in future for application.
*  Also as of now Developer want to keep this data in SQL DB and he chooses MariaDB. Yet they have plans to explore MongoDB and PostgreSQL in future for this application.
*  Developer also used SpringBoot for this application and they had a vision to deliver this application as service.


So you want to understand the technical configurations of application hence you are referred to use the developer documentation to setup and application. Now your task is to setup the application by referring the following documentation.

[Click here for application Configuration on servers, Only EC2](https://gitlab.com/clouddevops-b53/student-project/-/blob/main/First/components-on-servers.md)


Now as per the application architecture you need to design the infrastructure components. As Bob has already taken the stand on moving to AWS now we are going to use AWS to deploy this application.

Firstly as a initial kickoff you need to deploy the application and all its components on the servers instead of services in AWS. All you can use is EC2 service in AWS.

Once after your review of application and its components it is your responsibility to deliver the application using different services in AWS.

-------


Assume that you have done the review and proposed the following tools can be used in complete deployment of application from end to end in automated manner.

Following tools for Continuous Integration

* Git for Code Management. GitLab for UI tool of Git. 
* SonarQube for Code Quality 
* Sonatype Nexus for Artifact Management.
* 


# Documentaion to setup registration application on servers.

In total we do require three servers running different components on the server.

1. Web Server 
2. Application Server 
3. Database Server 


Following are the softwares which are used for different services.

1. Apache Web Server for Web Server 
2. Apache Tomcat for Application Server 
3. MariaDB for Database Server 

Following the Diagram been referred to setup application

![](images/03.PNG)


Following are the technicalities for the tools 

1. Apache Web Server 2.4.x 
2. Tomcat App Server 8.5.x 
3. MariaDB Server 10.x

OS can be either Ubuntu or CentOS, But this document would be on Centos 7.

#

### 1. Ensure you use the AMI `DevOps-LabImage-CentOS7` in North.Virginia Region and this AMI works with username and password ( centos / DevOps321 ), without which lot of challenges would be coming up.

Install Web Server 

```shell 
$ sudo yum install httpd -y
```

Update proxy config , Pointing to application server 

```shell 
$ cat /etc/httpd/conf.d/app-proxy.conf 
ProxyPass "/student" "http://APP-SERVER-IPADDRESS:8080/student"
ProxyPassReverse "/student"  "http://APP-SERVER-IPADDRESS:8080/student"
```

*Note: Replace APP-SERVER-IPADDRESS with IP address of tomcat server * 

```shell 
$ sudo curl -s https://learndevopswithaws.s3.ap-south-1.amazonaws.com/index.html -o /var/www/html/index.html
$ sudo systemctl enable httpd 
$ sudo systemctl restart httpd 
```


## 2. Setup Application Server 

Usually we run applications with one functional user in companies (Bot not with root user). So we are going to create one user and we run our application with that user. So application is based out of student admissions we can create a user with that name or any name of choice. 

Create an application user with name `student`. 

```shell 
$ sudo useradd student 
```

Our application is based out of java, So application server you are installing is also based on Java. Hence you need to install Java. 

```shell 
$ sudo yum install java 
```

Now perform all the following commands with `student` user. 

```shell 
$ sudo su - student 
student> wget http://apachemirror.wuchna.com/tomcat/tomcat-8/v8.5.84/bin/apache-tomcat-8.5.84.tar.gz ; tar -xf apache-tomcat-8.5.84.tar.gz
student> cd apache-tomcat-8.5.84
```

Student Admission application compiled latest version is available in following URL and you have to download that to application server.

```shell
student> wget https://learndevopswithaws.s3.ap-south-1.amazonaws.com/student.war -O webapps/student.war
```

In order our application server to contact database we need the driver of DB and we have to download that from following URL.

```shell
student> wget https://learndevopswithaws.s3.ap-south-1.amazonaws.com/mysql-connector.jar
mv mysql-connector.jar lib/mysql-connector.jar
```

Finally we need to provide the information of DB details to the application server and those credentials are referred by our application.
Usually such configuration files are kept under `conf/context.xml` file.

Add the following content by replacing the values of USERNAME, PASSWORD, DB-ENDPOINT and DATABASE in the following block and add these lines just before the last line in context.xml.

```xml
<Resource name="jdbc/TestDB" auth="Container" type="javax.sql.DataSource"
               maxTotal="100" maxIdle="30" maxWaitMillis="10000"
               username="USERNAME" password="PASSWORD" driverClassName="com.mysql.jdbc.Driver"
               url="jdbc:mysql://DB-ENDPOINT:3306/DATABASE"/>
``` 

Finally we have to start the tomcat application server.

```shell 
student> /home/student/apache-tomcat-8.5.38/bin/startup.sh 
```

Refer the log file `catalina.out` and ensure there were no errors in the startup log. 

## 3. Setup Database 

Install DB Server and start the service 

As our application is chosen to drive on MariaDB we have to install those packages.

```shell
$ sudo yum install mariadb-server -y
$ sudo systemctl enable mariadb 
$ sudo systemctl start mariadb
```

So far only the DB software is installed and it does not have any database inside it. So we have to create database and required tables on it. 

```shell 
$ wget https://devops-cloudcareers.s3.ap-south-1.amazonaws.com/studentapp-ui-proj.sql -O /tmp/studentapp.sql 
$ sudo mysql </tmp/studentapp.sql

```

Finally if we hit the Web Server Public IP then we would be able to fetch application and application will start updating the students data in database. 