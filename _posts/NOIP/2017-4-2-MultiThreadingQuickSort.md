---
layout: post  
title: 多线程快排测试CPU性能
category: NOIP
tags: Misc, NOIP
keywords: NOIP, OI
description: Multi-threading quick sort
---

今天随手撸了个小玩具，算是让我见识了一下AMD RyZen那改天换地的强大力量。

想必大家都知道快排，

我尝试手撸了一个之后发现并不能跑，并行这种东西是很傲娇的，按理说是要上锁的，或者wait线程。
但是我已经不想折腾这些了，而且我的打算是把它弄进之前那个算法库的，所以说我应该使用Java写。

但是，我已经太久没接触Java了（逃

所以说我还是股沟了一下，找到了[这篇文章](https://www.oschina.net/code/snippet_145230_44938)。

里面有一个2014年的大龄程序员手撸的并行快排。感谢这位程序员。根据原文的说法，

> Java 多线程 快速排序 1亿数据 3.5秒 <br/>
写了个Fork/Join的，但好像并没有更快。

然后我把代码抄下来（这正是我等垃圾程序员的职责所在啊），在自己的笔记本上跑了一波，1716ms。
这次运行我没有保留截图，因为下面有更精彩的。

我把运行脚本和JRE环境打包发给了我的朋友psc，他是拥有**AMD RyZen 1700X**的男人！

然后他把数据扩大了十倍！然后发来如下运行截图：

![](https://coding.net/u/ice1000/p/Images/git/raw/master/blog-img/9/0.png)

卧槽吓尿了。

然后psc说，整数排序太垃圾了，上浮点吧。

于是我改了代码（double占内存，要用float），又打包了一个。

// 未完待续

没错，这就是RyZen，是6700HQ的两倍。

