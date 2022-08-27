# [VMware虚拟机映射磁盘出错](https://www.cnblogs.com/Wikix/p/16554741.html)

虚拟机版本：VMware® Workstation 16 Pro 16.2.4 build-20089737

设置磁盘映射时，如果取消勾选只读，发现磁盘无法打开，显示一个问号。

出现这个是因为16.2.4版本的vstor2-x64.sys文件有BUG，替换之前版本的即可。

经测试VMware-workstation-full-16.1.2版本的文件是正常可用的，我已提取出来。

如担心文件不安全被篡改，可自行找一台电脑安装上述版本的然后提取。

 

**解决方法：**

1、下载此文件，「vstor2-x64.sys」下载链接：https://www.aliyundrive.com/s/49kKH81Xbf8

2、重启进入PE，进路径C:\Windows\SysWOW64\drivers，把下载的文件拖进去替换原来的。（PE下路径注意找到系统盘路径）

这里进入PE是因为在当前系统有进程占用此文件了，无法替换。

3、重启电脑即可。