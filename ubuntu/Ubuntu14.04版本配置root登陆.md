# Ubuntu14.04版本配置root登陆

1. 普通用户启动后，打开终端，输入：sudo su,输入密码。

2. 在终端继续输入：gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf 打开配置文件。

3. 该文件内容增加：greeter-show-manual-login=true ，然后保存，关闭gedit编辑器。

4. 在终端继续输入：passwd root，设置root管理员密码。

5. 配置完成后重新启动，显示login登陆框，输入用户名：root，密码后进行登陆。

6. 首次登陆可能会提示：Error found when loading /root/.profile错误，按下面方法解决。

7. 终端输入：nano /root/.profile

8. 对mesg n行进行注释,在前面加上#

9. 增加一行 tty -s && mesg n，ctrl+x 保存并退出，输入Y，回车。

10. 终端输入 init 6 重启系统,设置完成。
    ————————————————
    版权声明：本文为CSDN博主「Coder-hong」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
    原文链接：https://blog.csdn.net/ai_ljh/article/details/110406566