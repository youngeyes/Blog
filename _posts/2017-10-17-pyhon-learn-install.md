---
title: python入门学习之开发环境搭建
time: 2017.10.17
layout: post
tags:
  - 技术
  - python
  - 安装

series: python入门学习
excerpt: 系列博文，针对python学习的笔记，做一个系列，方便以后查阅总结。本篇主要介绍python开发环境的搭建。
---

##  Windows下python环境搭建
首先，去官网下载python开发包，打开官方网站：```http://python.org/```。点击"Downloads"，我们一般选择最新版本下载进行安装，当然也可以选择旧版本安装，这个看个人选择。下载完成后双击安装包安装即可，安装过程纯属傻瓜式。<br/>
> Tips：安装选项有两个，一个默认安装，一个自定义安装，一般我们选择自定义安装，好选择自定义安装路径，千万记得将选项“Add Python 3.X to Path”，选了这个后就不用配置环境变量了。

就这样next一直到安装完成，下一步配置环境变量，如果上面勾选了"Add Python 3.X to Path"选项就不用配置了。右键我的电脑，选择属性，在弹出的对话框中选择高级系统设置，点击环境变量，找到系统变量里面的Path，将python的安装目录配置到环境变量中。配置完成后在cmd命令行中输入python验证。<br/>
## Ubuntu下安装python
#### 1.通过ubuntu官方的apt工具包安装
> ```sudo apt-get install python3.5```

#### 2.从PPA安装apt工具包
> ```$ sudo apt-get install python-software-properties```<br/>
>  ```$ sudo add-apt-repository ppa:fkrull/deadsnakes```<br/>
> ```$ sudo apt-get update```<br/>
>  ```$ sudo apt-get install python3.5```

#### 3.验证python是否安装成功
打开终端，输入python --version，回车
