---
layout: post
title:  "常用linux命令"
date:   2018-05-10 22:14:54
categories: linux
tags: ubuntu16.04
---

* content
{:toc}

## 前言

本文列举了一些常用的linux环境下命令行的常用操作。




#### 进入文件夹

> cd 文件夹路径

#### 进入文件夹的图形界面

> nautilus 文件夹位置

#### 使用管理员权限

> su


#### 解压.tgz文件

> tar -zxvf 文件名

#### 解压.zip文件

> unzip 文件名

#### 解压.rar文件

> rar x 文件名

#### 删除一个文件夹下的所有文件

> sudo rm -rf 目录

#### 移动文件：

>  sudo mv 文件名 指定路径

#### 更改应用权限
>  sudo chmod 777 文件名

#### 查找安装软件的相关路径
> whereis 软件名

#### 磁盘空间剩余
> df -h

####linux下查看一个可执行文件或动态库依赖哪些动态库
> readelf -d PyGalaxy.so 或

> ldd PyGalaxy.so(可执行文件)

#### android虚拟机相关命令
列出所有已经创建了的虚拟机：android list avd

在命令行里打开虚拟机：emulator -avd 虚拟机名字

####如果ubuntu中存在多个jdk版本
1.配置默认jdk  
>  sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8.0_25/bin/java 300  

> sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.8.0_25/bin/javac 300

 后面两项可以不配置  
 > sudo update-alternatives --install /usr/bin/javah javah /usr/lib/jvm/jdk1.8.0_25/bin/javah 300  
 
 >   sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/jdk1.8.0_25/bin/jar 300  
  
2.版本切换命令，选择jdk版本：
> sudo update-alternatives --config java
 
 > sudo update-alternatives --config javac
 
3.测试： 
> java -version  

> javac -version

####ubuntu常见错误
Could not get lock /var/lib/dpkg/lock解决：
> sudo rm /var/cache/apt/archives/lock

> sudo rm /var/lib/dpkg/lock