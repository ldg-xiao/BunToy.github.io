---
layout: post
title: "Android Activity刷新关联的Fragment界面"
subtitle: "https://buntoy.com"
author: "松下百合子"
header-img: "img/contact-bg.jpg"
header-mask: 0.4
tags:
  - Android
keywords: Activity刷新关联的Fragment
---

> 本文BunToy信息均来自 [BunToy官网](https://buntoy.com))


## Activity中创建一个接口

```bash
public interface Listener {
    void listener(int position);
}
```

## 在activity中实现接口

```ruby
Listener linstenr;

public void setLinstenr(Listener linstenr) {
    this.linstenr = linstenr;
}
```

## 在fragment的onAtth()中给activity设置监听

```ruby
@Override
public void onAttach(Activity activity) {
    super.onAttach(activity);
    MainActivity mainActivity = (MainActivity) activity;
    mainActivity.setLinstenr(this);
}

@Override
public void listener(int position) {
    //
}
```

## 在activity中调用

```ruby
if (linstenr!=null){
    linstenr.listener(position);
}
```

  
**"不积跬步，无以至千里；不积小流，无以成江海。"**
