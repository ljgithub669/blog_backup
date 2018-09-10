---
title: linux基础命令
date: 2018-04-19 12:43:53
tags: 技术
---

一、文件操作和权限管理
---
1.只有root能执行的命令，在/sbin或/usr/sbin下（sbinsuper binary）

2.所有用户：在/bin或/usr/bin下
<!--more-->
3.`drwxr-xr-x 22`

`d` 表示目录

`- `表示二进制文件

`l`表示软件链接文件link

`22` 表示硬链接个数

4.`cd`意思是change directory

5.`pwd`意思是 print working directory

6.`cp -R`可以复制目录


7.`ctrl+c`终止命令


8.`mv`移动文件、改名


9.`head -20 /etc/name` 查看前20行


10.`tail -15 /etc/name` 查看后几行


11.软链接--->类似于快捷方式图标


`ln -s /name /newname`创建软连接


12.硬链接（不能跨分区生成链接）


没有s，功能比cp强大，可以同步更新比如`ln /name /newname`

13.`ls -i`(inode)


查看文件i节点，文件唯一数字标志，但一个i节点可对应多个文件，比如硬链接  

14.权限处理命令


	chmod
	 		 u + r

     		 g - w

     		 o = x

`u`   使用者

`g`   群组

`o`   其他人

15.`chmod 755 filename`


16.`su - lijie`切换用户

17.改变文件所有者

chown 用户名 文件名

18. 添加用户

`useradd lijie`

`passwd 11111111`

19.`chgrp 用户名 文件名`改变所属组

20.设置默认权限


`umask -S（大写）`查看默认权限

更改：`umask 权限掩码`（比如025，实际是777-025=752）


二、文件查找
---

1.which 命令

查看命令的绝对路径

2.whereis 命令

可以找到文件路径和帮助文档所在位置

3.find 搜素路径 搜索关键字 文件名

`find /home -name filename`

`-name`  根据文件名查找

`\*`  匹配任意字符

`find /home -name li*`

`？` 匹配当字符

***

`find /home -name l????`

`-size` 文件大小（block数据块，512字节=0.5KB）

100M=102400KB=204800block

大于 +

小于 —

`find /home -size +100`

***
`-user` 文件所有者

`find /home -user 用户名（root）`

***

时间值

以天为单位 `ctime atime mtime`

分钟  `cmin amin mmin` 

`c`  change(文件属性被改变过）

`a`  access（被访问过）

`m`  modify(被修改过)

`find /home -mmin -120`

`-a` (and)

`-o` (or)

***

`-type` 文件类型

 `f` 二进制文件

`l` 软连接文件

`d` 目录

`find /home -type d`

`find /home -type d -o -name li???`

`find /home -type d -exec ls -l {}\;`
查看文件详细信息

删除特殊文件名：`rm -rf "a b"`

或者`find . inum 156 -exec rm {} \;`

***
locate file

`grep 关键词 路径`

***

`man` 命令（help）

`info` 命令（类似man）

`whatis ls`

三、压缩包
===

1. 命令名称：`gzip 文件名`

只能压缩文件，并且不保留原文件

2. 解压

`gunzip 文件名`

`gzip -d 文件名`

3.`tar`:把目录打包成文件

`-c` 产生.tar打包文件

`-z` 打包同时压缩

`-f` 指定压缩后的文件名

`-v` 显示详细信息

`tar -zcvf newname oldname`

`file 文件名`:查看文件属性，判断是不是压缩包

---
可压缩目录
`zip -r test.zip test(保存源文件) `

`unzip`:解压

---

`.bz2(-k保留原文件)`

压缩:`bzip2 nnew.bz2 new`

解压:`bunzip2`

---

3.`write`可通讯

	write lijie  

	这里可以直接写内容

`ctrl+d`结束

---
`wall(write all 写给所有人)`

---
`ping 192.168.137.1`

`ping -s 5220 ip`；发包

`ping -c 6(显示次数) ip`

---

shell应用

bash

`clear=ctrl+l`

`ctrl+u`(删除之前的命令)

---
命令定义别名

`alias new=old`

`alise drm="rm -rf"`

删除别名:`unalise`

---
四、输入输出重定向(0输入，1输出，2出错信息)
===

输出：`ls -l /home > /home/log`

还可以追加:`ls -l /home >> /home/log`

输入：`wall < /home/log `

---
管道（|）：将一个命令的输出传送给另一个命令，作为另一个命令的输入。

`命令1 | 命令2 | 命令n`

`ls -l /etc | more`

`ls -l /etc | grep init`

`ls -l /etc | grep init | wc -l`

---
命令连接符；

`ls;date;pwd`

逻辑与

	命令1 && 命令2

	 √		  √

	 ×		  ×

`ls && pwd`

逻辑或（类似非）  ||

	命令1 || 命令2

	 ×		  √

	 √		  ×

---

命令替换符： 命令1 \`命令2\`

将一个命令的输出作为另一个命令的参数

ls -l \`which touch\`


---
















