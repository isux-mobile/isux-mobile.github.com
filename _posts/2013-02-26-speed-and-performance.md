---
layout: post
title: 加载和渲染的平衡
date: 2013-02-26 14:35
comments: true
categories: [前端]
author: yuguo
---

加载时间是指浏览器发出HTTP请求开始，到最终接收到所有的文件的时间。服务器响应越快，网速越快，文件越小，加载速度越快。如果用户在看到内容之前有长时间的加载等待，就会不耐烦而离开页面。

而渲染时间是指浏览器拿到资源之后，把画面在屏幕的可视区域绘制出来的时间。如果渲染时间较长，那么用户在手机上滚动页面的时候就会有“卡卡的”感觉，在创建普通文档型的页面的时候，其实渲染时间是非常快的，在5ms以下，也就是说1秒钟内，浏览器如果愿意，可以把当前页绘制200次，这时候滚动体验是非常流畅的。当网站属于复杂的App型页面的时候，如果样式或者节点处理的不好，渲染一屏需要50ms，那么浏览器在1秒内，最多也只能绘制20次。

描述1秒内能绘制多少次的名词叫FPS（Frame per second），测量单位是赫兹（HZ），一般来说FPS用于描述影片、电子绘图或游戏每秒播放多少帧，而赫兹则描述显示屏的画面每秒更新多少次。电脑的屏幕刷新频率是60HZ，所以web页面在桌面上的每帧渲染时间低于 1000ms / 60hz = 16.6ms 即可。但是要注意这里的渲染时间跟电脑的硬件是息息相关的。

> 由于人类眼睛的特殊生理结构，如果所看画面之帧率高于每秒约10-12帧的时候，就会认为是连贯的，此现象称之为视觉暂留。这也就是为什么电影胶片是一格一格拍摄出来，然后快速播放的。而超过大概85赫兹的图像，已经到达大脑处理图像的极限，人眼并无法分辨与更高更新率的差异。

所以我们在制作移动端页面的时候除了考虑加载速度，还需要考虑渲染时间，因为低端Android手机的性能可能比较差，那么同样的页面在低端手机上会有更低的FPS。那么哪些因素会导致页面渲染变慢呢？

* DOM数量
* background-position: fixed
* border-radius
* background-size （）
* box-shadow
* gradients

并不是说这些属性就不能用，只是说在可以考虑不用的时候尽量避免。

此外属性跟DOM数量是有非常大的关系的，同样的一个圆角阴影按钮，使用CSS3还是图片对于渲染速度影响并不大，但是如果显示区域有10个按钮，那么用图片的优势体现出来，图片渲染比CSS3更快。

重要的是掌握加载速度和渲染的平衡。

参考资料：

[http://perfectionkills.com/profiling-css-for-fun-and-profit-optimization-notes/](http://perfectionkills.com/profiling-css-for-fun-and-profit-optimization-notes/)

[http://www.pubnub.com/blog/css3-performance-optimizations](http://www.pubnub.com/blog/css3-performance-optimizations)

[http://jacwright.com/476/runtime-performance-with-css3-vs-images/](http://jacwright.com/476/runtime-performance-with-css3-vs-images/)

[http://paulirish.com/2011/dom-html5-css3-performance/](http://paulirish.com/2011/dom-html5-css3-performance/)