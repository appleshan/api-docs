section: common
id: auth
description: 接口授权
icon: icon-book
filter: auth
---

# 接口授权

## 授权
- 请求地址：/v3/api/common/auth
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须  | 字段说明 |
|:---:|----------|---------|:--------:|---------|
| 1   | username | string | 是 | 账号请找相关人员获取 |
| 2   | password | string | 是 | 密码请找相关人员获取,需要使用MD5对密码进行编码 |

样例：
```json
{
    "username": "",
    "password": ""
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|---------|----------|:-------:|---------|
| 1   | success   | boolean | | 是否成功 |
| 2   | errorCode | string | | 错误编码 |
| 3   | errorMsg  | string | | 错误信息 |
| 4   | data      | string | | 返回数据 |

样例：
```json
{
    "success":true,
    "errorCode":null,
    "errorMsg":null,
    "data":"eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOjMsImNyZWF0ZWQiOjE0OTgwMTQ4NTY5NTEsImV4cCI6MTUwNTIxNDg1Nn0.cLT7iRzBf5oM8rF_U6AAddlQQmPBCbSkGw8n1nvDxA_gmZB0aWO-zJbRzNKaRgmnObtI15pt0psp7bDnjviIxQ"
}
```

- 功能说明：

通过账号密码（username,password），获取 token。
