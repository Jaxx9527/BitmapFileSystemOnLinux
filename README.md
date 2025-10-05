# BitmapFileSystemOnLinux
Linux系統上基於Bitmap的檔案管理系统
## 題目要求
1. 为了方便文件系统的编写和测试，最好在VMWare虚拟机上实现。
2. Linux操作系统一般都会自带ramdisk设备(/dev/ram)，它能把一部分内存模拟成一个磁盘。所以，在实验的过程中可以使用ramdisk作为块设备，而不需要专门为该文件系统直接创建一个磁盘分区。
3. 文件系统的实现推荐参考Linux内核源代码中minix文件系统的实现方式。它的实现在(Linux内核源码目录/fs/minix/)目录中。
