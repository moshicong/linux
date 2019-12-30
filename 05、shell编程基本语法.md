### 概述

Shell 是一个命令行解释器，它为用户提供了一个向 Linux 内核发送请求以便运行程序 的界面系统级程序，用户可以用 Shell 来启动、挂起、停止甚至是编写一些程序。

#### shell 脚本的执行方式

创建一个 Shell 脚本，输出 helloworld

创建脚本文件：touch helloworld.sh

打开脚本文件：vi helloworld.sh

在 helloworld.sh 中输入如下内容 

#!/bin/bash
echo "helloworld"

1、首先要赋予helloworld.sh 脚本的+x权限

chmod 777 helloworld.sh

执行脚本 

./helloWorld.sh

2、bash或sh+脚本(不用赋予脚本+x权限)

sh helloWorld.sh

#### shell 中的变量

Linux Shell 中的变量分为“系统变量”和“用户自定义变量”，可以通过 set 命令查看系统变量。

系统变量:$HOME、$PWD、$SHELL、$USER 等等

显示当前 shell 中所有变量:set

#### 定义变量

基本语法: 变量=值

变量定义规则 

(1)变量名称可以由字母、数字和下划线组成，但是不能以数字开头。 

2)等号两侧不能有空格

(3)变量名称一般习惯为大写 

(4)双引号和单引号有区别，双引号仅将空格脱意，单引号会将所有特殊字符脱意

案例:

STR=“hello world”

A=8 定义变量A

unset A 撤销变量A

readonly B=2 声明静态的变量B=2，不能unset

export变量名 可把变量提升为全局环境变量，可供其他shell程序使用

#### 将命令的返回值赋给变量

A=`ls -la` 反引号，运行里面的命令，并把结果返回给变量 A

或者:A=$(ls -la) 等价于反引号

#### 设置环境变量

基本语法:

设置环境变量的值:
export 变量名=变量值 

查询环境变量的值:

echo $变量名 

修改后的配置信息立即生效:

source 配置文件

案例：

案例:

1、在/etc/profile 文件中定义 JAVA_HOME 环境变量 

export JAVA_HOME=/opt/module/jdk1.7.0_79 

export PATH=$PATH:$JAVA_HOME/bin

2、查看环境变量 JAVA_HOME 的值:

echo $JAVA_HOME

#### 位置参数变量

基本语法
$n :n 为数字，$0 代表命令本身，$1-$9 代表第一到第九个参数，十以上的参数，十以上的参数需要用大括号包含，如${10}

$* :这个变量代表命令行中所有的参数，$*把所有的参数看成一个整体

$@ :这个变量也代表命令行中所有的参数，不过$@把每个参数区分对待

$# :这个变量代表命令行中所有参数的个数

案例：

1、计算输入的参数 1 和参数 2 的两个数的和，并输出到控制台

```
#!/bin/bash
num1=$1
num2=$2
# 变量 sum 的和是 num1 加 num2 
sum=$(( $num1 + $num2))
# 打印变量 sum 的值
echo $sum

```

2、打印输入的参数总数、所有参数

```
#!/bin/bash
# 使用 $# 代表所有参数的个数 
echo "总共有 $# 参数" 
# 使用 $* 代表所有的参数 
echo "有以下参数: $*" 
# 使用 $@ 也代表所有参数
echo "有以下参数: $@" 

```

$* 与 $@ 的区别

$* 和 $@ 都表示传递给函数或脚本的所有参数，不被双引号“”包含时，都以$1 $2 ...$n 的形式输出所有参数

当它们被双引号“”包含时，“$*” 会将所有的参数作为一个整体，以 “$1 $2 ...$n” 的形式输出所有参数，“$@” 会将各个参数分开，以 “$1” “$2”...”$n” 的形式输出所有参数

#### 预定义变量

基本语法:

$? :最后一次执行的命令的返回状态，如果这个变量的值为0，证明上一个命令正确执行;如果这个变量的值为非0(具体是哪个数，由命令自己来决定)，则 证明上一个命令执行不正确了

$$ :当前进程的进程号(PID)
$! :后台运行的最后一个进程的进程号(PID)

### 运算符 

基本语法:

“$((运算式))” 或 “$[运算式]”

案例：

采用$[运算式]方式

```
S=$[(2+3)*4]
echo $S

```

2、expr 分步计算

```
S=`expr 2 + 3`
expr $S \* 4

```

3、expr 一步完成计算

```
expr `expr 2 + 3` \* 4
echo `expr \`expr 2 + 3\`\*4`

```

### 条件判断 

#### 判断语句

基本语法:

[ condition ] 注意 condition 前后要有空格

# 非空返回 true，可使用 $? 验证(0 为 true，>1 为 false)

案例:

1、非空返回 true

[ zhangsan ] 

2、为空，返回 false

[] 

#### 常用判断条件

两个整数之间比较 = 字符串比较

-lt 小于

-le 小于等于 

-eq 等于

-gt 大于

-ge 大于等于

-ne 不等于 

按照文件权限进行判断

-r 有读的权限 

-w 有写的权限 

-x 有执行的权限

按照文件类型进行判断

-f 文件存在并且是一个常规的文件 

-e 文件存在

-d 文件存在并是一个目录

案例：

判断 23 是否大于等于 22

[ 23 -ge 22 ]

判断test.txt是否有写权限

[ -w test.txt ]

判断 test.log 是否存在

[ -e /root/test.log ]

#### 流程控制 

基本语法:

```
if [ 条件判断式 ];then
程序
fi
```

或者

```
if[ 条件判断式 ]
then
程序
fi
```

注意事项:[ 条件判断式 ]，中括号和条件判断式之间必须有空格

#### case 语句

基本语法:

```
case $变量名 in
"值 1")
如果变量的值等于值 1，则执行程序 1 ;;
"值 2")
如果变量的值等于值 2，则执行程序 2 ;;
*)
    如果变量的值都不是以上的值，则执行此程序
;; esac

```

#### for 循环

```
for 变量 in 值 1 值 2 值 3...
do
程序
done

```

或者

```
for (( 初始值;循环控制条件;变量变化 ))
do
程序
done

```

#### while 循环

基本语法:

```
while [ 条件判断式 ]
do
程序
done

```

#### read 读取控制台输入

基本语法: read(选项)(参数)

选项:

-p:指定读取值时的提示符

-t:指定读取值时等待的时间(秒)

  参数

    变量 :指定读取值的变量名

案例:

read -p "please input your name:" NAME 

please input your name: 就是提示符 -p 的内容

#### 系统函数

basename 基本语法：

basename [pathname] [suffix] 

basename [string] [suffix]

basename 命令会删掉所有的前缀包括最后一 个(‘/’)字符，然后将字符串显示出来。

选项:
suffix 为后缀，如果 suffix 被指定了，basename 会将 pathname 或 string 中的 suffix 去掉。 

案例：
basename /opt/test.txt 

输出 :test.txt

basename /opt/test.txt .txt 

输出: test

#### dirname 基本语法

dirname 文件绝对路径 :从给定的包含绝对路径的文件名中去除文件名(非目录的部分)，然后返回剩下的路径(目录的部分)) 

案例:

dirname /opt/test.txt

输出: /opt















