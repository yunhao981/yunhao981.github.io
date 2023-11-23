---
title: Mac 系统挂掉之后
categories: 杂七杂八
tags: 杂七杂八
description: 
show: true
date: 2023-11-23 00:05:13
---

2015 年的 13寸 MacBook Pro 服役至今

macOS Sonoma 是已经吃不上了

所以试着用了 Open Core Legacy Pathcer 偷渡

一时邪念兴起，按了下系统更新

然后卡了 24 小时以上（

## 想要恢复系统，最好能保留原有数据

Option + Command + R 搓个结印开机进入恢复模式

1. 恢复至原机出厂系统 (OS X 10.11 El Capitan)
2. 恢复至仍旧支持的系统 (macOS 12 Monterey)
3. 恢复至偷渡的最新系统 (macOS 14 Sonoma)
4. 恢复到先前 Time Machine 备份

### 1. 恢复到 OS X 10.11

先前换了硬盘，970 Evo Plus

而第三方 pcie ssd 的支持从 10.12 才开始支持

所以在试着安装 10.11 的时候会直接找不到硬盘

### 2. 恢复到 macOS 12 Monterey

在选择硬盘的时候

`com.apple.BuildInfo.preflight.error error 21`

试着去磁盘工具里面修复了硬盘

重试并没有解决问题

### 3. 恢复到 macOS 14 Sonoma

因为先前已经偷渡到了新版本的 Sonoma，

这次又是在系统升级的时候炸的，

所以在选硬盘的时候提示说

`The volume cannot be downgraded.`

并不允许降级

### 4. 时光机？

在登录上 nas 选择备份并继续之后

回到了恢复菜单的入口处


## 放弃恢复系统，试着导出数据

其他文档都好说，至少都有一份备份

我只关心 10 卷胶卷的 raw 以及 go pro 录制的骑行视频

自冲自扫，加上一点简单的后期，花了大约一个月

即便底片在手上，要重新扫一卷至少也要一小时

移动硬盘是 NTFS 的，macOS 原生不支持写入

最大的 u 盘只有 32 GB，大概率塞不下

好在恢复模式下有终端可以用……

那就能 scp 了！

局域网内有一台 linux server

插了块硬盘但是没有挂载

所以先看下这块盘

```bash
fdisk -l
```

```
Disk /dev/sdb: 298.09 GiB, 320072933376 bytes, 625142448 sectors
Disk model: ST320LT007-9ZV14
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xfb4efb4e

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 625141759 625139712 298.1G 83 Linux
```

找到了这块盘的 device 是在 sdb1 上

直接把它挂载在 `/mnt` ，然后调整下文件用户组

```
sudo mount /dev/sdb1 /mnt
sudo mkdir photo
sudo chown -R parallels:parallels ./photo
```

之后在 mac 上冲进想要备份的目录的上一层，

用 scp 通过用户名密码认证把目录直接送到 server 上

```bash
cd /Volume/970EvoPlus\ -\ Data\Users\parallels\Photo
scp -r a7 parallels@192.168.2.70:/mnt/photo/a7/
```

### 痛快地抹盘重装！
