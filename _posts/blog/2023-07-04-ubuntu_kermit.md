---
layout: post
title: Ubuntu Kermit
categories: Blog
description: Ubuntu Kermit
keywords: kermit
---

## Ubuntu Kermit

1. Install
```
sudo apt-get install ckermit
```

2. Config
The configure file will exist in /etc/kermit/kermrc or ~/.kermrc:
```
set line /dev/ttyUSB0
set speed 115200
set carrier-watch off
set handshake none
set flow-control none
robust
set file type bin
set file name lit
set rec pack 1000
set send pack 1000
set window 5
```

3. Issue
```
C-Kermit>c Sorry, you must SET LINE or SET HOST first
```
出现这个的原因是kermit是root用户的，在运行时不会使用~/.kermrc配置
```
$usermod -G dialout [UserName]  //将user添加到dialout组即可，无须使用root
```
解决办法，将配置文件移动到root目录下
```
sudo mv ~/.kermrc /root/
```
