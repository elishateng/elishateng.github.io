---
layout: post
title: 利用Python对PDF文件做OCR识别
categories: Blog
description: 利用Python对PDF文件做OCR识别
keywords: Python, OCR, PDF
---

## 利用Python对PDF文件做OCR识别

> 原文请见 https://python.freelycode.com/contribution/detail/344

Hi朋友们！你们可能听说过使用Python进行OCR识别操作。在Python中，最出名的库便是Google所资助的tesseract。利用tesseract可以很轻松地对图像进行识别。现在问题来了，如果想对一个PDF文档进行OCR识别，该怎么做呢？

我现在所从事的一个项目，需要将PDF文件作为输入，从中输出文本，然后将文本存入数据库中。为此，我找寻了很久的解决方案，最终才确定使用tesseract。所以不要浪费时间了，我们开始吧。



### 1.安装tesseract

在不同的系统中安装tesseract非常容易。为了简便，我们以Ubuntu为例。在Ubuntu中你仅仅需要运行以下命令:

![blob.png](/images/blog/2020-python-ocr.png)

这将会安装支持3种不同语言的tesseract。


### 2.安装PyOCR

现在我们还需要安装tesseract的Python接口。幸运的是，有许多出色的Python接口。我们采用最新的一个：

![blob.png](/images/blog/2020-python-pyocr.png)


### 3.安装Wand和PIL

在我们开始之前，还需要另外安装两个依赖包。一个是Wand。它是Imagemagick的Python接口。我们需要使用它来将PDF文件转换成图像：

![blob.png](/images/blog/2020-python-wand.png)

我们也需要PIL因为PyOCR需要使用它。你可以查看官方文档以确定如何将PIL安装到你的操作系统中。


### 4.热身

让我们开始我们的脚本吧。首先，我们需要导入一些重要的库：

![blob.png](/images/blog/2020-python-import.png)

注意：我将从PIL导入的Image模块改名为PI了，因为如果不这样做的话，它将和wand.image模块发生重名冲突。


### 5.开始

现在我们需要获得OCR库（在本例中，即tesseract）的句柄以及我们在PyOCR中将使用的语言：

![blob.png](/images/blog/2020-python-start.png)

我们使用tool.get_available_languages()里的第二种语言，因为之前我曾尝试过，第二种语言就是英语。

接着，我们需要建立两个列表，用于存储我们的图像和最终的文本。

![blob.png](/images/blog/2020-python-start2.png)

下一步，我们需要采用wand将一个PDF文件转成jpeg文件。让我们试一试吧！

![blob.png](/images/blog/2020-python-start3.png)

注意：将PDF_FILE_NAME替换成当前路径下的一个可用的PDF文件名。

wand已经将PDF中所有的独立页面都转成了独立的二进制图像对象。我们可以遍历这个大对象，并把它们加入到req_image序列中去。

![blob.png](/images/blog/2020-python-image-array.png)

现在，我们仅仅需要在图像对象上运行OCR即可，非常简单：

![blob.png](/images/blog/2020-python-image-2-string.png)

现在，所有识别出的文本已经加到了final_text序列中了。你可以任意地使用它。我希望这个教程能够帮助到你们！

