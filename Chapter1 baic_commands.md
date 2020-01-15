基本命令
=====

### ps
```
ps -ef #提供正在运行的进程的完整列表
ps -ejh ##提供简洁正在运行的进程的完整列表
ps -exjf ##提供进程之间层次结构关系图

```

### pstree

```
pstree ## 获得进程视图。
pstree -n
```

### tree
```
tree  /yourdoc 用于查看文件的命令。
tree -d /yourdoc 只显示目录

tree -f /yourdoc 显示完整的路经

```

# RPM包初窥

## RPM的基本命令
```
rpm -q fpaste
rpm -qi fpaste ##查看状态信息
rpm -ql fpase ## fpaste查看路经

```

## RPM的依赖关系

```
rpm -q --requires fpaste
rpm -q --provides fpaste
rpm -qi python3
rpm -q --provides python3

```
### 更新服务器

* ubuntu和Debian上
```
sudo apt update && sudo apt upgrade -y
```
* 在Fedora,CentOS和RHEL:
```
sudo dnf upgrade
```

### 创建一个新的特权用户
```
adduser <username>
```

### 上传你的SSH密钥
```
ssh-copy-id <username>@ip_address
```

### 重启SSH服务
```
sudo service sshd restart
sudo systemcml restart sshd 
```

### 启动防火墙
```
sudo apt install ufw
```
### 设置SSH，HTTP，HTTPS的访问登录
```
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
```
* 启动ufw
```
sudo ufw enable
```
* 查看ufw支持哪些服务
```
sudo ufw status
```

## 移除无用的服务
```
sudo ss -atpu

```
* 在Debian/Ubuntu上删除未使用的服务
```
sudo apt purage <service_name>
```
* 在REd Hat/CentOS上删除未使用的服务
```
sudo yum remove <service_name>
```


## GNU binutils 
![二进制文件时中查找漏洞](https://mp.weixin.qq.com/s?__biz=MzI1NDQwNDYyMg==&mid=2247487822&idx=1&sn=325921788bb0c65d66a92abdf8cfe54a&chksm=e9c4e02fdeb369397b408432b36f62c7d1edde16bfce5154ac00688314692ea1998739c51c39&mpshare=1&scene=1&srcid=&sharer_sharetime=1571651980864&sharer_shareid=0c5c28d4ae5e6d9876a110af654b8490&pass_ticket=q0WqvTKZ8zz%2FN%2Bvt6LWWs6BB6K05FTmFkYU85%2F3CZWuJVPDDqK6Hf1giSjbC6FvE#rd)


## 更新linux的内核
* 在RHEL，CentOS和Fedora上:
```
sudo dnf update kernel
```
* 在Debian和ubuntu上

```
sudo apt update
sudo apt search linux-image
```
## 安装内核模块

```
sudo dnf install kmod-nvidia
sudo apt update
sudo apt install nvidia-kernel-common nvidia-kernel-dkms nvidia-glx nvidia-xconfig
```
* 查看正在运行的内核版本
```
uname -r
```
### 打印linux的设备信息
```
inxi -Fxz
### -F 得到完整的输出
-x 添加细节信息
-z 参数隐藏MAC和IP等私人身份信息

hwinfo --short
lshw -short
```

### 打印linux的设备CPU信息

```
lscpu
lshw -C cpu

lsgpu | grep -i mhz #查看CPU的速度

```
### 打印linux设备的内存

```
dmidecode -t memory | grep -i size ## 列出每根内存条和其容量
lshw -short -C memory #获得系统内存更多信息,包括类型，容量

dmidecode -t memory | grep -i  max ## 查看计算机可以安装的最大内存条
lshw -short -C memory | grep -i empty ## 查看是否有空内存卡的空槽

```

### 查看显卡设备信息
```
lspci | grep -i vga
lspci -v -s 00:02.0 ## perfetchsize #显示系统中显存的大小
nvidia-smi -l
```

## 磁盘文件系统和设备

* 显示每个磁盘设备的描述信息
```
lshw -short -C disk
```
* 列出所有磁盘及分区和大小
```
sudo lsblk
sudo fdisk -l

sudo blkid

```

* 列出usb和pci总线以及其他设备信息
```
lsusb
lspci
```
## 网络
* 查看你的网卡硬件信息
```
lshw -C network
ifconfig -a
ip link show
netstat  -i
```

## 软件
* 显示UEFI和BIOS的日期和版本
```
dmidecode -t bios
uname -a 
```

## 挂载磁盘
如果磁盘没有文件系统
```
sudo fdisk -l
mkfs.ext4 /dev/sdb1

常见的文件格式有:
ext4,nfs,exfat等等

```
## 命令行链接wifi
* 查看可以使用的无线网络
```
nmcli dev wifi
```
* 连接无线网
```
nmcli dev wifi connect 'yourname' password 'your password'
```







