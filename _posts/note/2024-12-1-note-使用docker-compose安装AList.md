---
title: "使用docker-compose安装AList "
description: "使用docker-compose安装AList的详细步骤，解决安装过程中的常见问题，设置密码，挂载百度网盘等操作。适用于Linux服务器和VPS。"
keywords: "docker-compose, AList, 安装AList, 使用docker-compose, 挂载网盘, AList文档, VPS, 2024 AList安装"
author: "AJAXM"
date: "2024-12-01"
category: "技术教程"
tags: ["AList", "Docker", "安装教程", "VPS", "网盘", "百度网盘", "自建网盘", "Linux", "Docker-Compose"]
---
# 使用docker-compose安装AList - 完整教程

## 简介

AList 是一款强大的文件管理和分享工具，支持多种网盘存储服务，如百度网盘、阿里云盘等。通过 **docker-compose** 部署 AList，能够帮助你轻松管理个人文件并支持挂载网盘。

## 目录

1. [准备工作](#准备工作)
2. [创建并配置docker-compose.yml](#创建并配置docker-composeyml)
3. [启动AList服务](#启动alist服务)
4. [修改管理员密码](#修改管理员密码)
5. [挂载百度网盘](#挂载百度网盘)
6. [常见问题解答](#常见问题解答)

## 准备工作

一台服务器，服务器已经安装了 Docker 和 docker-compose。如果尚未安装，可以参考以下步骤：

- 安装 Docker：[Docker 官方安装教程](https://docs.docker.com/get-docker/)
- 安装 docker-compose：[Docker Compose 安装教程](https://docs.docker.com/compose/install/)

## 开始安装

alist文档
[使用 Docker | AList文档](https://alist.nn.ci/zh/guide/install/docker.html#%E5%8F%91%E8%A1%8C%E7%89%88%E6%9C%AC)

在左边找到安装-使用docker-翻到docker-compose
复制
```
version: '3.3'
services:
    alist:
        image: 'xhofe/alist:latest'
        container_name: alist
        volumes:
            - '/etc/alist:/opt/alist/data'
        ports:
            - '5244:5244'
        environment:
            - PUID=0
            - PGID=0
            - UMASK=022
        restart: unless-stopped

```
接下来到服务器
创建文件alist
```
mkdir alist

```
进入alist文件
```
cd alist
```
创建docker-compose.yml文件夹
```
nano docker-compose.yml
```
在里面编写
```
version: '3.3'
services:
    alist:
        image: 'xhofe/alist:latest'
        container_name: alist
        volumes:
            - '/etc/alist:/opt/alist/data'
        ports:
            - '5244:5244'
        environment:
            - PUID=0
            - PGID=0
            - UMASK=022
        restart: unless-stopped
```

### **1. 文件版本**

```yaml
version: '3.3'
```

- 指定 `docker-compose` 文件版本。
- **说明**：`3.3` 是 Compose 文件的版本，确保兼容性和功能支持。

---

### **2. 服务名称**

```yaml
services:
    alist:
```

- 定义服务名称为 `alist`。
- **说明**：服务名称在 Compose 文件中用作标识，支持多个服务定义。

---

### **3. 镜像**

```yaml
image: 'xhofe/alist:latest'
```

- 指定容器使用的镜像：
- **名称**：`xhofe/alist`。
- **标签**：`latest`，表示最新版本。
- **作用**：下载并运行指定版本的 Alist 容器镜像。

---

### **4. 容器名称**

```yaml
container_name: alist
```

- 指定容器名称为 `alist`。
- **说明**：方便通过名称管理容器，如 `docker logs alist`。

---

### **5. 挂载卷**

```yaml
volumes:
    - '/etc/alist:/opt/alist/data'
```

- 挂载主机目录到容器：
- **主机目录**：`/etc/alist`，用于存储持久化数据。
- **容器目录**：`/opt/alist/data`，容器内部的数据路径。
- **作用**：实现数据持久化，避免容器删除时丢失数据。

---

### **6. 端口映射**

```yaml
ports:
    - '5244:5244'
```

- 映射主机和容器的端口：
- **主机端口**：`5244`。
- **容器端口**：`5244`。
- **作用**：通过主机的 `5244` 端口访问容器服务。

---

### **7. 环境变量**

```yaml
environment:
    - PUID=0
    - PGID=0
    - UMASK=022
```

- 配置容器运行的环境：
- **PUID** 和 **PGID**：指定容器的用户和用户组为 `root` (ID `0`)。
- **UMASK**：设置文件默认权限为 `755`。

---

### **8\. 重启策略**

```yaml
restart: unless-stopped
```

- 设置容器的自动重启策略：
- **unless-stopped**：容器异常退出时自动重启，手动停止后不再重启。


**启动**
```
docker-compose up -d
```

> [!在浏览器中输入 0.0.0.0:5244就可以访问了。]


## 修改密码
首先进入到安装alist的文件

**进入容器**
```
docker exec -it alist /bin/bash
```
随机生成密码
```
./alist admin random
```
手动设置新密码(NEW_PASSWORD替换成自己修改的密码)
```
./alist admin set NEW_PASSWORD
```

> [!注意] 这里只能修改密码，不能修改账户名


进入到主页后，点击最底下的管理，进入后台
<img src="https://ajaxm.com/static/img/_posts/alist1.png">
<img src="https://ajaxm.com/static/img/_posts/alist2.png">
这里可以修改账号密码

**挂载网盘**
挂载网盘需要获取刷新令牌，挂载路径为/
刷新令牌见官方文档
[简介 |AList 文档 --- Introduction | AList Docs](https://alist.nn.ci/guide/#support-storage)