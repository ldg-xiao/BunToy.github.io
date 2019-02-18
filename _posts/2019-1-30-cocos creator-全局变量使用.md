---
layout: post
title: "cocos creator 全局变量使用"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com) ;)


## 全局变量使用
   
```ruby
  window.DEFAULT_IP = "192.168.1.1";
```

这样你就可以随时访问DEFAULT_IP了（注意：全局变量一定不要和系统的全局变量重名，全局变量用之前一定要初始化）

全局变量一定在某个js中已经执行过，最好放在 onLoad() 中，已经加载过，否则访问不到。


![img](http://photocdn.sohu.com/20060929/Img245598050.jpg)


<div>  
<audio autoplay="autoplay" id="audio_play" loop="loop">
<source src="http://other.web.ra01.sycdn.kuwo.cn/resource/n1/128/39/43/732685092.mp3" type="audio/mpeg">
<source src= type="audio/mpeg">
</audio>

</div>
	
	 
**"不积跬步，无以至千里；不积小流，无以成江海。"**
