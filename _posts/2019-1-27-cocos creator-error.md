---
layout: post
title: "cocos creator 微信小游戏开发常见错误"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com/buntoy.html) ;)


## Script下同名文件js出现报错.
```ruby
Build Failed: Compile error: Filename conflict, the module "speed" both defined in "assets\Script\speed.js" and "assets\Script\speedCoini\speed.js"
at a (D:\Program Files (x86)\CocosCreator\resources\app.asar\editor\page\build\compile-worker.js:1:5962)
at D:\Program Files (x86)\CocosCreator\resources\app.asar\node_modules\globby\index.js:74:3
at D:\Program Files (x86)\CocosCreator\resources\app.asar\node_modules\async\lib\async.js:726:13
```
 
   原因：Script文件夹下出现了同名的 speed.js 文件，目前不支持同名文件，最好更改不同名字.
   
   参考：https://forum.cocos.com/t/topic/70001
   
![img](https://upload-images.jianshu.io/upload_images/2489070-95bd646b8ebb77a3.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/240/format/webp)

   
## 项目导出为微信小游戏JSON inpu出现报错.   
  ```ruby
VM447:1 gameThirdScriptError
Unexpected end of JSON input;at setTimeout callback function
SyntaxError: Unexpected end of JSON input
at JSON.parse ()
``` 
   原因：cocos creator中使用了存储数据带有JSON
```ruby
var userDetail = JSON.parse(cc.sys.localStorage.getItem("userDetail"));
if(userDetail ==null){}
```    
   JSON解析会出现错误，为空的话，
```ruby
// 在微信上
userDetail = ""
//  在调试网页上
userDetail = null;
```    
    
	结果需要更改为 
	if(userDetail ==""){}
   
   参考：https://forum.cocos.com/t/topic/65645/14
   
## 项目导出为微信小游戏图片路径出现报错.     
```ruby
ENOENT: no such file or directory, open 'G:\cocos\proj  7002   
```  
  cocos creator图片路径都正确，打包微信出现图片找不到，可以查看github路径查看7002错误，可以看到需要在 assets下面穿建一个resources 文件夹，所有图片路径放在这个下面，打包微信之后不会出现问题
   
## 布局创建节点时候调试出现6700.
```ruby
6700 Can't init canvas '%s' because it conflicts with the existing '%s', the scene should only have one active canvas at the same time
ENOENT: 6700 has same time canvas a time
```  
   原因在于同时使用了两个canvas, 应该布局问题，在你新的弹出框场景界面布局中删除多余的canvas这个，肯定多了个canvas

## 播放音乐提示警告信息
```ruby
Since 1.10, `cc.audioEngine` accept cc.AudioClip instance directly, not a URL string. Please directl  
```  
   
   原因在于cc新的版本中，使用了type 替换了原来的url，可以看一下代码使用
   
```ruby
 properties: {
       bgAudio:{
           default:null, 
           type:cc.AudioClip  //这里使用url 就会出现提示警告                                  
       },   
```    
 
**"Welcome to the producer side!"**
