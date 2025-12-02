---
layout: post
title: Add Nuget Package Source
categories: Blog
description: Add Nuget Package Source
keywords: dotnet, nuget
---

## Add Nuget Package Source
```
dotnet nuget add source http://xxx.xxx.xxx.xxx/xxx/api/v2 -n SourceName1
dotnet nuget add source https://xxx.xxx.xxx/dotnet/api/v3/index.json -n SourceName2 

dotnet nuget add source
dotnet nuget add source ~/local_packages -n "Local Nugets"


you can use the command to see current nuget sources:
dotnet nuget list source
```
