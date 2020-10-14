## Git


Git是一款免费、开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目, [官网](https://git-scm.com/)


### 使用准备

- 安装

Windows 下的安装包会自带一个 `gitbash`, 强制`gitbash + 命令` 的方式来使用 git

- 设置

```
git config --global user.name "xxx"
git config --global user.email "xxx@sensoro.com"
git config --global core.editor vim

```

- 远程托管平台添加公钥
    - `ssh-keygen`生成公私钥对
    - 找到平台对应配置项, 添加公钥


- 提示符修改(Mac 环境)

```
if [ -f ~/.git-prompt.sh ];then
    . ~/.git-prompt.sh
fi
export PS1='[vm \W$(__git_ps1 " (%s)")]\$ '

```

- 自动补全(Mac 环境)

```
if [ -f ~/.git-completion.bash ];then
    . ~/.git-completion.bash
fi

```

### 常用命令

功能 | 命令
-- | --
新建仓库 | git init
克隆仓库 | git clone <地址> [-o <主机名>]
*添加远程主机 | git remote add <主机名> <网址>
删除远程主机 | git remote rm <主机名>
查看远程主机 | git remote -v
推送本地分支 | git push <远程主机名> <本地分支名>:<远程分支名>
*推送本地新分支 | git push -u <远程主机名> <本地分支名>:<远程分支名>
拉取分支 | git pull <远程主机名> <远程分支名>:<本地分支名>
拉取分支 | git fetch <远程主机名> <远程分支名>:<本地分支名>
*新建分支,切换远端分支 | git checkout -b <分支>
*切换分支 | git checkout <分支>
合并分支 | git merge
查看分支 | git branch
查看远端分支 | git branch -a
分支改名 | git branch -m <原分支名> <新分支名>
删除分支 | git branch -d <分支>
查看修改状态 | git status
查看修改 | git diff
添加修改 | git add <文件>
添加所有修改 | git add -A
取消修改 | git checkout <文件>
提交修改 | git commit -am <信息>
查看历史提交 | git log
打标签 | git tag <标签名>
查看标签 | git tag
推标签 | git push --tags
添加子模块 | git submodule add <地址>
更新主仓库下的子模块 | git submodule update --recursive
首次拉取主仓库下的子模块 | git submodule update --init --recursive
将每一个子模块切到 master 分支 |git submodule foreach git checkout master
更新每一个子模块 | git submodule foreach git pull
删除已经track的文件 | git rm --cached ***

### 使用Git命令将本地项目上传至Gitlab上

#### 安装git

#### 在Gitlab上创建项目，如下图，点击右上角加号到项目创建页面, 填写项目名称, 选择项目访问权限, private为授权的组员才能访问.

![](../../img/Gitlab新建项目.png)

#### 打开本地项目源代码所在文件夹, 删除项目IDE配置信息
PS:这样是为了保证IDE配置信息不会上传到Gitlab中, 也可以使用命令行在上传时将配置文件过滤, 个人觉得可视化删除方便些

#### 鼠标右键打开gitbash here:

```
1.输入命令：git config --global user.name "xxxxxxxx"

2.输入命令：git config --global user.email "xxxxxxxx@sensoro.com"

3.输入命令：git init

4.输入命令：git remote add origin xxxxxxxx
  ---xxxxxxxx gitlabs上建立的项目的连接
  eg.git remote add origin git@gitlab.sensoro.com:Embedded/Embedded-Docs.git

5.输入命令：git add -A

6.输入命令：git commit -am xxxx
  ---xxxx 信息 可随意命名

7.输入命令：git push origin master
  ---将代码推送至Gitlab端。
```


### 远程仓库操作

* 克隆, 将远程仓库复制到本地

```
git clone git@gitlab.sensoro.com:Embedded/Embedded-Docs.git [-o gitlab]

-o 选项为可选项
```

* 拉取, 将远程仓库的更新同步到本地

```
git pull origin master
```

* 推送, 将本地的更新同步到远程仓库

```
git push oringin master
```

### .gitignore

屏蔽不想 track 的文件和路径

```
*.o
build/

```
注意: 对于已 track 的文件或文件夹, .gitignore是不起作用的

删除已 track 文件

```
git rm --cached xxxx(文件)
git rm -r --cached xxxx(文件夹)

```

### commit message

* 格式


```
<head>
空行
<body>
空行
<tail>
```


* 再次编辑 commit message

```
git commit --amend
```

### git checkout

* 回滚到某次提交

```
git checkout 6efcdacfb77a6e4df5571237b2ea6ebab063030c

```

* 回滚到某次操作

```
git reflog
git checkout ba1ff51

```

* 回滚某个分支

```
git checkout <tag>

```

### submodule

* git submodule update, 切换到对应版本


### hooks

* 路径 `.git/hooks/`

### 干活习惯

* 拉取-->回归-->修改-->提交-->推送
* 开发新功能: 新建分支-->修改-->测试-->合并

<span id="gitbash"></span>

## Git Bash

Git Bash 是 window git 自带的 MSYS2 命令行终端. 算是 windows 下比较简约好用的终端

### Add more to Git Bash

#### wget
* 下载 [wget](https://eternallybored.org/misc/wget/)
* 解压
* 移动 `wget.exe` 到 `C:\Program Files\Git\mingw64\bin\(根据实际安装路径)`

#### make
* 从[ezwinports](https://sourceforge.net/projects/ezwinports/files/)下载`make-4.1-2-without-guile-w32-bin.zip(或更新的版本)`
* 解压
* 将解压后的`bin, include, lib, share`等文件夹合并到`C:\Program Files\Git\mingw64\`

