---
layout: post
title: IMGUI vs RMGUI
categories: Blog
description: IMGUI vs RMGUI
keywords: imgui, rmgui
---

## IMGUI vs RMGUI

MGUI全称：Immediate Mode GUI。
IMGUI不同于我们常见的RMGUI（MFC、QT、WPF、GTK都是RMGUI）。在典型的RMGUI的应用程序中，我们创建了一堆小部件（widgets），它们通过布局显示在窗口上，我们可以查询小部件的状态，接受系统发来消息和数据，处理、生成新的状态，最终重绘小部件，用户看到改变。

在RMGUI中，代码至少分成3部分：创建、响应消息、删除。如果考虑到多个小部件之间需要传递消息，在系统运行时我们难以预测消息的传播、小部件状态的改变。虽然RMGUI这么麻烦，但在常规的应用开发中，依然是中流砥柱。但是在游戏开发中，用户与应用的交互十分频繁，游戏逐帧更新,复杂的RMGUI难以做到60FPS。在这种情况下IMGUI就可以展示它的威力。

Reference Link: https://blog.csdn.net/weixin_30613343/article/details/99668921


[UI开发今天学了两次新词：IMGUI RMGUI](http://www.cppblog.com/Error/archive/2015/06/25/211039.html)
大神的解释：

Immediate Mode GUI (IMGUI)。这种类型的更多的适用于显示区域实时刷新的程序里面，例如游戏和CAD等。
Retained Mode GUI (RMGUI)

用一个传统RMGUI库的时候，用户往往需要显式的初始化每一个控件对象。每个控件都是存在内存中的实体，并且每个控件都需要自己保存一部分数据（例如一个slider需要保存一个数值，Button要保存一个回调事件等），用户还需要在一个回调函数里将控件里的数据拷贝回程序本身中（MVC模式）。

IMGUI模式在使用上会更简单粗暴一些。控件没有自己的对象，不保存任何状态，不用单独的去实现UI和程序间数据的交换，甚至都不需要单独为事件写回调函数。每个控件就是一个函数，直接在程序的Draw()函数里要哪个控件就调用哪个函数就好了。

