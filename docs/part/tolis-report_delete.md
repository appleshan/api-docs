section: tolis
id: tolis-report
description: To LIS 检验报告单接口说明
icon: icon-book
filter: tolis-report
---

# To LIS 检验报告单

## 接收被撤销的检验报告
- 请求地址：/v3/api/tolis/report/success/delete
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | orgId | bigint(19) | 是 | 检测机构ID |
| 3 | appId | bigint(19) | 是 | 系统ID |
| 4 | data | string | | |
| 5 | barcode | varchar(15)   | YES | 条码号 |
| 6 | reportKey | varchar(45)   | YES | 外送报告key |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "barcode": "",
        "reportKey": ""
    }
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
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
    "data": "撤销报告成功"
}
```

- 处理逻辑：

