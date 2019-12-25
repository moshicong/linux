#### Linux 入门概述

Linux 内核最初只是由芬兰人林纳斯·托瓦兹(Linus Torvalds)在赫尔辛基大学上学时出 于个人爱好而编写的。

Linux 是一套免费使用和自由传播的类 Unix 操作系统，是一个基于 POSIX 和 UNIX 的 多用户、多任务、支持多线程和多 CPU 的操作系统。

Linux 能运行主要的 UNIX 工具软件、 应用程序和网络协议。它支持 32 位和 64 位硬件。

Linux 继承了 Unix 以网络为核心的设计 思想，是一个性能稳定的多用户网络操作系统。

目前市面上较知名的发行版有:Ubuntu、RedHat、CentOS、Debain、Fedora、SuSE、 OpenSUSE

#### Linux 特点

Linux 里面一切皆是文件，文件可以没有后缀，如果加上后缀只是为了区分文件类型

#### Linux 目录结构

/bin：是Binary的缩写，这个目录存放着系统必备执行命令

/boot：这里存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文 件，自己的安装别放这里

/dev：Device(设备)的缩写，该目录下存放的是Linux的外部设备，在Linux中访问设备的 方式和访问文件的方式是相同的

/etc：所有的系统管理所需要的配置文件和子目录

/home：存放普通用户的主目录，在Linux中每个用户都有一个自己的目录，一般该目录 名是以用户的账号命名的

/lib：系统开机所需要最基本的动态连接共享库，其作用类似于Windows里的DLL文件。 几乎所有的应用程序都需要用到这些共享库

/lost+found：这个目录一般情况下是空的，当系统非法关机后，这里就存放了一些文件

/media：linux系统会自动识别一些设备，例如U盘、光驱等等，当识别后，linux会把识 别的设备挂载到这个目录下

/misc: 该目录可以用来存放杂项文件或目录，即那些用途或含义不明确的文件或目录可 以存放在该目录下

/mnt：系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在 /mnt/上，然后进入该目录就可以查看光驱里的内容了

/net：存放着和网络相关的一些文件

/opt：这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库则就可 以放到这个目录下。默认是空的

/proc：这个目录是一个虚拟的目录，它是系统内存的映射，我们可以通过直接访问这 个目录来获取系统信息

/root：该目录为系统管理员，也称作超级权限者的用户主目录

/sbin：s就是Super User的意思，这里存放的是系统管理员使用的系统管理程序。 

/selinux：这个目录是Redhat/CentOS所特有的目录，Selinux是一个安全机制，类似于windows的防火墙

/srv：service缩写，该目录存放一些服务启动之后需要提取的数据

/sys: 这是linux2.6内核的一个很大的变化。该目录下安装了2.6内核中新出现的一个文件系统 sysfs 

/tmp：这个目录是用来存放一些临时文件的

/usr: 这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似与windows下的program files目录

/var：这个目录中存放着在不断扩充着的东西，我们习惯将那些经常被修改的目录放在这个目录下。包括各种日志文件

#### 防火墙

基本语法:

查看防火墙状态：service iptables status 

查看防火墙开机启动状态：chkconfig iptables –list 

临时关闭防火墙：service iptables stop 

关闭防火墙开机启动：chkconfig iptables off 

开启防火墙开机启动：chkconfig iptables on 

#### 关机重启

将数据由内存同步到硬盘中：sync

计算机将在 10 分钟后关机，并且会显示在登录用户的当前屏幕中：

```
shutdown –h 10 ‘This server will shutdown after 10 mins’
```
立马关机：shutdown –h now

系统立马重启：shutdown –r now

重启(等同于 shutdown –r now)：reboot

关机(等同于 shutdown –h now 和 poweroff)：halt

注意:不管是重启系统还是关闭系统，首先要运行 sync 命令，把内存中的数据写到磁 盘中。

#### 用户和用户组管理命令

##### useradd 添加新用户

基本语法：useradd 用户名

例如添加用户zhangsan：useradd zhangsan

##### passwd 设置用户密码

基本语法：passwd 用户名

例如添加zhangsan的密码：passwd zhangsan

##### id 判断用户是否存在

基本语法: id 用户名

例如判断zhangsan是否存在：id zhangsan

##### su 切换用户

基本语法: su 用户名称

例如切换到用户zhangsan：su zhangsan

##### userdel 删除用户

基本语法:

删除用户但保存用户主目录：userdel 用户名 

用户和用户主目录，都删除userdel -r 用户名 

例如：

删除用户但保存用户主目录：userdel zhangsan

删除用户和用户主目录，都删除：userdel -r zhangsan

##### who 查看登录用户信息

基本语法：

显示自身用户名称：whoami

显示登录用户的用户名：who am i

看当前有哪些用户登录到了本台机器上：who 

##### 设置普通用户具有 root 权限

修改 /etc/sudoers 文件，找到下面一行，在 root 下面添加一行

```
## Allow root to run any commands anywhere 
root ALL=(ALL) ALL
zhangsan ALL=(ALL) ALL
```
修改完毕，现在可以用 zhangsan 帐号登录，然后用命令 su - ，即可获得 root 权限进行操作。

##### usermod 修改用户

基本语法:usermod -g 用户组 用户名

将用户 zhangsan 加入 dev 用户组：usermod –g dev zhangsan

##### groupadd 新增组

基本语法: groupadd 组名


```
## 添加一个 test 组

groupadd test
```
##### groupdel 删除组

基本语法: groupdel 组名


```
groupdel test
```

##### groupmod 修改组

基本语法:groupmod -n 新组名 老组名

```
修改 test 组名称为 test1

groupmod –n test1 test
```









