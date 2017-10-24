section: common
id: contrast
description: 检验项目对照接口
icon: icon-book
filter: contrast
---

# 检验项目对照

## 机构项目对照
- 请求地址：/v3/api/common/contrast/org
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 英文名称 | 类型与长度 | 是否必须 | 备注 |
|:----:|----------|----------|------------|:--------:|------|
| 1 | token | daan_api_token | | | head 参数 |
| 2 | 机构id | orgId | bigint(19) | 是 | 机构关键字对应orgs.id |
| 3 | 系统id | appId | bigint(19) | 是 | 功能点、菜单对应那个系统，对应applications.id |
| 4 | 提交数据 | data | string | | | |

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

| 编号 | 字段名称 | 英文名称 | 类型与长度 | 是否必须 | 备注 |
|:----:|----------|----------|------------|:--------:|------|
| 1 | 是否成功 | success | boolean | | |
| 2 | 错误编码 | errorCode | string | | |
| 3 | 错误信息 | errorMsg | string | | |
| 4 | 返回数据 | data | string | | | |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": {}
}
```

- 处理逻辑：


## 区域项目对照
- 请求地址：/v3/api/common/contrast/area
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 英文名称 | 类型与长度 | 是否必须 | 备注 |
|:----:|----------|----------|------------|:--------:|------|
| 1 | token | daan_api_token | | | head 参数 |
| 2 | 机构id | orgId | bigint(19) | 是 | 机构关键字对应orgs.id |
| 3 | 系统id | appId | bigint(19) | 是 | 功能点、菜单对应那个系统，对应applications.id |
| 4 | 提交数据 | data | string | | | |

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

| 编号 | 字段名称 | 英文名称 | 类型与长度 | 是否必须 | 备注 |
|:----:|----------|----------|------------|:--------:|------|
| 1 | 是否成功 | success | boolean | | |
| 2 | 错误编码 | errorCode | string | | |
| 3 | 错误信息 | errorMsg | string | | |
| 4 | 返回数据 | data | string | | | |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": {}
}
```

- 处理逻辑：

