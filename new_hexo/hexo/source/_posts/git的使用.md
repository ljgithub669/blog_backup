---
title: git的使用
date: 2018-05-17 18:43:13
tags: 技术
---
一、内容简介
===
![](https://assets-cdn.github.com/images/modules/logos_page/Octocat.png)
<!--more-->
1. 在github上申请一个账号，包括**用户名**和**邮箱**，这是我们信息存储的最主要标识，一定要记住，后面会多次用到。
2. 我们申请的账号下，可以建立很多仓库，用来存放我们的文件。`git`的方便之处就在于可以轻松在不同仓库之间切换。
3. 本地电脑连接远程仓库（也就是网上的代码），需要通过ssh登录来实现，原理就是在本地电脑上输入`ssh-keygen -t rsa -C "642746796@qq.com"`（引号之内填你的邮箱），然后会生成一串公钥密文，在`~/ssh/`文件夹下，默认有`id_rsa`和`id_rsa.pub`这两个文件，打开后者，复制全部内容，然后去github官网上打开你的账户，把公钥粘贴进去。这样，本地电脑和远程仓库就形成了一一对应关系，本地上修改内容后，就可以通过`git push`来更新远程仓库，从而更新。

二、实际操作
===
1. 打开`git bash`，输入git账号信息，分别是`git config --global user.name "ljgithub669"`和`git config --global user.email "642746796@qq.com"`。然后输入`git config user.name`和`git config user.email`可以查看当前本地账户信息，也就是你刚才配置的信息。
2. 用`ssh -T git@github.com`测试连接情况。

这是我的电脑显示的情况，如果不一样，出现其他情况则输入yes
![](http://p6hlch5jf.bkt.clouddn.com/git_connect.png)
3. 接下来就很简单，只需要三步

- git add .

- git commit -m "描述"

- git push

以上三步都是在`git clone`的文件夹下进行的。其中`git add`也可以指定添加文件，例如`git add newfile`。

可以通过`git status`和`git log`来查看代码更改情况

三、踩过的坑
==
1.之前第一次尝试没有问题，很顺利。之后又申请了一个github账号，然后准备用两个账号熟悉一下git的使用，主要是学习git request的使用，然后就悲哀了，两个账号在切换的时候就出现了问题，显示一个账号禁止另一个账号进行`push`。

很久了，不知道怎么解决，直到看到一篇文章，还有**凭据**这个东西，需要注销第一个账号才能登陆第二个。我的电脑（win10）中的位置是：**控制面板--->用户账户--->凭据管理器**,在下面删除第一个github账号就可以顺利登陆第二个了。

这里有图
![](http://p6hlch5jf.bkt.clouddn.com/git_ping_ju.png)

2.之前不知道，一个git账号下可以有很多仓库，每个仓库独立，更改时只需要将其`git clone`到本地即可，然后本地更改后push就可以了。




---
* 相关链接[git常用命令](https://cnbin.github.io/blog/2015/05/30/git-ming-ling-da-quan/)