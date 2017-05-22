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

* 原因是：通常在局部安装了某个Terminal程序之后，此时程序可能在某个ruby gem的bin目录下，或者Application下（如：sublime），需要我们创建一个指向这个地址软链接，可以方便的访问它。

* Terminal访问程序原理：
Linux环境下通常我们将Terminal可访问的程序放在/bin, /usr/bin, /usr/local/bin，有时也会放在~/bin目录下。

* load过程：

	1. Terminal打开时当前user默认的shell会去读取自己的配置文件，一般在~目录下；
	2. 这个配置文件会去export上述几个路径，读取*/bin下的可执行文件；
	3. */bin下的可执行文件通常情况下是指向某个路径下的软链接（可以使用ln -s创建）；

基于上面的过程，我们在Terminal中访问得到command not found的具体原因可能如下：

* 当前调用的命令确实没有安装；
* 当前命令安装了，但是没有创建软链接到*/bin；
* 当前命令已创建软链接到*/bin，但是所在*/bin路径没有被export；

配置软链接：	

找到：文件~/.zshrc：

```
export PATH="/usr/bin:/bin:/usr/sbin:/sbin:$PATH"
```
添加：
export PATH="/usr/bin:/bin:/usr/sbin:/sbin:$PATH"













