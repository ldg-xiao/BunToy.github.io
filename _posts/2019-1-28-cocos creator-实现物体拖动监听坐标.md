---
layout: post
title: "cocos creator 物体拖动监听坐标"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com) ;)


## 物体拖动效果

通过CocosCreator由内置的cc.Node.EventType.MOUSE_MOVE鼠标（触摸）事件实现，返回参数为鼠标的坐标值。
   
根据鼠标的x,y实现物体的移动，即将鼠标放置在该节点上，实现移动。脚本代码如下：

```ruby
cc.Class({
    extends: cc.Component,

    properties: {
    },

    onLoad: function () {
        this.node.on(cc.Node.EventType.TOUCH_MOVE, function (event) { 
            var delta = event.touch.getDelta();
            this.x += delta.x;
            this.y += delta.y;

            console.log(this.x +" "+this.y)
        }, this.node);
    },
    start () {

    },

    // update (dt) {},
});
```

这里代码js,需要绑定到当前拖动的物体上，才能根据 this.node绑定. 打印结果就是当前移动物体的x,y 相对于父节点的锚点

![img](https://s2.ax1x.com/2019/01/30/klDmtO.png)

案例下载： https://pan.baidu.com/s/1ktP7CB6OWYElYoTgVtxcxw  提取码： z7q1 
	 
**"不积跬步，无以至千里；不积小流，无以成江海。"**
