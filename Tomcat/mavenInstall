
https://www.liquidweb.com/kb/install-java-8-on-centos-7/             java
 sudo yum install -y java-1.8.0-openjdk
yum install -y java-1.8*
   update-alternatives --config java
  java -version
find /usr/lib/jvm/java-1.8.0* | head -3
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.el7_8.x86_64
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.el7_8.x86_64/jre
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.el7_8.x86_64/jre/bin

ll /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.el7_8.x86_64/jre/bin
total 240
-rwxr-xr-x. 1 root root   8984 Apr 29 14:50 java
-rwxr-xr-x. 1 root root   9112 Apr 29 14:50 jjs
-rwxr-xr-x. 1 root root   9112 Apr 29 14:50 keytool

  vim ~/.bash_profile
  export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.el7_8.x86_64/jre/bin/java
    export PATH=$PATH:$JAVA_HOME
    echo $JAVA_HOME
     echo $PATH


Maven
wget https://mirrors.estointernet.in/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
 sudo tar -xvf apache-maven-3.6.3-bin.tar.gz
export M2_HOME=/opt/apache-maven-3.6.3
export M2=$M2_HOME/bin
export PATH=$PATH:$JAVA_HOME:$M2


Tomcat
sudo wget  http://apachemirror.wuchna.com/tomcat/tomcat-8/v8.5.55/bin/apache-tomcat-8.5.55.tar.gz
 sudo chown -R ec2-user:ec2-user apache-tomcat-8.5.55/

echo "export CATALINA_HOME=/opt/apache-tomcat-8.5.55" >> ~/.bash_profile
source ~/.bash_profile

/etc/sysconfig/selinux
sudo systemctl status firewalld
Disable Iptables Service
# systemctl disable iptables
Or
# service iptables save
# service iptables stop

Tomcat users:

<tomcat-users xmlns="http://tomcat.apache.org/xml"
              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
              xsi:schemaLocation="http://tomcat.apache.org/xml tomcat-users.xsd"
              version="1.0">

<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<role rolename="manager-jmx"/>
<role rolename="manager-status"/>
<user username="admin" password="admin" roles="manager-gui, manager-script, manager-jmx, manager-status"/>
<user username="deployer" password="deployer" roles="manager-script"/>
<user username="tomcat" password="s3cret" roles="manager-gui"/>

From <https://github.com/ValaxyTech/DevOpsDemos/blob/master/Tomcat/tomcat_installation.MD> 


</tomcat-users>


Enable Remote Access to Tomcat
By default, access to the Manager and Host Manager section is restricted to the localhost only, to allow access to these pages, you need to mention IP address or network range in configuration file.
# vi /usr/local/tomcat9/webapps/manager/META-INF/context.xml
Then look for the following line and change it to this to allow tomcat access from IP address 192.168.56.10.
allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1 |192.168.56.10" />
You can also allow tomcat access from the local network 192.168.56.0.
allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1 |192.168.56.**" />

vim  ../webapps/manager/META-INF/context.xml
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1|192.168.56.*" />



diff /opt/apache-tomcat-8.5.55/webapps/manager/META-INF/context.xml /opt/apache-tomcat-8.5.55/webapps/manager/META-INF/context.xml_bkp
20c20
<          allow=".*" />
---
>          allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
