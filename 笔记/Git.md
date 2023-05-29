# Git

## 1. Git / 准备工作

### 1.1 Git 下载

> [Git 官网](https://git-scm.com/)

### 1.2 Git 安装

> [Git 安装教程](https://www.runoob.com/git/git-install-setup.html)

### 1.3 打开 Git Bash

> 在工作文件夹下，右键选择 Git Bash Here，或者在任意文件夹下，右键选择 Git Bash Here，再 cd 到工作文件夹下
> 也可以在 VSCode 中打开终端，选择 Git Bash

### 1.4 配置 Git

配置用户名，便于别人知道是谁提交的

```shell
git config --global user.name "Your Name"
```

配置邮箱,便于别人联系你

```shell
git config --global user.email "
```

查看配置信息

```shell
git config --list
```

---

## 2. 通过实际操作学习 Git

> 在此之前确保在正确的文件夹下打开了 Git Bash

**初始化仓库**

```shell
git init
```

> 会在当前目录下生成一个 .git 的隐藏文件夹，这个文件夹是 Git 用来跟踪管理版本的，
> 一般不要修改这个文件夹中的内容，否则会导致仓库损坏

**创建一个 .md 文件，模拟一个项目**

```shell
echo "版本1" > Project.md # 创建一个 Project.md 文件，并写入 "版本1"
```

**查看状态**

```shell
git status # 查看状态

# 输出为:
On branch master # 当前所处分支

No commits yet # 没有提交

# 未跟踪的文件:
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        text.md

nothing added to commit but untracked files present (use "git add" to track)
```

**添加文件到暂存区**

```shell
git add Project.md # 添加文件到暂存区
```

**查看状态**

```shell
git status # 查看状态

# 输出为:
On branch master # 当前所处分支

No commits yet # 没有提交

# 要提交的变更:
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   text.md
```

**提交到本地仓库**

```shell
git commit -m "message" # 提交到本地仓库
```

> -m 后面的内容是提交的说明，可以随意写，但是最好写清楚这次提交的内容

**查看提交日志**

```shell
git log # 查看提交日志
# 输出为:
# hash值,作者,日期,提交说明
commit 9abada884a25f01b0068df5481ac632528f2d2dd (HEAD -> master) # HEAD -> master 表示当前所处分支
Author: sugerzzxDeskTop <sugerzzx@gmail.com>
Date:   Wed May 24 11:51:01 2023 +0800

    message # 提交说明
```

**创建.gitignore 文件，忽略不需要提交的文件**

```shell
touch .gitignore # 创建.gitignore文件
```

在.gitignore 文件中添加需要忽略的文件

```shell
echo "node_modules" >> .gitignore # 在.gitignore文件中添加需要忽略的文件
```

**连接远程仓库**

```shell
git remote add origin
```

---

<!-- 以下为ai自动生成 -->

- #### Git 基本操作

  ```shell
  # 初始化仓库
  git init
  # 查看状态
  git status
  # 添加文件到暂存区
  git add <file>
  # 添加所有文件到暂存区
  git add .
  # 提交到本地仓库
  git commit -m "message"
  # 查看提交日志
  git log
  # 查看提交日志(简化版)
  git log --pretty=oneline
  # 查看提交日志(简化版)
  git log --oneline
  # 查看提交日志(简化版)
  git log --oneline --graph
  # 查看提交日志(简化版)
  git log --oneline --graph --all
  # 查看提交日志(简化版)
  git log --oneline --graph --all --decorate
  # 查看提交日志(简化版)
  git log --oneline --graph --all --decorate --abbrev-commit
  # 查看提交日志(简化版)
  git log --oneline --graph --all --decorate --abbrev-commit --date=relative
  # 查看提交日志(简化版)
  git log --oneline --graph --all --decorate --abbrev-commit --date=relative --author="name"
  # 查看提交日志(简化版)
  git log --oneline --graph --all --decorate --abbrev-commit --date=relative --author="name" --since="2 days ago"
  # 查看提交日志(简化版)
  git log --oneline --graph --all --decorate --abbrev-commit --date=relative --author="name" --since="2 days ago" --before="1 days ago"
  # 查看提交日志(简化版)
  git log --oneline --graph --all --decorate --abbrev-commit --date=relative --author="name" --since="2 days ago" --before="1 days ago" --grep="message"
  # 查看提交日志(简化版)
  git log --oneline --graph --all --decorate --abbrev-commit --date=relative --author="name" --since="2 days ago" --before="1 days ago"
  ```

- #### Git 版本回退
  。。。
