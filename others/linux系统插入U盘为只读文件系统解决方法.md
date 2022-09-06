使用linux不管是centos还是ubuntu的小伙伴都难免遇到插入U盘的时候，不能对U盘进行操作。提示权限不足或者是只读文件系统。

## 解决方法

1. 插入U盘，打开终端输入 `df -h` 查看U盘信息:

   ![image-20220901172027813](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220901172027813.png)

   这里是我的信息,　可以看到U盘文件系统为 `/dev/sdb1`，挂载点为`/media/root/E8EC-11F7`

2. 卸载U盘，在终端上输入以下命令

   ```shell
   sudo umount /media/root/E8EC-11F7   //根据你的U盘挂载点相应调整
   ```

   卸载之后一定不能拔掉U盘！！！

3.  修复U盘文件系统故障，在终端上输入以下命令

   ```shell
    sudo dosfsck -v -a /dev/sdb1          //根据你的U盘文件相应调整
   ```

4. 重新挂载U盘即可解决. (拔了再插)。

