---
layout: post
title: "cocos creator 获取节点方式"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com) ;)


## 通过拖曳节点

要在挂载的脚本中通过代码声明一个变量属性，类型为cc.Node 或者cc.Button等等对应组件。
   
```ruby
  properties: {
        diamondLabel: {  //钻石label
            default: null,
            type: cc.Node
        },
  },
});
```

这样就会在脚本挂载的地方出来一个空的节点。

![img](http://mmbiz.qpic.cn/mmbiz_png/jlMCD4Fz8djK59zkCHIcGGiaVIEdTMsiam0jJpfIffnSfTb2KjOtMsEAayR4z8K318MPvtrEsLoWzbCGiawR2X8wg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

可以将层级管理器上的需要使用的节点拖到这个属性管理器空的控件上，然后通过代码获取到

```ruby
  this.diamondLabel.getComponent(cc.Label).string = diamonds   //更改宝石
```


## 通过从根节点查找

可以通过全局查找节点位置
   
```ruby
  cc.find("Canvas/mainCan/list/forging/detailBg/diamond/label").getComponents(cc.Label)[0].string = diamonds
```
	 
## 从当前节点开始查找childer,parent

可以通过子节点一层一层进行查找

![img](http://mmbiz.qpic.cn/mmbiz_png/jlMCD4Fz8djK59zkCHIcGGiaVIEdTMsiamVJIJNIB3Nj0myvxpdOwhDKbdu8hY4QMvQncichxxtHxWnUHibictH5YNQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

这里，son1是该节点this.node下的子节点，而son2为son1下的子节点，可以通过getChildByName函数进行一层一层查找。

也可以不通过名字，利用序列号进行查找,例如以下son1中有很多个son2

![img](http://mmbiz.qpic.cn/mmbiz_png/jlMCD4Fz8djK59zkCHIcGGiaVIEdTMsiamYR1ibM7KdPHuA3V9zUrYfBGB05A8566YDoJsuJpCGUvKzC86TQ9PBzQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

可以通过以下循环获取到每一个son2：

![img](http://mmbiz.qpic.cn/mmbiz_png/jlMCD4Fz8djK59zkCHIcGGiaVIEdTMsiamV8yeBTuibfiaCqjIGpIulFQYFuKeN8zVdaIBpzZPteHFJcB3bhGbunkQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

Creator中一个节点可以挂载多个组件，如下：

![img](http://mmbiz.qpic.cn/mmbiz_png/jlMCD4Fz8djK59zkCHIcGGiaVIEdTMsiamcY1GDmXZNjH33iauQTTWWZH5O013jcqke1PibOnTvrEdZHsGVVafKHBA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

Canvas节点中有Canvas组件、有gama和wgq两个脚本组件、有Label渲染组件等。以son节点为例

![img](http://mmbiz.qpic.cn/mmbiz_png/jlMCD4Fz8djK59zkCHIcGGiaVIEdTMsiampe2FmiawJSibRpEp0SKCfPCcdHAKDIERd88JGpURFaicy4XtOcIY28s7A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)
	
**"不积跬步，无以至千里；不积小流，无以成江海。"**
