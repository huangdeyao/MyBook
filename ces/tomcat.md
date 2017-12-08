# CentOS安装Tomcat

[http://tomcat.apache.org/download-80.cgi下载Tomcat8的安装文件apache-tomcat-8.0.26.tar.gz](http://tomcat.apache.org/download-80.cgi下载Tomcat8的安装文件apache-tomcat-8.0.26.tar.gz)

将apache-tomcat-8.0.26.tar.gz文件放到/usr/local目录下，执行如下脚本：   

\# cd /usr/local   

\# tar -zxvf apache-tomcat-8.0.26.tar.gz // 解压压缩包   

\# rm -rf apache-tomcat-8.0.26.tar.gz.tar.gz // 删除压缩包   

\# mv apache-tomcat-8.0.26 tomcat

启动Tomcat8

\# /usr/local/tomcat/bin/startup.sh //启动tomcat

Using CATALINA\_BASE:  /usr/local/tomcat   

Using CATALINA\_HOME:  /usr/local/tomcat   

Using CATALINA\_TMPDIR: /usr/local/tomcat/temp   

Using JRE\_HOME:        /usr/java/jdk1.8.0\_60   

Using CLASSPATH:      /usr/local/tomcat/bin/bootstrap.jar:/usr/local/tomcat/bin/tomcat-juli.jar   

Tomcat started.

如果出现下面错误：

Neither the JAVA\_HOME nor the JRE\_HOME environment variable is defined 

At least one of these environment variable is needed to run this program

则要注意提前设置java路径

在apache-tomcat-8.0.26/bin/setclasspath.sh中添加一下内容

export JAVA\_HOME=/usr/java/jdk1.8.0\_60 

export JRE\_HOME=/usr/java/jdk1.8.0\_60/jre   

export CLASSPATH=.:$JAVA\_HOME/lib:$JRE\_HOME/lib:$CLASSPATH   

export PATH=$JAVA\_HOME/bin:$JRE\_HOME/bin:$PATH

防火墙开放8080端口

增加8080端口到防火墙配置中，执行以下操作： 

\# vi /etc/sysconfig/iptables

\#增加以下代码   

-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 8080 -j ACCEPT

重启防火墙

\# service iptables restart

检验Tomcat8安装运行

通过以下地址查看tomcat是否运行正常： 

[http://192.168.11.52:8080/](http://192.168.11.52:8080/)

看到tomcat系统界面，说明安装成功！

停止Tomcat8

\#  /usr/local/tomcat/bin/shutdown.sh  //停止tomcat



