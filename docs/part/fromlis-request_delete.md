section: fromlis
id: fromlis-request
description: From LIS 申请单接口说明
icon: icon-book
filter: fromlis-request
---

# From LIS 申请单

## 接收被撤销的申请单
- 请求地址：/v3/api/fromlis/request/delete
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 英文名称 | 类型与长度 | 是否必须 | 备注 |
|:----:|----------|----------|------------|:--------:|------|
| 1 | token | daan_api_token |  |  | head参数 |
| 2 | 机构id | orgId | bigint(19) | 是 | 送检机构id |
| 3 | 系统id | appId | bigint(19) | 是 | 系统id |
| 4 | 提交数据 | data | string |  |  |
| 5 | 条形码 | barcode | string | 是 | 条形码 |

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

| 编号 | 字段名称 | 英文名称 | 类型与长度 | 是否必须 | 备注 |
|:----:|----------|----------|------------|:--------:|------|
| 1 | 是否成功 | success | boolean |  |  |
| 2 | 错误编码 | errorCode | string |  |  |
| 3 | 错误信息 | errorMsg | string |  |  |
| 4 | 返回数据 | data | string |  |  |  |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": "修改成功"
}
```

