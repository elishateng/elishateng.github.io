---
layout: post
title: Ubuntu Install Oracle JDK 8
categories: Blog
description: Ubuntu Install Oracle JDK 8
keywords: jdk
---

## Ubuntu Install Oracle JDK 8

1. 下载 jdk-8u251-linux-x64.tar.gz

2. 解压到/opt/jdk
```
sudo mkdir  -p /opt/jdk
```

3. Install Oracle Java 8 on Ubuntu 20.04 LTS with Alternatives
```
sudo update-alternatives --install /usr/bin/java java /opt/jdk/jdk1.8.0_251/bin/java 100
```

4. 如果有多个版本可以这么切换
```
sudo update-alternatives --config java
```

5. 配置环境变量

编辑 /etc/environment ，填入以下内容
```
JAVA_HOME=/opt/jdk/jdk1.8.0_251
JRE_HOME=/opt/jdk/jdk1.8.0_251/jre
```
使生效
```
source /etc/environment
```
