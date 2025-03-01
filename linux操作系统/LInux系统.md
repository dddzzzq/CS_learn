# LInux系统

## 1. 简介

​	Linux系统是以文件目录系统为根基的，即在Linux中所有东西都被当成文件，包括硬件，进程，命令，环境，目录等等均被视作文件，以/为根路径开始，依次展开，树状结构管理。

## 2. 常见命令

- pwd：printing working directory显示当前工作目录的路径
- cd：change directory 切换目录
- ls：list，列出目录下的内容
- mkdir：创建目录
- sudo：增加root权限，平常进入linux系统，进入的是Ubuntu用户，输入sudo su就切换到root用户。
- touch：创建文件
- vim：vim编辑器，或者nano编辑器，刚进入为命令模式，点击i键进入插入模式。按下esc键进入命令模式，输入:wq即可保存返回终端
- cp（copy）：复制文件，cp 1.md 2.md指的是把1.md的内容复制到2.md中，-r复制整个目录
- cat（concatenate）：连接文件并输出到终端，可以看到文件内容。
- rm（remove）：删除文件或者目录，-r，递归目录，-f强制删除
- scp（secure copy）：安全复制，可以远程复制文件
- crtl+S锁屏，crtl+q解锁

## 3. 安装应用

例如安装node.js

1. apt update：advanced package tool
2. apt install snap:安装snap安装管理器
3. snap install node --classic 
4. node -v

## 4. 计算机硬件体系结构

### 4.1 操作系统冯诺依曼体系结构

- 计算机处理的指令和数据一律用二进制数据表示
- 顺序执行程序
- 计算机硬件由运算器、控制器、存储器、输入设备和输出设备五大部分组成

### 4.2 网络连接

- IP地址
  - IP地址是一种逻辑地址，用来标识网络中的一个个主机。
    - IP地址 = 网络地址 + 主机地址
    - 在IPV4协议中，IP地址是一个4*8bit（1字节）二进制串。
- 子网掩码NETMASK
  - **功能**：将IP地址分为网络地址与主机地址两部分
- 默认网关GATEWAY
  - 连接两个不同网络的设备都可以叫做网关设备；网关的作用就是实现两个网络之间的通讯和控制
  - 网关地址就是网关设备的IP地址
- 域名服务器DNS
  - DNS是域名服务器，用来解析域名的（即实现IP地址与域名之间的转换）

## 5. Linux软件

GNU/Linux（内核）

### 	5.1 Linux分支

​		***下载一般用双不用单***

1. RedHat（收费）
   - Centos，主要注重服务器
2. Debain（免费）
   - Ubuntu，主要有良好的视图

### 	5.2 下载Linux

下载镜像iso文件

1.**分类**：

- everything
- minimal
- netinstall
- DVD
- 。。。

2.操作系统的位数：64位

## 6. 虚拟机安装与配置

### 	6.1 虚拟化技术

步骤：

1. 安装VM
2. 新建虚拟机，此时为空操作系统
3. 编辑虚拟机设置：修改DVD，选到下载的操作系统iso文件
4. 进行操作系统的安装

## 7. 硬盘分区

### 7.1 /boot 引导分区

​	size：256mb

### 7.2 /swap

​	size：2*内存

### 7.3 /

​	剩下所有

root用户密码：123456

按下reboot，启动虚拟机！

## 8. 网络配置

 

 











 