---
title: python入门学习之变量和数据类型
time: 2017.08.26
layout: post
tags:
  - 技术
  - python
  - 变量
  - 数据类型

series: python入门学习
excerpt: 系列博文，针对python学习的笔记，做一个系列，方便以后查阅总结。本篇主要介绍python开发中的变量和数据类型，对python中常用的变量和数据类型做一个总结。
---
## 变量
变量是程序中用来保存数据的内存单元，可以通过变量名称来操作这些数据和内存分配情况。在计算机程序里，变量可以是任意数据类型，但是变量的命名需要符合规范，即变量名必须是大小写英文、数字和```_```的组合，且不能以数字开头。例如：<br/>
> a = 1 &emsp;&emsp;&emsp;&emsp;&emsp;<font color="red">#变量a是一个整数</font><br/>
> t123 = 'abc' &emsp;&emsp;<font color="red">#变量t123是一个字符串</font><br/>
> flg = True &emsp;&emsp;&emsp;<font color="red">#变量flg是一个布尔值</font><br/>
> 12_p = 1.23 &emsp;&emsp;<font color="red">#变量12_p不符合规范</font>

python中给变量赋值是用等号```=```，一个变量可以反复多次赋值，与某些语言不同的是每次赋值都可以是不同数据类型的值，例如：<br/>
> a = 123 <font color="red">#给变量a赋值为整数</font><br/>
> print(a)<br/>
> a = 'abc'<font color="red">#给变量a赋值为字符串，不会报错</font>

python中变量在计算机内存中的表示也很重要，这样可以更方便的理解计算机是怎么处理变量命名赋值的。当我们写```a = 'abc'```时：<br/>
&emsp;&emsp;python解释器干了两件事：<br/>
&emsp;&emsp;1.在内存中创建了一个```'abc'```的字符串。<br/>
&emsp;&emsp;2.在内存中创建了一个名为```a```的变量，并把它指向```'abc'```。
## 常量
常量就是不可变的变量，python中没有限定常量的关键字，但通常用全部大写的变量名来表示常量，这只是人们的一种习惯上用法，例如：<br/>
> PI = 3.14159265359

## 数据类型
#### 整数
python可以处理任意大小的整数，包括正整数，负整数，0，例如：```1```，```100```，```-300```，```0```，等。
#### 浮点数
浮点数即是小数，浮点数可以用数学写法，如```1.22```，```3.1415```，``` -3.22```，对很大或很小的浮点数，必须用科学计数法表示，把10用e代替。<br/>
#### 字符串
字符串是以单引号```'```或双引号```"```括起来的任意文本，比如```'abc'```，```"xyz"```等等。如果字符串本身包含```'```或```"```，则需要用到转义字符```\```。<br/>
#### 布尔值
布尔值只有```True```、```False```两种，要么为```True```，要么为```False```，在python中直接使用```True```、```False```来表示布尔值，还可以用布尔运算计算出来。例如：<br/>
```
>>> True
True
>>> False
False
>>> 3 > 2
True
>>> 3 > 5
False
```
&emsp;&emsp;布尔值还可以用```and```、```or```和```not```运算。例如：<br/>
```
>>> True and True
True
>>> True and False
False
>>> False and False
False

>>> True or True
True
>>> True or False
True
>>> False or False
False

>>> not True
False
>>> not False
True
```
#### 空值
&emsp;&emsp;空值是Python里一个特殊的值，用```None```表示，它不等同于```0```。
