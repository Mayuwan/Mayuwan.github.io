---
layout: post
title:  "解决安装vmware tools之后仍不能在主机和虚拟机之间传送文件的问题"
date:   2018-12-06 22:14:54
categories: virtual machine
tags: 环境配置
---

* content
{:toc}




### 环境

主机：win10

虚拟机：ubuntu 16.04


### 问题

今天用VMware装好ubuntu虚拟机的时候，是可以将文件拖拽到虚拟机里的，不知道怎么的突然不可以了。弄了半天，重装了VMware Tools仍热不行。于是就换了一种方法：通过设置共享文件夹，虚拟机能读取共享文件夹的内容，与拖拽文件的效果是一样的。

### 解决

1.首先要确定是否自动装载了 VMware Tools 虚拟 CD-ROM 映像。使用mount命令查看。结果类似如下：

>  /dev/chrom on /mnt/cdrom yupe iso9660

某些发行版上的装载点是 /media/VMware Tools 而不是 /mnt/cdrom。差不多的形式，如果有看2。如果没有，需要安装VMware Tools 工具。
[安装VMware Tools](https://docs.vmware.com/cn/VMware-Workstation-Pro/15.0/com.vmware.ws.using.doc/GUID-08BB9465-D40A-4E16-9E15-8C016CC8166F.html)

2.虚拟机设置->选项，启用共享文件夹，选择你想放置共享文件夹的路径

![share.png](https://smile-album.oss-cn-beijing.aliyuncs.com/share.PNG)

3.查看共享文件夹的内容

> cd /mnt/hgfs/

> ls

就可以看到共享文件夹里的内容了。
