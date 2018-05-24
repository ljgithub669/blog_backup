---
title: make命令用法
date: 2018-04-22 23:50:50
tags: 技术
---
1.使用make命令需要条件：同一个文件夹下多个.c文件和一个makefile文件，如图：
![](http://p6hlch5jf.bkt.clouddn.com/make_list1.png)
<!--more-->

2.各个文件内容如下图：
![](http://p6hlch5jf.bkt.clouddn.com/make_file.png)

3.主要是makefile的内容

		name ： file1.o filee2.o
			gcc -o name file1.o file2.o

其中name自己可以随便取。

4.具体执行过程：直接敲`make`即可，如图
![](http://p6hlch5jf.bkt.clouddn.com/make_make1.png)

5.然后文件夹下会生成一个名为main的可执行文件，敲`./main`即可运行，如图
![](http://p6hlch5jf.bkt.clouddn.com/make_run1.png)