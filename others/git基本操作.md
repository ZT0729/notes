# git基本操作

官方教程：[Git - Book (git-scm.com)](https://git-scm.com/book/zh/v2)

![git](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/git.jpg)

* 工作区：
* 暂存区：
* 本地仓库：
* 远方仓库：

git 的所有配置文件都是保存在本地！

查看不同级别的配置文件

```shell
#查看系统 config
git config --system --list

#查看当前用户（global）配置
git config --global --list
```

## git 相关的配置文件：

- Git\etc\gitconfit : git 安装目录下的 gitconfig --system 系统级

- C:\Users\Administrator\ .gitconfig 只适用于当前登录用户的配置 --global 全局

##  1. git 设置用户名与邮箱

首次安装 git 后先设置用户名和邮箱，之后每次 git 提交都会使用该信息，写入你的提交中。

```shell
git config --global user.name "tian"  #名称
git config --global user.email xxx@qq.com   #邮箱
```

## 2. 生成公钥和秘钥

```shell
ssh-keygen -t rsa -C "xxx@qq.com"
```

生成公钥和私钥，不需要设置名称与密码，按3次Enter。



查看公钥命令：

```shell
cat ~/.ssh/id_rsa.pub
```

或者直接去用文本编辑器打开公钥文件查看

公钥路径：`C:\Users\Administrator\.ssh\id_rsa.pud`    `Administrator`:为你当前登入的用户名。



## 3. 使用

### 3.1 初始化仓库

```shell
git init        //init     初始化所在文件夹
```

初始化后，文件夹内会多出来一个 `.git` 的隐藏文件夹。git 的所有记录都在这个文件夹内，一般来说我们不需要去研究里面文件的作用。

![image-20220824221322203](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220824221322203.png)

初始化以后，所在文件夹在终端上会显示 `master`，也就是我们的主分支。初始化后默认处于主分支上。

![image-20220824221933987](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220824221933987.png)

### 3.2 查看仓库状态

```shell
git status       //因为 git 里有好几个区，你可能操作着就不知道自己在那个状态了，可以使用git status 查看
```

![image-20220824223039610](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220824223039610.png)

可以知道当前分支在 master 主分区上；你还没有任何提交信息；有一个未追踪文件 也就是 xx.md 还没有加入暂存区。就需要使用 `git add` 命令来将 xx.md 加入暂存区。

### 3.2 将文件添加到暂存区

```shell
git add xx.md   //添加 xx.md 到暂存区。
```

再次使用 `git status` 查看下

![image-20220824223910501](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220824223910501.png)

就可以看到可以进行 `git commit` 提交的文件。

在进行 `git commit` 将文件提交给本地仓库。

### 3.3 commit 提交

``` shell
git commit \\提交到本地仓库
```

输入完后进入 `commit` 提交信息界面，由于默认是 vim 编辑器，所以使用 vim 进行编辑，(`i` 进入输入模式，`esc` 退到命令模式，`:wq` 在命令模式下输入 退出并保存，`:q!` 在命令模式下输入 退出不保存）`#` 号后面是被注释 不显示的，所以在第一行输入就可以了。

![image-20220824224844539](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220824224844539.png)

输入完信息直接  `:wq` 退出保存。

![image-20220824225002589](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220824225002589.png)输入完后退出到刚刚的界面，这里也会提示一个文件被修改，插入一条信息

![image-20220824225300229](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220824225300229.png)

这时再次 `git status`

![image-20220824225547050](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220824225547050.png)

这里可以看到提示说工作区已经没有东西了，也就是我们把所有文件都提交到本地版本库了。



#### 3.3.1 以下情况：（已追踪文件修改后）

xx.md 新建一行版本2 保存。

然后将 `git add` 添加到暂存区。

之后再在 xx.md 中新增1行 版本3。

再使用 `git status` 会发现该文件有两种状态。

![image-20220825003417494](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825003417494.png)

xx.md 文件同时出现在暂存区和非暂存区，实际上 Git 只不过暂存了你运行 `git add` 命令时的版本。 如果你现在提交，`xx.md` 的版本是你最后一次运行 `git add` 命令时的那个版本，而不是你运行 `git commit` 时，在工作目录中的当前版本。 所以，运行了 `git add` 之后又作了修订的文件，需要重新运行 `git add` 把最新版本重新暂存起来。

再次运行 `git add` 将文件重新暂存起来，之后在使用 `git status` 查看状态。

![image-20220825003902945](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825003902945.png)

之后在`git commit` 就可以了 。

`git commit` 不需要每次都进入 vim编辑器里添加提交信息，只需要在后面加上 `-m` ,后面双引号里添加提交信息就可以了。适合提交简单的信息。![image-20220825004302316](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825004302316.png)

### 3.4 查看之前提交版本

之后我们可以使用 `git log` 来查看前面版本。 

![image-20220825004532749](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825004532749.png)

可以看到有两个版本，除了提交的版本信息以外，还可以看到是谁提交的。还可以看到一串哈希数字，代表每次不同的 commit。HEAD-> 表示我们现在在 master 主分支上。

### 3.5 忽略文件

在实际开发中肯定会遇到不需要提交的文件，就需要让 `git` 来忽略掉这些文件。

比如创建一个 sex.jpg 图片文件，不需要提交到仓库中。

可以创建 .gitignore 文件，可以用 `touch` 命令来创建， 之后在用 `git status` 查看状态。

![image-20220825011034499](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825011034499.png)

可以看到两个文件都可以看到图片还存在。

只需在 .gitignore 文件内添加文件名称和后缀就表示我们要忽略的文件。之后在 `git status` 下 就可以看不到图片未追踪提示了。

![image-20220825011427028](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825011427028.png)

## 4.操作分支

![](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/git%20%E6%B5%81%E7%A8%8B%E5%88%86%E6%94%AF.jpg)

### 4.1 创建新分支

使用 使用 `git branch` 命令添加新分支

```shell
git branch bad-boy       //添加名为 bad-boy 的分支
```

添加分区后不会马上跳转到新分支上，先用 `git branch` 查看是否创建成功。

![image-20220825192855040](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825192855040.png)

可以看到 bad-boy 分支创建成功。

### 4.2 切换分支

使用 `git checkout` 切换到新分支上

```shell
git checkout bad-boy   //切换到新分支上。
```

![image-20220825193200904](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825193200904.png)

切换成功，文件夹里的文件是直接从 master 主支那里复制过来的。

假设将 xx.md 和 sex.jpg 删除掉，并提交到版本库，会对主支有影响吗？

git commit -a 就是直接可以从工作区一下子进入到本地版本库。

在使用 `git checkout master`切换到主分支就知道有没有问题了。

![image-20220825194058728](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825194058728.png)可以看到 xx.md 已经回来了，但 sex.jpg 文件没有回来，没办法因为我们让 git 不要去追踪那张照片。

### 4.3 删除分支

我们可以用 `git branch -d + 分支名` 进行删除，

![image-20220825194409902](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825194409902.png)这里会提示我们还为把分支合并过来。

如果我们非常确定删除一个分支的时候可以用 -D 来代替 -d。

![image-20220825194613705](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825194613705.png)

如果我们要创建分支，并且马上切换到新分支上，可以使用 `git checkout -b`

```shell
git checkout -b temp  //新建temp分支并切换到这个分支上
```

![image-20220825194914441](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825194914441.png)

在 xx.md 新增一行，并且把新增内容合并到主支 master 里。

增加完后在 `git checkout` 换到主分支看下是否也有被增加，

### 4.4 合并

`git merge` 是把别的分支合并到当前所处的分支上，从其他地方合并过来，

合并后再在 xx.md 新整一条内容，并提交下 -a 和 -m 可以写到一起。

![image-20220825200212274](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825200212274.png)现在 temp 分支 xx.md 是没有第 5 行的,如果 temp 分支也新增第 5 行但是和主分支的不一样，提交 commi t一下。

现在再将 master 内容合并过来，

会发现有冲突，并且文本上也有提示![image-20220825201738914](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825201738914.png)

HEAD 部分表示我们当前位置，下面就是合并过来的内容。也就是 master 的内容。

我们只需自己修改文本选择正确的就可以了，当然可以使用 merge 工具来处理。

## 5. 远程仓库 （Github）

现在远程仓库创建好项目然后把项目复制到本地。

或者。

在本地创建好项目推送到远程仓库上。

### 5.1 Github创建仓库

注册登入好 github，在首页右上角点击 + 号，创建仓库。

![image-20220825204602505](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825204602505.png)

点击好后![image-20220825204911666](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825204911666.png)

设置完就可以点击下方 Create repository 进行创建了。相当于执行了 `git init  ` 命令。

![image-20220825205232037](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825205232037.png)

先创建一个文件

![image-20220825205359154](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825205359154.png)

之后滚动到页面下方填写 commit 的主题和内容

![image-20220825205606265](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825205606265.png)

最后就可以点击 commit new file，相当于执行了 `git add ` 和 `git commit`。



### 5.2设置ssh免密登录

配置好后 ssh 就不用在提示需要登录。

找到本地 git 生成的公钥，用编辑器打开将内容复制。

打开你的 github 主页，进入个人设置 -> SSH and GPG keys -> New SSH key，把复制的内容粘贴进去，title 随便填，保存即可，我们的公钥就添加成功了，设置好如下图

![image-20220905225902958](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220905225902958.png)

检测是否设置成功：

输入命令：   

```shell
ssh -T git@github.com 
```

如果提示 Are you sure you want to continue connecting (yes/no)?，输入 yes，然后会看到：

Hi xxx! You've successfully authenticated, but GitHub does not provide shell access.

看到这个信息说明SSH已配置成功！ 



### 5.3 克隆远程仓库到本地仓库

假设要把本地仓库复制到本地，可以点击仓库 Code 按钮，如果我们直接选择 Download 就只会下载当前最新版本的文件，而其中的版本历史和记录不会下载。![image-20220825210045625](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825210045625.png)也就是压缩文件里没有 .git 文件夹的，那就肯定要用 Clone 了，直接在 https 下链接旁旁边点击赋值按钮，就可以把连接复制下来。接着在git bash 命令行直接使用 `git clone + 刚刚的连接`就可以拷贝远程仓库了

![image-20220825210521393](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825210521393.png)

![image-20220825210649730](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825210649730.png)

在 Github 上一开始的主支名字叫 “main”，而如果我们在本地使用 git 不进行设置的话，主支名字则是 master。

现在在 linn.md上新增一行内容，并 commit 提交下。

### 5.4 查看本地厂仓库与那些厂库有联系

先用 `git remote -v` 来查看下本地仓库和那些远程仓库有联系，因为是刚刚从 Github 上复制下来当然就会显示那个 Github 远程仓库的地址了。

![image-20220825211438265](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825211438265.png)

origin 代表远程仓库的名字，这样你 push 的时候就可以用 origin 来代替 url 了

### 5.5 推送到远程仓库

比如你要更新到远程仓库，就可以使用 `git push ` 根据提示操作

![image-20220825211821439](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825211821439.png)

就可以在 github 上看到已经成功把本地仓库内容更新到远程仓库了。

![image-20220825212040164](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825212040164.png)

如果在远程仓库上新增一行内容，![image-20220825212157179](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825212157179.png)然后还是提交下 commit。

### 5.6 拉取远程仓库到本地仓库

我们可以使用 `git fetch`，我们的本地文件是暂时不会发生变动的，只是拉到了本地版本库，fetch 是可以指定远程仓库和分支名的。

### 5.7 本地厂库与远程仓库对比

我们想知道本地版本库和远程仓库的区别，这时候就需要用到git diff，直接在后面加上远程仓库名和分支名就可以看到区别了。![image-20220825212715317](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220825212715317.png)

### 5.8 远程厂库拉取到工作区

如果没问题就直接用git pull把远程仓库的内容直接整合到工作区，这个时候如果我们使用git log就可以看到所有的历史版本了。而且本地文件也已经被修改了。

`git pull = git fetch + git merge`



