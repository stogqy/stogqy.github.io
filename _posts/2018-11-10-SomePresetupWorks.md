---
layout: post
title: "快速github pages搭建个人博客 —— 新手向"
data: 2018-11-10
categories: Tutorials
tags:  教程 tutorial github
---
* content
{:toc}
*一些准备工作*

## Ubuntu下使用Git

安装git：

`sudo apt install git`

生成SSH Keys：

`ssh-keygen -t rsa -C "stogqy@gmail.com"`

​	按照提示操作即可，默认的key保存位置是：～/.ssh

复制SSH key到Github：

复制～/.ssh/id_rsa-pub中的内容

登录github->Settings->SSH and GPG keys->New SSH key，就像这样：

![](Pics/2018-11-10 01-05-20屏幕截图.png)

测试是否成功：

`ssh -T git@github.com`

如果看到这样的，就成功了：

![](Pics/2018-11-10 01-08-36屏幕截图.png)

Clone项目到本地：

`git clone git@github.com:stogqy/stogqy.github.io`

这就完成了。

