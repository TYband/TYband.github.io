---
layout: post
title: 使用 Gost 隧道优化gbf游戏体验 
category: VPS
tags:
  - VPS
  - 碧蓝幻想
  - 网络优化
  - Gost

description: 想提升游玩《碧蓝幻想》的流畅度？本教程详细介绍如何利用 Gost 隧道搭建高速代理，降低延迟，优化网络连接，让游戏体验更上一层楼。
keywords: 碧蓝幻想加速, Gost 隧道, VPS 游戏加速, 网络延迟优化, 游戏代理设置, 碧蓝幻想流畅玩法
date: 2024-11-03T19:44:54+08:00
---
**使用时不允许fq，别瞎想**
## 1.安装gost：

在根目录下载构建gost

git clone --recursive [https://github.com/happyharryh/gost.git](https://github.com/happyharryh/gost.git)

2. ## 安装go

进入go.dev找到相应压缩包

wget [https://go.dev/dl/go1.23.2.linux-amd64.tar.gz](https://go.dev/dl/go1.23.2.linux-amd64.tar.gz)

此处是解压go 压缩包名可替换

```
tar -C /usr/local -xzf go1.23.2.linux-amd64.tar.gz
```

配置环境变量

```
nano ~/.bashrc
```

如果不是root就执行

```
sudo  nano ~/.bashrc
```

打开后复制到代码最底下 ctrl+x 按y 回车

```
echo "export PATH=\$PATH:/usr/local/go/bin" >> ~/.bashrc
```

加载配置

```
source ~/.bashrc
```

验证go是否安装成功

```
go version
```

## 3.使用go来构建build

先进入到gost目录

```
cd gost
```

构建gost

```
go build ./cmd/gost/
```

构建好后输入

```
ls
```

可以看到里面有一个gost的可执行文件

```
gost
```

这样就安装好了！

---

