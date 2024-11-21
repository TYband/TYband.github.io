---
title: "如何使用 Docker 部署和优化静态页面 Homepages | 完整指南"
author: "ajaxm"
date: "2024-11-21"
tags: 
  - Docker
  - 静态页面部署
  - 网站优化
  - Homepages
  - Web 开发
  - 网站管理
categories:
  - 技术
  - 教程
  - 网站搭建
  - Docker 教程
keywords: 
  - 使用 Docker 部署静态页面
  - 如何部署 Homepages
  - Docker 静态网站优化
  - Homepages 完整配置教程
  - 网站管理和部署
  - Docker 安装指南
---


### **教程：安装并配置 `ghcr.io/gethomepage/homepage` 镜像**

#### **前提条件**

- 服务器已安装 Docker 和 Docker Compose。
- 
### **创建 Docker Compose 配置**

1. 创建一个目录来存放配置文件 `/home/user/gethomepage`：

```
mkdir ~/gethomepage
cd ~/gethomepage
```
2. 创建 `docker-compose.yml` 文件并编辑：

```
nano docker-compose.yml
```
3. 在文件中添加以下配置（记得根据需要修改路径和配置）：

```
version: '3'

services:
  homepage:
    image: ghcr.io/gethomepage/homepage:latest
    container_name: homepage
    ports:
      - 3000:3000
    volumes:
      - /path/to/config:/app/config  # 确保配置目录存在
      - /var/run/docker.sock:/var/run/docker.sock  # 可选，用于 Docker 集成
```

**说明：**

- `image`: 使用 `ghcr.io/gethomepage/homepage:latest` 镜像。
- `container_name`: 指定容器名称（可自定义）。
- `ports`: 映射容器内的 3000 端口到主机的 3000 端口，您可以根据需要更改端口。
- `volumes`: 将本地的 `/path/to/config` 目录挂载到容器的 `/app/config`，配置文件。

### **启动服务**

1. 在 `docker-compose.yml` 文件所在的目录，使用以下命令启动服务：

```
docker-compose up -d
```

这将启动 `homepage` 服务并在后台运行。
2. 查看容器日志：

```
docker-compose logs -f
```
3. 访问网站：`http://<your-server-ip>:3000` 

### **步骤 4：配置 `homepage` 内容**

1. **修改配置文件：** 进入您挂载的本地配置目录 `/path/to/config`，编辑该目录中的文件来修改网站内容。

例如，如果您有 `config.json` 或其他配置文件，您可以编辑这些文件来修改网站的标题、描述、布局等。

```
cd /path/to/config
nano config.json
```

2. **重新启动容器：** 

```
docker-compose restart
```

### **步骤 5：自定义网站内容**

如果您需要自定义网站内容（如 HTML、CSS 或图像），可以直接将文件放入挂载的 `/path/to/config` 目录中。您可以覆盖默认的 HTML 页面或添加自己的文件。

1. **替换或添加 HTML 文件**： 将您的 `index.html` 文件替换掉默认的文件：

```
cp /your/local/path/index.html /path/to/config/
```
2. **修改 CSS 或 JS 文件**： 

### **步骤 6：管理 Docker 容器**

- **停止服务：**

```
docker-compose down
```
- **删除容器和镜像：** 

```
docker-compose down --rmi all
```
- **查看正在运行的容器：**

```
docker ps
```
- **删除单个容器：** 

```
docker rm <container_id>
```