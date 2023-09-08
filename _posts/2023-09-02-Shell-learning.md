---
layout: post
title: "SHELL学习"
data:  2023-09-02
categories: Tutorials
tags:  Tutorial Coding Learning SHELL 
---

* content
{:toc}

## 基本用法

- {} () [] [[]]

{}跟python的差不多，${var}等价于$var。
()在脚本中等价于反引号，可增加代码的可读性。
方括号语句为[ "$HOME" == "$pwd" ]，注意里面的空格。在bash里面[]里面用== > 之类的似乎不用转义，但在zsh里面须用/转义。
此时用[[]]就可以不用转义直接使用 == < >等比较符。所以一般用[[]]多。

- if语句

if [条件]; then
  <do thins here>
fi

- while

while [conditions] 
do
  <do things here>
done

- for

for var in con1 con2 con3 ...
do
  <do things here>
done

for ( ( i=1; i<=$var; i=i+1 ) )
do
  <do things here>
done

- case

case $var in 
  "one" )
    <do things here>
    ;;
  "two" ) 
    <do things here>
    ;;
  "three" )
    <do things here>
    ;;
esac

### 引号

单引号不转义，里头改啥就是啥
双引号转义，可以装变量进去
反引号则执行局部代码

### 关于参数

$0  脚本本身
$1  第一个参数
$n  第n个参数
$#  参数的个数
$@  "$1" "$2" ...
$*  "$1 $2 $3 ..."
shift 参数往后滑移一位

