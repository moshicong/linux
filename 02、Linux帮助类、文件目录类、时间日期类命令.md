### 帮助命令

#### man 获得帮助信息

基本语法:man [命令或配置文件]

案例：man ls

#### help 获得 shell 内置命令的帮助信息

基本语法:help 命令

案例：help cd

#### 常用快捷键

ctrl + c:停止进程

ctrl+l:清屏

ctrl + q:退出

tab 键：获取提示信息

上下键:查找执行过的命令

ctrl +alt:linux 和 Windows 之间切换

### 文件目录类

#### pwd 显示当前工作目录的绝对路径

基本语法:pwd

####  ls 列出目录的内容

基本语法:ls [选项] [目录或是文件] 

选项:
-a :全部的文件，连同隐藏档(开头为 . 的文件) 一起列出来

-d :仅列出目录本身，而不是列出目录内的文件数据

-l :长数据串列出，包含文件的属性与权限等等数据

每行列出的信息依次是: 文件类型与权限、链接数、文件属主、文件属组 文件大小用byte来表示、建立或最近修改的时间、名字

案例：ls -al

drwxr-xr-x. 3 root root 4096 5月 27 14:03 .. 

drwxr-xr-x. 3 root root 4096 5月 27 14:14 hello

#### mkdir 创建一个新的目录

基本语法:mkdir [-p] 要创建的目录 

选项:

-p:创建多层目录

案例：

mkdir test

mkdir -p user/test

#### rmdir 删除一个空的目录

基本语法:rmdir 要删除的空目录

案例：

rmdir test

#### touch 创建空文件

基本语法: touch 文件名称

案例：

touch test.sh

#### cd 切换目录

基本语法: 

cd 绝对路径

cd 相对路径

cd ~或者 cd :回到自己的家目录

cd - :回到上一次所在目录

cd .. :回到当前目录的上一级目录

cd -P :跳转到实际物理路径，而非快捷方式路径

案例：

1、使用 mkdir 命令创建 test 目录

mkdir test

2、使用绝对路径切换到 test 目录

cd /root/test/

3、使用相对路径切换到 test 目录

cd ./test/

4、回到自己的家目录，也就是 /root 这个目录

cd ~

5、cd- 回到上一次所在目录

cd -

6、回到当前目录的上一级目录，也就是 /root 的上一级目录的

cd ..

#### cp 复制文件或目录

基本语法:

cp source dest :复制 source 文件到 dest

cp -r sourceFolder targetFolder :递归复制整个文件夹

案例:

1、复制文件

cp test.sh test

2、递归复制整个文件夹

cp -r test test1

#### rm 移除文件或目录

基本语法:

rmdir deleteEmptyFolder :删除空目录

rm -rf deleteFile :递归删除目录中所有内容

案例 

1、删除空目录

rmdir test

2、递归删除目录中所有内容

rm -rf test1

#### mv 移动文件与目录或重命名

基本语法:

mv oldNameFile newNameFile :重命名 

mv /temp/movefile /targetFolder :移动文件

案例：

1、重命名

mv test.sh test1.sh

2、移动文件

mv test1.sh test1

#### cat 查看文件内容

查看文件内容，从第一行开始显示

基本语法:

cat [选项] 要查看的文件 

选项:

-A :相当于 -vET 的整合选项，可列出一些特殊字符而不是空白而已

-b :列出行号，仅针对非空白行做行号显示，空白行不标行号

-E :将结尾的断行字节 $ 显示出来

-n :列出行号，连同空白行也会有行号，与 -b 的选项不同

-T :将 [tab] 按键以 ^I 显示出来

-v :列出一些看不出来的特殊字符

#### tac 查看文件内容

查看文件内容，从最后一行开始显示，tac 是 cat 的倒写

基本语法:

cat [选项参数] 要查看的文件

案例：

1、从第一行顺序显示

cat test1.sh

2、从最后一行倒序显示

tac test1.java

#### more 查看文件内容

查看文件内容，一页一页的显示文件内容

基本语法:

more 要查看的文件 

快捷键使用说明

空白键 (space):代表向下翻一页

Enter:代表向下翻一行

q:代表立刻离开 more ，不再显示该文件内容

Ctrl+F :向下滚动一屏

Ctrl+B :返回上一屏

= 输出当前行的行号

:f 输出文件名和当前行的行号

案例：

more test1.sh

#### less 查看文件内容

less 的作用与 more 十分相似，都可以用来浏览文字档案的内容，不同的是 less 允许 使用[pageup] [pagedown]往回滚动

基本语法:

less 要查看的文件 

快捷键使用说明

空白键 :向下翻动一页

[pagedown]:向下翻动一页

[pageup] :向上翻动一页

/字串 :向下搜寻『字串』的功能

?字串 :向上搜寻『字串』的功能

q :离开 less 这个程序

案例：

less test1.sh

#### head 查看文件内容

查看文件内容，只看头几行

基本语法:

head -n 10 文件 :查看文件头 10 行内容

案例:

查看 test1.sh 前 2 行的内容

head -n 2 test1.sh

#### tail 查看文件内容

查看文件内容，只看最后几行

基本语法:

tail -n 10 文件名 :查看文件最后 10 行内容

tail –f 文件名 :实时追踪该文档的所有更新

案例：

1、查看最后 5 行内容

tail -n 5 test1.sh

2、实时追踪该档的所有更新

tail -f test1.sh

#### 重定向命令

基本语法: 

ls –l > 文件 :列表的内容写入文件中，覆盖原来的文件内容

ls –al >>文件 :列表的内容追加到文件末尾，不覆盖

#### echo

基本语法:

echo 要显示的内容 >> 存储内容的的文件 :将要显示的内容，存储到文件中

echo 变量名 :显示变量的值

案例：

显示 JAVA_HOME 的路径

echo $JAVA_HOME

#### ln 软链接

基本语法:

ln –s [原文件] [目标文件] :给原文件创建一个软链接，软链接存放在目标文件目录

案例：

ln -s /opt/module/test.txt /opt/t.txt

结果输出：

lrwxrwxrwx. 1 root root 20 6 月 17 12:56 t.txt -> /opt/module/test.txt

创建一个软链接

ln -s /opt/module/hadoop-2.7.2/ /opt/software/hadoop

cd 不加参数进入是软链接的地址

cd hadoop

cd 加参数进入是实际的物理地址

cd -P hadoop

#### history 查看所敲命令历史

基本语法: history

### 时间日期类

基本语法:

date [OPTION]... [+FORMAT]

#### date 设置系统时间

基本语法:

date -s 字符串时间

date -s "2019-12-23 23:52:18"

#### date 显示当前时间

基本语法:

date :显示当前时间

date +%Y :显示当前年份

date +%m :显示当前月份

date +%d :显示当前是哪一天

date +%Y%m%d (或者 date +%Y/%m/%d ) :显示当前年月日各种格式

date "+%Y-%m-%d %H:%M:%S" :显示年月日时分秒

#### date 显示非当前时间

基本语法:

date -d '1 days ago' :显示前一天日期

date -d yesterday +%Y%m%d :显示前一天日期

date -d next-day +%Y%m%d :显示明天日期

date -d 'next monday' :显示下周一时间

#### cal 查看日历

基本语法:

cal [选项]  (不加选项，显示本月日历) 

选项:

-3 ，显示系统上月、本月、下月的日历

具体某一年，显示这一年的日历

案例：

1、显示上月、本月、下月的日历

cal -3 

2、显示 2019 年日历

cal 2019



















