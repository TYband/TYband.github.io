---
title: "如何使用debian11搭建minecraft服务器搭建 Minecraft 服务器 | 完整教程 (Fabric + Java 安装)"
author: "ajaxm"
date: "2024-11-20"
tags: 
  - Minecraft
  - 服务器搭建
  - Java
  - Fabric
  - 游戏教程
  - Minecraft 服务器
categories:
  - 游戏
  - 教程
  - 服务器搭建
  - Minecraft 教程
keywords: 
  - Minecraft 服务器搭建
  - 如何搭建 Minecraft 服务器
  - Minecraft Fabric 服务器
  - Java 安装教程
  - Minecraft 1.21 服务器
  - Linux Minecraft 服务器
---

# 安装 Java

> [!注意] 关于java版本
> 如果你需要安装**高版本服务端**，请跳过**安装java**直接按照**低版本java升级高版本java的办法**执行

```
sudo apt install openjdk-17-jdk -y
```

### 验证 Java 安装：
```
java -version
```

### 创建 Minecraft 服务器目录
```
mkdir -p ~/minecraft-server
cd ~/minecraft-server
```

# 下载 Minecraft 服务端文件
[下载 Minecraft 服务器启动器 |织物 --- Download Minecraft Server Launcher | Fabric](https://fabricmc.net/use/server/)
我需要搭建的是1.21，所以将可执行服务器启动器下载到当前目录。
```
curl -OJ https://meta.fabricmc.net/v2/versions/loader/1.21-pre1/0.16.9/1.0.1/server/jar
```

### Launch command: 启动命令：
使用以下命令运行具有 2GB RAM 的可执行服务器启动器。稍等片刻后，Minecraft 服务器将准备就绪。
```
java -Xmx2G -jar fabric-server-mc.1.21-pre1-loader.0.16.9-launcher.1.0.1.jar nogui
```


# 低版本java升级高版本java的办法

从 [Adoptium](https://adoptium.net/) 官方网站获取 OpenJDK 21
[Latest Releases | Adoptium](https://adoptium.net/zh-CN/temurin/releases/?os=linux&arch=x64)
**选择 JDK 21**
- 操作系统：Linux
- 架构：x64
- JDK 版本：21

<img src="https://ajaxm.com/static/img/_posts/mc1.png">

我是选择下载下来放在上面创建好的minecraft-server文件夹中。
**解压文件**（将压缩包名字换成自己下载好的）
```
sudo tar -xzf OpenJDK21U-jdk_x64_linux_hotspot_21.0.5_11.tar.gz -C /usr/lib/jvm
```

检查是否解压成功：
```
ls /usr/lib/jvm
```
#### 设置默认 Java

将安装的 Java 添加到系统的 `update-alternatives`：
第一段将openjdk-21修改成你下载的文件夹名。
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/openjdk-21/bin/java 1

sudo update-alternatives --config java
```

#### 验证 Java 版本
然后验证java版本
```
java -version
```

#### 运行 Fabric 服务端
```
java -Xmx4G -Xms2G -jar fabric-server-launch.jar nogui
```


# 错误解决
1.缺少必要的配置文件 `server.properties` 和 `eula.txt`
<img src="https://ajaxm.com/static/img/_posts/mc1.png">
解决步骤：
```
echo "eula=true" > eula.txt
```

启动服务就会解决。

```
java -Xmx4G -Xms2G -jar fabric-server-mc.1.21-pre1-loader.0.16.9-launcher.1.0.1.jar nogui
```

# 服务器参数
修改 `server.properties` 文件
```
nano server.properties
```

### 基本设置自查

- **accepts-transfers=false**  
    是否允许玩家间传输物品（跨服务器传输物品）`false` 表示不允许。
    
- **allow-flight=false**  
    是否允许玩家飞行，`false` 表示不允许。
    
- **allow-nether=true**  
    是否允许进入地狱，`true` 表示允许。
    
- **broadcast-console-to-ops=true**  
    控制台信息是否广播给管理员，`true` 表示广播。
    
- **broadcast-rcon-to-ops=true**  
    是否将 RCON（远程控制）信息广播给管理员，`true` 表示广播。
    
- **bug-report-link=**  
    Bug 报告的链接（通常为空，指向反馈页面的 URL）。
    
- **difficulty=easy**  
    设置游戏难度，`easy` 表示简单难度。
    
- **enable-command-block=false**  
    是否启用命令方块，`false` 表示禁用。
    
- **enable-jmx-monitoring=false**  
    是否启用 JMX 监控，`false` 表示禁用。
    
- **enable-query=false**  
    是否启用查询（用于服务器状态查询），`false` 表示禁用。
    
- **enable-rcon=false**  
    是否启用 RCON（远程控制协议），`false` 表示禁用。
    
- **enable-status=true**  
    是否启用服务器状态检查（玩家可查看服务器状态），`true` 表示启用。
    
- **enforce-secure-profile=true**  
    是否强制使用安全的玩家档案，`true` 表示启用。
    
- **enforce-whitelist=false**  
    是否强制使用白名单，`false` 表示不强制。
### 游戏设置
- **entity-broadcast-range-percentage=100**  
    实体广播范围百分比，`100` 表示完全广播，控制远程玩家能够看到实体（如怪物、玩家等）的范围。
    
- **force-gamemode=false**  
    是否强制玩家进入特定游戏模式，`false` 表示不强制。
    
- **function-permission-level=2**  
    功能命令权限级别，`2` 是常见的权限设置，控制函数的使用权限。
    
- **gamemode=survival**  
    默认游戏模式，`survival` 表示生存模式。
    
- **generate-structures=true**  
    是否生成结构（如村庄、要塞等），`true` 表示生成。
    
- **generator-settings={}**  
    世界生成设置，通常为空表示使用默认生成设置。
    
- **hardcore=false**  
    是否启用硬核模式，`false` 表示不启用。
    
- **hide-online-players=false**  
    是否隐藏在线玩家，`false` 表示不隐藏。
    
- **initial-disabled-packs=**  
    初始禁用的数据包（通常为空）。
    
- **initial-enabled-packs=vanilla**  
    初始启用的数据包，`vanilla` 表示启用默认的 Minecraft 数据包。
    
- **level-name=world**  
    世界名称，`world` 表示世界名称是默认的。
    
- **level-seed=**  
    世界种子（空表示随机生成）。
    
- **level-type=minecraft**
    
      
    世界类型，`minecraft:normal` 表示普通世界。
    
- **log-ips=true**  
    是否记录玩家 IP，`true` 表示记录。
    
- **max-chained-neighbor-updates=1000000**  
    最大链式邻居更新次数，控制区块更新的数量。
    
- **max-players=20**  
    最大玩家数量，`20` 表示最大支持 20 个玩家。
    
- **max-tick-time=60000**  
    最大游戏时钟时间（单位：毫秒），`60000` 表示一分钟内允许的最大时钟时间。
    
- **max-world-size=29999984**  
    最大世界大小，单位为块（`29999984` 为 Minecraft 的世界边界）。
    
- **motd=A Minecraft Server**  
    服务器欢迎消息（`motd`），可以在 Minecraft 中看到，`A Minecraft Server` 为默认消息。
### 网络和安全设置

- **network-compression-threshold=256**  
    网络压缩阈值，`256` 表示超过 256 字节的数据会进行压缩。
    
- **online-mode=true**  
    是否启用在线模式，`true` 表示启用。启用时，玩家需要通过 Mojang 的验证才能加入。
    
- **op-permission-level=4**  
    OP 权限级别，`4` 表示最高权限。
    
- **player-idle-timeout=0**  
    玩家空闲超时时间，`0` 表示禁用超时，玩家可以无限制地保持在线。
    
- **prevent-proxy-connections=false**  
    是否防止代理连接，`false` 表示不防止。
    
- **pvp=true**  
    是否启用玩家对玩家（PVP）战斗，`true` 表示启用。
    
- **query.port=25565**  
    服务器查询端口，默认为 `25565`。
    
- **rate-limit=0**  
    连接速率限制，`0` 表示没有速率限制。
    
- **rcon.password=**  
    RCON 密码（通常为空，设置时用于远程控制）。
    
- **rcon.port=25575**  
    RCON 端口，默认为 `25575`。
### 其他设置

- **region-file-compression=deflate**  
    区域文件压缩格式，`deflate` 是一种常见的压缩方式。
    
- **require-resource-pack=false**  
    是否强制要求资源包，`false` 表示不强制。
    
- **resource-pack=**  
    资源包的 URL（如果启用了资源包）。
    
- **resource-pack-id=**  
    资源包的唯一标识符。
    
- **resource-pack-prompt=**  
    提示玩家是否使用资源包的消息。
    
- **resource-pack-sha1=**  
    资源包的 SHA1 校验和，用于验证资源包的完整性。
    
- **server-ip=**  
    绑定的 IP 地址，通常为空，表示绑定到所有 IP 地址。
    
- **server-port=25565**  
    服务器端口，默认是 `25565`。
    
- **simulation-distance=10**  
    游戏模拟范围，`10` 表示每个玩家周围 10 个区块的模拟距离。
    
- **spawn-animals=true**  
    是否生成动物，`true` 表示生成。
    
- **spawn-monsters=true**  
    是否生成怪物，`true` 表示生成。
    
- **spawn-npcs=true**  
    是否生成 NPC，`true` 表示生成。
    
- **spawn-protection=16**  
    生成保护区范围，`16` 表示生成区周围 16 块范围内是保护区。
    
- **sync-chunk-writes=true**  
    是否同步区块写入，`true` 表示同步。
    
- **text-filtering-config=**  
    文本过滤配置（通常为空）。
    
- **use-native-transport=true**  
    是否使用本地传输，`true` 表示启用。
    
- **view-distance=10**  
    玩家视距，`10` 表示玩家能够看到 10 个区块范围内的内容。
    
- **white-list=false**  
    是否启用白名单，`false` 表示不启用。