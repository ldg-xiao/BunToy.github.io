---
layout: post
title: "cocos creator 播放音乐"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com) ;)


## 播放音乐
  
   方式一：
   
```ruby
cc.loader.loadRes('bgAudio', cc.AudioClip, function (err, clip) {
     cc.audioEngine.play(clip);
});
```

这里bgAudio 必须放到resources下面作为音乐文件.就可以直接播放了.

   方式二：

```ruby
  properties: {
       bgAudio:{
           default:null, 
           type:cc.AudioClip                                       
       },
    },
```
 
 然后将此 bgAudio属性绑定到 资源中，Texture下文件拖到这个节点上绑定. js代码播放：
 
```ruby 
   cc.audioEngine.play(this.bgAudio, false, 0.5);
```   
   

<div>  
<iframe frameborder="0" id="video" src="https://vd.yinyuetai.com/hc.yinyuetai.com/uploads/videos/common/83460165C222BB7939AC879691683340.mp4" allowfullscreen></iframe>
</div>
	
	 
**"不积跬步，无以至千里；不积小流，无以成江海。"**
