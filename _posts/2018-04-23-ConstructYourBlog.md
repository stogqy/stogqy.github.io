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
## 1. 注册并登陆刚才github

到[这里](https://www.github.com)注册一个github账号，然后登陆，你将会看到这个界面：

  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-1.png)
  看到右下角的用红色方框选中的 Your repositories 选项卡，这时候你的repositories应该显示为0，因为我已经建立了两个所以显示是2。这个repositories就是仓库的意思，你可以建立多个仓库，然后把你自己的项目存放到这个仓库里头。我们可以直接建立我们自己的仓库来存放博客文件，当然这里有个更加简便的方法，那就是拷贝别人的模板。
## 2. fork一个别人建立好的模板
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
## 3. 设置仓库
  上一步我们已经fork别人的仓库到了我明自己名下，但是这时候我们还不能直接使用，因为github pages默认的博客入口是『  **注册名.github.io**』，因此我们需要设置一下这个仓库名，将它改成我们自己的仓库，点击上图中的 settings ，进入设置页面：
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-6.png)
  将对话框中的仓库名改成我们自己的名称，比如我的注册名是stogqy，那么我应该填写 stogqy.github.io。
  继续往下拉，进入 github pages 设置：
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-7.png)
  这个下拉框中将source改为master branch，然后点击save，就完成了仓库设置。
  这时候，输入网址『  **注册名.github.io**』就能进入我们的博客了。
## 4. 修改并更新博客/
  我们fork到的只是别人的博客，里面的内容都是别人的，因此我们需要通过 github desktop 将其同步到本地进行修改，然后再将修改文件同步回仓库。

通过github desktop将仓库同步下来后，可以看到我们的项目结构：
  ![](https://raw.githubusercontent.com/stogqy/stogqy.github.io/master/_posts/Pics/20180423/20180423-8.png)
- 『favicon.ico』为网站的图标，当我们将博客降入收藏夹时，可以看得到一个图标，我们可以用ps或ai自己设计一个，保存为png格式，然后重新命名为.ico后缀即可
- 『\_config.yml』为配置文件，其中保存着我们的博客配置信息，打开后我们可以看到：

``` hxml
# Welcome to Jekyll!
#
# This config file is meant for settings that affect your whole blog, values
# which you are expected to set up once and rarely need to edit after that.
# For technical reasons, this file is *NOT* reloaded automatically when you use
# 'jekyll serve'. If you change this file, please restart the server process.

# Site settings
title: STOGQY | Bio
brief-intro: 「欢迎访问」
baseurl: "" # the subpath of your site, e.g. /blog
url: "https://stogqy.github.io" # the base hostname & protocol for your site

permalink: /:year/:month/:day/:title/

# other links
#twitter_username: gaohaoyang126
#facebook_username: gaohaoyang.water
github_username:  STOGQY
email: STOGQQ@GMAIL.COM
#weibo_username: 3115521wh
#zhihu_username: gaohaoyang
#linkedIn_username: gaohaoyang
#dribbble_username:

description_footer: 本站记录我生物学习之旅！

# comments
# two ways to comment, only choose one, and use your own short name
# 两种评论插件，选一个就好了，使用自己的 short_name
#duoshuo_shortname: #STOGQY
#disqus_shortname: STOGQY

# statistic analysis 统计代码
# 百度统计 id，将统计代码替换为自己的百度统计id，即
# hm.src = "//hm.baidu.com/hm.js?xxxxxxxxxxxx";
# xxxxx字符串
#baidu_tongji_id: cf8506e0ef223e57ff6239944e5d46a4
#google_analytics_id: UA-72449510-4 # google 分析追踪id

# Build settings
markdown: kramdown

kramdown:
  input: GFM
  syntax_highlighter: rouge

# port
# port: 1234

# url
category_dir: category/
tag_dir: tag/

# excerpt
excerpt_separator: "\n\n\n\n"

# paginate
gems: [jekyll-paginate]
paginate: 6
```

按照自己的需求更改成自己的信息即可。

- 『\_posts』文件夹中存放的是我们的博文，我们通过添加markdown文件到这个文件夹即可更新博客。更新博文后，通过github desktop同步到我们的仓库，即可完成更新。

## 5. 更多使用技巧
  待补充










