# BitmapFileSystemOnLinux
Linux系統上基於Bitmap的檔案管理系统
## 題目要求
在Linux操作系统上，简单地实现一个基于位示图的文件系统  
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
編譯標準：C99  

## 運行結果
```
sudo su
modprobe brd rd_nr=1 rd_size=640
dd if=/dev/zero of=/dev/ram0 bs=512 count=1280
```
图2.2.1 创建及初始化ramdisk shell命令
<table >
<tr>
  <td><img width="100%" alt="image" src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.2.2.png" />

</tr>
  <tr>
    <td align="center"> 	 图2.2.2创建及初始化ramdisk shell执行记录截图  
  </td>
  </tr>
</table> 
本系统未自带ramdisk设备(/dev/ram)，使用图2.2.1命令创建及初始化ramdisk，运行结果如图2.2.2所示。

<table >
<tr>
  <td><img width="100%" alt="image" src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.3.png" />

</tr>
  <tr>
    <td align="center"> 	 图2.3 实现格式化截图   </td>
  </tr>
</table>   
图2.3展示了，ramdisk内原本有内容，执行格式化后，内容被清除。  
<table >
<tr>
  <td><img width="100%" alt="图2.4.1 获取目录内容截图（有内容）   " src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.4.1.png" />
</td>
  <td><img width="100%" alt="图2.4.2 获取目录内容截图（无内容） " src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.4.2.png" />
</td>
</tr>
  <tr>
    <td align="center">图2.4.1 获取目录内容截图（非空目录）    </td>
    <td align="center"> 图2.4.2 获取目录内容截图（空目录） 	</td>
  </tr>
</table>
图2.4.1和图2.4.2展示了，ramdisk内原本有内容时与无内容时获取目录内容函数执行结果。  




<table >
<tr>
  <td><img width="100%" alt="image" src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.5.png" />

</tr>
  <tr>
    <td align="center"> 	  图2.5 实现创建文件及目录截图   </td>
  </tr>
</table>

图2.5展示了，ramdisk创建文件及创建目录后，获取目录内容结果。  
<table >
<tr>
  <td><img width="100%" alt="image" src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.6.1.png" />
</td>
  <td><img width="100%" alt="image" src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.6.2.png" />
</td>
</tr>
  <tr>
    <td align="center">图2.6.1 实现复制文件/目录截图                          </td>
    <td align="center">     图2.6.2 实现复制文件截图	</td>
  </tr>
</table>

图2.6.1展示了，复制文件及创建目录后，获取目录内容结果。  
图2.6.2展示了，复制文件后文件内容成功被复制。  

<table >
<tr>
  <td><img width="100%" alt="image" src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.7.1.png" />
</td>
  <td><img width="100%" alt="image" src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.7.2.png" />
</td>
</tr>
  <tr>
    <td align="center">图2.7.1写入文件截图 </td>
    <td align="center"> 	  图2.7.2 读取文件截图   </td>
  </tr>
</table>

                                     
图2.7.1和图2.7.2展示了，写入文件与读取文件结果截图。  

<table >
<tr>
  <td><img width="100%" alt="image" src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.8.1.png" />
</td>
  <td><img width="100%" alt="image" src="https://raw.githubusercontent.com/Jaxx9527/BitmapFileSystemOnLinux/refs/heads/main/img/2.8.2.png" />
</td>
</tr>
  <tr>
    <td align="center">图2.8.1 文件删除截图 </td>
    <td align="center"> 图2.8.2 目录删除截图	</td>
  </tr>
</table>

    		       	 
图2.8.1和图2.8.2展示了，文件或目录删除功能结果截图。
