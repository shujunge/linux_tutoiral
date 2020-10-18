[shell 教程](https://zhuanlan.zhihu.com/p/102176365)
======

## shellcheck工具
shellcheck myscript.sh 可以用shellcheck检查shell脚本的错误。

## Shell 是什么？

Shell 是一个命令解释权，它为用户提供了一个向 Linux 内核发送请求以便运行程序界面系统级程序，用户可以用 Shell 来启动、挂起、停止甚至是编写一些程序。
## examples
### 编写hello.sh
```
#!/bin/bash 
echo 'hello world!'
```

### 运行方式
```
sh hello.sh  
or
chmod +x hello.sh 
./hello.sh
```

* #! 告诉系统这个脚本需要什么解释器来执行。
* 文件扩展名 .sh 不是强制要求的。方法1 
* 直接运行解释器，hello.sh 作为 Shell 解释器的参数。此时 Shell 脚本就不需要指定解释器信息，第一行可以去掉。
* 方法2 hello.sh 作为可执行程序运行，Shell 脚本第一行一定要指定解释器。

## Shell 变量

Shell 变量分为**系统变量** 和**自定义变量**。系统变量有$HOME、$PWD、$USER等，
显示当前 Shell 中所有变量：set 。
变量名可以由字母、数字、下划线组成，不能以数字开头。


### 基本语法
* 定义变量：变量名=变量值，等号两侧不能有空格，变量名一般习惯用大写。
* 删除变量：unset 变量名 
* 声明静态变量：readonly 变量名，静态变量不能unset。
* 使用变量：$变量名将命令返回值赋给变量（重点）
* A= `ls` 反引号,执行里面的命令

* A=$(ls) 等价于反引号

## Shell 环境变量




if else
------
```
#!/bin/bash

if [ $1 == $2 ];then
   echo "a == b"
elif [ $1 -gt $2 ];then
   echo "a > b"
elif [ $1 -lt $2 ];then
   echo "a < b"
else
   echo "error"
fi

```

for 循环
-----

* example1 

```
#!/bin/bash
for loop in 1 2 3 4 5
do
    echo "The value is: $loop"
done

```
*  example2 

```
#!/bin/bash
# sum of 1 to 100

Sum=0
for i in {1..100};do
        Sum=$(($Sum+$i))
done
echo "Sum is $Sum"
```
* example3

```
#!/bin/bash
j=$1
for ((i=1; i<=j; i++))
do
touch file$i && echo file $i is ok
done
```

while 循环
----

```
#!/bin/bash
i=0
while [[ $i<3 ]]
do
    echo $i
    let "i++"
done

```

while的判断条件可以从键盘输入，成为交互式的脚本
------

```
#!/bin/bash
echo 'press <CTRL-D> exit'
while read num
do
    echo "you input is $num"
done
```
case
-----
```
#!/bin/bash
case $1 in
    1) echo 'You have chosen 1'
    ;;
    2) echo 'You have chosen 2'
    ;;
    *) echo 'You did not enter a number between 1 and 2'
    ;;
esac

```






