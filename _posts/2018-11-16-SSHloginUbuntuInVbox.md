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

可以通过`lsb_release -a`查看版本号信息。

当然最后别忘记更新一下：

```shell
#更新软件列表
sudo apt-get update
#更新软件包
sudo apt-get upgrade
```



## SSH连接Virtualbox里的Ubuntu

1. 设置虚拟机网络连接方式为桥接模式，共享本机的活动网卡。

2. 设置本机IP和虚拟机IP在同一个网段。

   当然你也可以直接设置成DHCP自动获取。这样的话，你需要在window下面用ipconfig -all把本机和虚拟机的IP地址记下，然后再去连接，然而下次IP变了你可能又得重新改IP了，比较麻烦，所以干脆直接手动设置IP比较方便，比如：

```shell
#通过netplan设置静态IP
#sudo vim /etc/netplan/50-cloud-init.yaml
network:
    ethernets:
        enp0s3:
            addresses:
            - 10.164.210.13/16
            dhcp4: false
            gateway4: 10.164.0.1
            nameservers:
                addresses:
                - 8.8.8.8
                - 114.114.114.114
                - 202.120.2.100
                search: []
    version: 2
#将IP地址、DNS和geteway4换成自己的即可
#然后再应用一下
sudo netplan apply
```

3. 在Ubuntu中安装并启动OPENSSH：

```shell
   #安装SSH
   sudo apt install openssh-server
   #启动服务
   sudo /etc/init.d/ssh restart
```


4. 本机通过Xshell或其他软件连接Ubuntu，IP地址就是刚才虚拟机的，端口用默认的22就好了，用户名和密码按照实际情况输入即可。

WSL也可以通过这样的方式连接，只是需要一些额外的设置：
``` shell
sudo vim /etc/ssh/sshd_config
#允许用户名密码方式登录:`
#PasswordAuthentication yes`
#重启SSH`
sudo service ssh restart
```
ps. 如果xshell下路径太长可以改一下`~/.bashrc`文件中的这句话：
`PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$`，将其中的小写w改成大写即可

## SSH进阶玩法——反向SSH

**目的**

具有公网IP的机器远程SSH连接内网主机

**操作**

1. 内网主机主动连接公网主机

``` shell
# 内网主机执行
autossh -M 2222 -NfR 1111:localhost:22  -i xxx.pem username@ServerIP -p 22
# 公网主机执行该命令查看是否开始监听
ss -ant | grep 1111
```
autossh可以自动重连，防止中断，它通过本地的2222端口监听ssh信息，如果断了就会自动重连；-f：后台执行；-N：不实际连接而是port forwarding转发端口；-R：反向ssh，指定的是公网主机的1111端口，本地为22端口；-i：通过秘钥免密登录；-p：指定22端口，不加也行，默认就是22。

2. 在公网主机远程反向连接到内网主机

```shell
ssh username@localhost -p1111
```
至此就完成远程连接了。

3. 通过秘钥免密登录

虽然现在已经可以远程连接了，但是每次都需要额外输入密码，因此可以通过秘钥实现无密码访问：
```shell
#在公网主机生成秘钥
ssh-keygen -t rsa
#会询问我们放到哪里，按照所需防止即可，然后上传到公网主机
#内网主机创建authorized_keys
touch ~/.ssh/authorized_keys
#将刚才的秘钥拷贝到该文件
cat id_rsa.pub >authorized_keys
#更改权限
chmod 600 authorized_keys
#然后就可以通过key免密访问了
ssh username@localhost -p1111

```
## 搭建NFS服务

NFS 即网络文件系统（Network File-System），可以通过网络让不同机器、不同系统之间可以实现文件共享。通过 NFS，可以访问远程共享目录，就像访问本地磁盘一样。NFS 只是一种文件系统，本身并没有传输功能，是基于 RPC（远程过程调用）协议实现的，采用 C/S 架构。

1. 安装NFS软件包：

```shell
sudo apt-get install nfs-kernel-server  # 安装 NFS服务器端
sudo apt-get install nfs-common         # 安装 NFS客户端
```
2. 添加 NFS 共享目录

```shell
sudo vim /etc/exports`
# 添加/shared_folder *(rw,sync,no_root_squash)     
# * 表示允许任何网段 IP 的系统访问该 NFS 目录
sudo chmod 777 shared_folder	#将某目录设置为共享目录，其权限设置为777。
sudo chown ipual:ipual /nfsroot/ -R   # ipual 为当前用户，-R 表示递归更改该目录下所有文件
sudo /etc/init.d/nfs-kernel-server start	#启动服务
```
3. 客户机连接
```shell
sudo mount -t nfs [192.x.12.123 IP]:/shared_folder /mnt/mount_target_folder -o nolock	#在客户机中将其mount过去
```