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
+ dev:设备文件目录，存放linux系统下的设备文件，访问该目录下文件，相当于访问某个设备
+ etc:存放系统配置文件
+ home:用户的家目录，新建用户时，该用户的宿主目录存放在这里
+ lib  lib64:系统使用的函数库的目录，相当于windows的dll文件库
+ media ：自动挂载的目录，如U盘插入会自动挂载，会在/media目录下生成一个目录
+ mnt :被系统管理员使用，手动挂载一些临时媒体设备的目录
+ opt :存放安装系统后用户安装的可选的应用软件
+ proc :系统进程目录
+ root :root用户的家目录
+ run :?
+ srv :服务启动后需要访问的数据目录，如www服务需要访问的网页数据存放在/srv/www内
+ tmp :临时存放文件的目录，任何人都可以访问，重要文件不存放在此目录
+ sys :?
+ usr :应用程序存放目录
+ var :存放系统执行过程中经常变化的文件，如/var/log
### 4、操作文件和目录
wildchar:通配符
* ‘*’ ：0，1，more char
* ?   : 1 char
* [character] :one char in set
* [!character]:not one char in set
* [[:class:]]:one char in class 
 + [:digit:]:number
 + [:lower:]:lower char
 + [:upper:]:upper char
 + [:alnum:]:num+alpha
 + [:alpha:]:lower and upper
#### 4.1 mkdir
 mkdir:make directory 创建目录
 
 语法：mkdir dir1  或者mkdir dir1 dir2 dir3
#### 4.2 cp
 cp:copy  复制
 
 语法：cp item1 item2   复制文件item1到目录item2
 
      cp item1... item2   复制item1..等文件到目录item1
      
参数：
* -a:--archive
* -i:--intercative   交互式的，若目标文件已存在，复制时会询问是否覆盖
* -r:--reccursive    递归
* -u:--update        更新
* -v:--verbose       显示详细信息
#### 4.3 mv
mv:move  移动/重命名文件

语法：mv item1 item2   重命名        mv item1... directory 移动item1...到目录directory
* -i:intercative  交互式
* -r:递归
* -v:显示详细信息
#### 4.4 rm
rm:remove  删除文件或者目录 

语法：rm item1...删除一个或多个文件或目录
* -f:force 忽略不存在的文件，不出现警告信息
* -i:交互式的
* -v:显示详细信息
* -r：递归删除
* -rf:删除目录

注：linux和windows不同，没有回收站之类的机制，linux系统删除不可恢复；例rm * .html
#### 4.5 ln
ln:link 链接

语法：ln file link :create hard link创建硬链接
      ln -s item link :create symbol link创建符合链接/软链接
what is hard link?   what is symbol link?

* 硬链接：只能对文件，不能对文件夹；ls-li值相同；删除时需要把所有链接删除才行
* 符号链接：不仅能对文件，还可以对文件夹；原文件被删除时，符号链接失效
### 5、使用命令
command :
+ execute binary  二进制可执行程序
+ buildin bash 系统内置的bash命令
+ shell function shell函数
+ alias 别名
####七个命令
* type 显示命令类型的信息
* which 显示命令的所在路径
* help 显示内嵌命令的相关信息
* man manual:用户手册，比help命令详细
* apropos:在whatis数据库中查找字符串；apropos keword equal to man -k keyword
* whatis :查看命令的简要说明
* info：information :man命令的替代物;n:next node p:preview node u:up q:quit 
enter:jump to link space:pagedown
* alias:设置命令别名  alias name='command string'  alias:list alias command  unalias name 
删除别名
### I/O重定向
redirection:重定向
* stdout:standard out device 标准输出
* stderr:standard error device 标准错误输出
* stdin:standard input device 标准输入
+ redirect standard output:语法command > filename命令输出到filename文件中
command >> filename追加输出到filename文件中

stdin:0   stdout:1 stderr:2
command > filename 2>&1  同时正常输出重定向和错误重定向
command &> filename 和上面的命令等价
无用信息重定向：useless message :/dev/null类似于垃圾桶



	
	
	
	
	