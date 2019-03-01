---
layout:     post
title:    "Android错误：Connect to 127.0.0.1.1080 [/127.0.0.1] failed: Connection refused: connect"
subtitle:   "异常错误"
author:     "松下百合子"
header-img: "img/huoying/92583.jpg"
header-mask: 0.3
catalog: true
tags:
- Android
---

文章转载自[BunToy](https://BunToy.github.io/)

> 参考链接：[Android](http://www.cnblogs.com/jason-zhang-cn/p/9914572.html)

### Android studio编译错误

同步gradle时发生如下错误：

```ruby
> Could not resolve all dependencies for configuration ':classpath'.
> Could not resolve com.github.dcendents:android-maven-gradle-plugin:1.3.
Required by:
project :
> Could not resolve com.github.dcendents:android-maven-gradle-plugin:1.3.
> Could not get resource 'https://jcenter.bintray.com/com/github/dcendents/android-maven-gradle-plugin/1.3/android-maven-gradle-plugin-1.3.pom'.
> Could not GET 'https://jcenter.bintray.com/com/github/dcendents/android-maven-gradle-plugin/1.3/android-maven-gradle-plugin-1.3.pom'.
> Connect to 127.0.0.1:1080 [/127.0.0.1] failed: Connection refused: connect
```

原因：gradle.properties 文件中使用了代理　　

- 有2个地方需要修改（如果2个地方都存在以下内容，视自己情况而定）

#### 删除掉项目中 gradle.properties中的代理；

```ruby
systemProp.https.proxyPort=1080
systemProp.http.proxyHost=127.0.0.1
systemProp.https.proxyHost=127.0.0.1
systemProp.http.proxyPort=1080
```

> 但是项目下的gradle.properties中 并没有添加

#### 删除c盘下默认.gradle 文件下 gradle.properties中的代理；

> 我就是这里删除了解决了。



