---
layout: post
title:  "DroidBox环境搭建"
categories: 工具
tags:  ubuntu16.04 Droidbox
---

* content
{:toc}

## 前言

Ubuntu16.04操作系统下配置Droidbox工具




###安裝 JDK8
在/usr/lib/jvm/下解压[jdk-8u5-linux-x64.tar.gz](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)(自行下载)，得到文件夹：jdk1.8.0_05。版本号不同，此处略有不同。

###配置环境变量

1 ，按下键Ctrl + Alt+ T打开终端，在命令行输入
>  sudo gedit ~/.profile

2 ，打开文件后，在末尾加上
```js
 export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_05
 export CLASSPATH=$CLASSPATH:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
 export PATH=$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bint
```

3 ，然后保存关闭，使用source更新下
> source ~/.profile

4 ，使用env命令察看JAVA_HOME的值
> env
如果JAVA_HOME=/usr/lib/jvm/jdk1.7.0_04，说明配置成功

###安装SDK
1 ，在documents下新建文件夹
My_Program/workspace/Android，将android-sdk-linux.tar.gz（自行下载）放到刚新建打文件夹下。

2 ，打开文件后，在末尾加上
```js
 export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_05
 export CLASSPATH=$CLASSPATH:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
 export PATH=$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bint
```

3 ，进入android-sdk-linux，进入该文件夾的tools，然后复制该文件夾的位置，把它叫做str	
  

4 ，按下键Ctrl + Alt+ T打开一個终端，然後使用下面的命令：
> cd str(之前复制的路径)

> ./android

现在，Android SDK管理器将被运行。可以观察到Android 4.1.2版本已经被安装。

5 ，按下键Ctrl + Alt+ T打开终端，在命令行输入： sudo gedit ~/.profile

6 ，打开文件后，在末尾加上:
```js
 export ANDROID_SDK_HOME=/home/myw/Documents/My_Program/workspace/Android/android-sdk-linux
```
在PATH后面追加：:$ANDROID_SDK_HOME/tools:/$ANDROID_SDK_HOME/platform-tools

7 ，然后保存关闭，使用source更新下
> source ~/.profile

###编辑 ".bashrc"

1 ，按下 CTRL + ALT + T 打开一个新的终端并键入以下命令 : 
> gedit ~/.bashrc

2 ，添加以下代码到整个文本的顶部，然后将它保存。 （不要关闭文件）
```js
export PATH=${PATH}:~/android-sdk-linux/tools
export PATH=${PATH}:~/android-sdk-linux/platform-tools
```
3 ，贴上之前复制的路径str來替换'~'，然后保存并关闭文件

4 ，注销并重新登录您的Ubuntu系統

###配置python环境
打开一个终端，输入python命令，如果成功进入python环境，则不需要安装，否则：
1 ，在想要的位置创建目录：mkdir python

2 ，在想要的位置创建目录：mkdir python

3 ，在想要的位置创建目录：mkdir python
```js
 ./configure -prefix=/usr/local/python-2.7.11
make
make install	
```

###下载droidbox工具并运行
####获取droidbox工具
[DroidBox](https://github.com/pjlantz/droidbox)(自行下载)
 
###开启AVD
1.右键点击DroidBox_4.1.1，选择终端打开

2.输入命令:
>./startemu.sh <AVD name>

#### 分析apk
当模拟器开启正常显示之后，输入以下命令开始分析apk:
> ./droidbox.sh <file.apk> <duration in secs (optional)> 
