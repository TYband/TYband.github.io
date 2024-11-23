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

## 4.配置gost

1.如果你是落地+中转+SwitchyOmega  
例：  
落地机：监听本地8888端口

```
./gost -L=:8888
```

8080端口是中转机接收连接的端口，并将数据转发到落地机的8888端口。

```
./gost -L=:8080 -F=zero://落地机IP:落地机配置gost的端口号
```

SwitchyOmega配置

```
代理协议：socks5或者http
代理服务器：输入你中转机的ip地址
端口：中转机监听的端口（例子中为8080）
```

---

2.如果你是落地+本地+SwitchyOmega  
Windows 客户端构建

```
env GOOS=windows GOARCH=amd64 go build ./cmd/gost/
```

构建好后打开你的服务器文件，找到gost.exe下载到本地，右键gost.exe文件空白处 在终端中打开，再把gost.exe拖进cmd中输入 按照步骤做可以去掉“<路径>\\gost.exe”

<路径>\\gost.exe -L :8080 -F zero://服务器IP:8888

```
服务器启动：./gost -L zero://:8888
```

SwitchyOmega

```
代理协议：socks5或者http
    代理服务器：输入127.0.0.1
    端口：中转机监听的端口（例子中为8080）
```

---

3.socat+gost+SwitchyOmega  
socat端为转发（ipv6 only），gost为落地(也需要有ipv6)。

安装脚本，创建一个install\_socat.sh 并打开

```
nano install_socat.sh
```

如果不是root

```
sudo nano install_socat.sh
```

给执行权限

```
chmod +x install_socat.sh
```

在脚本文件夹下输入

```
./install_socat.sh
```

使用脚本（[https://www.nodeseek.com/post-70660-1](https://www.nodeseek.com/post-70660-1)）Nodeseek论坛maizi大佬的脚本 这里我使用gpt添加了一个删除转发 脚本如下：

```
#!/bin/bash

# 显示主菜单
show_menu() {
    clear
    echo "===================================="
    echo "==欢迎使用maizi制作的socat转发面板=="
    echo "==如遇困难请联系TG:https://t.me/tel_with_maizi_bot=="
    echo "===================================="
    echo "请选择:"
    echo "0. 退出脚本"
    echo "-----------------------------------------------------------------"
    echo "1. 一键部署转发"
    echo "2. 添加转发"
    echo "3. 移除转发"
    echo "4. 查看转发"
    echo "5. 启动服务"
    echo "-----------------------------------------------------------------"
}

handle_error() {
    echo -e "\e[31m发生错误，操作未成功完成。\e[0m"
    exit 1
}

countdown() {
    local SECONDS=3
    echo -e "\e[32m操作成功完成，将在 $SECONDS 秒后返回主菜单...\e[0m"
    while [ $SECONDS -gt 0 ]; do
        echo -n "$SECONDS..."
        sleep 1
        ((SECONDS--))
    done
    echo
}

initialize_socat_start() {
    echo "初始化转发列表文件..."
    > /usr/local/bin/socat-start.sh || handle_error
    chmod +x /usr/local/bin/socat-start.sh || handle_error
}

add_forwarding() {
    # 清除现有的#!/bin/bash和wait
    sed -i '/^#!/d' /usr/local/bin/socat-start.sh
    sed -i '/^wait$/d' /usr/local/bin/socat-start.sh
    while true; do
        read -p "请输入IP地址: " ip
        read -p "请输入端口: " port
        # 添加新的转发规则
        echo "/usr/bin/socat TCP6-LISTEN:${port},fork,reuseaddr TCP6:[${ip}]:${port} &" >> /usr/local/bin/socat-start.sh
        echo "转发规则已添加。"
        read -p "是否继续添加(Y/N)? " answer
        if [[ "$answer" != "Y" && "$answer" != "y" ]]; then
            # 用户完成添加，将#!/bin/bash和wait分别添加到文件的首尾
            sed -i '1i#!/bin/bash' /usr/local/bin/socat-start.sh
            echo "wait" >> /usr/local/bin/socat-start.sh
            chmod +x /usr/local/bin/socat-start.sh || handle_error
            countdown
            break
        fi
    done
}

deploy_socat() {
    echo "更新软件源并安装 socat..."
    cat > /etc/apt/sources.list << EOF || handle_error
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye main contrib non-free
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-updates main contrib non-free
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bullseye-backports main contrib non-free
deb https://security.debian.org/debian-security bullseye-security main contrib non-free
EOF
    apt-get update || handle_error
    apt-get install -y socat || handle_error
    initialize_socat_start
    echo "创建并配置socat服务..."
    cat > /etc/systemd/system/socat.service << EOF || handle_error
[Unit]
Description=Internet Freedom

[Service]
DynamicUser=true
ProtectSystem=true
ProtectHome=true
ExecStart=/usr/local/bin/socat-start.sh
Restart=always

[Install]
WantedBy=multi-user.target
EOF
    systemctl daemon-reload || handle_error
    systemctl enable socat.service || handle_error
    echo -e "\e[32m服务已安装完成\e[0m"
    countdown
}

view_forwarding() {
    echo "当前转发规则如下："
    cat /usr/local/bin/socat-start.sh || handle_error
    read -p "按任意键返回主菜单..."
}

remove_forwarding() {
    echo "清除所有转发规则..."
    > /usr/local/bin/socat-start.sh || handle_error
    echo "所有转发规则已被清除。"
    countdown
}

start_service() {
    systemctl daemon-reload || handle_error
    systemctl restart socat.service || handle_error
    echo -e "\e[32msocat服务已启动。\e[0m"
    countdown
}

while true; do
    show_menu
    read -p "请输入您的选择（0-5）: " choice
    case $choice in
        0)
            echo "退出脚本。"
            break
            ;;
        1)
            deploy_socat
            ;;
        2)
            add_forwarding
            ;;
        3)
            remove_forwarding
            ;;
        4)
            view_forwarding
            ;;
        5)
            start_service
            ;;
        *)
            echo "无效输入，请重新输入。"
            ;;
    esac
done
```

进入脚本后：

```
按1一键部署转发 
部署好之后按2 
ip:你的落地机ipv6地址
端口：落地gost监听的端口（8888）
启动服务 换端口转发后必须重新启动服务
```

启动落地gost：

```
./gost -L=:8888 -F=zero://中转机ip:8888
```

---

如果你看了b站视频 购买了沪日专线  
沪日专线+本地+SwitchyOmega  
沪日专线：

```
    ./gost -L zero://:8888

如果你购买的是cloudIPLC，需要设置端口转发内网8888转51081（转一个喜欢的就行）
```

本地：  
请先先构建好客户端并且下载到本地

```
gost.exe -L :8080 -F zero://你的IPLC外网ip:你的IPLC映射过8888后的端口
```

SwitchyOmega

```
代理协议：SOCKS5
代理服务器：127.0.0.1
代理端口：8080
为什么是8080：因为gost.exe监听本地8080端口 所以代理服务器为127.0.0.1。
```