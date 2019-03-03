---
layout: post
title: "cocos creator 动作系统scaleTo,scaleBy"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com) ;)

> [动作官方教程:http://docs.cocos.com/creator/manual/zh/scripting/actions.html](http://docs.cocos.com/creator/manual/zh/scripting/actions.html) 

> [动作API:http://docs.cocos.com/creator/manual/zh/scripting/action-list.html(http://docs.cocos.com/creator/manual/zh/scripting/action-list.html) 

## scaleTo
  
  将节点大小缩放到指定的倍数。返回 ActionInterval
   
```ruby
参数列表
duration Number --标识持续动画时间
sx Number scale parameter in X  ---标识x缩放倍数
sy Number scale parameter in Y, if Null equal to sx  --如果两个参数x,y缩放相同
```
 
简单案例：

```ruby 
// It scales to 0.5 in both X and Y.
var actionTo = cc.scaleTo(2, 0.5); --持续2秒，缩小到原来0.5倍
// It scales to 0.5 in x and 2 in Y
var actionTo = cc.scaleTo(2, 0.5, 2); --持续2秒，x缩小到原来0.5倍, y 缩放都原来2 倍
//节点执行动画
this.startBtn.runAction(actionTo)

this.node.setScale(2);
var action = cc.scaleTo(5,2,2);
this.node.runAction(action);
scaleTo就是在变化为原始的多少倍，由于已经设置了setScale(2),所以再用scaleTo到2倍不发生变化；

var action1 = cc.scaleTo(5,2,2);
var action2 = cc.scaleTo(5,2,2);
var seq = cc.sequence(action1,action2);
this.node.runAction(seq); //只会变为原始的2两倍大小，第二个action2实际上没有执行；
``` 

参考api: https://docs.cocos.com/creator/api/zh/modules/cc.html#scaleto

重复两个缩小，放大动作：

```ruby 
var scaleTo = cc.scaleTo(0.8,0.9);  //持续0.8s 缩小到原来0.9倍
var reverse = cc.scaleTo(0.8,1); //持续0.8s 从原来0.9 再放大到 正常1
var seq = cc.sequence(scaleTo,reverse);  //执行指定的顺序
var repeat = cc.repeatForever(seq);
this.startBtn.runAction(repeat);
``` 

![img](https://s2.ax1x.com/2019/01/31/k1U8Z8.gif)

## scaleBy
  
  按指定的倍数缩放节点大小。返回 ActionInterval
   
```ruby
参数列表
duration Number duration in seconds
sx Number sx scale parameter in X
sy Number | Null sy scale parameter in Y, if Null equal to sx
```

案例

```ruby
this.node.setScale(2);
var action = cc.scaleBy(5,2,2);  //此时节点会乘以2倍，变为原来2倍
this.node.runAction(action);

scaleBy就是在现有的基础上，乘以多少倍。
var action1 = cc.scaleBy(5,2,2);
var action2 = cc.scaleBy(5,2,2);
var seq = cc.sequence(action1,action2);
this.node.runAction(seq);    //此时节点会变为原始的4倍大小
```

如果比较caleTo和scaleBy的区别，可以参考：https://blog.csdn.net/xiaownezi666/article/details/81634932

<div>  
<iframe frameborder="0" id="video" src="https://vd.yinyuetai.com/hc.yinyuetai.com/uploads/videos/common/F0640164EFEFD7D44719C79709D90E7E.mp4" allowfullscreen></iframe>
</div>
	
	 
**"不积跬步，无以至千里；不积小流，无以成江海。"**
