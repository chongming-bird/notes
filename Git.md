# 【Git】

## Git简介

> **Git是一个免费的、开源的分布式版本控制系统**，可以快速高效地处理从小型到大型的各种项目
>
> - Git Bash : Unix和Linux风格的命令行，使用最多，推荐最多
> - Git CMD：Windows风格的命令行
> - Git GUI：图形化命令行
>
> **版本控制：**
>
> | 版本 | 文件名      | 用户 | 说明                   | 日期       |
> | :--- | :---------- | :--- | :--------------------- | :--------- |
> | 1    | service.doc | 张三 | 删除了软件服务条款5    | 7/12 10:38 |
> | 2    | service.doc | 张三 | 增加了License人数限制  | 7/12 18:09 |
> | 3    | service.doc | 李四 | 财务部门调整了合同金额 | 7/13 9:51  |
> | 4    | service.doc | 张三 | 延长了免费升级周期     | 7/14 15:17 |
>

### 版本控制

> 版本控制（Revision control）是一种在开发过程中用于管理我们对文件、目录或工程等内容的修改历史，方便查看更改历史记录，备份以便恢复以前的版本的软件工程技术。
>
> - 实现跨区域多人协同开发
> - 追踪和记载一个或者多个文件的历史记录
> - 组织和保护你的源代码和文档
> - 统计工作量
> - 并行开发、提高开发效率
> - 追踪记录整个软件的开发过程
> - 减轻开发人员的负担，节省时间，同时降低人为错误
>

简单来说就是用于管理多人协同开发项目的技术

没有进行版本控制或版本控制本身缺乏正确的流程管理，在软件开发过程中会引入许多问题，比如软件代码的一致性、软件内容的冗余、软件过程的事物性、软件开发过程中的并发性、软件源代码的安全性，以及软件的整合问题。

### 工作机制

**Git有三个分区：本地库、暂存区和工作区**

