---
layout: post
title: FFmpeg Video to Gif
categories: Blog
description: FFmpeg Video to Gif
keywords: ffmpeg, gif
---

## FFmpeg Video to Gif

ffmpeg download:　http://ffmpeg.org/download.html

https://github.com/BtbN/FFmpeg-Builds/releases
```
ffmpeg-n7.0-latest-win64-gpl-7.0.zip
ffmpeg-n7.0-latest-win64-gpl-shared-7.0.zip
ffmpeg-n7.0-latest-win64-lgpl-7.0.zip (Recommand)
ffmpeg-n7.0-latest-win64-lgpl-shared-7.0.zip
```
这些FFmpeg的压缩包文件名中的差异主要体现在它们所使用的许可证（GPL vs LGPL）以及是否包含共享库（shared）上。以下是它们之间的主要区别：

许可证（License）差异：

GPL (GNU General Public License) 是一种广泛使用的开源许可证，它要求使用GPL许可证发布的软件（以及任何基于该软件的作品）都必须以GPL许可证发布。这意味着，如果您在您的软件或项目中使用了GPL版本的FFmpeg，那么您的软件或项目也必须开源，并且使用GPL许可证1。

LGPL (Lesser GNU General Public License) 是GPL的一个变种，它允许用户将LGPL许可的软件链接到专有软件（非开源软件）中，而不需要将整个软件或项目开源。LGPL要求修改LGPL许可软件的用户必须开源他们的修改，但不需要开源他们的整个项目1。

是否包含共享库（Shared Libraries）：

文件名中包含shared的压缩包提供了FFmpeg的动态链接库（DLLs），这意味着这些库可以在多个程序之间共享，而不是每个程序都包含一份完整的库代码。这种方式可以节省磁盘空间，但程序在运行时需要这些库是可用的2。

不包含shared的压缩包则提供了静态链接的FFmpeg库，即这些库被直接包含在程序中，程序运行时不需要额外的库文件。这种方式的程序更加独立，但可能会占用更多的磁盘空间2。

综上所述，选择哪个压缩包取决于您的具体需求：

如果您希望您的软件或项目保持专有（不开源），那么您应该选择LGPL版本的FFmpeg。

如果您打算将FFmpeg嵌入到您的专有软件中，并且希望节省磁盘空间，那么您应该选择lgpl-shared版本。

如果您希望您的软件或项目完全开源，并且不介意增加一些磁盘空间占用，那么您可以选择GPL版本，并根据需要选择是否包含共享库。



cmd or powershell:
```
> ffmpeg -i input.mp4 -vf fps=10,scale=320:-1 output.gif
```
//这里 -i input.mp4 指定输入视频文件，-vf fps=10,scale=320:-1 是视频过滤器，用于设置帧率和大小，这里设置帧率为 10 fps，宽度为 320（高度自动保持比例）output.gif 是输出 GIF 文件名。

