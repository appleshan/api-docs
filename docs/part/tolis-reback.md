section: tolis
id: tolis-reback
description: To LIS 退单报告单接口说明
icon: icon-book
filter: tolis-reback
---

# To LIS 退单报告单

## 接收退单报告
- 请求地址：/v3/api/tolis/report/reback/commit
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | token | daan_api_token | | | head 参数 |
| 2 | 机构id | orgId | bigint(19) | 是 | 机构关键字对应orgs.id |
| 3 | 系统id | appId | bigint(19) | 是 | 功能点、菜单对应那个系统，对应applications.id |
| 4 | 提交数据 | data | string | | |
| 5 | 提交数据 | barcode | varchar(15) | YES | [条码号] — 标本对应的条码号 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "barcode": ""
    }
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | 是否成功 | success | boolean | | |
| 2 | 错误编码 | errorCode | string | | |
| 3 | 错误信息 | errorMsg | string | | |
| 4 | 返回数据 | data | string | | |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": "退单成功。"
}
```

- 处理逻辑：


## 接收被撤销的退单报告
- 请求地址：/v3/api/tolis/report/reback/delete
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | token | daan_api_token | | | head 参数 |
| 2 | 机构id | orgId | bigint(19) | 是 | 机构关键字对应orgs.id |
| 3 | 系统id | appId | bigint(19) | 是 | 功能点、菜单对应那个系统，对应applications.id |
| 4 | 提交数据 | data | string | | |
| 5 | 提交数据 | barcode | varchar(15)   | YES | [条码号] — 标本对应的条码号 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "barcode": ""
    }
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | 是否成功 | success | boolean | | |
| 2 | 错误编码 | errorCode | string | | |
| 3 | 错误信息 | errorMsg | string | | |
| 4 | 返回数据 | data | string | | |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": "撤消成功。"
}
```

- 处理逻辑：

