---
title: app测试adb安卓调试和monkey
time: 2017.08.30
layout: post
tags:
  - 技术
  - app
  - adb
  - monkey

excerpt: app测试往往需要借助一些工具来完成，测试机器可以是真机也可以是sdk安卓模拟器，这时候需要借助adb调试工具，adb是Android提供的一个通用的调试工具，俗称安卓调试桥，此篇博文除了对adb调试命令的总结外，还对monkey稳定性测试做一个总结。
---
## adb安卓调试命令
#### adb devices
查找通过数据线连接到计算机的移动设备和本级运行的Android模拟器，如果要通过adb devices查找到真实的移动设备，必须在真机上打开usb调试功能，这个命令可以显示出连接到计算机的设备清单，如果没有，则显示为空。<br/>
```
>adb devices
List of devices attached
372bf8c8        device
```
372bf8c8是设备的名字（设备序列号），我用的是自己的Android机，如果用sdk安卓模拟器，设备的名字为设备名+连接端口号，例如：emulator-5554<br/>
#### adb shell
通过这个命令可以进入到Android的文件目录中，进入Android文件目录后，可以使用linux中的部分命令，可以使用exit退出这个命令模式。如有多个设备时，需在adb后面加上```-s 设备序列号```来指定进入哪个设备的文件目录，例如：<br/>
```
C:\Users\young>adb shell
shell@android:/ $ exit
exit
C:\Users\young>adb -s 372bf8c8 shell
shell@android:/ $
C:\Users\young>adb shell cat /proc/cpuinfo      #查看cpu信息
```
adb shell 可以将模拟器中的数据信息通过```>```符号保存到本地，例如：<br/>
```
adb shell dumpstate > /本地地址/文件名
adb shell dumpstate     #查看系统信息
```
#### adb install
此命令是用来安装app应用程序，通过此命令可以安装包的app应用程序安装到对应的移动设备上。<br/>
格式：```adb -s 设备序列号 install 要安装的应用（路径\名称）```<br/>
如果通过adb devices查找到的设备只有一个，则（-s 设备序列号）可以省略，如果有多个，必须指定，不然会报错。<br/>
不指定设备安装应用：<br/>
```
adb install d:\163.apk
```
指定设备安装应用：<br/>
```
adb -s emulator-5554 install d:\163.apk
```
覆盖安装：<br/>
```
adb -s emulator-5554 install -r d:\163.apk
```
#### adb uninstall
此命令用来卸载已安装的应用，卸载的应用要带上应用在系统中的包名，包名可以通过```adb shell pm list package```来查看安装的包名，同样的如果有多个设备需指定设备序列号。<br/>
```
abd uninstall com.baidu.tieba   #不指定设备卸载
adb -s emulator-5554 uninstall com.baidu.tieba   #指定设备卸载
adb -s emulator-5554 uninstall -k com.baidu.tieba   #如果需要保留一些缓存文件，可以加上-k
```
#### adb pull
通过这个命令可以将模拟器或真机上面的文件取到计算机上面。<br/>
格式：```adb pull 模拟器路径/文件名 计算机上路径/[文件名]```，例如：<br/>
```
C:\Users\young>adb pull /sdcard/ttan.ini d:/
4 KB/s (65 bytes in 0.015s)
```
#### adb push
与adb pull相反，通过adb push这个命令可以将计算机上的文件上传到模拟器或真机上面。<br/>
格式：```adb push 计算机上路径/文件名 模拟器路径/文件名```，例如：<br/>
```
C:\Users\young>adb push d:/test.txt /sdcard/test.txt
1 KB/s (31 bytes in 0.015s)
```
#### adb服务的开启和关闭
```
adb start-server    #如果adb服务处于异常或需要重启，可以使用这个命令
adb kill-server     #如果需要关闭adb服务，可以使用这个命令
```
#### 查看应用程序包信息
```
adb shell pm list package   #查看安装的应用程序信息
adb shell pm list package -f    #查看包的安装路径和包名
adb shell pm list package -i    #查看包及包的安装者
adb shell pm list package -3    #查看第三方安装包的信息
```
#### 使用telnet访问模拟器
1. 必须开通本机的telnet功能
2. 使用```telnet +计算机地址 +模拟器端口```，例如：```telnet 127.0.0.1 5554```
3. 查看计算机上的鉴权码，windows上的```C:\Users\用户名``` 目录下有个```.emulator_console_auth_token```文件，里面的内容就是鉴权码
4. 使用```auth +鉴权码```开启模拟器功能，授权之后可以对模拟器进行一些操作，可以用help查看命令
5. 模拟电话：```gsm call 10086```
6. 模拟短信：```sms send 10086 "短信内容"```
## monkey测试
monkey是Android系统自带的一个命令行工具，monkey可以向被测的应用程序发送伪随机事件，实现对应用程序的稳定性和健壮性的测试。<br/>
格式：```adb shell monkey -p 包名 随机操作次数```<br/>
示例：```adb shell monkey -p com.baidu.tieba 100```<br/>
**参数：**<br/>
1. -v  一共分为3个级别，分别是-v，-v -v ，-v -v -v 。示例：```adb shell monkey -v -v -v -p com.android.calculator2 1000 > d:\download\2.txt```
2. 事件类型
    1. --pct-touch                    触摸事件百分比
    2. --pct-motion                 手势事件百分比
    3. --pct-pinchzoom          二指缩放百分比，即只能手机上的放大缩小手势操作
    4. --pct-trackball              轨迹球事件百分比（现在已经没有了）
    5. --pct-rotation               屏幕旋转百分比
    6. --pct-nav                     基本导航事件百分比（智能手机上基本没有）
    7. --pct-majornav            主要导航事件百分比
    8. --pct-syskeys              系统按钮事件百分比
    9. --pct-appswitch          启动activity事件百分比
    10. --pct-flip                   键盘轻弹百分比
    11. --pct-anyevent          其他类型事件百分比
3. 调试类型
    1. --ignore-crashes 忽略程序崩溃
    2. --ignore-timeouts 忽略超时异常
    3. --ignore-security-exceptions 忽略发送许可错误
    4. --kill-process-after-error 通知系统停止发生错误的进程
    5. --monitor-native-crashes 监视并报告Android系统中本地代码的崩溃事件
4. 脚本示例
    ```
    Adb shell monkey -p com.XXX.XXX --pct-touch 40 --pct-motion 25 --pct-appswitch 10 --pct-rotation 5 -s 12345 --throttle 400 --ignore-crashes –ignore-timeouts –v 5000
    ```
