---
title: argc和argv
date: 2018-04-05 00:12:54
tags: 技术
---
基于此文章：[探究argc与argv的鱼与渔](http://mp.weixin.qq.com/s/l3WgCfgQUjv2hyuqD-BScg)

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=0 height=0   
    src="http://music.163.com/m/song?id=496774187&userid=590854430">  
</iframe> 

一、含义解读
---
- **argc:**读作arg C,是argument counter的缩写，意思是参数计数器。

- **argv:**读作arg V，是argument vector的缩写，vector是数组的意思，合起来意思是参数组成的数组。

<!--more-->
二、来源
---
- 出现在C/C++里，在`int main(int argc,char *argv[])`里。
- python中也有出现

三、用法
---
1.使用时需要用到命令行，即输入`.exe`文件，空格，参数。例如：`a.exe kk5 21ao 深度 `,内容可以随便输入。

2.具体操作：

>>>编辑代码

>>g++编译
>
>命令行运行

3.代码如下：

	#include<iostream>
	using namespace std;	
	int main(int argc,char *argv[])
	{
		cout<<"argc is: "<<argc<<endl;                 //A

		for(int i=0;i<argc;i++)
		{
			cout<<"argv["<<i<<"]="<<argv[i]<<endl;     //B
		}

	return 0;
	}

名称命名为`argc.cpp`，A输出结果为输入字符串的个数，B输出结果为每个字符串的单独显示。

四、运行过程的图片

![](http://p6hlch5jf.bkt.clouddn.com/argc_argv.png)

我用gcc编译会报错，但gcc编译c语言没问题，所以就用了g++。