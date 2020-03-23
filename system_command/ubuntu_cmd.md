linux常用的命令
==============

``` python
import warnings
warnings.filterwarnings('ignore')
import os
os.environ["CUDA_VISIBLE_DEVICES"] ="2"
import matplotlib.pyplot as plt
plt.switch_backend('agg')
```
````
-i http://pypi.v2ex.com/simple
-i http://mirrors.aliyun.com/pypi/simple
-i https://pypi.tuna.tsinghua.edu.cn/simple
-i https://pypi.mirrors.ustc.edu.cn/simple/

````

升级nodejs和npm版本：
========
如果node不是最新的，node有一个模块叫n，是专门用来管理node.js的版本的。使用npm（NPM是随同nodejs一起安装的包管理工具）安装n模块
$ sudo npm install -g n
然后，升级node.js到最新稳定版
$ sudo n stable
旧版本的 npm，也可以很容易地通过 npm 命令来升级，命令如下：
$ sudo npm install npm -g
使用n模块安装的最新node

组里服务器
-----
ssh -p 6000 wzf@39.100.108.239

错误问题：vi上下左右键显示为ABCD的问题
==========
解决方法： 
只要依次执行以下两个命令即可完美解决Ubuntu下vi编辑器方向键变字母的问题。
* 执行命令 sudo apt-get remove vim-common
* 执行命令 sudo apt-get install vim


libtorch的编译命令:
======
```
cmake -DCMAKE_PREFIX_PATH=/libtorch ..
```

ubuntu状态栏显示:
----
>>> indicator-sysmonitor &
 
tensorflow:
指定服务器上的GPUO
```
export CUDA_VISIBLE_DEVICES=2

```

tmux kill-session -t 0

jupyter notebook
-------------
* 生成gif图片
>>> convert -resize 768x576 -delay 20 -loop 0 *.jpg myimage.gif

* 图片转化为pdf
>>> convert -compress Group4 linguistics_thesis_b_thresh.png output.pdf

播放音乐
------
>>> timidity *.mid  //http://blog.topspeedsnail.com/archives/10508
>>> play *.mp3

显示图片
-----
eog *.gif or *.png



```
ps aux|grep a //a为程序名称
conda info --envs //安装的环境

```

//查看程序是否有内存泄漏
g++ main.cpp -o a
valgrind --tool=memcheck --leak-check=yes ./zf "data" "m_data" 1



```
//将rm
$ git clone https://github.com/lagerspetz/linux-stuff

$ sudo mv linux-stuff/scripts/saferm.sh /bin

$ rm -Rf linux-stuff

在 .bashrc 文件中设置别名，

alias rm=saferm.sh

执行下面的命令使其生效，

$ source ~/.bashrc

通过命令 ulimit -s 查看linux的默认栈空间大小，默认情况下 为2~10M
```

安装deb
------
dpkg -i <package.deb>
卸载deb
----
dpkg -r <package>

网易云音乐
-----
>>netease-cloud-music


静态文件库的生成(.a):
1.g++ -c zf.cpp  ##将zf.cpp和zf.h生成目标文件.o
2.ar cqs zf.a zf.o#将生成的目标文件生成.a文件静态链接库
3.g++ main.cpp zf.a -o main#生成最终的执行文文件
动态文件库的生成(.so)：
g++ one.cpp two.cpp three.cpp -fPIC -shared -o libtest.so  ###多个cpp文件生成动态库so
编译cpp文件:
g++ test.cpp -o test
编译c文件:
gcc test.cpp -o test
在linux下添加C++的环境路径: ##C++的环境变量CPLUS_INCLUDE_PATH (C的则是C_INCLUDE_PATH)
export CPLUS_INCLUDE_PATH="$CPLUS_INCLUDE_PATH:/usr/local/include/eigen3"
编译opencv3 c++程序
`pkg-config opencv --libs --cflags opencv`

xkill

cmake的安装与卸载:
安装文件:
make install
卸载文件:
nake uninstall
or
cat install_manifest.txt | sudo xargs rm




##查看cuda信息
cat /usr/local/cuda/version.txt
cat  /usr/local/cuda/version.txt 即可查询

##查看cudnn的信息在其头文件里

cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2  即可查询


boost库信息查看
>>>dpkg -S /usr/include/boost/version.hpp

conda的源
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
conda config --set show_channel_urls yes



关闭linux文件管理器
>>> ps -A | grep nautilus
>>> sudo kill pid
随便点击一个文件即可重启文件管理器



centos系统下安装mongodb安装
https://blog.csdn.net/liang_henry/article/details/79582766
在根目录下创建文件/data/db

查看进程的线程信息
top -H -p {进程id}
查看进程的信息
lsof -p {进程id}

##wget download googledrive

