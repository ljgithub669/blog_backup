---
title: C/C++及Python的自定义引包
date: 2018-04-14 21:09:57
tags: 技术
---
一、C/C++的自定义头文件引用
===
* 为什么要写这篇文章呢？
 
> 当我们用C/C++写程序时，头文件引用每次都会用到`#include <stdio.h>`或`#include <iostream>`，并且这个头文件还放在编译软件内部，需要自己去找，一般放在include包含头文件的地方。

<!--more-->

这里简单进行举例，比如vc6.0中上面两个头文件的位置
![stdio.h](http://p6hlch5jf.bkt.clouddn.com/vc_stdio.h.png)

都在include文件下
![](http://p6hlch5jf.bkt.clouddn.com/vc_iostream.png)

而Dev_C++的不在一起

![stdio.h](http://p6hlch5jf.bkt.clouddn.com/dev_stdio.h.png)

![iostream](http://p6hlch5jf.bkt.clouddn.com/dev_iostream.png)

以下以Dev_C++为例，因为它的编译器是gcc和g++，使用较为方便

![这是头文件的代码，挺多的](http://p6hlch5jf.bkt.clouddn.com/stdio_code.png)
`这是头文件的代码，挺多的`

* 需要了解多文件编译链接的话，可以看看我的这篇博客[gcc编译链接](https://ljgithub669.github.io/2018/03/23/gcc%E7%BC%96%E8%AF%91%E9%93%BE%E6%8E%A5/)

**好了，现在开始进入正题：**

1.一般一个功能模块都是用`name.h`和`name.c`两个文件来完成的，.h文件中写函数声明和定义，.c文件中写函数的主体。调用时只需要include头文件即可。自定义头文件的话，我们可以把函数主体和定义声明写在同一个.h文件里。（开始我也好奇既然可以写在一个文件里，那为什么要分开写呢？原来当一个工程项目很大是，出现错误时可以更精准的定位，便于维护）。

2.首先我们写一个头文件`fun.h`

		#include <stdio.h>
	
		int fun();    //进行函数声明
		int fun()     //函数主体.
		{
			printf("Your first head file.\n");
			printf("Bye!");
		}

3.然后再写个主函数main.c

		#include <stdio.h>
		#include "fun.h"
		int main()
		{
			fun();     //调用定义的函数
			printf("Just do it!\n");
			return 0;
		}

4.我们把这个`fun.h`放在和`stdio.h`相同的路径下，不就可以随时在机器上使用这个头文件了吗。
将代码粘贴到include路径下，如下：

![](http://p6hlch5jf.bkt.clouddn.com/fun.h.png)

然后在DOS下cd进入main.c所在文件夹，gcc进行编译（这里提示一下，gcc编译经常会出现报错，解决方法是在最后一行加上空格，其实就是报错的原因，仔细看能看懂）

![](http://p6hlch5jf.bkt.clouddn.com/gcc_zidingyi_.h_.png)
运行a.exe
![](http://p6hlch5jf.bkt.clouddn.com/gcc_run_.h_.png)
以为预处理命令要在include文件夹下找一遍，直到发现fun.h，所以运行时有些慢

* **后期可以随便发挥**

二、Python自定义引包`import package_name`
===

1.其实原理和C/C++一样，就是有些地方不同

我们来写一个自己的python包，结构是这样的

	---package
		---__init__.py
		dog
			---__init__.py
			---module1.py
			---module2.py
		cat
			---__init__.py
			---module1.py
			---module2.py			

这个结构的意思是：我们创建了一个包名称`package`，也就是一个文件夹，在文件夹内，分别有`---__init__.py`,`dog`,`cat`这三个文件，`cat`和`dog`下又分别有`---__init__.py`,`---module1.py`,`---module2.py`这三个文件，也就是我们的函数代码。

关于`---__init__.py`存在的意义，请自行谷歌，那里有更专业的回答。

![](http://p6hlch5jf.bkt.clouddn.com/python_import.png)
这是存储的内容

2.接下来把这个`package`放到python下的Lib/site-packages里即可。

3.写一个python的main.py进行调用，我们需要这样引入`from package.dog.module1 import fun1`,main.py代码如下：

		from package.dog.module1 import fun1
		fun1

这样即可，python就是十分简短，需要引用其他module可以自行引入。

4.接下来实际展示，感兴趣的话可以自己操作。

![](http://p6hlch5jf.bkt.clouddn.com/python_run.png)
		