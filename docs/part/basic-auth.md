section: basic
id: auth
description: 接口授权说明
icon: icon-heart
filter: shuoquan sq
---

# 接口授权

## 接口授权及认证步骤

获取接口授权,开发者需要按照如下步骤完成:
1. 通过接口平台相关人员获取账号密码`username`,`password`
2. 通过请求获取 token
3. 生成 signature, 

## 获取 token

`token`是接口平台的全局唯一接口调用凭据，调用各接口时都需使用`token`。开发者需要进行妥善保存。`token`的有效期目前为30分钟，需定时刷新，重复获取将导致上次获取的`token`失效。

### 获取测试连接

请联系接口平台相关人员获取测试地址URL,文档后面将使用`{url}`代替连接
> 例:`http://www.baidu.com/auth` = `{url}/auth`

<p class="warning no-bg">
  注意:开发期间请勿直接使用 http://api.ykhealth.cn 连接调试
</p>

### 授权接口 - 获取 token

名称       | 内容 
----------|------------
请求地址   | {url}/auth
请求类型   | POST

参数

```json
{
  "username": "",  //账号请找相关人员获取
  "password": "" //密码请找相关人员获取,需要使用MD5对密码进行编码
}
```

<p class="warning">
  注意密码需要进行MD5编码
</p>

测试用例
```javascript
// jQuery测试用例
var user = {"username":"xxxx","password":"xxxx"};
$.ajax({
    url:'{url}/auth',
    contentType: 'application/json',
    type:'POST',
    dataType:'JSON',
    data:JSON.stringify(user),
    success: function(res){
       console.log(res); //  接口返回
    }
});
```

接口返回

```json
{
  "success": true,
  "errorCode": null,
  "errorMsg": null,
  "data": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOjMsImNyZWF0ZWQiOjE0OTA2NzkzMDkwOTIsImV4cCI6MTQ5MDY4MTEwOX0.bKbKgthKFuDq3h_dlB3aysydZfD7Y_Wu_xdKFWljn-GODTf_k3SEaeMvSds_j-regTj8wRGEz3STZFLmURWXZg" 
}
```

<p class="warning">
  上面`JSON`返回的`data` = `token`
</p>

## 生成 signature

数字签名是`POST`请求所需要的,如果使用`POST`请求的接口,必须生成数字签名

请按以下步骤执行(`JavaScript代码为例`)
#### 获取token 

获取`token`步骤 [GO](#获取接口授权)

```javascript
var token = 'eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOjMsImNyZWF0ZWQiOjE0OTA2NzkzMDkwOTIsImV4cCI6MTQ5MDY4MTEwOX0.bKbKgthKFuDq3h_dlB3aysydZfD7Y_Wu_xdKFWljn-GODTf_k3SEaeMvSds_j-regTj8wRGEz3STZFLmURWXZg'
```

### 生成随机字符串

```javascript
var echostr = Math.random().toString(36).substring(2, 10)

```

### 对称加密秘钥

需要联系接口平台相关人员获取

```javascript
var secretKey = '联系相关人员获取secretKey'
```

### 生成签名

以`JavaScript`为例

<p class="warning">
   参考: [各种语言版本的基于HMAC-SHA256编码](http://blog.csdn.net/js_sky/article/details/49024959)
  (参考链接中,会进行base64编码,请勿进行base64编码)
</p>

> 签名公式: `signature = HMACSHA256([key]token,[context](secretKey + echostr))`


```javascript
// 借助第三方编码Hmac-SHA256
<script src="http://cdn.bootcss.com/crypto-js/3.1.9/crypto-js.min.js"></script>
<script type="text/javascript">
var token = 'eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOjMsImNyZWF0ZWQiOjE0OTA2NzkzMDkwOTIsImV4cCI6MTQ5MDY4MTEwOX0.bKbKgthKFuDq3h_dlB3aysydZfD7Y_Wu_xdKFWljn-GODTf_k3SEaeMvSds_j-regTj8wRGEz3STZFLmURWXZg';
var echostr = Math.random().toString(36).substring(2, 10);//随机字符串 期望值:xdb93f5p
var secretKey = '联系相关人员获取secretKey'; // 对称加密秘钥
var encodeMessage = secretKey + echostr;//(对称加密秘钥 + 随机字符串) 期望值:联系相关人员获取secretKeyxdb93f5p
var signature = CryptoJS.HmacSHA256(encodeMessage, token);
document.write(signature);//期望值如:c9afcf9d73d86cf53f63df6159fdeb0c233e5091e99bc2078cf54a9347157c4a
</script>
```
<p class="tip">
  `signature` 生成成功
</p>

### 测试签名

名称       | 内容 
----------|------------
请求地址   | {url}/api/test-signature
请求类型   | POST

请求头参数

```json
{
  "DAAN-API-TOKEN": "eyJhbGciOiJIUzUxMiJ9.eyJ...", // token
  "echostr": "xdb93f5p", // 随机字符串
  "signature" : "c9afcf9d73d86cf53f63d..." //签名
}

```

测试用例

```javascript
// jQuery测试用例
<script src="http://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
<script src="http://cdn.bootcss.com/crypto-js/3.1.9/crypto-js.min.js"></script>
<script type="text/javascript">
$(function(){
    var token = 'eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOjMsImNyZWF0ZWQiOjE0OTA3MTUzODk5ODEsImV4cCI6MTQ5MDcxNzE4OX0.L8BuXUPRn8-TSq0Pmsm7oJ_cz9rGX6A6ui3U2c22UNG1DBlSvrmH5O0qHIIT3sWySZD_Xdwzu_nqWJkBp38A8w';
    var echostr = Math.random().toString(36).substring(2, 10);//随机字符串 期望值:xdb93f5p
    var secretKey = '联系相关人员获取secretKey'; // 对称加密秘钥
    var encodeMessage = secretKey + echostr;//(对称加密秘钥 + 随机字符串) 期望值:联系相关人员获取secretKeyxdb93f5p
    var signature = CryptoJS.HmacSHA256(encodeMessage, token);
    $.ajax({
        url:'{url}/api/test-signature',
        headers: { 'DAAN-API-TOKEN': token,'echostr':echostr,'signature':signature},
        contentType: 'application/json',
        type:'POST',
        dataType:'JSON',
        success: function(res){
            console.log(res); // 接口返回
        }
    })

});
</script>
```

返回结果
```json
{
  "success": true,
  "errorCode": null,
  "errorMsg": null,
  "data": "[c9afcf9d73d86cf53f63df6159fdeb0c233e5091e99bc2078cf54a9347157c4a]签名通过校验"
}
```
