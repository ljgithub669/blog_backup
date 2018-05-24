python包的安装方法
===
> 前提实在win的DOS界面下


1. 配置好python环境变量后（一般在python/Scripts这个目录下有pip这个下载工具），直接使用`pip install 包名称（比如numpy）`,如果下载不了，就要使用另一种方法。

2. 同样，安装轮子（其实是安装wheel这个工具，命令是pip install wheel）,然后去[这个网站](https://www.lfd.uci.edu/~gohlke/pythonlibs/#opencv)下载相应的.whl文件。然后把它放在刚才配置好的路径下（刚才是python/Scripts下），然后在DOS下cd进入这个目录，用` pip install opencv_python-3.4.1-cp36-cp36m-win_amd64.whl`进行安装。（这里只是举个例子）。

其他python用法介绍：
---

 安装Anaconda后，可以通过`conda create --name test_py3 python=3.6`创建一个py3.6的环境。通过`activate py3.6`切换到python3.6环境。
