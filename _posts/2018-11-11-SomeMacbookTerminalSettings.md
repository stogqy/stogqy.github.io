---
layout: post
title: "一些常用的Macbook终端设置"
data:  2018-11-11
categories: Tips
tags: Macbook Terminal 终端
---

* content
{:toc}
*本文将持续更新*

[本文引用KeithTt的博文](https://www.cnblogs.com/keithtt/)，我只是收集给自己看的，感谢分享。

## 设置终端颜色

终端的设置保留在~/.bash_profile文件中，如果没有的话，直接touch一个，把这些attach上去：

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

```

```

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

```markdown

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