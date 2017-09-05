---
title: OA环境搭建JavaWeb+mysql+Tomcat
time: 2016.08.20
layout: post
tags:
  - 技术
  - jdk
  - mysql
  - tomcat
excerpt: 此博文针对服务器搭建javaweb作个记录，主要涉及到jdk、mysql的安装以及环境变量的配置方法，采用tomcat作为web服务器，当然还可以用其他的比如apache等。
---
> 目录
> * 安装jdk
> * 安装mysql
> * 安装Tomcat

## 环境配置
1.OA系统：Java开发的.jsp网页<br/>
2.Web服务器：tomcat7.0<br/>
3.数据库：mysql<br/>
4.jdk：jdk1.7<br/>
5.操作系统：windows server 2008 r2

## 安装jdk
1.jdk下载，[官网下载地址](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) [百度云盘下载](http://pan.baidu.com/s/1dFtj2DV)<br/>
2.正常安装，安装很简单，根据jdk安装向导安装即可，记住安装的安装路径，配置环境变量。
<img class="single-img" src="https://youngeyes.github.io/Blog/img/post/path1.png" data-src="https://youngeyes.github.io/Blog/img/post/path1.png">
新建JAVA_HOME环境变量，如图：
<img class="single-img" src="https://youngeyes.github.io/Blog/img/post/path2.png" data-src="https://youngeyes.github.io/Blog/img/post/path2.png">
对path变量进行编辑，在path变量末尾加上` ;%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;`
新建CLASSPATH变量，变量值为：`.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;`
配置完成后，运行cmd验证jdk是否安装成功，在cmd中输入命令javac或java -version验证jdk是否安装成功。

## 安装mysql
1.[百度云下载](http://pan.baidu.com/s/1mip8nOG);[官网下载](https://dev.mysql.com/downloads/mysql/)<br/>
2.下载完成后运行安装，安装一直按向导安装即可，选择类型选择Typical即可。<br/>
3.配置mysql环境变量，方便mysql的使用，进入mysql安装目录到bin，将此目录写入环境变量path末尾。<br/>
4.安装mysql服务，cmd命令行输入命令mysqld install，提示服务安装成功，命令net start mysql启动服务。<br/>
5.使用root用户进入mysql数据库，打开cmd命令行输入命令mysql -u root -p，初始密码为空。<br/>

## 安装Tomcat服务器
1.[百度云下载](http://pan.baidu.com/s/1mizbGpU);[官网下载](http://tomcat.apache.org/download-70.cgi)<br/>
2.官网下载按照向导安装即可，百度云下载的不需要安装，直接点击下载包bin目录下startup.bat文件。<br/>
> 注意：Tomcat默认端口是8080，如果端口占用，需要更改conf文件下的server.xml文件，把8080端口改为其他的。

3.安装完成后，`http://localhost:8080/`本地可以访问说明安装完成。<br/>

## 配置OA系统
上面安装都完成之后，就可以配置OA系统了，将OA系统的程序包放到tomcat的webapps文件下即可。可以试试用浏览器能不能访问OA系统呢。