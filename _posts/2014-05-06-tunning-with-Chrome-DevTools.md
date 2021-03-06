---
layout: articles
title: 使用Chrome DevTools 调试
tags: [前端,工具]
---
以前调试js代码都是用FireBug,一度让代码的编写轻松很多.最近又开始写点小东西,顺便研究了下Chrome DevTools这款谷歌浏览器自带的调试工具.于是果断抛弃了FireBug转而使用Chrome DevTools.
它不但提供了html,css,js代码的审查和改写这些基本功能.并且还提供了各种类型断点、各种属性的查看.还能让你从内存、cpu使用、页面渲染等各角度全方位的审查你的应用.当然还有很多高级功能,感觉都可以单独写本书了.最赞的是详细的文档[Chrome DevTools](https://developers.google.com/chrome-developer-tools/),还有配套的视频(英文)!!

<!--more-->
虽然Chrome DevTools的功能很多,但是对于一些简单的应用也用不到那么多功能.就像前面看了,学了很多东西,但是写起代码来又是另一种感觉.这次的代码主要用到了以下这些功能:

1. Elements面板,主要是查看html和css的状态、dom模型和属性,还有dom上的事件监听器这些基本信息.当然还有属性断点,事件的模拟这些高级特性.
2. Network面板,由于这次的程序比较简单一般就看看资源加载情况,是否是缓存.像Replay XHR,响应信息这些也都没用到.
3. Sources面板,一般也就用用普通的断点和代码美化功能。像各种高级断点用的比较少.属性查看功能也算用的多的.目前唯一发现的缺点就是异常的提示没有FireBug友好和IE基本一个德行.
4. Timeline面板,用来看一个操作流程中的cpu和内存信息.一般问题定位后使用Profile面板比较多,主要是看看哪个方法执行时间比较长,然后对其进行相应的调优.最后的阶段看看有没有内存泄露之类的.

最后resource面板,用于查看与应用存储有关的信息.Audits面板,用于审查网页符不符合一些最佳实践.由于程序不是很复杂,有很多功能目前还没用上.但是有了这些功能,今后调试复杂程序,手机端的程序时就会方便很多.

