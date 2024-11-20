---
title: "浅浅记录一下Linux上GNU Screen的使用：安装、启动、管理会话和快捷键指南"
source: "https://blog.usr9.com"
author: "lemonburger"
published: "2024-11-15"
created: "2024-11-15"
category: note
description: "总是会使用，但总是会忘掉，每次都去搜索，不如整理一份备忘"
tags:
  - "Linux"
  - "GNU Screen"
  - "终端会话管理"
  - "Linux教程"
  - "ubuntu"
---


# 介绍

screen是一款终端多路复用器，它允许用户在一个终端会话中管理多个终端会话。这对于系统管理员或者任何需要远程多任务处理的用户来说，是一个非常有用的工具。

# 主要功能

- **会话保留** ：即使网络连接断开或者ssh关闭，终端会话仍然保持运行。
- **多窗口管理** ：在单个窗口中创建多个终端会话，类似于标签页的功能。
- **终端分割** ：可以在同一个屏幕中分割出多个区域，每个区域显示不同的会话。
- **会话共享** ：可以与其他用户共享会话，共同进行操作。
- **复制模式** ：方便地在会话之间复制和粘贴文本。
# 安装

```
sudo apt-get update
```

```
sudo apt-get install screen
```

# 启动screen

直接输入
```
screen
```
之后就会进入新的screen会话，要退出但不关闭会话，可以使用快捷键 *Ctrl+A* 然后 *D*

## 创建有名字的窗口

```
screen -S name
```
其中name修改成自己需要设置的

# 列出所有会话
```
screen -ls
```
列出后会有id显示，这时候可以通过id重连会话
# 重连会话

screen -r 窗口ID 或者是窗口的名字

```
screen -r ID
screen -r name
```

### 终端窗口管理

- **新建窗口** ：在当前会话中创建一个新窗口：

按 `Ctrl+A` 然后按 `C`。
- **切换窗口** ：在屏幕会话中切换到下一个窗口：

按 `Ctrl+A` 然后按 `N`。

切换到上一个窗口：

按 `Ctrl+A` 然后按 `P`。

### 分割窗口

- **水平分割** ：按 `Ctrl+A` 然后按 `S`。
- **垂直分割** ：按 `Ctrl+A` 然后按 `|`。
- **切换区域** ：按 `Ctrl+A` 然后按 `Tab`。
- **关闭分割窗口** ：按 `Ctrl+A` 然后按 `X`。

### 终止会话

- **关闭窗口** ：按 `Ctrl+A` 然后按 `K`，然后确认。
- **杀死会话** ：通过命令：
```
screen -S my\_session -X quit
```

### 其他有用的命令

- **锁定屏幕** ：按 `Ctrl+A` 然后按 `X`。
- **查看帮助** ：按 `Ctrl+A` 然后按 `?`。
- **重命名当前窗口** ：按 `Ctrl+A` 然后按 `A`，然后输入新的名称并按Enter确认。

## 常见快捷键一览

- `Ctrl+A d`：退出当前会话但不关闭。
- `Ctrl+A c`：创建一个新窗口。
- `Ctrl+A n`：切换到下一个窗口。
- `Ctrl+A p`：切换到上一个窗口。
- `Ctrl+A S`：水平分割窗口。
- `Ctrl+A |`：垂直分割窗口。
- `Ctrl+A X`：关闭当前分割的窗口。
- `Ctrl+A ?`：查看所有快捷键。


## 参考

- [GNU Screen 手册页](https://man7.org/linux/man-pages/man1/screen.1.html)
- [GNU Screen 官方网站](https://www.gnu.org/software/screen/)
- [Ubuntu 官方文档 - 使用 Screen](https://help.ubuntu.com/community/Screen)
- [How to Use Linux Screen](https://linuxize.com/post/how-to-use-linux-screen/)
