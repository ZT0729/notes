# 虚拟机ubuntu和windows主机之间无法复制粘贴问题

我是在 VMware虚拟机安装的 Ubuntu14.04 版本的，安装完之后，也安装了VMware Tools。但就是无法在两者之间进行粘贴和复制，也无法互拖文件。在网上找到方法如下：

### 1. 先更新一下软件列表

```shell
sudo apt-get update
```

### 2. 安装VMware tools

```shell
sudo apt-get autoremove           #卸载已有工具
sudo apt-get install open-vm-tools    #安装open-vm-tools
sudo apt-get install open-vm-tools-desktop     #open-vm-tools
```

### 3. 重启Ubuntu

```shell
shutdown -r now
```

重启Ubuntu之后，发现就可以和Windows主机之间相互复制粘贴，拖文件了。