---
layout: post
title: "BunToy android问题"
subtitle: 'Android'
author: "Daniel"
header-style: text
tags:
  - Android
---


## 1. Buntoy开发中出现问题

  1). Android Studio中app出现红叉无法编译
  
     因为集成了kotlin环境而导致app下的iml文件中jdkName和jdkType发生了改变找不到Android SDK引起的。
	 在app代码目录下找到这个 app.iml这个文件
	 
	 <orderEntry type="jdk" jdkName="Kotlin SDK" jdkType="KotlinSDK" />
	 
    改成
	 
	<orderEntry type="jdk" jdkName="Android API 27 Platform" jdkType="Android SDK" />

  2). apk打包后混淆代码问题
  
    在debug环境下安装apk都是正常运行，但是打包签名后出现问题，一般跟混淆代码有关。
	
	*首先考虑代码下的是否有异常问题，提示报错，查看bug log 
	
	*如果出现的问题没有报错log,可以继续查看当前页面是否有提示toast，对应try catch代码包裹，先注释重新编译，查看异常。
	
	*没有任何提示情况下，在当前页面看是否有对应java bean对象类，保持当前java类不被混淆
	
	*还有一种情况，就是查询当前操作相关的逻辑代码，涉及到相关类，把此相关类混淆再编译试试。
   
   