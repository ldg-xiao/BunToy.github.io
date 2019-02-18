---
layout: post
title: "cocos creator 存储与读取数据"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/home.jpg"
header-mask: 0.4
tags:
  - cocos creator
---

> 本文BunToy版本信息均来自 [BunToy官网](https://buntoy.com/buntoy.html) ;)


## 存储与读取数据

我们在游戏中通常需要存储用户数据，如音乐开关、显示语言等，如果是单机游戏还需要存储玩家存档。 Cocos Creator 中我们使用 cc.sys.localStorage 接口来进行用户数据存储和读取的操作。

存储简单数据

```ruby
cc.sys.localStorage.setItem(key, value)
```

上面的方法需要两个参数，用来索引的字符串键值 key，和要保存的字符串数据 value。

例如假设键值为 gold:

```ruby
cc.sys.localStorage.setItem('gold', 100);
```

存储复杂数据，通过将对象序列化为 JSON 后保存：

```ruby
var userdate = {
    goldCoin: userDetail.goldCoin,
    Diamonds: diamonds,
    goldCoinSpeed: userDetail.goldCoinSpeed,
}
cc.sys.localStorage.setItem("userDiamonds", JSON.stringify(userdate));
```
 
读取简单数据

```ruby
cc.sys.localStorage.getItem(key)
```
和 setItem 相对应，getItem 方法只要一个键值参数就可以取出我们之前保存的值了。对于上文中储存的用户数据：

读取复杂数据

```ruby
var userDetail = JSON.parse(cc.sys.localStorage.getItem("userDetail"));
console.log(userDetail.goldCoin);
console.log(userDetail.Diamonds);
```

参考：https://blog.csdn.net/qq_38504811/article/details/86153458 

   

**"Welcome to the producer side!"**
