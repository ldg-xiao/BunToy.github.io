---
layout: post
title: "cocos creator button响应监听事件"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com) ;)


## 通过编辑器实现（最常用方式）

(1)首先要创建脚本BtnClick1.js，添加监听事件btnClick1函数，（需要把这个js文件绑定到需要点击的按钮上，来启动btnClick1 函数).

```ruby
btnClick1: function (event, customEventData) {
//这里 event 是一个 Touch Event 对象，你可以通过 event.target 取到事件的发送节点
var node = event.target;

var button = node.getComponent(cc.Button);

//这里的 customEventData 参数就等于你之前设置的 "click1 user data"
cc.log("node=", node.name, " event=", event.type, " data=", customEventData);
}
```

(2)将js绑定到点击按钮上，按一下步骤进行操作

   1.首先在层级管理器中，找到你要点击的按钮，点击这个按钮，
   
   2.然后右边这个按钮的属性检查器就会出现。（所有操作就在这个属性检查器里）.
   
   3.继续属性检查器最下方有个“ 添加组件 ”按钮， 点击-用户脚本组件 - 找到那个js脚本BtnClick1, 此时会出现一个新的属性层级叫BtnClick1.
   
   4.继续属性检查器最下方有个“ 添加组件 ”按钮， 点击-UI组件-Button, 此时会出现一个新的属性层级叫Button。
   
   5.接下来在这个Button层级里，找到Click Event 有个输入框为0，，手动改为1，下方点击出现了几个框.
   
   6.继续第一个cc.node ，需要在 层级管理器中你点击的按钮，拖到这个cc.node 输入框即可，框就会有对应按钮名称（注意下面图片中是别人绑定的canvas,这里绑定的是你要点击button）
     第二框，需要选择这个脚本js 文件，第三个框，选择绑定的点击事件函数名btnClick1， 操作完了，保存好
	（customEventData 自定义事件数据,可以不用管）

  
   ![img](https://img2018.cnblogs.com/blog/55799/201812/55799-20181212212324190-1574535819.png)
   
   以上步奏参考自：https://www.cnblogs.com/chevin/p/7893963.html， 做了步奏更详细更改. 
   
   如果还是不明白，可以添加微信手把手教你绑定.
   
## 通过编辑器&代码实现

   (1)创建脚本BtnClick3.js，增加onLoad函数
```ruby
onLoad() {
        this.node.on(cc.Node.EventType.TOUCH_START, function (event) {
            cc.log("TOUCH_START event=", event.type);
        });

        this.node.on(cc.Node.EventType.TOUCH_MOVE, function (event) {
            cc.log("TOUCH_MOVE event=", event.type);
        });

        this.node.on(cc.Node.EventType.TOUCH_END, function (event) {
            cc.log("TOUCH_END event=", event.type);
        });
    }
```
这里点击事件对应点击开始，移动，结束事件状态，可以自己更改尝试下.

(2)然后跟方式一一样，在层级管理器中点击按钮,右边出现对应属性管理器，
	
继续属性检查器最下方有个“ 添加组件 ”按钮， 点击-用户脚本组件 - 找到那个js脚本BtnClick3, 此时会出现一个新的属性层级叫BtnClick3.
   
就可以了。
	 
	 
	 
**"Welcome to the producer side!"**
