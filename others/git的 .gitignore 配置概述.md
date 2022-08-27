# git的 .gitignore 配置概述



## **使用场景**

.gitignore 配置文件用于**配置不需要加入版本管理的文件**，配置好该文件可以为我们的版本管理带来很大的便利。比如项目的本地配置信息，如果你上传到Git中去其他人pull下来的时候就会和他本地的配置有冲突，所以这样的个性化配置文件我们一般不把它推送到git服务器中。

## 忽略文件的原则

- 忽略操作系统自动生成的文件，比如缩略图等；
- 忽略编译生成的中间文件、可执行文件等，也就是如果一个文件是通过另一个文件自动生成的，那自动生成的文件就没必要放进版本库，比如Java编译产生的.class文件；
- 忽略你自己的带有敏感信息的配置文件，比如存放口令的配置文件。
- 忽略一些没有必要上传的大文件、图片等

## Git忽略规则

详细的忽略规则可以参考[官方英文文档](https://git-scm.com/docs/gitignore)

可以组合官方[配置文档](https://github.com/github/gitignore)使用

#### 1、Git 忽略规则优先级

在 .gitingore 文件中，每一行指定一个忽略规则，Git 检查忽略规则的时候有多个来源，它的优先级如下（由高到低）：

- 从命令行中读取可用的忽略规则
- 当前目录定义的规则
- 父级目录定义的规则，依次递推
- $GIT_DIR/info/exclude 文件中定义的规则
- core.excludesfile中定义的全局规则

#### 2、Git 忽略规则匹配语法

在 .gitignore 文件中，每一行的忽略规则的语法如下：

- 空格不匹配任意文件，可作为分隔符，可用反斜杠转义
- `#` 开头的文件标识注释，可以使用反斜杠进行转义
- `!` 开头的模式标识否定，该文件将会再次被包含，**如果排除了该文件的父级目录，则使用 ! 也不会再次被包含。**可以使用反斜杠进行转义
- `/` 结束的模式只匹配文件夹以及在该文件夹路径下的内容，但是不匹配该文件
- `/` 开始的模式匹配项目跟目录
- 如果一个模式不包含斜杠，则它匹配相对于当前 .gitignore 文件路径的内容，如果该模式不在 .gitignore 文件中，则相对于项目根目录
- `**` 匹配多级目录，可在开始，中间，结束
- `?` 通用匹配单个字符
- `[]` 通用匹配单个字符列表

#### 3、常用匹配示例：

- `bin/`: 忽略当前路径下的bin文件夹，该文件夹下的所有内容都会被忽略，不忽略 bin 文件
- `/bin`: 忽略根目录下的bin文件
- `/*.c`: 忽略 cat.c，不忽略 build/cat.c
- `debug/*.obj`: 忽略 debug/io.obj，不忽略 debug/common/io.obj 和 tools/debug/io.obj
- `**/foo`: 忽略/foo, a/foo, a/b/foo等
- `a/**/b`: 忽略a/b, a/x/b, a/x/y/b等
- `!/bin/run.sh`: 不忽略 bin 目录下的 run.sh 文件
- `*.log`: 忽略所有 .log 文件
- `config.php`: 忽略当前路径的 config.php 文件

#### 3、定义Git全局的 .gitignore 文件

除了可以在项目中定义 .gitignore 文件外，还可以设置全局的 git .gitignore 文件来管理所有Git项目的行为。这种方式在不同的项目开发者之间是不共享的，是属于项目之上Git应用级别的行为。

这种方式也需要创建相应的 .gitignore 文件，可以放在任意位置。然后在使用以下命令配置Git：

```shell
git config --global core.excludesfile ~/.gitignore
```

#### 4、查看 gitignore 规则

如果你发下 `.gitignore` 写得有问题，需要找出来到底哪个规则写错了，可以用 `git check-ignore` 命令检查：

```shell
$ git check-ignore -v HelloWorld.cpp
.gitignore:1:*.cpp    HelloWorld.cpp
```

## 注意

.gitignore只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。解决方法就是先把本地缓存删除，然后再提交。