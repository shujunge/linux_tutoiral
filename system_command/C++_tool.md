
c++库
======
* swig
* boost
```
sudo add-apt-repository ppa:mhier/libboost-latest
sudo apt update
sudo apt install libboost1.68-dev
dpkg -S /usr/include/boost/version.hpp //查看boost的版本
sudo apt autoremove libboost1.68-dev
```
* [cgal](https://blog.csdn.net/TQCAI666/article/details/89430036)
```
g++ prova.cpp -lCGAL -o a
```

* libtorch
* opencv
* eigen3

c++性能测试库
=====
* gprof2dot (pip install gprof2dot)
* gprof (GCC自带的命令)

c++单元测试库
=====
* googletest


C++代码检查库
=====
* Cpplint

C++内存泄露检测工具
=====
* valgrind
```
sudo apt-get install valgrind
```

cmake教程
=====

当编译一个需要第三方库的项目时，需要知道：
## 去哪找头文件（.h），-I（GCC）
添加头文件目录: INCLUDE_DIRECTORIES
它相当于 g++ 选项中的 -I 参数的作用，也相当于环境变量中增加路径到 CPLUS_INCLUDE_PATH 变量的作用：

```
include_directories(../../../thirdparty/comm/include)

```

## 去哪找库文件（.so/.dll/.lib/.dylib/...），-L（GCC）
添加需要链接的库文件目录:LINK_DIRECTORIES()
它相当于 g++ 命令的 -L 选项的作用，也相当于环境变量中增加 LD_LIBRARY_PATH 的路径的作用
```
link_directories("/home/server/third/lib")
```
## 需要链接的库文件的名字：-l（GCC）
link_libraries用在add_executable之前，target_link_libraries用在add_executable之后

```
link_libraries(python3.7m)
add_executable(bar ${CMAKE_CURRENT_SOURCE_DIR}/examples/bar.cpp)
```
```
add_executable(bar ${CMAKE_CURRENT_SOURCE_DIR}/examples/bar.cpp)
target_link_libraries(bar python3.7m)

```
### 链接动态、静态库

```
以下写法都可以： 
target_link_libraries(myProject comm)       # 连接libhello.so库，默认优先链接动态库
target_link_libraries(myProject libcomm.a)  # 显示指定链接静态库
target_link_libraries(myProject libcomm.so) # 显示指定链接动态库

//再如：
target_link_libraries(myProject libcomm.so)　　#这些库名写法都可以。
target_link_libraries(myProject comm)
target_link_libraries(myProject -lcomm)
```

## 宏定义
它相当于 g++ 命令的 -D 选项的作用（-DCPU_ONLY），用于宏定义。add_definitions(-DCPU_ONLY)
```
add_definitions(-DMATPLOTLIBCPP_PYTHON_HEADER=Python.h)
```
## 添加子文件夹
使用 add_subdirectory
```
add_subdirectory(Foundation_Classes)
add_subdirectory(Behavioral_Patterns)
add_subdirectory(Creational_Patterns)
add_subdirectory(Structural_Patterns)
```


## examples

```
cmake_minimum_required(VERSION 3.3)
project (MatplotlibCPP_Test)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(PYTHONHOME /home/zf/anaconda3)

include_directories(${PYTHONHOME}/include/python3.7m)
include_directories(${PYTHONHOME}/lib/python3.7/site-packages/numpy/core/include)
link_directories(${PYTHONHOME}/lib)

add_definitions(-DMATPLOTLIBCPP_PYTHON_HEADER=Python.h)

add_executable(bar ${CMAKE_CURRENT_SOURCE_DIR}/examples/bar.cpp)
target_link_libraries(bar python3.7m)
```


[性能测试工具](https://blog.csdn.net/weixin_30846599/article/details/98321166)
=======

vmstat
----

查看缺页中断
---
* ps -o pid,psr,comm -p pid //psr列
* taskset -a -p -c 0-30 pid //设置pid进程运行在0~30核上
* top -H -d 1 -p pid //查看pid进程的线程 //按f，选择需要显示的列 //top命令后按1可显示CPU列表，shift+p排序

strace
-----
* strace -cp pid_name -f //统计pid进程所有系统调用的耗时占比
* pstack //查看线程栈


