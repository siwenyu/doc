# nodeppt使用

一. 百度大神的作品：https://github.com/ksky521/nodePPT

二. 使用：

1. 安装：`npm install -g nodeppt`
2. 一般软件安装都可以直接运行命令，运行发现：

```
➜  bin git:(master) nodeppt start -p 8080
zsh: command not found: nodeppt
```
而切换到安装目录可以执行：

```
➜  bin git:(master) pwd
/usr/local/Cellar/node/6.3.0/libexec/npm/lib/node_modules/nodeppt/bin
➜  bin git:(master) ./nodeppt start -p 8080

```
http://172.20.130.28:8080/  窗口已经打开。

查看：
[添加软连接](https://github.com/siwenyu/doc/blob/master/fe/%E6%B7%BB%E5%8A%A0%E8%BD%AF%E8%BF%9E%E6%8E%A5.md)



编译：

* 把指定的文件指定到指定的文件夹：

```
	nodeppt generate ./demo.html ./siwen -a
```

把当前目录下的demo.html文件编译到当前路径下的siwen的文件夹中。

* 指定端口打开指定的文件夹，打开该文件夹中的html文件。

```
nodeppt start -p 8090 -d ./siwen/
```
缺点：
* 不能监控文件修改自动生产
* 只能访问html文件，htm文件会输出源码。







