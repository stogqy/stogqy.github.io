---
layout: post
title: "MAFFT序列比对图文教程 - 小白"
data:  2018-11-10
categories: Tutorials
tags:  教程 tutorial Biology
---

* content
{:toc}
## MAFFT介绍

MAFFT是一款类似于ClusterW的多重序列比对软件,想了解详细信息的可以上他们的[官网](https://mafft.cbrc.jp/alignment/software/)看看。关于多重序列比对软件的选择，想了解的童鞋可以看一下这篇文章：

Wong K M, Suchard M A, Huelsenbeck J P. Alignment uncertainty and genomic analysis. Science, 2008, 319: 473-6.

## 下载

MAFFT是全平台支持的，请根据自己的系统，到[官网](https://mafft.cbrc.jp/alignment/software/)下载对应的软件版本。我下载的是2018-08-22的win64版本：

https://mafft.cbrc.jp/alignment/software/mafft-7.409-win64-signed.zip

下载好之后解压到任何想防止的地方，我没试过中文路径有没有影响，如果想避免麻烦的话，直接放到英文路径即可。

## 使用

进入文件目录，双击`mafft.bat`文件，即可打开软件：

![img1](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181110/1.png)

**1. 载入序列**

将FASTA格式的序列复制到软件目录，然后拖到窗口即可载入序列：

![img2](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181110/2.png)

**2. 选择输出文件**

在窗口填写输出文件名，然后按enter，这个随意命名：

![img3](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181110/3.png)

**3. 选择输出格式**

有6种输出格式可选：

Output format?

  1. Clustal format / Sorted

  2. Clustal format / Input order

  3. Fasta format   / Sorted

  4. Fasta format   / Input order

  5. Phylip format  / Sorted

  6. Phylip format  / Input order

一般我们就选4好了，让它按照源文件顺序输出比对好的fasta格式文件即可。
然后会让你选择比对方式，有6种可选：

  Strategy?

  1. --auto

  2. FFT-NS-1 (fast)

  3. FFT-NS-2 (default)

  4. G-INS-i  (accurate)

  5. L-INS-i  (accurate)

  6. E-INS-i  (accurate)

如果也是跟我一样的小白，直接选1好了。
附带参数也别管了，直接确定即可。然后再按确定即可完成比对：

![img4](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181110/4.PNG)

出现类似这样的，就是跑完了：

![img5](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181110/5.PNG)

然后直接按确定退出比对，比对完成之后在软件目录我们会得到一个输出结果，我们直接把它拷到我们想要的目录即可。

**4. 绘制比对结果图**

推荐ESPript进行着色，它的网址是：

[http://espript.ibcp.fr/ESPript/cgi-bin/ESPript.cgi](http://espript.ibcp.fr/ESPript/cgi-bin/ESPript.cgi)

最好用Chrome浏览器打开，我之前用过Safari好像最后不会弹出结果窗口。

首先在Aligned Sequence处把我们的比对结果选上；

然后把二级结构的PDB文件勾上；

再点击SUBMIT即可：

![img6](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181110/6.PNG)

对了，别忘记勾选输出格式，一般我就默认，方便后续修改字体和排列啥的。
![img7](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181110/7.PNG)

然后会弹出一个窗口：

![img8](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181110/8.PNG)

点击对应的文件，就是最终的比对结果了：

![img9](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20181110/9.PNG)