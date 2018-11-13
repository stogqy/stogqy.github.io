---
layout: post
title: "一些准备小小的工作"
data:  2018-11-09
categories: Tutorials
tags:  tutorial github
---

* content
{:toc}
*一些准备工作*

## Ubuntu下使用Git

安装git：

`sudo apt install git`

生成SSH Keys：

`ssh-keygen -t rsa -C "stogqy@gmail.com"`

按照提示操作即可，默认的key保存位置是：～/.ssh

复制SSH key到Github：

复制～/.ssh/id_rsa-pub中的内容

登录github->Settings->SSH and GPG keys->New SSH key，就像这样：

![img1](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts//Pics/20181109/1.png)

测试是否成功：

`ssh -T git@github.com`

如果看到这样的，就成功了：

![img2](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181109/2.png)

Clone项目到本地：

`git clone git@github.com:stogqy/stogqy.github.io`

这就完成了远程库的克隆。然后每次更改之后先按照如下操作：

`git add .				#将所有操作都添加到暂存区`

`git commit -m "your words here"	#添加comments`

`git push				#上传操作`


![img3](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181109/3.png)

每次都快执行这些操作。

***如何插入图片***

每次插入图片都非常烦，如果仅仅是本地预览的话，我的方法是在typora的表头加入这么一句话：

`typora-root-url: ..`

然后在_posts/Pics目录下按照日期建立对应的图片文件夹，比如我现在这个是20181109，然后将图片拷贝到这个文件夹内，按照这个方法插入：

`![imgx](./Pics/20181109/y.png)	#这个x是对应的序号，y是你的文件名字，通常为了方便我都是1、2、3、4这样的序号，反正一天的也不会有太多，这样比较好找`

这样就能正确看到图片了。

但是Github博客却不能正确显示图片，非常奇怪，因此我按照这个方式把图片拷贝进目录之后，按照这个格式写图片的路径：

`https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181109/3.png`

就能看到正确的图片了，当然就是有点麻烦，每次都要拷一堆东西进来，而且本地预览的时候都需要联网加载，这也意味着如果不fetch上去的话，一开始是看不到自己的图片的，只能先本地预览，然后再转换成网址再上传，好蛋疼！