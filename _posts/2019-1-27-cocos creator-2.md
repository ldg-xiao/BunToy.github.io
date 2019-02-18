---
layout: post
title: "cocos creator UI弹窗遮罩屏蔽触发事件"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy版本信息均来自 [BunToy官网](https://buntoy.com/buntoy.html) ;)


## UI弹窗遮罩屏蔽触发事件的处理.

   所遇情况： 游戏场景中，会设计很多的UI弹窗，当弹窗出现后，点击UI界面后却触发场景中的按钮、触摸事件。
   
   解决办法：在UI上添加组件：BlockInputEvents （当前你要弹框的根组件上）
   
   实图： 添加组件——> 添加UI组件——> Block Input Events
   
   ![img](https://img-blog.csdn.net/20180823091708826?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0xJWUlGUkVE/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
   
  
   参考：https://blog.csdn.net/liyifred/article/details/81974449

**"Welcome to the producer side!"**
