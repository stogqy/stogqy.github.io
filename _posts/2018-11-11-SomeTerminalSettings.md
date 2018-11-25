---
layout: post
title: "一些常用的终端设置"
data:  2018-11-11
categories: Tips
tags: Terminal
---

* content
{:toc}
*本文将持续更新*

[本文引用KeithTt的博文](https://www.cnblogs.com/keithtt/)，我只是收集给自己看的，感谢分享。

## 设置终端颜色

Mac终端的设置保留在~/.bash_profile文件中，如果没有的话，直接touch一个，把这些attach上去：

```shell
#enables colorin the terminal bash shell export
export CLICOLOR=1

#sets up thecolor scheme for list export
export LSCOLORS=gxfxcxdxbxegedabagacad

#sets up theprompt color (currently a green similar to linux terminal)
export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;36m\]\w\[\033[00m\]\$ '

#enables colorfor iTerm
export TERM=xterm-color
```

完成后载入配置：

```shell
$ source .bash_profile
```

其中LSCOLORS的意义为：

```shell
a       black
b       red
c       green
d       brown
e       blue
f       magenta
g       cyan
h       light grey
A       bold black, usually shows up as dark grey
B       bold red
C       bold green
D       bold brown, usually shows up as yellow
E       bold blue
F       bold magenta
G       bold cyan
H       bold light grey; looks like bright white
x       default foreground or background

文件类型：
1. directory
2. symbolic link
3. socket
4. pipe
5. executable
6. block special
7. character special
8. executable with setuid bit set
9. executable with setgid bit set
10. directory writable to others, with sticky bit
11. directory writable to others, without sticky

```

## 设置alias

Mac的终端是没带一些常用的alias命令的，可以把这些照例添加的终端的配置文件~/.bashrc_profile中：

```shell
#some alias
alias ll = "ls -lG"
alias la = "ls -a"
```

## 设置vim语法高亮

vim的配置文件在~/.vimrc中：

```shell
syntax on
set ruler
```

## 设置tab智能补全

终端自带的tab补全比较严格，大小写，空格之类常见的都不能有。这些保存在~/.inputrc文件中：

```shell
set completion-ignore-case on
set show-all-if-ambiguous on
TAB: menu-complete
```

不仅要source，可能还需要重启终端。

## 让终端显示行号

在.vimrc中插入`set number`然后`source ~/.vimrc`即可。

## 设置代码自动补全

需要保证你的Vim版本大于7.3584。

### 安装Vundle

首先在`~`目录下创建`.vimrc`文件，如果有则无视。

然后用git把Vundle克隆下来：

```shell
$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

将以下内容保存到`.vimrc`文件:

```shell
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
 
set nocompatible              " be iMproved, required
filetype off                  " required
"设置Vundle的运行路径并初始化
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" Vundle安装位置与插件路径不同时，需要Vundle插件的路径
"call vundle#begin('~/some/path/here')
"------------------要安装的插件不能写在此行前！------------------
 
"Vundle对自己的调用，不可删去
Plugin 'VundleVim/Vundle.vim'
"以下是所支持的各种不同格式的示例
"需要安装的插件应写在调用的vundle#begin和vundle#end之间
"如果插件托管在Github上，写在下方，只写作者名/项目名就行了
 
Plugin 'Valloric/YouCompleteMe'
Plugin 'majutsushi/tagbar'
Plugin 'vim-syntastic/syntastic'
Plugin 'vim-airline/vim-airline-themes'
Plugin 'vim-airline/vim-airline'
 
"如果插件来自vim-scripts(官方)，写插件名就行了
" Plugin 'L9'
 
"如果Git仓库不在Github上，需要提供完整的链接
" Plugin 'git://git.wincent.com/command-t.git'
 
"本地的插件需要提供文件路径
" Plugin 'file:///home/gmarik/path/to/plugin'
"一定要确保插件就在提供路径的文件夹中(没有子文件夹，直接在这层目录下)
"运行时目录的路径
"Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
"避免插件间的命名冲突
"Plugin 'ascenator/L9', {'name': 'newL9'}
"------------------要安装的插件不能写在此行后！------------------
call vundle#end()            " required
filetype plugin indent on    " required
"要忽略插件缩进更改，请改用：
"filetype plugin on
"
" 安装插件的相关指令
":PluginList			- 列出已安装插件
":PluginInstall			- 安装新添加的插件;添加`!`或使用`:PluginUpdate`来更新已安装插件
":PluginSearch xxx		- 寻找名字带有xxx的插件;添加`!`刷新本地缓存
":PluginClean			- 删除已经从列表移除的插件;添加`!`静默卸载
":h						- 帮助和说明文档 
"Vundle的设置到此为止了
"
"该配置文件来自_YingCao的博客，感谢分享，原文内容在：https://blog.csdn.net/qq_33505303/
```

最后在vim中执行`:PluginInstall`即可，这步会有点漫长，推荐去看篇文献或者去吃个饭。

### 安装YouCompleteMe插件

#### ubuntu

首先安装cmake和python头文件：

```shell
sudo apt install cmake
sudo apt install python3-dev
#更新一下，安装essential
sudo apt update
sudo apt install -y build-essential
```

然后`cd ~/.vim/bundle/YouCompleteMe`进行安装：

```shell
python3 install.py --clang-completer
```

这个过程大概十几分钟，具体根据网速而定。

#### CentOS

突发奇想在阿里云买了三个月的主机玩玩，结果登上去发现带的Vim是7.4的不支持YCM，于是开始更新Vim：

```shell
# 卸载老版本
yum remove vim -y
#安装ncurses
yum -y install ncurses-devel.x86_64
#安装git
yum -y install git
#克隆vim下来
git clone https://github.com/vim/vim.git
#安装vim
cd vim/src
make
make install
#添加路径
vi /etc/profiled.d/path.sh
---
#!/bin/bash
export PATH=$PATH:/usr/local/bin/vim
---
source /etc/profiled.d/path.sh
```

然后按之前ubuntu类似的操作修改`.vimrc`文件下载YCM等等。

但是在编译安装YCM的时候我又遇到了编译器的问题，尼玛！于是：

```shell
yum install -y python36-devel.x86_64
 yum install -y gcc gcc-c++ ncurses-devel bison
```

然后再:

```shell
python36 install.py --clang-completer
```

还是不行，提示：

YouCompleteMe unavailable: requires Vim compiled with Python (2.7.1 or 3.4 )

然后`vim -v | grep python`一看，原来这个版本的vim不支持python，得了换个能兼容的版本吧：

```shell
#先看看系统内的vim，能卸载的全给卸载了
rpm -qa | grep vim
#xxxx是你看到的vim
sudo rpm -e xxxxx
#获取vim源码
wget ftp://ftp.vim.org/pub/vim/unix/vim-8.1.tar.bz2
#解压
tar -xjf vim-8.1.tar.bz2
cd vim81
#安装
./configure --enable-multibyte --enable-rubyinterp=yes --enable-pythoninterp=yes --enable-python3interp=yes
#这里我遇到了一些问题，chmod +x configure可解决
make
make install
```

然后再`vim -v | grep python`看看，这下显示能兼容python3了，但是我的`/usr/local/bin`目录里头没有python3，只有python、python36之类的，不过既然它只要求python3，那么我们直接软连接一个好了：

```shell
ln -s /usr/local/bin/python36 /usr/local/bin/python3
```

然后重新执行`python36 install.py --clang-completer`，顺利通过。

