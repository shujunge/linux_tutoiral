shell 教程
======


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






