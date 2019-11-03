# linux bash

### 1、什么是shell

	定义：在计算机中，shell俗称壳，是为使用者提供操作界面的软件。类似于DOS环境下的cmd
	bash:Bourne Again shell,大多数Linux都以bash作为缺省的shell，运行sh时，其实调用的是bash
	登陆环境中：普通用户命令行显示$,root用户显示#，su命令切换到root用户
	~代表用户的home目录；cd 切换目录
	几个简单的命令：date：显示当前日期时间
	               cal:calendar显示日历
	               df:disk free 显示linux磁盘使用情况；df -h  可读，易读的
	               free:显示内存使用情况；加上-h：human代表人类可读的格式
	               exit:退出当前连接
### 2、文件系统中跳转
+ pwd
	
	print working directory:打印当前工作路径
+ ls
	
	list:后面加目录可以查看此目录下的所有文件  -a显示所有文件，.开头的文件是隐藏文件
+ cd

	change directory:切换目录
	cd 相对路径和绝对路径：
	1.绝对路径：路径的写法一定由根目录/写起，如/usr/share/doc这个目录
	2.相对路径：路径的写法不是由/写起，由/usr/share到/usr/share/doc 输入：cd doc/
				/usr/share/doc切换到/usr/share/man 输入 cd ../man  ..返回上层目录
	cd命令的快捷操作方式：cd 切换家目录   cd -上个命令目录  cd ~等同cd 回到家目录 cd ~username
	切换到username的家目录   cd ..上层目录
	
### 3、探索操作系统

#### 3.1 ls命令

* ls    
* ls /usr/    
* ls -l /usr

command命令     -options选项参数     arguments文件名或目录名称

short options :-a

long options :--all

short options combine :-al  ==> -a -l

* ls command options:
 + -a , --all 列出目录下的所有内容，包括隐藏的
 + -d , --directory 只列出目录的信息，不列出目录里的文件信息
 + -F ，--classify 文件或目录名字后加一个字符的分类标识
 + -h , --human-readable 可读的格式
 + -l ,(long)长格式输出
 + -r ,--reverse  反序输出，默认正序a--z
 + -t ,--time 按修改日期排序
* ls long format

drwxr-xr-x. 243 root root  8192 1月  15 2019 share   为例
 + d  first character (d,目录 -文件 |链接)
 + 1 group owner user 2 group owner group 3 group all user
   
   r--   read   w-- write   x-- excute
 + 243  链接个数
 + root  owner user
 + root  owner group
 + 8192  byte size
 + 1月 15 2019 文件创建时间或者最后修改时间
 + share  文件名

#### 3.2 file命令

file:观察文件类型，file filename 来查看文件是属于ASCII或者是数据文件或是二进制文件，
或者有没有使用到动态链接库等信息。

**在windows操作系统中，是利用文件的后缀名来判断文件的类型，例如.png是图片文件；linux系统的文件
类型与后缀名无关。**

#### 3.3 less命令
less:对文件或其他输出进行**分页显示**的工具，是linux正统查看文件内容的命令，功能极其强大；less
的用法比more更加弹性，用more查看文件内容的时候，只能向后翻页，不能向前翻；使用less后，不仅可以向后
翻页，还可以向前翻页，更利用浏览一个文件的内容。而且less里/搜索词，可以实现文件内搜索，n/N向前向后显示。
#### 3.4 浏览linux根目录	
ls l- / ---->显示linux根目录
+ bin:命令文件目录,包含了供管理员和普通用户使用的重要的linux命令和二进制可执行文件 -->/usr/nin
+ boot:存放系统的内核文件及引导装载程序文件
+ 

	
	
	
	
	