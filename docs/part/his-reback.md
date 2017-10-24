section: his
id: his-reback
description: HIS 退单报告接口说明
icon: icon-book
filter: his-reback
---

# HIS 退单报告

## 提供退单报告列表(已退单)
- 请求地址：/v3/api/his/report/reback/list
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|---------|----------|:-------:|-----|
| 1 | daan_api_token | | | head 参数 |
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 4 | data | string | | 提交数据 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {}
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:----:|--------|----------|:-------:|-----|
| 1 | success | boolean | | 是否成功 |
| 2 | errorCode | string | | 错误编码 |
| 3 | errorMsg | string | | 错误信息 |
| 4 | data | string | | 返回数据 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": {}
}
```


## 提供单个退单报告明细
- 请求地址：/v3/api/his/report/reback/detail
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|---------|----------|:-------:|-----|
| 1 | daan_api_token | | | head 参数 |
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 4 | data | string | | 提交数据 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {}
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:----:|--------|----------|:-------:|-----|
| 1 | success | boolean | | 是否成功 |
| 2 | errorCode | string | | 错误编码 |
| 3 | errorMsg | string | | 错误信息 |
| 4 | data | string | | 返回数据 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": {}
}
```


## 接收退单报告获取成功的通知
- 请求地址：/v3/api/his/report/reback/success
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|---------|----------|:-------:|-----|
| 1 | daan_api_token | | | head 参数 |
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 4 | data | string | | 提交数据 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {}
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:----:|--------|----------|:-------:|-----|
| 1 | success | boolean | | 是否成功 |
| 2 | errorCode | string | | 错误编码 |
| 3 | errorMsg | string | | 错误信息 |
| 4 | data | string | | 返回数据 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": {}
}
```