![image-20220702063423364](https://chongming-images.oss-cn-hangzhou.aliyuncs.com/images-masterimage-20220702063423364.png)

![image-20220702064104923](https://chongming-images.oss-cn-hangzhou.aliyuncs.com/images-masterimage-20220702064104923.png)

- **工作区（Working Directory）**

  是我们直接编辑的地方，例如IDEA正在编写的代码、记事本打开的文本等，肉眼可见，直接操作。

- **暂存区（Stage 或 Index）**

  数据暂时存放的区域，可在工作区和版本库之间进行数据的交流，工作区的代码需要先添加到暂存区。

- **本体库（commit History）**

  存放已经提交的数据，push的时候，就是把这个区的数据 push到远程仓库了。

**git的工作流程：**

1. 在工作区中增删、修改文件；
2. 将需要进行版本管理的文件放入暂存区域；
3. 将暂存区域的文件提交到git仓库。

因此，git管理的文件有三种状态：已修改（modified）,已暂存（staged）,已提交(committed)

**Git中无法单独删除一个版本的代码，只能基于上一个版本提交一个删除所需代码的新版本**

### 代码托管中心

> 代码托管中心是基于网络服务器的代码远程仓库，我们一般简单称为远程库

 **代码托管中心分类：**

- **局域网**

  GitLab

- **互联网**

  GitHub（外网）

  Gitee 码云（国内网站）

## 安装

> 官网地址： https://git-scm.com/

## 常用命令

### 命令列表

|                  命令                   |      作用      |
| :-------------------------------------: | :------------: |
|           `git config --list`           |  查看已有配置  |
| `git config --global user.name 用户名 ` |  设置用户签名  |
|  `git config --global user.email 邮箱`  |  设置用户签名  |
|               `git init `               |  初始化本地库  |
|              `git status`               | 查看本地库状态 |
|            `git add 文件名`             |  添加到暂存区  |
|    `git commit -m "日志信息" 文件名`    |  提交到本地库  |
|              `git reflog`               |  查看历史记录  |

|           命令           |             作用             |
| :----------------------: | :--------------------------: |
| `git checkout -- <file>` |        丢弃工作区更改        |
| `git reset HEAD <file>`  |        丢弃暂存区更改        |
| `git reset --hard HEAD^` | 丢弃本地版本库更改(版本穿梭) |
|        `自求多福`        |      丢弃远程版本库更改      |

### 设置用户签名

**语法：**

```bash
git config --global user.name 用户名

git config --global user.email 邮箱

# 查看已设置信息
git config --list
```

**说明：**

签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看到，以此确认本次提交是谁做的。

Git 首次安装必须设置一下用户签名，否则无法提交代码。

**注意：**设置用户签名和将来登录GitHub（或其他代码托管中心）的账号没有任何关系。

```txt
[user]
	name = Chongming
	email = shuejian2190427@163.com
[core]
	autocrlf = true
```

### 初始化本地库

> 初始化本地库，即将当前文件夹交给git管理

**语法：** 

```bash
# 在需要初始化的文件夹下执行
git init	
```

初始化后，会在当前目录下生成一个隐藏目录：`.git`

### 查看本地库状态

**语法：** 

```bash
# 在需要查看的本地库下执行
git status
```

- **首次查看（工作区无文件）：**

```ba
$ git status
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
```

### 添加到暂存区

> 将工作区的文件添加到暂存区

**语法：**

```bash
git add 文件名
## 回退
git reset HEAD 回退
```

- **工作区有文件未添加到暂存区时：**

```bash
$ git status
On branch master
No commits yet
# 提示有未被追踪的文件
Untracked files:
 (use "git add <file>..." to include in what will be committed)
 hello.txt
nothing added to commit but untracked files present (use "git add" 
to track)
```

- **暂存区有新文件未被提交：**

```bash
$ git status
On branch master
No commits yet
# 提示有更改未被提交
Changes to be committed:
# 提示删除暂存区文件的命令如下：
 (use "git rm --cached <file>..." to unstage)
 new file: hello.txt
```

- **工作区有文件被修改：**

```bash
On branch master
# 提示修改未被添加到暂存区
Changes not staged for commit:
 (use "git add <file>..." to update what will be committed)
 # git checkout -- 文件名 可以放弃工作区的修改，让工作区的文件回到最近一次add或commit的状态
 (use "git checkout -- <file>..." to discard changes in working 
directory)
 modified: hello.txt
no changes added to commit (use "git add" and/or "git commit -a")
```

### 提交本地库

**语法：**

```bash
git commit -m "日志信息" 文件名
```

- **成功提交后**

```bash
[master (root-commit) 33bb3d1] practice o be committed:
 1 file changed, 1 insertion(+)
 create mode 100644 heelo.txt
```

### 查看历史版本

**语法：**

```bash
git log 查看版本详细信息
# git log --pretty=oneline
```

```bash
git reflog 查看历史命令
# 英文状态下按Q退出
```

### 版本穿梭

**语法：**

```bash
git reset --hard 版本号
# 回到上一个提交
git reset --hard HEAD^
# 回到上上一个提交
git reset --hard HEAD^
# 回到上100个提交
git reset --hard HEAD~100
```

**效果：**

```bash
--首先查看当前的历史记录，可以看到当前是在 8ca5c3b 这个版本
$ git reflog
8ca5c3b (HEAD -> master) HEAD@{0}: commit: second
33bb3d1 HEAD@{1}: commit (initial): practice

--切换到 33bb3d1 版本，也就是第一次提交的版本
$ git reset --hard 33bb3d1
HEAD is now at 33bb3d1 practice o be committed:


--切换完毕之后再查看历史记录，当前成功切换到了 86366fa 版本
$ git reflog
33bb3d1 (HEAD -> master) HEAD@{0}: reset: moving to 33bb3d1
8ca5c3b HEAD@{1}: commit: second
33bb3d1 (HEAD -> master) HEAD@{2}: commit (initial): practice
```

## 忽略文件

有些某些文件不需要纳入版本控制中，比如数据库文件，临时文件，设计文件等

可以在主目录下建立".gitignore"文件，此文件有如下规则：

1. 忽略文件中的空行或以井号（#）开始的行。
2. 可以使用Linux通配符。例如：
   - 星号（*）代表任意多个字符
   - 问号（？）代表一个字符
   - 方括号（[abc]）代表可选字符范围
   - 大括号（{string1,string2,...}）代表可选的字符串等。

3. 如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略。
4. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下。
5. 如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。

```bash
# 为注释
*.txt        # 忽略所有.txt结尾的文件
!lib.txt     # lib.txt除外
/temp        # 仅忽略项目根目录下的temp文件
build/       # 忽略build/目录下的所有文件
doc/*.txt    # 会忽略doc目录下所有的.txt结尾的文件
```

## 分支管理

### 简介

> ![image-20220702073233862](https://chongming-images.oss-cn-hangzhou.aliyuncs.com/images-masterimage-20220702073233862.png)
>
> 在版本控制过程中，同时推进多个任务，可以为每个任务创建单独分支。使用分支意味着程序员可以把自己的工作从开发主线上分离开来，开发自己分支的时候，不会影响主线分支的运行。
>
> 分支底层其实也是指针的引用。
>
> 分支的好处：
>
> - 同时并行推进多个功能的开发，提高开发效率
> - 各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支造成任何影响，把失败的分支删除重新开始即可。

### 命令列表

|          命令          |             作用             |
| :--------------------: | :--------------------------: |
|  `git branch 分支名`   |           创建分支           |
|    `git branch -v`     |           查看分支           |
|    `git branch -a`     |      查看本地和远程分支      |
| `git checkout 分支名`  |           切换分支           |
| `git branch -d 分支名` |           删除分支           |
|   `git merge 分支名`   | 把指定的分支合并到当前分支上 |

当需要临时切换分支时,使用`git stash`保存当前分支的工作区,以便切换回来后可以继续工作

|               命令                |        作用        |
| :-------------------------------: | :----------------: |
|            `git stash`            |      保存草稿      |
|         `git stash list`          |     查看草稿箱     |
|         `git stash apply`         |      恢复草稿      |
|         `git stash drop`          |      删除草稿      |
|          `git stash pop`          |   恢复并删除草稿   |
| `git stash apply|drop <stash-id>` | 恢复\|删除指定草稿 |

### 合并分支

**语法：**

```bash
# 拉取分支
git pull 别名 分支

# 在当前分支的基础上合并另一个分支
git merge 要合并的分支名
```

**冲突：**

合并分支时，两个分支在同一个文件的同一个位置有两套完全不同的修改，Git 无法替我们决定使用哪一个，必须人为决定新代码内容。

**产生冲突：**

```bash
$ git merge hot-fix
Auto-merging heelo.txt
CONFLICT (content): Merge conflict in heelo.txt
Automatic merge failed; fix conflicts and then commit the result.

# 假如当前分支有冲突：
lenovo@DESKTOP-GPUT1FD MINGW64 ~/Desktop/git练习 (master|MERGING)
```

**解决冲突：前往有冲突的文件进行修改**

```bash
# git会自动标识出有冲突的代码
<<<<<<< HEAD
当前分支的代码
=======
要合并分支的代码
>>>>>>> 分支名

# 示例：
<<<<<<< HEAD
holle warlb！
是单都怕我
=======
hello world！
砸瓦鲁多
>>>>>>> hot-fix
```

**解决冲突后需要重新添加到暂存区并提交**

### 变基合并

> `git` 鼓励大量使用分支---**"早建分支!多用分支!"**
>
> 其一，多用分支并不会造成太多存储开销
>
> 其二，多建分支有利于分解工作逻辑
>
> 因此，新功能的开发、bug的修复都可以建立新的分支
>
> 缺点就是过多的分支会导致分支错综复杂，难以理清

**`git rebase`**：对某一段线性提交历史进行编辑、删除、复制、粘贴

**PS: **不要用`rebase`玩已经提交到公共仓库的commit，自己瞎搞的分支除外

#### 合并commit

如图: 希望将BCD的提交合并成一个提交

![img](https://chongming-images.oss-cn-hangzhou.aliyuncs.com/images-master202311201651833.webp)

```bash
 # -i = --interactive 弹出交互式界面
 # startpoint endpoint 编辑区间,通过版本id
 # 不指定endpoint,则区间默认终点是当前HEAD所指向的commit
 # 前开后闭区间
 git rebase -i [startpoint]  [endpoint]
```

![img](https://chongming-images.oss-cn-hangzhou.aliyuncs.com/images-master202311201705572.webp)

> - pick：保留该commit（缩写:p）
> - reword：保留该commit，但我需要修改该commit的注释（缩写:r）
> - edit：保留该commit, 但我要停下来修改该提交(不仅仅修改注释)（缩写:e）
> - squash：将该commit和前一个commit合并（缩写:s）
> - fixup：将该commit和前一个commit合并，但我不要保留该提交的注释信息（缩写:f）
> - exec：执行shell命令（缩写:x）
> - drop：我要丢弃该commit（缩写:d）

根据需求,编辑commit:

```bash
pick b4d576b add b.php
s 90bc004 and c.php
s 45edfda add d.php
```

#### 复制commit

![img](https://chongming-images.oss-cn-hangzhou.aliyuncs.com/images-master202311201705067.webp)

```bash
# 前开后闭
# --onto 复制到哪个分支上
git rebase [startpoint] [endpoint] --onto [branchName]
# 复制完后还要切换一下master版本的head
git reset --hard E'
```



## 远程仓库

### 命令列表

|              命令              |                             作用                             |
| :----------------------------: | :----------------------------------------------------------: |
|        `git remote -v`         |                   查看当前所有远程地址别名                   |
| `git remote add 别名 远程地址` |                       给远程地址起别名                       |
|      `git push 别名 分支`      |                推送本地分支上的内容到远程仓库                |
|    `git push -u 别名 分支`     | 推送同时关联别名主机，之后直接使用git push即可推送当前分支到关联主机 |
|       `git clone 地址名`       |                      克隆远程仓库到本地                      |
|  `git fetch 地址别名 分支名`   |                   抓取远程分支，不自动合并                   |
|   `git pull 地址别名 分支名`   |   将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并   |

### 添加远程库

**语法：**

```bash
# 添加到远程库，并给远程地址起别名
git remote add 别名 远程地址

# 查看当前所有远程地址别名
git remote -v
```

**git默认别名是origin**

### 移除远程库

**语法：**

```bash
 git remote rm 远程地址（别名）
```

### 推送本地库

**语法：**

```bash
git push 别名 分支
```

### 克隆远程库

**语法：**

```bash
git clone 远程地址
```

### 拉取远程库

**语法：**

```bash
git pull 别名 分支
```

## 里程碑式标签

> 新版本的发布可以用版本号标示, 以示重要, 可以通过标签永久性标记特定的提交, 然后可以理解成分支一样引用

`git tag` 创建标签

```bash
# 默认head版本
git tag v0.0.1 
# 指定版本
git tag v0.0.1 commit_id
git tag -a v0.0.1 "标签说明信息" commit_id
```

|           命令           |            作用            |
| :----------------------: | :------------------------: |
|        `git tag`         |          列出标签          |
|     `git show <tag>`     | 显示标签以及对应的提交信息 |
|    `git tag -d <tag>`    |          删除标签          |
| `git push origin <tag>`  |          推送标签          |
| `git push origin --tags` |        推送全部标签        |
|  `git tag -l "v1.0.0*"`  |     查找标签(正则表达)     |



## SSH认证

> 使用SSH协议可以让远程库免密登录

### 生成公钥

> 何谓公钥：
>
> - 1.很多服务器都是需要认证的，ssh认证是其中的一种。在客户端生成公钥，把生成的公钥添加到服务器，以后连接服务器就不用每次都输入用户名和密码了。
> - 2.很多git服务器都是用ssh认证方式，只需要把生成的公钥发送给代码仓库管理员，让他把公钥添加到服务器上，就可以通过ssh自由地拉取和提交代码了。

**生成公钥：**

```bash
ssh-keygen
# 提示确认存放公钥的地址，默认在用户文件夹下
# 提示要求输入和确认密码，不需要密码就直接enter
```

### 查看公钥

**1.通过命令窗口**

- 打开 **git bash** 窗口
- 进入 **.ssh** 目录：`cd ~/.ssh`
- 找到 **id_rsa.pub** 文件：`ls`
- 查看公钥：`cat id_rsa.pub` 或者 `vim id_rsa.pub`

**2.直接输入命令 ：`cat ~/.ssh/id_rsa.pub`**

**3.直接打开用户（一般都是 Administrator）下的 .ssh 文件夹，打开它里面的 id_rsa.pub 文件**

### 设置github

-> 点击头像(Acount) 

-> 选择设置(Settings)

-> SSH and GPG keys

-> 右侧的NEW SSH Key

-> 填写Title

​	最好是有意义的名称,比如`xxx for github`密钥, 填写生成的公钥,一般是以`ssh-rsa` 开头的一大串字符

-> 保存(Add SSH Key).

****

校验ssh协议是否设置成功

```bash
ssh -T git@github.com
```

## 换行符转换

> `CR`为回车符，`LF`为换行符。
>
> Windows结束一行用CRLF，Mac和Linux用LF。

**切换换行符转换**

```shell
git config --global core.autocrlf [true|false|input]

# false 取消自动转换功能。适合纯Windows
# true  提交代码时把CRLF转换成LF，签出时LF转换成CRLF。适合多平台协作
# input 提交时把CRLF转换成LF，检出时不转换。适合纯Linux或Mac
```

# 【GitBook】

> https://www.gitbook.com/
>
> `gitbook` 生成电子书主要有三种方式:
>
> - `gitbook-cli` 命令行操作,简洁高效,适合从事软件开发的相关人员.
> - `gitbook-editor` 编辑器操作,可视化编辑,适合无编程经验的文学创作者.
> - `gitbook.com` 官网操作,在线编辑实时发布,适合无本地环境且科学上网的体验者

## 前置条件

> 前置条件
>
> - 安装git
> - 安装node.js

安装 gitbook-cli

```bash
# 安装
npm install -g gitbook-cli
# 查看版本
gitbook --version
```

## 命令操作

### 初始化

```bash
$ gitbook init
```

初始化项目,按照 `gitbook` 规范会自动创建 `README.md` 和 `SUMMARY.md` 两个文件。

其实 `SUMMARY.md` 是电子书的章节目录,`gitbook` 会初始化相应的文件目录结构,所以主要是用于**开发初始阶段**.

### 启动

启动本地服务,程序无报错则可以在浏览器预览电子书效果: [http://localhost:4000](http://localhost:4000/)

由于能够实时预览电子书效果,并且大多数开发环境搭建在本地而不是远程服务器中,所以主要用于**开发调试阶段**.

```bash
$ gitbook serve
```

### 构建

构建静态网页而不启动本地服务器,默认生成文件存放在 `_book/` 目录,当然输出目录是可配置的,暂不涉及,见高级部分.

输出静态网页后可打包上传到服务器,也可以上传到 `github` 等网站进行托管,因而主要用于**发布准备阶段**.

```bash
$ gitbook build
```

