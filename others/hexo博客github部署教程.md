# hexo博客github部署教程

## 1. 安装 node.js

### 1.1 下载 node.js 安装包

[Node.js (nodejs.org)](https://nodejs.org/zh-cn/)

直接登入上方链接Node.js 官网下载长期维护版，稳定性更好一些，bug 少![image-20220904213118725](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904213118725.png)

### 1.2 安装

之后双击打开安装包，之后点击 Next，![](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904213229476.png)一勾选协议，再点击Next，![image-20220904213359700](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904213359700.png)

设置安装位置，默认C盘，可自定义，这里我安装在D盘![image-20220904213812221](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904213812221.png)

下图根据本身的需要进行，我选择了默认Node.js runtime，而后Next

Node.js runtime ：表示运行环境
npm package manager：表示npm包管理器
online documentation shortcuts ：在线文档快捷方式
Add to PATH：添加到环境变量

![image-20220904214114650](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904214114650.png)

之后默认不勾选，点击Next。再点击安装。

![image-20220904214200148](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904214200148.png)

![image-20220904214306877](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904214306877.png)

之后等待，下图，就安装完成了。

![image-20220904214331501](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904214331501.png)

### 1.3 查看环境变量

安装完成后，.msi格式的安装包已经将[node](https://so.csdn.net/so/search?q=node&spm=1001.2101.3001.7020)启动程序添加到系统环境变量path中,能够在系统变量中进行查看验证，我这里是win11：在【设置】右键→【系统】→【高级系统设置】打开系统属性，再点击点击【高级】→【环境变量】。

![image-20220904214927381](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904214927381.png)选中 Path，再点击编辑。

![image-20220904215140806](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904215140806.png)

可以看到 node.js 已经添加到环境变量。

![image-20220904215459210](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904215459210.png)

打开命令行输入 `node -v` 和 `npm -v` 查看 node 和npm 的版本，出现就是安装成功了。

![image-20220904215934451](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904215934451.png)

 默认状况下，我们在执行 `npm install -g XXXX` 时，下载了一个全局包，这个包的默认存放路径C:\Users\Administrator\AppData\Roaming\npm\node_modules（Administrator 为你电脑管理员的用户名，我这里是48228）下，能够经过CMD指令 `npm root -g` 查看。

![image-20220904220107833](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904220107833.png)

npm常用命令：

>* npm -v：查看 npm 安装的版本。
>* npm init：会引导你建立一个 package.json 文件，包括名称、版本、作者等信息。
>* npm list：查看当前目录下已安装的 node 包。
>* npm ls：查看当前目录下已安装的 node 包。
>* npm install moduleNames：安装 Node 模块到本地目录node_modules下。
>* npm install < name > -g：将包安装到全局环境中。
>* npm install < name > --save：安装的同时，将信息写入package.json中，项目路径中若是
>* package.json 文件时，直接使用 npm install 方法就能够根据 dependencies 配置安装全部的依赖包，这样代码提交到git时，就不用提交 node_modules 这个文件夹了。
>* npm install < name> --save-dev：安装的同时，将信息写入 package.json 中项目路径中若是有package.json 文件时，直接使用 npm install 方法就能够根据 devDependencies 配置安装全部的依赖包，这样代码提交到git时，就不用提交 node_modules 这个文件夹了。
>* npm uninstall moudleName：卸载 node 模块。

### 1.4 环境配置

1. 打开安装的目录（默认安装情况下在C:\Program Files\nodejs）

2. 在安装目录下新建两个文件夹【node_global】和【node_cache】![image-20220904220831792](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904220831792.png)

3. 再次打开CMD命令窗口，输入 `npm config set prefix “你的路径\node_global”`（`“你的路径”默认安装的状况下为 C:\Program Files\nodejs`）

4. 再输入 `npm config set cache “你的路径\node_cache” ` ，执行的时候用管理员权限打开CMD，否则有可能会提示权限不够报错。![image-20220904221349135](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904221349135.png)

5. 设置环境变量，在`系统变量`中新建

   变量名：`NODE_PATH`

   变量值：`你的安装路径\node_global\node_modules`

   （ 用来告诉系统， 下载的模块或者包都在这里了）

   ![image-20220904221738990](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904221738990.png)

6. 编辑 `用户变量（环境变量）`的 Path，将默认的 C 盘下 `APPData\Roaming\npm` 修改成 `你的路径\node_global`，点击确定![image-20220904222107155](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904222107155.png)

7. 最后在`系统变量` 中 Path 里添加 %NODE_PATH%![image-20220904222521841](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904222521841.png)

8. 配置完成后，安装个module测试下，打开cmd窗口，输入以下命令 `npm install express -g`  进行模块的全局安装。![image-20220904222746084](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904222746084.png)在刚刚创建的文件夹中就可看到安装的 express 模块。![image-20220904222906097](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904222906097.png)

9. 更换 npm 模块源为淘宝镜像源。 [淘宝 NPM 镜像]([npmmirror 中国镜像站](https://npmmirror.com/)) 。在 CMD 中输入下列命令。

```
npm config set registry https://registry.npmmirror.com
```

![image-20220904223627113](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904223627113.png)

使用定制的 cnpm (gzip 压缩支持) 命令行工具代替默认的 npm（cnpm的用法与npm的用法相同，只是npm在执行命令时被更改为cnpm）:

```
npm install -g cnpm --registry=https://registry.npmmirror.com
```

![image-20220904224918393](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220904224918393.png)

## 2. 安装hexo

打开 git bash 输入以下命令

```shell
npm install -g hexo
```

运行以下命令查看 hexo 版本

```shell
hexo -v
```

首先创建一个文件夹用来存放博客文件（最好路径不要包含中文），比如我在 F:/public/hexo 在用 git bash 使用 cd 命令进入该文件夹（或者直接在文件夹内用右键打开 git bash，）。

```shell
cd F:/public/hexo
```

再使用 `hexo init` 命令来初始化这个文件夹

![image-20220905223232699](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220905223232699.png)出现 Start blogging with Hexo！ 就是初始化完成。

可以使用 `hexo s` 命令进行本地部署。

![image-20220905223445332](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220905223445332.png)

本地部署就完成了，命令行不要关，在浏览区输入 http://localhost:4000 就可打开部署的网站，在命令行中安 ctrl+c 停止部署。网站画面如下。

![image-20220905223641062](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220905223641062.png)

## 3. 将Hexo部署到Github

### 3.1 Github创建个人仓库
首先，需要有一个github账号。登上账号后建一个仓库：仓库名为你的用户名.github.io，
举例如下：
创建一个和你用户名相同的仓库，后面加.github.io，
只有这样，将来要部署到GitHub的时候，才会被识别，也就是xxx.github.io，其中xxx就是你注册GitHub的用户名.![image-20220905225104577](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220905225104577.png)

### 3.2 配置SSH免密登录

设置ssh免密登录，配置好后 ssh 就不用在提示需要登录。

找到本地 git 生成的公钥，用编辑器打开将内容复制。

打开你的github主页，进入个人设置 -> SSH and GPG keys -> New SSH key，把复制的内容粘贴进去，title随便填，保存即可，我们的公钥就添加成功了，设置好如下图

![image-20220905225902958](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220905225902958.png)

检测是否设置成功：

输入命令：   

```shell
ssh -T git@github.com 
```

如果提示 Are you sure you want to continue connecting (yes/no)?，输入 yes，然后会看到：

Hi xxx! You've successfully authenticated, but GitHub does not provide shell access.

看到这个信息说明SSH已配置成功！ 

### 3.3 安装hexo-deployer-git 插件

在博客文件夹中打开 git bash 输入下面命令，安装 hexo-deployer-git 插件

```shell
npm install hexo-deployer-git --save
```

之后修改博客文件夹内 _config.yml 文件。在 # Deploment 如图修改

![image-20220905231031193](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220905231031193.png)

> type：部署类型  我们用 git
>
> repo：仓库地址，就是 github 你要部署的仓库ssh链接
>
> branch：部署分支，主分支 main

### 3.4 上传

在博客文件夹中打开 git bash 依次执行下面命令

```shell

hexo cl   #清除缓存文件 db.json 和已生成的静态文件 public
hexo g       #生成网站静态文件到默认设置的 public 文件夹(hexo generate 的缩写)
hexo d       #自动生成网站静态文件，并部署到设定的仓库(hexo deploy 的缩写)

```

之后再上 github 博客的仓库，就可以看到你的博客文件夹内文件都上传到github博客仓库了，就表示成功了。

![image-20220905232427146](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220905232427146.png)

现在就可以使用xxx.github.io来访问你的博客了，xxx为你的用户名。

![image-20220905232633386](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220905232633386.png)

## 4. 安装主题

这里推荐 [Butterfly](https://butterfly.js.org/) 这就上它的文档网站就有详细的安装教程，这里就不多讲了。
