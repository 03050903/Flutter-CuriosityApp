> 基于Flutter开发，适配Android与iOS。
项目同时适合Flutter的练手学习，覆盖了基本框架的使用，与原生的交互等。
# 相关文章
# [Flutter实战详解--高仿好奇心日报](https://juejin.im/post/5c31f7236fb9a04a04412d0b)
#### 示例图片

![iOS](https://upload-images.jianshu.io/upload_images/1220329-62d314b156276dc8.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/368/format/webp)
![Android](https://upload-images.jianshu.io/upload_images/1220329-c7029e812f786c27.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/391/format/webp)
![](https://upload-images.jianshu.io/upload_images/1220329-2aeb5f302e90080d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/1220329-15c08710c6749458.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/1220329-374dcb2ce43faabf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/1220329-7f1f971a9f589476.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/1220329-f204a0988ff15398.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/1220329-675c1fe530e3770a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

由于[flutter_webview_plugin](https://pub.dartlang.org/packages/flutter_webview_plugin)这个插件只支持加载url,于是就需要做一些修改.

*   iOS
    在`FlutterWebviewPlugin.m`文件中的`- (void)navigate:(FlutterMethodCall*)call`方法中的最后一排,将`[self.webview loadRequest:request]`方法改为`[self.webview loadHTMLString:url baseURL:nil]`
*   Android
    在`WebViewManager.java`文件中`webView.loadUrl(url)`方法改为`webView.loadData(url, "text/html", "UTF-8")`,以及下面那排的`void reloadUrl(String url) { webView.loadUrl(url); }`改为`void reloadUrl(String url) { webView.loadData(url, "text/html", "UTF-8"); }`

