---
layout: post
title:  "ubunut下翻墙（亲测有效）"
date:   2019-10-30 15:58:54
categories: ubuntu
tags: 翻墙
---

* content
{:toc}

## 前言

最近准备开始科研，发现ubuntu系统竟然不能使用google，感觉很不方便，上网搜索翻墙资料，实践了很多都不可行
。最后终于能使用google,记录一下。






### 客户端安装过程 



#### windows系统

1.下载shadowsocksR客户端

链接：https://pan.baidu.com/s/1XvtLCKaM25iI1b3hRa_3iA 
提取码：yzv7 
复制这段内容后打开百度网盘手机App，操作更方便哦

2。解压后，启动shadowsocksR，设置相应参数。设置完毕后，就可翻墙，使用chrome浏览器即可翻墙，


#### ubuntu系统


1.下载shadowsocksR客户端


需提前下好git


```js
wget https://onlyless.github.io/ssr

sudo mv ssr /usr/local/bin

sudo chmod 766 /usr/local/bin/ssr

ssr install

ssr config
```


2.修改config.json文件，修改对应的参数


```js
{
    "server": "0.0.0.0",
    "server_ipv6": "::",
    "server_port": 8388,
    "local_address": "127.0.0.1",
    "local_port": 1080,

    "password": "m",
    "method": "aes-128-ctr",
    "protocol": "auth_aes128_md5",
    "protocol_param": "",
    "obfs": "tls1.2_ticket_auth_compatible",
    "obfs_param": "",
    "speed_limit_per_con": 0,
    "speed_limit_per_user": 0,

    "additional_ports" : {}, // only works under multi-user mode
    "additional_ports_only" : false, // only works under multi-user mode
    "timeout": 120,
    "udp_timeout": 60,
    "dns_ipv6": false,
    "connect_verbose_info": 0,
    "redirect": "",
    "fast_open": false
}

```


3.启动ssr

> sudo ssr start


4.设置火狐浏览器
首选项 → 常规 → 网络代理设置 → 设置」中选择「手动代理配置」，然后填入你的本地监听的p和端口，以及选择 SOCKS5。
设置完成后，访问google，正常访问。


