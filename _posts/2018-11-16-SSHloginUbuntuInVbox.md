---
layout: post
title: "VirtualBox一些设置"
data:  2018-11-16
categories: Tips
tags: Virtualbox SSH
---

* content
{:toc}
*本文持续更新*'

## 把Ubuntu默认更新源更改为阿里源
Ubuntu存放更新源的信息位于`etc/apt/sources.list`文件，因此我们只需要修改该文件即可。

首先备份一下源文件：

```shell
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak.2018_11_17
```
然后用vim添加下列信息进去：
```shell
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
```
里面的bionic是ubuntu的版本号信息，我装的是18.04，版本号就是bionic。

> 可以通过`lsb_release -a`查看版本号信息。

## SSH连接Virtualbox里的Ubuntu

1. 设置虚拟机网络连接方式为桥接模式，共享本机的活动网卡

2. 设置本机IP和虚拟机IP在同一个网段。

   当然你也可以直接设置成DHCP自动获取。这样的话，你需要在window下面用ipconfig -all把本机和虚拟机的IP地址记下，然后再去连接，然而下次IP变了你可能又得重新改IP了，比较麻烦，所以干脆直接手动设置IP比较方便。

3. 在Ubuntu中安装并启动OPENSSH：

   ```shell
   #安装SSH
   sudo apt install openssh-server
   #启动服务
   sudo /etc/init.d/ssh restart
   ```

4. 本机通过Xshell或其他软件连接Ubuntu，IP地址就是刚才虚拟机的，端口用默认的22就好了，用户名和密码按照实际情况输入即可。