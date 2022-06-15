# Git 学习笔记

官方参考手册：https://git-scm.com/docs

## Git 基本工作流程

- 工作区 Workspace
- 暂存区 Index/Stage
- 本地仓库 Repository
- 远程仓库 Remote

![img](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cb9f8ca142574d9faf226c7811617816~tplv-k3u1fbpfcp-zoom-in-crop-mark:1304:0:0:0.awebp)

## Setup and Config

### config

```bash
# 列举config中的所有变量集，包括它们的值
git config --list
--add  # 添加配置项
--unset  # 删除配置项

# 配置用户信息
git config --global user.name "your name"  # 配置用户名
git config --global user.email "your email"  # 配置用户邮箱

# 查询配置信息
git config --list  # 列出当前配置
git config --local --list  # 列出repository配置
git config --glocal --list  # 列出全局配置
git congig --system --list  # 列出系统配置
```

### help

显示帮助信息

```bash
git help name
```

## Getting and Creating Projects

### init

创建新的Git仓库

```bash
git init  # 创建一个新的本地仓库
```

### clone

拷贝一个远程仓库到本地

```bash
git clone URL  # 从远程git仓库复制项目
```

## Basic Snapshotting

### status

查看工作区状态，输出一般有三种状态：

- Changes to be committed: 已经在暂存区, 等待添加到HEAD中的文件
- Changes not staged for commit: 有修改, 但是没有被添加到暂存区的文件
- Untracked files: 没有tracked过的文件, 通常有两类，一类是工作区中从未git add过的文件，另一类是编译过的程序文件（.pyc，.obj，.exe等），这类文件可以放入.gitignore中、

常用指令：

```bash
git status  # 查看文件状态
git status -s  # 获得简短的输出结果，绿色表示已添加到暂存区，红色表示未添加到zan'cun区，M表示修改，D表示删除，??表示untracked
```

### diff

比较文件的不同，即比较文件在缓存区和工作区的差异

```bash
git diff  # 查看尚未缓存的改动
git diff --cached  # 比较暂存区和本地仓库最后一次提交的差异
git diff --staged  # 显示差异统计
git diff HEAD  # 自上次提交以来工作树的修改
```

### add

```bash
# 工作区——>暂存区
git add XXX  # 提交到暂存区
git add .  # 提交工作区所有文件到暂存区，会根据.gitignore做过滤
git add *  # *是shell的通配符，添加.开头外的所有文件，不会根据.gitignore做过滤（慎用）
git add filename  # 提交工作区中指定文件到暂存区
git add dirname  # 提交工作区中某个文件夹中所有文件到暂存区
```

### commit

```bash
# 暂存区——>本地仓库
git commit -m "message"  # 提交暂存区的文件到本地仓库
git commit -a -m "messgae"  # 跳过git add步骤直接提交到本地仓库，只对修改和删除的文件有效，新文件仍需git add，否则为untracked状态
git commit --amend  # 修改提交记录
```

### reset

回退版本，可以指定退回某一次提交的版本 

#### HEAD

当前分支的指针，总是指向该分支的最后一次提交，可以看做是上一次提交的快照

![这里写图片描述](https://img-blog.csdn.net/20180819222755855)

```bash
HEAD  # 表示当前版本
HEAD^  # 上一个版本
HEAD^^  # 上上一个版本
HEAD^^^  # 上上上一个版本
HEAD~0  # 表示当前版本
HEAD~1  # 上一个版本
HEAD~2  # 上上一个版本
HEAD^3  # 上上上一个版本
```

常用指令

```bash
git reset [--soft | --mixed | --hard] [HEAD]
--soft  # 回退到之前的版本，不会修改暂存区和工作区的内容，将重置HEAD带来的新差异放进暂存区
--mixed  # 默认，可以不用带该参数，重置暂存区文件与上一次的提交保持一致，工作区文件内容保持不变
--hard  # 撤销所有未提交的修改内容，将暂存区和工作区都回退到之前版本
```

### rm

删除文件

```bash
git rm <file>  # 将文件从工作区和暂存区中删除
git rm -f <file>  # 强制删除，如果文件删除之前修改过且已经add到暂存区则必须使用强制删除
git rm --cached <file>  # 将文件从暂存区移除，但仍保留在工作区
git rm -r *  # 递归删除，*表示目录
```

## Branching and Merging

```bash
# 分支命令
git branch  # 查看所有分支，当前分支前会加星号
git branch 分支名  # 创建分支

# 查看提交记录
git log
git log --oneline  # 每次提交记录以单行显示
```

 
