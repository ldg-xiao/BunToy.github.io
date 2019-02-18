---
layout: post
title: "Markdown使用语法"
subtitle: "Dreamers among programmers"
author: "松下百合子"
header-img: "img/post-bg-dreamer.jpg"
header-mask: 0.4
tags:
  - Markdown
---

> 本文汇集Markdown使用方法 [Markdown使用](https://coding.net/help/doc/project/markdown.html#i-10) ;)

Markdown 语法介绍

Markdown 是一种轻量级标记语言，让写作者专注于写作而不用关注样式。Coding 的许多版块均采用了 Markdown 语法，比如冒泡、讨论、Pull Request 等。

## 标题

用 Markdown 书写时，只需要在文本前面加上『# 』即可创建一级标题。同理，创建二级标题、三级标题等只需要增加『# 』个数即可，Markdown 共支持六级标题。如下所示：
```ruby
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
点击预览可以看到效果：
![img](https://dn-coding-net-production-pp.codehub.cn/d46c3a8f-b74a-4008-ad1d-a56be443d5fa.png)

## 限制图片大小并居中

许多 MarkDown 编辑器中直接按原图大小显示图片，造成版面凌乱如何让图片像简书中那样大小一致居中显示呢？使用该命令`<img src="图片地址" width="图片显示宽度" height="显示高度" alt="图片名称"/>`设置图片大小，再用`<div align=center></div>`命令包裹达到居中效果。
```ruby
<img src="http://ww2.sinaimg.cn/bmiddle/88070423gw1ep30aw8an  
7g204d04gkgd.gif" width="400" height="400" alt="亦菲表演机器猫"/>

如果你使用的是md，那么还可以使用如下语法 ![](链接地址 =宽x高)

![亦菲表演机器猫](http://ww2.sinaimg.cn/bmiddle/88070423gw1ep  
30aw8an7g204d04gkgd.gif =400x400)
```

效果：
![img](https://upload-images.jianshu.io/upload_images/204349-cc4fa6630712a7e1.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/157/format/webp)



[^_^]: # <img src="https://upload-images.jianshu.io/upload_images/1494908-0c38bde3c5349293.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240"  alt="上海鲜花港 - 郁金香" /><br>

[github源码](https://github.com/xiabing0802/justdo8-appcan)  https://github.com/xiabing0802/justdo8-appcan

[web试玩](http://www.willspace.cn/container/app_design_3/index.html)  http://www.willspace.cn/container/app_design_3/index.html

[AppCan框架](http://newdocx.appcan.cn/)  http://newdocx.appcan.cn/


有一类程序员是 visionary 型的，为了实现一些超前的 idea，绕过某些技术的限制，他们写的 code 晦涩高深得只有他们自己能懂，做出来的 tool 看上去很美好结果处处是坑出了 bug 根本没法查，但正是这类人不断创造出新的东西，在洗礼之后成为一个个 big thing。

我每周都要被 infra 的坑 block 得无法工作几次搞得非常沮丧，后来我发现这个锅除了要扔给 FB 外，还有一大半要扔给我周围这群 visionary 的同事们，我工作直接需要接触到的区区五六个人，发起/创造了 Infer, React, Reason, ReasonReact, BuckleScript...

所以这大概就是见证/参与这些 idea 成长的代价吧，也意识到这些东西不是在刚开始就像后来大家接受流行时那么美好的。React 发布 5 周年生日时回放 Jordan/Tom 2013 年第一次对外发布 React/JSX 的视频。我问 Jordan 说你后来怎么没再去分享了。他说你不知道我那天讲完下来被所有听众指着批评。React 第一次在内部使用是 2011 年在 news feed，然后是 2012 年 instagram (pete hunt)，所以这个时间其实很长很长。

很多人（包括我）都会经常觉得 XYZ 新事物跟老东西比太新、太不成熟、体验太不好、想要解决的问题太多、解决方案太 overkill、然后就没有然后了，但其实说不定你在看的这个就是 next big thing 呢。这些梦想家们 vision 里的 big picture 太大了，有的人可能在半个 picture 出来的时候就可以看出来了，有的人则可能要等到整个 picture 都快填满了才看得出来。

如果不是因为 Ads/Messenger 的坑深 React/Reason/Flux 也就不会在这里诞生了，

如果不是因为 Facebook 的坑深 GraphQL/Infer/Hack/Flow/Buck 也就不会在这里诞生了。

正是有一群开垦者不怕坑深才使得各种 idea 成为了大家手上好用的 tool 啊。

梦想家程序员们的工作价值于实干主义的程序员，总是很容易在过程中被低估、忽视，或是得不到尊重。而又在流行之后被神化，仿佛是那个人早已洞察一切一样。其实梦想家的工作，也是一点点累加，一点点迭代起来的。他们也需要伯乐和追随者的支持和帮助。

Chenglou 这个人总是在巨兴奋与巨沮丧之间切换，这段时间下来，我开始能感受这种情绪的来源了。

他总是用一句话来总结他回答我的吐槽、抱怨、疑问、惊叹，我就用这句话来结尾好了：


https://www.jianshu.com/p/45faddb1526d?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation

https://coding.net/help/doc/project/markdown.html#i-5

https://www.imooc.com/article/23400

**"Welcome to the producer side!"**
