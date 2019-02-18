---
layout: post
title: "cocos creator 节点显示与隐藏"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com) ;)


## 隐藏和显示有两种方式：

(1) 禁止节点node的运行，方法是this.node.active=false,[此时隐藏了节点，且节点不再运行];
   
恢复节点正常运行，this.node.active=true;或者使用this.node.active = !this.node.active
	
(2).改变该节点的不透明度，更改了透明度只是看不到，但node上的脚本还在正常运行；

方法是this.node.opacity=0;//透明，此时看不到；

this.node.opacity=255;//完全不透明，此时显示；

两者使用是有区别的，
![img](https://images2018.cnblogs.com/blog/1228967/201808/1228967-20180822224205990-1162089476.jpg)

第二种方式代码：

```ruby
this.scheduleOnce(function(){ 
   this.node.opacity=255; 
},2);
//scheduleOnce是cc中特有定时器方法，执行一次，2标识2秒后执行
```


	 
	 
**"不积跬步，无以至千里；不积小流，无以成江海。"**
