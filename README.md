# BitmapFileSystemOnLinux
Linux系統上基於Bitmap的檔案管理系统
## 題目要求
1. 为了方便文件系统的编写和测试，最好在VMWare虚拟机上实现。
2. Linux操作系统一般都会自带ramdisk设备(/dev/ram)，它能把一部分内存模拟成一个磁盘。所以，在实验的过程中可以使用ramdisk作为块设备，而不需要专门为该文件系统直接创建一个磁盘分区。
3. 文件系统的实现推荐参考Linux内核源代码中minix文件系统的实现方式。它的实现在(Linux内核源码目录/fs/minix/)目录中。
## 需求分析
在 Linux 上实现一个简单的文件系统，其核心功能依赖位示图来管理磁盘块。  
实现的基本的功能包括：新增、删除、重命名、读写、拷贝目录或文件。   
另外还需完成初始化文件系统、显示目录内容功能。  

## 運行環境
Ubuntu 14.04 LTS  
gcc version 4.8.4  
编译标准：C99  

## 運行截圖
```
sudo su
modprobe brd rd_nr=1 rd_size=640
dd if=/dev/zero of=/dev/ram0 bs=512 count=1280
```
图2.2.1 创建及初始化ramdisk shell命令

![图2.2.2创建及初始化ramdisk shell执行记录截图](https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.2.2.png)  
 图2.2.2创建及初始化ramdisk shell执行记录截图  
本系统未自带ramdisk设备(/dev/ram)，使用图2.2.1命令创建及初始化ramdisk，运行结果如图2.2.2所示。

