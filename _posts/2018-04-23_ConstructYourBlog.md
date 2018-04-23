---
layout: post
title: "快速github pages搭建个人博客 —— 新手向"
data: 2018-04-23
categories: Tutorials
tags:  教程 tutorial github
---
* content
{:toc}

*本教程将持续更新*
## 1. 注册github
  网址：www.github.com
## 2. 登陆刚才注册好的账户，你应该看到如下页面
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-1.png)
  看到右下角的用红色方框选中的 Your repositories 选项卡，这时候你的repositories应该显示为0，因为我已经建立了两个所以显示是2。这个repositories就是仓库的意思，你可以建立多个仓库，然后把你自己的项目存放到这个仓库里头。我们可以直接建立我们自己的仓库来存放博客文件，当然这里有个更加简便的方法，那就是拷贝别人的模板。
## 3. fork一个别人建立好的模板
  我们使用的是jekyll生成我们的博客，这个类似于WordPress，但是jekyll使用起来更加简单，我们可以通过markdown文件来更新我们的博客。
  访问这个[网站](http://jekyllthemes.org)可以获取超多的模板。
  另一个更加简单的方法就是，当你浏览别人的博客时，如果看到好用的模板，直接『借用』过来即可。比如我看到HyG的这个博客，我感觉还可以：
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-2.png)
  那么我可以直接进入他的github，找到他这个博客所在仓库，然后复制到我们刚才建立好的自己的仓库即可。要找到他的博客仓库很简单，我们上面建立博客仓库的时候知道，github pages所在仓库的名字就是『注册名.github.io』，那么我们直接访问『github.com/注册名』就是了。
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-3.png)
  我们点击红框里面的仓库名，就可以看到他的博客源文件了：
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-4.png)
  点击红框李的fork，就将它保存到了我们的用户名下：
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-5.png)
## 4. 设置仓库
  上一步我们已经fork别人的仓库到了我明自己名下，但是这时候我们还不能直接使用，因为github pages默认的博客入口是『  **注册名.github.io**』，因此我们需要设置一下这个仓库名，将它改成我们自己的仓库，点击上图中的 settings ，进入设置页面：
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-6.png)
  将对话框中的仓库名改成我们自己的名称，比如我的注册名是stogqy，那么我应该填写 stogqy.github.io。
  继续往下拉，进入 github pages 设置：
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-7.png)
  这个下拉框中将source改为master branch，然后点击save，就完成了仓库设置。
  这时候，输入网址『  **注册名.github.io**』就能进入我们的博客了。
## 5. 修改并更新博客
  我们fork到的只是别人的博客，里面的内容都是别人的，因此我们需要通过 github desktop 将其同步到本地进行修改，然后再将修改文件同步回仓库。"_posts"文件夹中存放的是我们的博文，我们通过添加markdown文件到这个文件夹即可更新博客。
## 6. 更多使用技巧
  待补充














