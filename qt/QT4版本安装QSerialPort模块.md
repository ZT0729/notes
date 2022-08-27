# QT4 版本安装 QSerialPort模

之前qt代码是用 qt5 写的，之后移植到 qt4 上就会报错，提示这个找到这个库。由于是 qt4 的版本，所以不能直接使用 qt 自带的 QSerialPort 模块，需要手动添加一下

![image-20220820151451572](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220820151451572.png)

方法如下：

1. 先下载模块包（qtserialport-opensource-src-5.3.2.rar），下载地址：https://wwu.lanzouv.com/iegbr09w3vpg

2. 下载后，解压后会发现一个 qtserialport.pro ，先将。user删除，然后用qt打开这个项目。![image-20220820152252661](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220820152252661.png)

3. 之后点击项目->构建–>添加构建步骤–>make–>在Make参数栏填写 `install`![image-20220820152745798](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220820152745798.png)

4. 之后点击编译。编译就安装完成l。添加完成后看下添加的是 Release 还是 Debug 版本![image-20220820153057269](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220820153057269.png)

5. 之后在项目中的pro文件里添加 `CONFIG += serialport`

6. 在头文件中添加

   ```C++
   #include <QtSerialPort/QSerialPort>
   #include <QtSerialPort/QSerialPortInfo>
   ```

7. 这就完成了。