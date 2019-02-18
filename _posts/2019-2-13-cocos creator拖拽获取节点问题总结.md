---
layout: post
title: "cocos creator获取节点拖拽绑定问题总结"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
keywords: cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com) ;)


## 获取节点出现问题

js绑定在`blast`节点上,  `blood`与它并列, 如图所示。

![img](https://s2.ax1x.com/2019/02/13/k0f5in.png)

```bash
properties: {
   blood: {
     default: null,
     type: cc.Node
   },
 },
```

但是在js脚本中 使用 this.blood 总是获取不到。 console.log(this.blood)打印如下：

![img](https://s2.ax1x.com/2019/02/13/k0foR0.png)

但是打印 console.log(this.blood.node)打印如下：

![img](https://s2.ax1x.com/2019/02/13/k0hQOS.png)

可以根据打印节点结果，使用 this.blood.node 便可以访问当该节点。


## 实现帧动画

绘制动画注意：
  
- 创建一个空节点，点击属性列表中的add property按钮，选择添加cc.Sprite.spriteFrame，通常会没有这个选项。此时需要在此空节点下再创建一个 精灵spirit，然后点击此节点添加就会出现。
- 在每帧添加动画中，拖拽图片到对应的帧中，此时鼠标跟着帧动即可加入。 当为某一个帧添加事件时候可以，在此帧上方点击出现白色箭头时候，点击左边有个添加事件按钮，然后双击上方白色按钮，会显示事件框。
  
参考：
- https://www.jianshu.com/p/7d9574f179eb
- https://www.jianshu.com/p/9874f917602d

使用过程：
   
   ```ruby
   var animal=this.getComponent(cc.Animation);
        animal.play("small")
        animal.showEnd=function(){  //某一帧结束执行监听事件
           
            this.node.active=false;  //添加消失

            this.blood.node.active=true;
            var fadeOut=cc.fadeOut(0.4);
            this.blood.node.runAction(fadeOut);

            // var nodeBlood = cc.find("Canvas/main/blood");//通过访问路径来获取节点
            // nodeBlood.active=true;
            // var fadeOut=cc.fadeOut(0.4);
            // nodeBlood.runAction(fadeOut);
        }.bind(this)
   ```

## 实现文本提示效果

类似合成游戏，合成的每个人物弹出获取金币提示效果，结合上面的问题。

```ruby
   var animal=this.getComponent(cc.Animation);
        animal.play("small")
        animal.showEnd=function(){
           
            this.node.active=false;  //添加消失

            this.blood.node.active=true;
            var fadeOut=cc.fadeOut(0.4);
            this.blood.node.runAction(fadeOut);

            // var nodeBlood = cc.find("Canvas/main/blood");//通过访问路径来获取节点
            // nodeBlood.active=true;
            // var fadeOut=cc.fadeOut(0.4);
            // nodeBlood.runAction(fadeOut);
        }.bind(this)
   ```

源码地址： https://pan.baidu.com/s/1mkX2VVlJ9hrWCpDFENjYvg
  
**"不积跬步，无以至千里；不积小流，无以成江海。"**
