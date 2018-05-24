---
title: gcc编译连接
date: 2018-03-23 20:08:57
tags: 技术
---
在Windows的DOS下实现gcc编译和链接
---
这里主要看的是两篇写的很详细的文章

<!--more-->

[C语言多文件编译初探（一）](https://blog.csdn.net/candcplusplus/article/details/7317472)

[C语言多文件编译初探（二）](https://blog.csdn.net/candcplusplus/article/details/53326368)
***
1.首先，你的Windows电脑的编译器需要是gcc,不清楚的话按`win+r`,输入cmd，打开DOS命令行界面。然后输入`gcc -v`,这个是用来查看你gcc版本的，如果提示不是内部或外部指令，则你的编译器不是gcc。反之，如果出现如下图片，则可以进行下一步了。
![图片](http://p6hlch5jf.bkt.clouddn.com/gcc.png)

---
2.如果没有gcc，可以通过下载Dev-C++,使用其bin下的gcc.exe。在环境变量中配置Dev_C++下的bin。

![Dev_C++](http://p6hlch5jf.bkt.clouddn.com/dev.png)

3.此时就可以在DOS中使用gcc了。gcc可以将c/c++文件编译为.o文件，然后链接生成可执行文件.exe。
4.接下来我们写两个源文件，一个头文件，用来模拟多文件编译过程。
	
	//创建一个main.c文件
	#include<stdio.h>
	int main()
	{
	fun();
	return 0;
	}


--

	//创建一个fun.c文件,用来创建函数	
	#include<stdio.h>
	void fun()
	{
	int a=3,b=6;
	printf("%d+%d=%d",a,b,a+b);	
	}

--

	//创建一个fun.h文件，用来声明fun()这个函数
	//这个就很简单
	void fun();
5.接下来就到关键时刻了，先生成.o文件，命令是`gcc -c fun.c main.c`,前面`-c`是指只执行编译这一步，如果没有，就会直接生成.exe
文件。这里是为了便于理解。执行完这一步，会发现源代码文件夹下有`fun.o和main.o`这两个文件，这就是目标文件，即二进制文件。下一步链接就需要这两个目标文件。

6.链接命令是`gcc fun.o main.o`,这个默认生成的.exe文件是a.exe,如果觉得这样的名字不好，可以自己命名，只需要在后面加个-o name.exe即可。例如`gcc fun.o main.o -o mine.exe`,执行完后源代码目录下就会有.exe文件生产。最终所有文件如下：

![](http://p6hlch5jf.bkt.clouddn.com/list.png)

* **以上就是gcc编译链接多文件的流程**

---