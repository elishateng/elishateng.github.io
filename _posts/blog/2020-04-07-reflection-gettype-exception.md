---
layout: post
title: Assembly GetTypes Exception
categories: Blog
description: some word here
keywords: Assembly, Refection, GetTypes, GetExportedTypes
---

在使用C#的反射的功能时，我们需要加载某一个DLL，然后去获取其中的属性或方法。如果AAA.dll中引用了BBB.dll，我们在加载AAA.dll后，再去获取所有的Types，代码如下：

```.cs
Assembly asb = Assembly.LoadFile(@"X:\xxx\bin\Debug\AAA.dll");
Type[] types = asb.GetTypes();
```

The following exception reported:
> System.Reflection.ReflectionTypeLoadException: 'Unable to load one or more of the requested types. Retrieve the LoaderExceptions property for more information.'

这种情况出现时，我们不好排查具体的原因。

如果我们换另一个方法GetExportedTypes，则会报另一个错误，代码如下：

```.cs
Assembly asb = Assembly.LoadFile(@"X:\xxx\bin\Debug\AAA.dll");
Type[] types = asb.GetExportedTypes();
```

The following exception reported:
> System.IO.FileNotFoundException: 'Could not load file or assembly 'BBB, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null' or one of its dependencies. The system cannot find the file specified.'

这时候我们可以确定，在加载AAA.dll时，没有找到其引用的BBB.dll，所以我们不妨尝试把BBB.dll拷贝到我们运行的exe目录，再次执行，发现都运行通过！

原因可以确定了。