### Some of the commands practised
```
man passwd
man cat
cat /etc/passwd -e
cat /etc/passwd -n
tac /etc/passwd 
man tac
head /etc/passwd
tail /etc/passwd
head -n 3 /etc/passwd
tail -n 5 /etc/passwd
man sed
sed -n -e '10-15p' /etc/passwd
sed -n -e '10,15p' /etc/passwd
sed -e '10,15p' /etc/passwd
sed -n '10,15p' /etc/passwd
man sed
cat > myfile.txt
cat myfile.txt
sed -n 's/fox/coati/;s/dog/dingo/;p' myfile.txt
sed -n 's/fox/coati/;s/dog/dingo/p' myfile.txt
sed ' ' myfile.txt
sed -n ' ' myfile.txt
sed -e /etc/passwd
sed /etc/passwd
sed -n -e '10-15p' /etc/passwd
sed -n -e '10,15p' /etc/passwd
man sed
man cut
cut -d : -f1 /etc/passwd
cut -d : -f2 /etc/passwd
cut -d : -f3 /etc/passwd
cut -d : -f4 /etc/passwd
cut -d : -f5 /etc/passwd
cut -d : -f6 /etc/passwd
cut -d : -f7 /etc/passwd
cut -d : -f8 /etc/passwd
cut -d : -f2 /etc/passwd
cat > sample.txt
cat sample.txt
vim sample.txt
cat sample.txt
cat sample.txt | grep I | wc -l
cat sample.txt | grep you | wc -l
man wc
cat sample.txt | grep you
cat sample.txt | grep -o -i you | wc -l
man grep
grep --help
cat sample.txt | grep -o -i I | wc -l
cat sample.txt | grep -o I | wc -l
curl google.com
curl https://raw.githubusercontent.com/codesud/Linux-commands/main/LINUX-CLI.md
curl -O https://raw.githubusercontent.com/codesud/Linux-commands/main/LINUX-CLI.md
ls -ltr
wget https://raw.githubusercontent.com/codesud/Linux-commands/main/LINUX-CLI.md
ls -ltr
cat LINUX-CLI.md.1 
wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.86/bin/apache-tomcat-8.5.86.tar.gz
wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.86/bin/apache-tomcat-8.5.86.tar.gz --no-check-certificate
ls -ltr
tar -xf apache-tomcat-8.5.86.tar.gz 
ls -ltr
du -h apache-tomcat-8.5.86
du -sh apache-tomcat-8.5.86
pwd | du -sh
top
```
```
cat /etc/passwd
useradd mike
sudo useradd mike
cat /etc/passwd
sudo useradd mitchell
sudo useradd michael
cat /etc/passwd
id centos
id mike
sudo su -
sudo su - root
sudo su mike
sudo passwd mike
sudo su mike
cat /etc/sudoers
sudo cat /etc/sudoers
sudo vim /etc/sudoers
sudo su mike
exit
```

```
sudo cat /etc/passwd
sudo useradd mike
sudo useradd mitchell
sudo useradd michael
sudo useradd tom
sudo useradd tim
sudo useradd tango
sudo groupadd devops team
sudo groupadd devopsteam
sudo groupadd hrteam
sudo usermod -aG devopsteam mike
sudo usermod -aG devopsteam mitchell
sudo usermod -aG devopsteam mchael
sudo usermod -aG devopsteam michael
sudo usermod -aG hrteam tom
sudo usermod -aG hrteam tim
sudo usermod -aG hrteam tango
sudo groupadd cloudteam
sudo usermod -aG cloudteam mike
id mike
id michel
id michael
id mitchell
id tom
sudo groupadd compensationteam
sudo usermod -aG compensationteam tom
id tom
cat /etc/group
cat /etc/passwd
cat -n /etc/passwd
cat /etc/sudoers
sudo cat /etc/sudoers
sudo vim /etc/sudoers
sudo passwd mike
sudo su mike
sudo vim /etc/sudoers
sudo su mike
sudo cat /etc/passwd
sudo cat ~/.bash_history
```

```
sudo su mitchell
sudo useradd congo
sudo usermod -aG compensationteam congo
sudo cat /etc/group
exit
last
last | grep centos | wc -l
w
sudo touch sample.txt
ls -ltr
sudo find . -type f -name "sample.txt" -exec rm {} \;

whereis touch
whereis sudo
whereis init
which touch
which sudo
which init

cd /usr/bin
ls -ltr | awk '{print $NF}'
ls -ltr | awk '{print $NF}' | wc -l

sudo touch recipes.txt
sudo vim recipes.txt
ls -ltr
sudo ln recipes.txt newrecipes.txt
ls -ltr
cat newrecipes.txt
cat recipes.txt
sudo vim recipes.txt
cat recipes.txt
cat newrecipes.txt

sudo yum install glances -y
glances

top
ps
ps -ef
ps -u root
top
cat /proc/loadavg
w
w | grep load
who
uptime
ps -a
cat /proc/loadavg
fsck
fstab
df
du
lsblk
fs
bc
nslookup
dig
cal
```