!wget -O /usr/sbin/gdrivedl 'https://files.matthuisman.nz/gdrivedl'
!chmod +x /usr/sbin/gdrivedl
!gdrivedl https://drive.google.com/open?id=1RNvis4rLLoOwF6eWkxdcyjAJPEAox0Dq ./caffe.pth
!gdrivedl 11DLJkuhRHHdRziYc2dQBiyPzf6QGn041
!gdrivedl ID_name


!pip install pillow==4.1.1
%reload_ext autoreload
%autoreload


keras　loss:
"mean_absolute_percentage_error"


解决办法：在导入matplotlib的时候指定不需要GUI的backend（Agg、Cairo、PS、PDF和SVG）。例如：

import matplotlib.pyplot as plt
plt.switch_backend('agg')
 

创建文件目录
path="./data"
isExists=os.path.exists(path)

if isExists:
	shutil.rmtree(path)
os.makedirs(path)


import argparse
parser = argparse.ArgumentParser(usage="it's usage tip.", description="help info.")
parser.add_argument("--n_anchors", type=int, required=True, default=6, help="the port number.", dest="n_anchors")
args = parser.parse_args()
n_anchors=args.n_anchors


python3.5编程
import sys 
for line in sys.stdin:
    x = line.strip()



colab download kaggle dataset:
================================================================================================================
Please follow the steps below to download and use kaggle data within Google Colab:
1. Go to your account, Scroll to API section and Click Expire API Token to remove previous tokens
2. Click on Create New API Token - It will download kaggle.json file on your machine.
3. Go to your Google Colab project file and run the following commands:
1) ! pip install -q kaggle
2) from google.colab import files
files.upload()
Choose the kaggle.json file that you downloaded
3) ! mkdir ~/.kaggle
! cp kaggle.json ~/.kaggle/
Make directory named kaggle and copy kaggle.json file there.
4) ! chmod 600 ~/.kaggle/kaggle.json
Change the permissions of the file.
5) ! kaggle datasets list
- That's all ! You can check if everything's okay by running this command.

Download Data
! kaggle competitions download -c 'name-of-competition'
Use unzip command to unzip the data:
For example,
Create a directory named train,
! mkdir train
unzip train data there,
! unzip train.zip -d train
================================================================================================================


jupyter config c++
======
conda install xeus-cling


ananconda安装
======
1.配置环境
* tensorflow
* keras
* tqdm
* 


##下载百度云盘
### wget -c --referer=百度云分享链接 -O 保存的文件名 "百度云实际下载地址"

wget -c --referer=https://pan.baidu.com/s/1Ii6K39qUQA2dAi0OuYR8rA -O test.zip "https://nbct01.baidupcs.com/file/c7a6941bd7517b14b58eb769501b7b17?bkt=en-864c1d195a8f2f4199aa224a2a925341f1b538b4705b5a341d9ee02564d1428c98d6322c315b5c5151a87d535ac4a6336ec71da96b6cd0e75b1d949ff0957b4c&fid=1120520097-250528-620341684288309&time=1571126218&sign=FDTAXGERLQBHSKfW-DCb740ccc5511e5e8fedcff06b081203-mkoytlNb3%2F7tbCPwMablZxQVVKU%3D&to=67&size=79645&sta_dx=79645&sta_cs=16&sta_ft=rar&sta_ct=2&sta_mt=0&fm2=MH%2CYangquan%2CAnywhere%2C%2Cshanxi2%2Cct&ctime=1570761142&mtime=1571126020&resv0=cdnback&resv1=0&resv2=&resv3=&resv4=&vuk=1120520097&iv=0&htype=&randtype=&newver=1&newfm=1&secfm=1&flow_ver=3&pkey=en-a9f87379ea859d598fe6999a3740492a658c883d8df38348a815fdb95fa1dcbc0eec242298494a1cf0e64e70b2402163ad64b0e86aa05d96305a5e1275657320&sl=68616270&expires=8h&rt=sh&r=532140574&vbdid=3938021557&fin=1010--2019%E5%B9%B4%E5%A4%A9%E6%99%BA%E6%9D%AF%E7%AB%9E%E8%B5%9B-%E6%B0%94%E8%B1%A1.rar&fn=1010--2019%E5%B9%B4%E5%A4%A9%E6%99%BA%E6%9D%AF%E7%AB%9E%E8%B5%9B-%E6%B0%94%E8%B1%A1.rar&rtype=1&dp-logid=6671753221359838277&dp-callid=0.1&hps=1&tsl=200&csl=200&csign=xruvo%2BPiNN%2BZwCFn9cKpuGf5wHg%3D&so=0&ut=6&uter=4&serv=0&uc=3007230825&ti=76168191086d6f2915ad9f44017d6cee3b57b73577b7d895&by=themis"


https://pan.baidu.com/s/12ti73ktzIM9fX7tKrsWC8w
提取码: nwxx

