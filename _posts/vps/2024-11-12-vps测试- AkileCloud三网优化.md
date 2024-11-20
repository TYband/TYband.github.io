---
layout: post
title: "AkileCloud三网优化VPS测试 - 性能与稳定性分析"
description: "详细评测AkileCloud提供的三网优化VPS服务,包括网络性能、稳定性和性价比分析。适合寻找高质量VPS服务的用户参考。"
category: vps
tags:
    - VPS
    - AkileCloud
    - 网络优化
    - 性能测试
    - 云服务器
keywords: VPS测试, AkileCloud, 三网优化, 服务器性能, 网络稳定性
author: "AJAXM"
date: 2023-11-03T16:11:54+08:00
---

## Tokyo BGP Pro V4

**JPPro-Light**

- **CPU**: 1核
- **内存**: 1024 MB
- **硬盘**: 10 GB
- **带宽**: 300M
- **流量**: 700G/月
- **超出限速**: 共享 10Mbps
- **重置流量**: ¥22.00
- **IPv4**: 1个
- **IPv6**: 1个
### 价格
- ¥24.99/月


## 融合怪测评
```
测评频道: https://t.me/vps_reviews                    
VPS融合怪版本：2024.11.08
Shell项目地址：https://github.com/spiritLHLS/ecs
Go项目地址：https://github.com/oneclickvirt/ecs
---------------------基础信息查询--感谢所有开源项目---------------------
 CPU 型号          : AMD EPYC 7402P 24-Core Processor
 CPU 核心数        : 1
 CPU 频率          : 2794.748 MHz
 CPU 缓存          : L1: 128.00 KB / L2: 512.00 KB / L3: 16.00 MB
 AES-NI指令集      : ✔ Enabled
 VM-x/AMD-V支持    : ✔ Enabled
 内存              : 163.13 MiB / 964.81 MiB
 Swap              : [ no swap partition or swap file detected ]
 硬盘空间          : 2.47 GiB / 9.77 GiB
 启动盘路径        : /dev/sda2
 系统在线时间      : 1 days, 0 hour 9 min
 负载              : 0.12, 0.05, 0.01
 系统              : Ubuntu 20.04.6 LTS (x86_64)
 架构              : x86_64 (64 Bit)
 内核              : 5.4.0-156-generic
 TCP加速方式       : bbr
 虚拟化架构        : KVM
 NAT类型           : Full Cone
 IPV4 ASN          : AS61112 AKILE LTD
 IPV4 位置         : Tokyo / Tokyo / JP
 IPV6 ASN          : AS51847 Nearoute
 IPV6 位置         : Koganei / Tokyo / Japan
 IPV6 子网掩码     : 128
----------------------CPU测试--通过sysbench测试-------------------------
 -> CPU 测试中 (Fast Mode, 1-Pass @ 5sec)
 1 线程测试(单核)得分: 		1543 Scores
---------------------内存测试--感谢lemonbench开源-----------------------
 -> 内存测试 Test (Fast Mode, 1-Pass @ 5sec)
 单线程读测试:		39202.23 MB/s
 单线程写测试:		16233.43 MB/s
------------------磁盘dd读写测试--感谢lemonbench开源--------------------
 -> 磁盘IO测试中 (4K Block/1M Block, Direct Mode)
 测试操作		写速度					读速度
 100MB-4K Block		29.0 MB/s (7071 IOPS, 3.62s)		26.0 MB/s (6348 IOPS, 4.03s)
 1GB-1M Block		106 MB/s (101 IOPS, 9.90s)		106 MB/s (100 IOPS, 9.90s)
-------------IP质量检测--基于oneclickvirt/securityCheck使用-------------
数据仅作参考，不代表100%准确，如果和实际情况不一致请手动查询多个数据库比对
以下为各数据库编号，输出结果后将自带数据库来源对应的编号
ipinfo数据库  [0] | scamalytics数据库 [1] | virustotal数据库   [2] | abuseipdb数据库   [3] | ip2location数据库    [4]
ip-api数据库  [5] | ipwhois数据库     [6] | ipregistry数据库   [7] | ipdata数据库      [8] | db-ip数据库          [9]
ipapiis数据库 [A] | ipapicom数据库    [B] | bigdatacloud数据库 [C] | cheervision数据库 [D] | ipqualityscore数据库 [E]
IPV4:
安全得分:
声誉(越高越好): 0 [2] 
信任得分(越高越好): 3 [8] 
VPN得分(越低越好): 91 [8] 
代理得分(越低越好): 99 [8] 
社区投票-无害: 0 [2] 
社区投票-恶意: 0 [2] 
威胁得分(越低越好): 99 [8] 
欺诈得分(越低越好): 0 [1] 93 [E]
滥用得分(越低越好): 0 [3] 
ASN滥用得分(越低越好): 0.0021 (Low) [A] 
公司滥用得分(越低越好): 0.0039 (Low) [A] 
威胁级别: low [9 B] 
黑名单记录统计:(有多少黑名单网站有记录):
无害记录数: 0 [2]  恶意记录数: 0 [2]  可疑记录数: 0 [2]  无记录数: 94 [2]  
安全信息:
使用类型: hosting [0 7 9 A] DataCenter/WebHosting/Transit [3] hosting - high probability [C] business [8]
公司类型: business [0 A] hosting [7]
是否云提供商: Yes [7 D] 
是否数据中心: Yes [0 1 A C] No [5 6 8]
是否移动设备: No [5 A C] Yes [E]
是否代理: No [0 1 4 5 6 7 8 9 A B C D] Yes [E]
是否VPN: Yes [E] No [0 1 6 7 A C D]
是否Tor: No [0 1 3 6 7 8 A B C D E] 
是否Tor出口: No [1 7 D] 
是否网络爬虫: No [9 A B E] 
是否匿名: No [1 6 7 8 D] 
是否攻击者: No [7 8 D] 
是否滥用者: No [7 8 A C D] Yes [E]
是否威胁: No [7 8 C D] 
是否中继: No [0 7 8 C D] 
是否Bogon: No [7 8 A C D] 
是否机器人: No [E] 
DNS-黑名单: 314(Total_Check) 0(Clean) 4(Blacklisted) 16(Other) 
IPV6:
安全得分:
欺诈得分(越低越好): 0 [1] 
滥用得分(越低越好): 0 [3]
ASN滥用得分(越低越好): 0.0015 (Low) [A] 
公司滥用得分(越低越好): 0 (Very Low) [A] 
威胁级别: low [B] 
安全信息:
使用类型: business [A] DataCenter/WebHosting/Transit [3]
公司类型: hosting [A] 
是否云提供商: Yes [D] 
是否数据中心: Yes [1 A] 
是否移动设备: No [A] 
是否代理: No [1 A B D] 
是否VPN: No [1 A D] 
是否Tor: No [1 3 A B D] 
是否Tor出口: No [1 D] 
是否网络爬虫: No [A B] 
是否匿名: No [1 D] 
是否攻击者: No [D]
是否滥用者: No [A D] 
是否威胁: No [D] 
是否中继: No [D] 
是否Bogon: No [A D] 
DNS-黑名单: 314(Total_Check) 0(Clean) 0(Blacklisted) 314(Other) 
Google搜索可行性：YES
-------------邮件端口检测--基于oneclickvirt/portchecker开源-------------
Platform  SMTP  SMTPS POP3  POP3S IMAP  IMAPS
LocalPort ✔     ✔     ✔     ✔     ✔     ✔    
QQ        ✘     ✘     ✔     ✘     ✔     ✘    
163       ✘     ✘     ✔     ✘     ✔     ✘    
Sohu      ✘     ✔     ✔     ✘     ✔     ✘    
Yandex    ✔     ✔     ✔     ✘     ✘     ✘    
Gmail     ✔     ✔     ✘     ✘     ✘     ✘    
Outlook   ✔     ✘     ✔     ✘     ✔     ✘    
Office365 ✔     ✘     ✔     ✘     ✔     ✘    
Yahoo     ✘     ✔     ✘     ✘     ✘     ✘    
MailCOM   ✘     ✔     ✔     ✘     ✔     ✘    
MailRU    ✔     ✔     ✘     ✘     ✔     ✘    
AOL       ✘     ✔     ✘     ✘     ✘     ✘    
GMX       ✘     ✘     ✔     ✘     ✔     ✘    
Sina      ✘     ✘     ✔     ✘     ✔     ✘    
-----------------------全国延迟检测--本脚本原创-------------------------
 联通上海	   37  | 联通太原	   69  | 联通福州	   63  |
 联通大连	   83  | 联通WuXi	   46  | 电信武汉	   47  |
 电信杭州	   39  | 电信宁波	   48  | 电信扬州	   45  |
 电信长沙	   57  | 电信苏州	   59  | 电信南京	   59  |
 电信Zhenjiang	   55  | 移动杭州	   36  | 移动福州	   65  |
 移动Beijing	   74  |
--------------------自动更新测速节点列表--本脚本原创--------------------
位置		 上传速度	 下载速度	 延迟
Speedtest.net	 187.29Mbps	 246.30Mbps	 1.54ms	
中国香港	 18.50Mbps	 11.12Mbps	 103.43ms	
联通上海5G	 17.45Mbps	 9.77Mbps	 51.30ms	
联通WuXi	 27.99Mbps	 5.62Mbps	 39.64ms	
电信浙江	 19.30Mbps	 3.54Mbps	 77.81ms	
电信Zhenjiang5G	 20.46Mbps	 3.18Mbps	 41.51ms	
移动Beijing	 11.19Mbps	 50.58Mbps	 98.79ms	
------------------------------------------------------------------------
 总共花费      : 10 分 16 秒
 时间          : Tue Nov 12 06:03:02 UTC 2024
------------------------------------------------------------------------
```