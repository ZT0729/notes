# ubuntu14.04 安装 svn 图形化客户端 RabbitVCS

在 Windows 端用的是 TortoiseSVN，鼠标右击非常方便，并文件图标都有状态说明。所以在 ubuntu 就非常不想用命令行，太折磨人了。在网上查了查 发现 RabbitVCS  与 TortoiseSVN 操作都挺像的。就记录下安装方式 也防止以后不知道怎么安装要现搜索。

## 1. 将 RabbitVCS 添加到源里。

**命令**：

```shell
sudo add-apt-repository ppa:rabbitvcs/ppa
```

一路回车。

## 2.导入秘钥

如果第一步出现了秘钥key，那就不用输入这个命令了

**命令**：

```c++
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 34EF4A35
```

同一路回车。

## 3. 更新软件源

**命令**：

```c++
sudo apt-get update
```

等着就好了。

## 4. 安装依赖库

**命令**：

```c++
sudo apt-get install python-nautilus python-configobj python-gtk2 python-glade2 python-svn python-dbus python-dulwich subversion meld
```

一路回车

## 5. 安装RabbitVCS

好像是 ubuntu 版本 >=12.04 的 nautilus 用的是 3 版本；如果是ubuntu 版本 <12.04 就是 nautilus 不是nautilus3。

**命令**：

```shell
sudo apt-get install rabbitvcs-cli  rabbitvcs-core rabbitvcs-gedit rabbitvcs-nautilus3
```

## 6. 检查右击有没有RabbitVCS SVN

在文件目录里鼠标右击下看看右击菜单里有没有RabbitVCS SVN。如果没有重启下文件管理器。

![image-20220822221646969](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220822221646969.png)

**命令**：

```shell
nautilus -q  
```



  