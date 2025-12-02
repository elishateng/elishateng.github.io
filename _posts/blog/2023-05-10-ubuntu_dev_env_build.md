---
layout: post
title: Ubuntu Development Environment Build
categories: Blog
description: Ubuntu Development Environment Build
keywords: ubuntu, development
---

## Ubuntu Development Environment Build
1. 安装Ubuntu 18.04 https://www.linuxtechi.com/ubuntu-18-04-server-installation-guide/

2. 配置国内源 https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/

3. 安装ubuntu-desktop
```
sudo apt-get install ubuntu-desktop
```

4. 添加用户和删除用户
```
sudo adduser spark
sudo vim /etc/sudoers
sudo userdel -r spark
```

5. 更新git并配置命令补全
```
sudo apt update

sudo apt install make libssl-dev libghc-zlib-dev libcurl4-gnutls-dev libexpat1-dev gettext unzip

sudo wget https://github.com/git/git/archive/v2.24.1.tar.gz -O git.tar.gz
tar -xf git.tar.gz cd git-*
sudo make prefix=/usr/local all sudo make prefix=/usr/local install git --version
git config --global user.name "Your Name" git config --global user.email "youremail@yourdomain.com"
git config --list

sudo mkdir /opt/git-2.24.1/ sudo cp git-2.24.1/contrib/completion/git-completion.bash /opt/git-2.24.1/ sudo vi /etc/profile.d/bash_completion.sh

add the following line: . /opt/git-2.24.1/git-completion.bash
```

6. 安装Oracle Java https://www.jianshu.com/p/75f0f34b599d

7. 安装dotnet sdk https://docs.microsoft.com/en-us/dotnet/core/install/linux-package-manager-ubuntu-1804

8. 安装并配置samba
```
sudo apt-get install samba

sudo smbpasswd  -a smbname

sudo gedit /etc/samba/smb.conf

--------------------------------------
[xuhy]

     comment = user name
     path = /home/username
    writable = yes
    public = no
    valid users = username
    write list = username
--------------------------------------

sudo service smbd restart
```

9. 开启和关闭图形界面
```
1. 关闭用户图形界面
sudo systemctl set-default multi-user.target
sudo reboot

2. 开启用户图形界面
sudo systemctl set-default graphical.target
sudo reboot
```

10. [Ubuntu 20.04 install reference](https://www.linuxtechi.com/ubuntu-20-04-lts-installation-steps-screenshots/)
