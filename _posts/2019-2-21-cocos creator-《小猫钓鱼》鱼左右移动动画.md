---
layout: post
title: "cocos creator-《小猫钓鱼》鱼左右移动动画"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/huoying/92580.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com)


## 小鱼左右移动涉及动画：

关于动作，参考官方教程以及API：

http://docs.cocos.com/creator/manual/zh/scripting/actions.html  官方教程

http://docs.cocos.com/creator/manual/zh/scripting/action-list.html  动作API

关于properties的参数说明，请参考官方文档：

http://docs.cocos.com/creator/manual/zh/scripting/reference/attributes.html

![img](https://img-blog.csdn.net/20181015191607517?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3p6eDAyMw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

```ruby
start () {
let action = cc.sequence(
cc.moveTo(5,320,this.node.y),//向右移动
cc.flipX(true),//翻转X
cc.moveTo(5,-320,this.node.y),//向左移动
cc.flipX(false)//翻转X
);
this.node.runAction(cc.repeatForever(action));//重复运动
},
```
   
- 首先`cc.sequence()` 表示 动画顺序执行动作，创建的动作将按顺序依次运行。使用方法可以参看：https://docs.cocos.com/creator/api/zh/modules/cc.html#sequence
- `cc.moveTo(5,320,this.node.y)` 表示在5s时间里向右移动320px, this.node.y 即为当前节点初始的y轴坐标位置(这里320是屏幕一半)
- `cc.flipX(true)` 表示x轴翻转，图形反向，相对于图片，（比如上面第二个使用false,图片初始跟翻转后一样，所以不需要用false）
- `cc.moveTo(5,-320,this.node.y)` 表示当前节点向左移动到 x= -320位置，y轴不变，时间为5s
- `cc.repeatForever(action)` 表示动作一直重复执行action      


注意到一开始的运动速度，和后面的速度好像有点不一致哦。原因起始很简单，第一段移动的路程和后面移动的路程不一致，而我们设定的移动时间是相同的，因此速度上面就有了差异。


```ruby
    start() {
        let x = this.node.x;
        let y=this.node.y;
        let duration = 5 - (this.node.x + 320) / 640 * 5;
        let action = cc.sequence(
            cc.moveTo(duration, 320, y),
            cc.flipX(true),//翻转X
            cc.moveTo(duration, x, y),

            cc.moveTo(5 - duration, -320, y),
            cc.flipX(false),//翻转X
            cc.moveTo(5 - duration, x, y),
        );
        this.node.runAction(cc.repeatForever(action));//重复运动
    },
```

## 小鱼左右移动添加速度变化：

给鱼增加一个属性Speed，用来控制鱼的速度。

```ruby
properties: {
        mSpeed: {
            default: 1,
            type: cc.Float,
            tooltip: "鱼的速度,默认正常速度为1，最小值为0.1，最大值为10",
            min: 0.1
        },
    },
```


再次优化结果如下：

```ruby
start() {
        let x = this.node.x;
        let duration = 5 - (this.node.x + 320) / 640 * 5;
        let sqeAction = cc.sequence(
            cc.moveTo(duration, cc.v2(320, this.node.y)),
            cc.flipX(true),//翻转X
            cc.moveTo(duration, cc.v2(x, this.node.y)),

            cc.moveTo(5 - duration, cc.v2(-320, this.node.y)),
            cc.flipX(false),//翻转X
            cc.moveTo(5 - duration, cc.v2(x, this.node.y)),
        );

        let action = cc.speed(cc.repeatForever(sqeAction), this.mSpeed);
        this.node.runAction(action);//重复运动
    },
```

到属性管理器中更改属性值速度：2 可以看到明显加快速度。

- cc.speed() 修改动作速率,例如；var newAction = cc.speed(action, 0.5);

源码：https://pan.baidu.com/s/14L4QZZhxLGP66jJCw-Lkug
	 
**"不积跬步，无以至千里；不积小流，无以成江海。"**
