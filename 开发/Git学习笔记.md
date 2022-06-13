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
# 配置用户信息
git config --global user.name "your name"  # 配置用户名
git config --global user.email "your email"  # 配置用户邮箱

# 查询配置信息
git config --list  # 列出当前配置
git config --local --list  # 列出repository配置
git config --glocal --list  # 列出全局配置
git congig --system --list  # 列出系统配置
```

## Getting and Creating Projects

```bash
# 初始化git仓库
git init  # 创建一个新的本地仓库
git clone URL  # 从远程git仓库复制项目
```

## Basic Snapshotting

```bash
git status  # 查看文件状态
git diff  # 比较工作区中当前文件和暂存区之间的差异

# 工作区——>暂存区
git add XXX  # 提交到暂存区
git add .  # 提交工作区所有文件到暂存区，会根据.gitignore做过滤
git add *  # *是shell的通配符，添加.开头外的所有文件，不会根据.gitignore做过滤（慎用）
git add filename  # 提交工作区中指定文件到暂存区
git add dirname  # 提交工作区中某个文件夹中所有文件到暂存区

# 暂存区——>本地仓库
git commit -m "message"  # 提交暂存区的文件到本地仓库
git commit -a -m "messgae"  # 跳过git add步骤直接提交到本地仓库
git commit --amend  # 修改提交记录
```

## Branching and Merging

```bash
# 分支命令
git branch  # 查看分支
git branch 分支名  # 创建分支
git chec

# 查看提交记录
git log
git log --oneline  # 每次提交记录以单行显示
```

