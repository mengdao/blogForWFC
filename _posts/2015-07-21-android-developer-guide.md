---
layout: page
title: "Android代码规范"
category: android
date: 2015-07-21 16:50:50
---
+ 关于文件命名(xml，类..)，要求名字具有可读性。
 1. xml文件名需最少包含两个要素：所属业务信息，例如poi,mdd...;功能描述，例如add,more,modify...
 2. 类名最少要包含所属业务信息。
+  xml中的控件命名。强烈建议使用小驼峰法，以便类中的变量名称和xml中保持一致，更容易理解和检索，同时减轻命名癌患者的压力，达到一次命名，终身受用的疗效。例如：
```
TextView randomMddName = (TextView)mddContentView.findViewById(R.id.randomMddName);
```
+ 如非特殊情况try catch的影响范围要缩到最小。
+ 如果是修改某个文件中的某些代码，尽量避免使用全局的格式化，以免增加代码review的工作量。
+ 发布到git上的代码中，禁止出现以下日志代码
```
 Log.d/e...
 System.print...
 MfwLog.d("$CLASS_NAME$", "$METHOD_NAME$ $var$ = " + )...
```

```
所有日志都要用以下形式
		if(MfwCommon.DEBUG){
    		MfwLog.d("$CLASS_NAME$", "$METHOD_NAME$ $var$ = " + );
		}
```
为了提高编码效率，通常我们可以通过配置Live Templates来实现日志代码的快速输入。配置方式如下图，
![7D2A5104-7E23-4CDF-A55C-00A68A13A0B4](http://gitlab.mafengwo.com/uploads/mobiledev/travelguidewiki-android/f4e539c423/7D2A5104-7E23-4CDF-A55C-00A68A13A0B4.png)

+ 开发环境用的参数尽量避免硬编码，例如MfwCommon.DEBUG/MfwCommon.DEBUG_EVENT，通过config.properties文件进行配置，以免无意中发布到线上。配置方式如下：
    在主工程的src根目录下，新建文件名为config.properties的文件，文件内容是键值对的形式，一行是一对，例如debug=true，目前只支持DEBUG、DEBUG_EVENT和DEBUG_DATA，可根据需要新增。

+ 设计资源有统一的定义，包括字体颜色、大小、背景色、分割线，相关文档请点击[这里](http://mdocs.codingview.com/android/android-ui-guide.html)查看

+ git的分支名最好用自己的代号或者名字开头，不要使用公共的名称开头，因为这会导致切换分支太费劲，例如：
~~gradle-developer-xsgg~~是不建议的, xsgg-gradle-developer是值得称赞的。顺便解释一下，xsgg是许声哥哥的缩写。

+ 不要在Activity或者fragment生命周期的几个方法中执行耗时过长的代码，总耗时超过50ms就会引起切换不流畅，如果一定要有耗时的代码，建议放到子线程中执行。

+ 为了方便开发和测试，应尽量统一debug.keystore，尤其是在涉及到地图开发和多人共用一台测试机的时候。统一的debug.keystore放在主工程的根目录下。



欢迎大家一起补充和修改，让我们一起营造一个舒适的、靠谱的、友爱与ji情的环境...