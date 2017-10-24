section: his
id: his-request
description: HIS 申请单接口说明
icon: icon-book
filter: his-request
---

# HIS 申请单

## 接收被撤销的申请单
- 请求地址：/v3/api/his/request/delete
- 请求方法：post
- 请求参数：

| 编号 | 英文名称 | 类型与长度 | 是否必须 | 备注 |
|:---:|---------|----------|:------:|------|
| 1 | daan_api_token | | | head 参数 |
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 4 | data | {} | | |
| 5 | requestNo | varchar(15) | 是 | 检验申请流水号，标志唯一记录 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "requestNo": ""
    }
}
```

- 返回结果：

| 编号 | 英文名称 | 类型与长度 | 是否必须 | 备注 |
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
    "data": "该医嘱撤销成功"
}
```

