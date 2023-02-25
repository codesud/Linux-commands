### Some of the commands practised
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