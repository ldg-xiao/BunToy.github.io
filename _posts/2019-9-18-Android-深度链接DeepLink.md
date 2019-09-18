---
layout:     post
title:    "Android-DeepLink深度链接"
subtitle:   "DeepLink使用"
author:     "松下百合子"
header-img: "img/huoying/92592.jpg"
header-mask: 0.3
catalog: true
tags:
- Android
---

> DeepLink当做笔记记之。

文章转载自[菜鸟教程](https://blog.csdn.net/u012426327/article/details/77966700) 

> 源码：https://github.com/xiabing0802/DeepLink-1


### DeepLink 
-  DeepLink 从字面意思可以理解为「深度链接」，那么 DeepLink 在 Android 开发中有什么作用呢？简单来说，可以用这种技术实现 web 页面点击一个链接跳转至 APP 指定的某一页面。这种技术的好处是可以为我们的 APP 导流。
 



### 使用
- 在AndroidManifest.xml中设置

```ruby
<uses-permission android:name="android.permission.INTERNET"/>
```

- 添加intent-filter

```ruby
<activity android:name=".DeepLinkActivity">
            <intent-filter>
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />

                <data
                    android:host="share"
                    android:scheme="go" />
            </intent-filter>
</activity>
```

- 在html文件中

```ruby
<div>
    <a id="J-call-app" href="javascript:;" class="label">立即打开&gt;&gt;</a>
    <input id="J-download-app" type="hidden" name="storeurl" value="http://m.chanyouji.cn/apk/chanyouji-2.2.0.apk">
</div>
```
- 用 go://share/main?name=tomcat&age=100 在手机浏览器中打开

- android activity中打开页面解析

```ruby
private void getDataFromBrowser() {
        Uri data = getIntent().getData();
        try {
            scheme = data.getScheme(); // "will"
            host = data.getHost(); // "share"
            params = data.getPathSegments();
            String testId = params.get(0); // "uuid"

            String path =data.getPath();
            String name =data.getQueryParameter("name");
            String age =data.getQueryParameter("age");

            tv_data.setText("Scheme: " + scheme + "\n" + "host: " + host + "\n" + "params: " + testId + "\n" + "path: " + path+
                    "\n" + "name: " + name +"\n" + "age: " + age );
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
```


