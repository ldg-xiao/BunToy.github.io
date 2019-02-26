---
layout:     post
title:    "Android Mvp+Retrofit+Rxjava+RxLifecycle的封装和使用"
subtitle:   "框架学习"
author:     "松下百合子"
header-img: "img/huoying/92582.jpg"
header-mask: 0.3
catalog: true
tags:
- Android
---

文章转载自[BunToy](https://BunToy.github.io/);

> 在开发BunToy本体过程中发现以前使用的Rxjava使用引起的内存泄漏,回顾项目解决,就实践一下;

### 添加依赖

```ruby
compile 'com.squareup.retrofit2:retrofit:2.3.0'
compile 'com.squareup.retrofit2:converter-gson:2.3.0'
compile 'com.squareup.retrofit2:adapter-rxjava2:2.3.0'
compile 'com.squareup.okhttp3:logging-interceptor:3.8.0'
compile 'io.reactivex.rxjava2:rxandroid:2.0.1'
compile 'com.trello.rxlifecycle2:rxlifecycle-components:2.1.0'
```

- 使用RxLifeCycle是因为在使用Rxjava的过程中,当发布一个订阅后,页面被finsh,此时订阅的逻辑还没完成,容易引发内存泄漏的问题.

### 基础类

#### 在BaseActivity中继承RxAppCompatActivity

```ruby
public class BaseActivity extends RxAppCompatActivity {
}
```

#### 在BasePresenter中写拿到LifecycleProvider的方法,方便后边的RetrofitService设置手动关闭订阅.

```ruby
public class BasePresenter {

    private LifecycleProvider<ActivityEvent> provider;

    public BasePresenter(LifecycleProvider<ActivityEvent> provider) {
        this.provider = provider;
    }

    public LifecycleProvider<ActivityEvent> getProvider() {
        return provider;
    }
}
```

- 当我们在activity中初始化presenter的时候,由于activity继承的RxAppCompatActivity,只需要传this就可以把LifecycleProvider传过来了.

#### 使用mvp,需要新建抽象类BaseView

```ruby
public interface BaseView {

    /**
     * 显示Loading
     */
    void showProgressDialog();

    /**
     * 隐藏Loading
     */
    void hideProgressDialog();

    /**
     * 显示错误信息
     *
     * @param msg 错误信息
     */
    void showError(String msg);
}
```

### 接口地址类和请求参数接口类

#### 新建接口地址类Constant

```ruby
public class Constant {

    /**
     * 服务器地址(基类地址)
     */
    public static final String SERVER_URL = "http://www.kuaidi100.com/";

    /**
     * 接口请求地址
     */
    public static class UrlOrigin {

      //--------------------------------------------------
      //拼接的尾部地址都写下边
        /**
         * 获取快递信息
         */
        public static final String get_express_info = "query";
    }
}
```

#### 新建请求参数接口类RetrofitService

```ruby
public interface RetrofitService {

    /**
     * 获取快递信息
     * Rx方式
     * @return Observable<ExpressInfo>
     */
    @GET(Constant.UrlOrigin.get_express_info)
    Observable<ExpressInfo> getExpressInfoRx(@QueryMap Map<String,String> map);
}
```

注意: @GET(Constant.UrlOrigin.get_express_info)括号中的参数为Constant的尾部地址”query”.


### Retrofit工具类

#### 新建RetrofitHelper

```ruby
public class RetrofitHelper {

    private static RetrofitHelper retrofitHelper;
    private RetrofitService retrofitService;

    public static RetrofitHelper getInstance() {
        return retrofitHelper == null ? retrofitHelper = new RetrofitHelper() : retrofitHelper;
    }

    private RetrofitHelper() {
        // 初始化Retrofit
        Retrofit retrofit = new Retrofit.Builder()
                .baseUrl(Constant.SERVER_URL)
                .addConverterFactory(GsonConverterFactory.create()) // json解析
                .addCallAdapterFactory(RxJava2CallAdapterFactory.create()) // 支持RxJava
                .client(RetrofitUtils.getOkHttpClient()) //打印请求参数
                .build();
        retrofitService = retrofit.create(RetrofitService.class);
    }

    public RetrofitService getRetrofitService() {
        return retrofitService;
    }
}
```

#### 新建DataManager

```ruby
public class DataManager {

    private static DataManager dataManager;
    private RetrofitService retrofitService;

    public static DataManager getInstance() {
        return dataManager == null ? dataManager = new DataManager() : dataManager;
    }

    /**
     * 初始化Retrofit,拿到RetrofitService
     */
    private DataManager() {
        retrofitService = RetrofitHelper.getInstance().getRetrofitService();
    }

  //---------------------------------------------------------
  //从下边开始,就是各个接口的请求
    /**
     * 获取快递信息
     * @return Observable<ExpressInfo>
     */
    public Observable<ExpressInfo> getExpressInfo(Map<String,String> map) {
        return retrofitService.getExpressInfoRx(map);
    }
}
```

在DataManager中初始化RetrofitHelper,并通过RetrofitHelper重的getRetrofitService()方法拿到RetrofitService.

​然后在DataManager中做网络请求,返回拿到的javabean,如上面代码中的getExpressInfo()方法.

本文的demo地址:http://download.csdn.net/download/huchengzhiqiang/10032097

参考地址：https://blog.csdn.net/huchengzhiqiang/article/details/78296892