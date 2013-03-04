---
layout: post
title: 用Fiddler对移动设备抓包
date: 2013-03-04 14:35
comments: true
categories: [前端]
author: yuguo
---

手机抓包与配host
---

在PC上，我们可以很方便地配host，但是手机上如何配host和抓包，就需要把手机中的所有请求转到PC端。

这里主要使用fiddler和远程代理，实现手机配host的操作，具体操作如下：

1. 首先，保证PC和移动设备在同一个局域网下（在我们的办公网络中，也就是Tencent-Freewifi）；
2. PC上开启fiddler，并在设置中勾选`allow remote computers to connect`
![image](/files/2013/1/web-debug-5.png)
3. 手机上设置代理，代理IP为PC的IP地址，端口为8888（这是fiddler的默认端口）。通常手机上可以直接设置代理，如果没有，可以去下载一个叫ProxyDroid的APP来实现代理的设置。对于iOS来说，在Wifi>当前wifi，进去之后可以设置HTTP代理。
4. 此时你会发现，用手机上网，走的其实是PC上的fiddler，所有的请求包都会在fiddler中列出来，配合willow使用，即可实现配host，甚至是反向代理的操作。

常见问题
---

1. 台式机可以买无线网卡接入FreeWifi，但同时连接有线网和无线网的时候会出现bug，可以把有线网络禁用。
2. Fiddler选择All Processes，所有的请求都通过Fiddler。
