---
layout: post
title: "VirtualBox一些设置"
data:  2018-11-16
categories: Tips
tags: Virtualbox SSH
---

* content
{:toc}
*本文持续更新*

## 用SSH连接Virtualbox里的Ubuntu

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