---
layout: post
title: "一些准备小小的工作"
data: 2018-11-10
categories: Tutorials
tags:  教程 tutorial github
typora-root-url: Pics/
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

![img](20181110/1.png)

测试是否成功：

`ssh -T git@github.com`

如果看到这样的，就成功了：

![img](20181110/2.png)

Clone项目到本地：

`git clone git@github.com:stogqy/stogqy.github.io`

这就完成了远程库的克隆。然后每次更改之后先按照如下操作：

`git add .			#将所有操作都添加到暂存区`

`git commit -m "your words here"	#添加comments`

`git push						#上传操作`


![img](20181110/3.png)

每次先