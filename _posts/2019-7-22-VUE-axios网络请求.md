---
layout:     post
title:    "VUE-axios网络请求"
subtitle:   "Vue开发"
author:     "松下百合子"
header-img: "img/huoying/92585.jpg"
header-mask: 0.3
catalog: true
tags:
- VUE
---

> 在项目中

文章转载自[博客园](https://www.cnblogs.com/liuyishi/p/9459289.html) 


### axios 模拟本地请求

[参考](https://www.jianshu.com/p/39553cc705ea) 

>  这里wallet.json 文件放到static 目录下面

```javascript
this.axios.get('../../static/wallet.json')
          .then(data => {
            console.log(data)
            this.list=data.data
          })
          .catch(error => {
            console.log(error);
});
```















