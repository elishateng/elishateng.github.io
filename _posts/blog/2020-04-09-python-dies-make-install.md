---
layout: post
title: Ubuntu 16.04 install python-2.7.17
categories: [cate1, cate2]
description: some word here
keywords: keyword1, keyword2
---

## Ubuntu 16.04 install python-2.7.17

### 1. 安装依赖

```shell
sudo apt-get install build-essential checkinstall
sudo apt-get install libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev
```

### 2. 下载并解压缩

```shell
wget https://www.python.org/ftp/python/2.7.17/Python-2.7.17.tgz
tar -xvf Python-2.7.17.tgz
```

### 3. 编译安装 ，一路回车安装完成

```shell
./configure --enable-optimizations
make
sudo checkinstall
```

安装位置：/usr/lib/python2.7

### 4. 安装 PIP

```shell
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.pytar -xvf Python-2.7.17.tgz
```

### 5. 显示版本信息

```shell
python --version
```

### 6. 卸载 python

```shell
sudo dpkg -r python
```

### 7. 错误解决

#### Error

```
Compiling /usr/local/lib/python2.7/xml/dom/xmlbuilder.py ...
Listing /usr/local/lib/python2.7/xml/etree ...
Compiling /usr/local/lib/python2.7/xml/etree/ElementInclude.py ...
Compiling /usr/local/lib/python2.7/xml/etree/ElementPath.py ...
Compiling /usr/local/lib/python2.7/xml/etree/ElementTree.py ...
Compiling /usr/local/lib/python2.7/xml/etree/__init__.py ...
Compiling /usr/local/lib/python2.7/xml/etree/cElementTree.py ...
Listing /usr/local/lib/python2.7/xml/parsers ...
Compiling /usr/local/lib/python2.7/xml/parsers/__init__.py ...
Compiling /usr/local/lib/python2.7/xml/parsers/expat.py ...
Listing /usr/local/lib/python2.7/xml/sax ...
Compiling /usr/local/lib/python2.7/xml/sax/__init__.py ...
Compiling /usr/local/lib/python2.7/xml/sax/_exceptions.py ...
Compiling /usr/local/lib/python2.7/xml/sax/expatreader.py ...
Compiling /usr/local/lib/python2.7/xml/sax/handler.py ...
Compiling /usr/local/lib/python2.7/xml/sax/saxutils.py ...
Compiling /usr/local/lib/python2.7/xml/sax/xmlreader.py ...
Compiling /usr/local/lib/python2.7/xmllib.py ...
Compiling /usr/local/lib/python2.7/xmlrpclib.py ...
Compiling /usr/local/lib/python2.7/zipfile.py ...
Makefile:1098: recipe for target 'libinstall' failed
make: *** [libinstall] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.
```

#### Solution

I saw this (and reported this issue in SF's tracker) at some time around
2.2/2.3 (just cann't recall). I don't know what causes this problem
exactly, but in my case the installation succeeded if I removed prevoius
python's library directory (/usr/lib/python2.x or
/usr/local/lib/python2.x). The module that stopped installation was
exactly the same.

```shell
sudo rm -rf /usr/lib/python2.x
sudo rm -rf /usr/local/lib/python2.x
```

### Referrence

> http://www.firstsolver.com/wordpress/?p=4370

> https://bytes.com/topic/python/answers/691250-python-dies-make-install