wget -c --referer=https://pan.baidu.com/s/12ti73ktzIM9fX7tKrsWC8w -O radar.tar "https://nj.baidupcs.com/monitor.jpg?xcode=1a81b0bbd448fc36f65202d7e8f159404c932f26aaa77f9c&t=15711293771571129377645"


[terminator使用说明](https://blog.csdn.net/bestBT/article/details/81221378)
==========

Ctrl+Shift+O 水平分割终端（分成上下两个窗口）
Ctrl+Shift+E 垂直分割终端（分成左右两个窗口）
Ctrl+Shift+W 关闭当前终端 
Ctrl+Shift+X 放大（还原）当前终端 
F11 全屏 
Ctrl+Shift+G 清屏 
Ctrl+Shift+Right/Left 在垂直分割的终端中将分割条向右/左移动 
Ctrl+Shift+S 隐藏/显示滚动条 
Ctrl+Shift+Q 关闭所有终端（退出程序） 
Ubuntu自带的终端是gnome-terminal(/usr/bin/gnome-terminal)
,虽然能用但是不能支持屏幕分割和选择复制等功能，于是换用terminator作为默认终端
设置默认Terminal为Terminator
gsettings set org.gnome.desktop.default-applications.terminal exec   /usr/bin/terminator
gsettings set org.gnome.desktop.default-applications.terminal exec-arg "-x"





As the first step you should remove 2.48.2-0ubuntu1 version of libglib2.0-0 with this command:

>>sudo dpkg -r --force-all libglib2.0-0
After that you should install libglib2.0-0 and fix broken packages:

>>sudo apt update
>>sudo apt install -f
>>sudo apt install libglib2.0-0 
Finally you can install:

>>sudo apt install libglib2.0-dev




grub修复
=======
>>>insmod normal
>>>normal
>>>sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update <回车>
>>>sudo apt-get install -y boot-repair && boot-repair<回车>

u盘变成自读模型
=====
>>> df -h
>>>sudo umount /media/zoutao/disk //卸载之后一定不能拔掉U盘
>>> sudo dosfsck -v -a /dev/sdb5 //修复U盘文件系统故障


创建文件夹快捷方式
=====
>>> ln -s your_dir ~/Desktop/

wget 无法建立 SSL 连接
======
>>> wget --no-check-certificate https://pjreddie.com/media/files/yolov3.weights


编译opencv
=====
查看系统默认的版本
-----
pkg-config --modversion opencv
pkg-config --cflags opencv
pkg-config --libs opencv

更换不同的路径
-----
>>> CMAKE_INSTALL_PREFIX=/usr/local/opencv3
>>> export PKG_CONFIG_PATH=/usr/local/opencv3/lib/pkgconfig
>>> export LD_LIBRARY_PATH=/usr/local/opencv3/lib

查找系统中所有的OpenCVConfig.cmake文件:

>>> sudo find / -name OpenCVConfig.cmake
>>> /home/zfw/opencv_library/share/OpenCV/OpenCVConfig.cmake
修改程序中CMakeList.txt中相关语句如下：
set(OpenCV_DIR /home/zfw/opencv_library/share/OpenCV)
find_package(OpenCV  REQUIRED)


* [下载 ippicv_2017u3_lnx_intel64_general_20170822.tgz](https://blog.csdn.net/u010739369/article/details/79966263?utm_source=blogxgwz3)

>>> cmake  -D CMAKE_INSTALL_PREFIX=/home/wzf/opencv_library –D WITH_VTK=ON -D OPENCV_EXTRA_MODULES_PATH=/home/alisa/Documents/package/opencv-3.4.0/opencv_contrib-3.4.0/modules/ -D CUDA_NVCC_FLAGS="-std=c++11 --expt-relaxed-constexpr" -D WITH_NVCUVID=ON -D BUILD_opencv_cudacodec=OFF -D ENABLE_CXX11=YES ..

>>> cmake  -D CMAKE_INSTALL_PREFIX=/home/wzf/opencv_library -D WITH_NVCUVID=OFF -D BUILD_opencv_cudacodec=OFF -D ENABLE_CXX11=YES ..

* git clone --recursive https://github.com/Microsoft/LightGBM 


wget下载github的pdf
=======
github: https://github.com/firmianay/security-paper/blob/master/Compiler/Getting_Started_with_LLVM_Core_Libraries/Getting%20Started%20with%20LLVM%20Core%20Libraries.pdf
>>> wget https://raw.githubusercontent.com/firmianay/security-paper/master/Compiler/Getting_Started_with_LLVM_Core_Libraries/Getting%20Started%20with%20LLVM%20Core%20Libraries.pdf

ubuntu install pyaudio
=====
```
sudo apt-get install libasound-dev portaudio19-dev libportaudio2 libportaudiocpp0
pip install pyaudio
```


