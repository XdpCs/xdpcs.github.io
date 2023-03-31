---
title: "Git 学习"
description: "Welcome to XdpCs’s blog!"
date: "2022-11-18"
tags: ["git"]
showComments: true
---

## 原理

* 本地仓库由`git`维护三棵"树"
* 第一个是`工作目录`,它拥有实际的文件
* 第二个是`暂存区`，它类似于缓存的存在，临时保存你的改动
* 第三个是`HEAD`,它指向最后一次提交的结果
  ![在这里插入图片描述](images/git.jpg)

## 概念

### 分支

* 分支是用来将特性开发隔离开。在你创建仓库的时候，`master`或`main`是默认的分支。我们一般在其他分支上进行开发，完成后再将它们合并到主分支上
* 你在本地创建的分支，如果不推送到远端仓库，这个分支就只能在本地可见

## 命令

* 命令只介绍在开发过程中，常用的命令

### 创建新的`git`仓库

```shell
git init
```

### 添加到暂存区

```shell
git add <filename>
git add .
```

* `git add <filename>` ,添加具体文件到暂存区
* `git add .`,将所有变动添加到暂存区
* 这是`git`基本工作流程的第一步，将文件添加到暂存区

### 提交

```shell
git commit -m "提交信息"
```

* 将改动提交到本地仓库的`HEAD`中
* 这是`git`基本工作流程的第二步，将文件提交到本地仓库的`HEAD`中

### 推送

```shell
git push origin master
```

* 将改动提交到远端仓库，可以将`master`换成任何你想要推送的分支
* 这是`git`基本工作流程的第三步，推送到远端仓库

```shell
git remote add origin <server>
```

* 将你的仓库连接到远端仓库，若你本地仓库未和远端仓库建立关系

### 分支

```shell
git checkout -b feature_xdp
```

* 创建一个叫做`feature_xdp`的分支

```shell
git checkout master
```

* 切换到主分支

### 更新与合并

```shell
git pull <远程主机名> <远程分支名>:<本地分支名>
```

* 标准格式
* 以当前工作目录进行获取（fetch）并合并（merge）远端的改动

```shell
git pull
git pull origin
```

* 将远端仓库的`origin`的`master`分支拉取到本地，并与本地的当前分支进行合并

```shell
git pull origin master:feature_xdp
```

* 将远端仓库的`origin`的`master`分支拉取过来，与本地的`feature_xdp`分支合并

```shell
git pull origin master
```

* 如果远端仓库的分支是与当前分支合并，则冒号后面的部分可以省略

```shell
git merge <branch>
```

* 合并其他分支到当前分支

### 冲突

* `git pull <远程主机名> <远程分支名>:<本地分支名>` 和 `git merge <branch>`,在两种情况下，`git`
  会尝试自动合并改动，但是并不是每一次都会成功，可能会出现冲突。这个时候，需要你手动修改来合并这些冲突

```shell
git add <filename>
```

* 合并完成后，需要将它们添加到暂存区

```shell
git diff <source_branch> <target_branch>
```

* 可以使用该命令预览差异，在合并改动之前

### log

```shell
git log
```

* 查看本地仓库历史记录

```shell
git log --author=XdpCs
```

* 只看`XdpCs`的提交记录

```shell
git log --pretty=oneline
```

* 每一条提交记录只占一行输出

```shell
git log --graph --oneline --decorate --all
```

* 通过树形结构来展示所有的分支，每个分支都标明它的名字和标签

```shell
git log --name-status
```

* 查看哪些文件发生改变

### 标签

* 通过创建标签，发布软件是一个不错的方法

```shell
git tag 1.0.0 1fd11181114
```

* 创建一个叫`1.0.0`的标签，`1fd11181114`是你想要标记的`提交ID`
* `提交ID`可以通过上面的`git log`获取
* 只要`提交ID`具有指向唯一性，`提交ID`可以少几位

### 替换本地改动

```shell
git checkout -- <filename>
```

* 使用`HEAD`中最新的内容替换掉你工作目录中的文件
* 已添加到暂存区的改动和新文件不会受到影响

```shell
git fetch origin
git reset --hard origin/master
```

* 丢弃本地的所有改动和提交，从远端服务器获取最新的版本历史，并将本地分支指向它

### 克隆仓库

```shell
git clone ../xdpcs.github.io
```

* 创建一个本地仓库的克隆版本

```shell
git clone git@github.com:XdpCs/Solidity-Learning.git
```

* 克隆一个远端服务器上的仓库