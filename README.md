# miniprogram-wxPay
小程序web-view组件调起

###1、在index.js里边的Page-->data里定义一个newsurl变量
```
Page({
  data: {
    newsurl: "http://app.artron.net/tulu-test/wx.html",
  },
  onLoad: function(){...}
  })
```
###2、在index.wxml里添加一个we-view组件
```
<view class='container'>
  <web-view src='{{newsurl}}'></web-view>
</view>
```

###3、wx.html里的代码为：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
    <meta name="description" content=""/>
    <meta name="keywords" content=""/>
    <meta name="viewport"
          content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no,target-densitydpi=high-dpi,minimal-ui "/>
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <meta name="format-detection" content="telephone=no"/>
    <meta name="msapplication-tap-highlight" content="no"/>
    <meta name="apple-mobile-web-app-capable" content="yes"/>
    <meta name="apple-mobile-web-app-status-bar-style" content="blank"/>
    <link rel="apple-touch-icon-precomposed" href="http://pubunder.artron.net/pubimgs/m/icon.png">

</head>
<body>
<button class="btn" style="border: 1px solid #000;">点击</button>
<!--- 重要！！！！！！---!>
<script src="http://res.wx.qq.com/open/js/jweixin-1.3.2.js"></script>
<script src="http://qrcode.artron.net/weixin/check.php"></script>
<!--- 重要！！！！！！---!>

<script>
document.querySelector('.btn').addEventListener('click',function(){
<!--- 重要！！！！！！---!>
    console.log(wx)
    //是否在小程序环境中
    console.log(window.__wxjs_environment === 'miniprogram') // true
    var params = "1234";
    var path = '/pages/wxpay/wxpay?params='+params;

    //通过JSSDK的api使小程序跳转到指定的小程序页面
    wx.miniProgram.navigateTo({ url: path });
},false)
<!--- 重要！！！！！！---!>
</script>
</body>
</html>
```

###4、var path = '/pages/wxpay/wxpay?params='+params;可通过params字段传输字段，多个参数用&符号，和小程序push新页面传参方式相同。

参考链接1：详细介绍微信小程序使用WEB-VIEW控件进行微信支付 ： https://blog.csdn.net/wocoa/article/details/79247989
参考链接2：微信小程序开发之webview组件内网页实现微信原生支付：https://www.jianshu.com/p/aa29852ab695
