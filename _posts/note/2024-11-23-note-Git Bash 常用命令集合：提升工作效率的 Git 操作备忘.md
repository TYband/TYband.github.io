---
title: "Git Bash 常用命令集合：提升工作效率的 Git 操作指南"
description: "本文介绍了 Git Bash 的常用命令集合，帮助开发者提高工作效率。包括常见的 Git 命令、分支管理、远程仓库操作等内容，适合初学者和进阶用户。"
keywords: "Git Bash, Git 常用命令, Git 分支, Git 操作, 版本控制, GitHub, 开发工具"
author: "AJAXM"
date: "2024-11-26"
categories: ["Git", "开发工具", "编程"]
tags: ["Git", "Git Bash", "命令行", "开发工具"]
open_graph:
  title: "Git Bash 常用命令集合：提升工作效率的 Git 操作指南"
  description: "掌握 Git Bash 常用命令，提升开发工作效率！本文详细介绍 Git 的基本命令、分支管理、远程操作等内容，适合各类开发者。"
  type: "article"
---


### 一、基础命令

1. **初始化仓库**

```
git init
```

创建一个新的 Git 仓库（空仓库）。
2. **克隆远程仓库**

```
git clone <repository_url>
```

克隆远程仓库到本地目录。
3. **查看仓库状态**

```
git status
```

显示工作目录和暂存区的状态，查看哪些文件被修改，哪些文件还未提交。
4. **查看提交历史**

```
git log
```

查看当前分支的提交历史。
5. **查看差异**

```
git diff
```

查看当前工作区和暂存区之间的差异。
6. **添加文件到暂存区**

```
git add <filename>
```

将文件添加到暂存区，为提交做准备。如果要添加所有更改的文件，可以使用：

```
git add .
```
7. **提交更改**

```
git commit -m "Commit message"
```

提交暂存区的文件到本地仓库，并附上提交信息。
8. **查看文件修改历史**

```
git blame <filename>
```

显示某个文件的每一行是由哪个提交修改的。

### 二、分支管理

1. **查看当前分支**

```
git branch
```

查看当前仓库中所有分支，并标记出当前所在的分支。
2. **创建新分支**

```
git branch <branch_name>
```

创建一个新分支，但不会切换到该分支。
3. **切换分支**

```
git checkout <branch_name>
```

切换到指定的分支。如果要创建并切换到新分支，可以使用：

```
git checkout -b <branch_name>
```
4. **合并分支**

```
git merge <branch_name>
```

将指定的分支合并到当前分支。
5. **删除分支**

```
git branch -d <branch_name>
```

删除本地分支。如果该分支还未合并，会提示错误。使用 `-D` 强制删除。
6. **查看分支图谱**

```
git log --oneline --graph --decorate --all
```

查看所有分支的提交历史图谱。

### 三、远程仓库操作

1. **查看远程仓库**

```
git remote -v
```

查看当前仓库配置的远程仓库地址。
2. **添加远程仓库**

```
git remote add origin <repository_url>
```

将远程仓库添加为 `origin`。
3. **推送到远程仓库**

```
git push origin <branch_name>
```

将本地的分支推送到远程仓库。
4. **拉取远程仓库的更改**

```
git pull origin <branch_name>
```

从远程仓库拉取指定分支的更新并合并到本地。
5. **获取远程更新（不合并）**

```
git fetch
```

获取远程仓库的所有更新，但不会自动合并到本地分支。
6. **推送标签到远程仓库**

```
git push origin <tag_name>
```
7. **删除远程分支**

```
git push origin --delete <branch_name>
```

### 四、标签管理

1. **创建标签**

```
git tag <tag_name>
```

创建一个标签，通常用于标记重要的提交（如发布版本）。
2. **查看标签**

```
git tag
```
3. **推送标签到远程仓库**

```
git push origin <tag_name>
```
4. **删除标签**

```
git tag -d <tag_name>
```

### 五、工作流和高级命令

1. **重置文件到最后一次提交**

```
git checkout -- <filename>
```

恢复某个文件的修改到最后一次提交的状态。
2. **撤销最后一次提交**

```
git reset --soft HEAD~1
```

撤销上一次提交，但保留修改，放回暂存区。

```
git reset --hard HEAD~1
```

完全撤销上一次提交，并删除所有修改（慎用）。
3. **创建空提交**

```
git commit --allow-empty -m "Empty commit"
```

创建一个没有任何更改的提交，通常用于触发 CI 流程等。
4. **查看当前 HEAD 的状态**

```
git reflog
```

查看 HEAD 和分支的历史记录，可以用来找回丢失的提交。
5. **清理未使用的文件**

```
git clean -f
```

删除工作区中未跟踪的文件。
6. **查看修改的文件**

```
git diff <filename>
```

