---
layout: post
title: "cocos creator 微信小游戏分享"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy版本信息均来自 [BunToy官网](https://buntoy.com/buntoy.html) ;)


## 微信小游戏分享功能

添加微信分享功能代码出现分享代码总是没有执行.
 
   原因：必须使用可要申请上线使用的 appid，(不能为测试使用的appid),开发中随意选择一个cocos creator打包的appid，导致最后无法执行.
   
   同时需要使用转发的代码有两种,被动转发，和 程序内转发

   被动转发:
```ruby
   wx.showShareMenu({
            withShareTicket: true
   });
   wx.onShareAppMessage(function(res){
            return {
                title: "经典打飞机游戏始终好玩如初，来吧！一起回味经典的乐趣。",
                imageUrl: "https://www.zzxgame.com.cn/Share/share.png",
                success(res){
                    console.log(res)
                },
                fail(res){
                    console.log(res)
                } 
            }
    })
```

   游戏内主动转发：
   
   判断是否微信游戏： console.log("点cc.sys.platform === cc.sys.WECHAT_GAME:" + (cc.sys.platform === cc.sys.WECHAT_GAME))
 ```ruby
   //邀请好友进入房间 
var shareImgUrl = 'https://img.52mvp.com/shr_pool/wx_img/201805/share_friend.jpg'; 
if (typeof (wx) !== "undefined") {   //cc.sys.isMobile && 
    wx.shareAppMessage({ 
         title: '我发现了一个很好玩的小游戏，赶紧一起来台球帝国打台球吧~', 
         imageUrl: shareImgUrl, 
         success: function (res){
            console.log('分享成功', res) 
           //wx.showToast({ title: '分享成功', }) 
        }, fail: function (res) { 
            console.log('分享失败', res) 
    } }) 
} 
```  

**"Welcome to the producer side!"**
