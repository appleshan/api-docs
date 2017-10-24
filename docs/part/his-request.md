section: his
id: his-request
description: HIS 申请单接口说明
icon: icon-book
filter: his-request
---

# HIS 申请单

## 接收提交的申请单
- 请求地址：/v3/api/his/request/commit
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 4 | data | string | | 提交数据 |
| 5 | subjectNo | varchar(15)  | 是 | 病人ID号 |
| 6 | subjectNoType | varchar(12)  | 否 | 病人ID号类型，例如：门诊号、住院号、体检号等 |
| 7 | treatmentTypeName          | varchar(10)  | 是 | 就诊类型，值：1-住院,2-门诊,3-体检 |
| 8 | itemCount      | int(11)      | 否 | 就诊次数 |
| 9 | subjectFeeType      | varchar(10)  | 否 | 费别，例如：农合、医保、免费等 |
| 10 | subjectName          | varchar(30)  | 是 | 病人姓名 |
| 11 | sexName           | varchar(6)   | 是 | 性别，值：男、女、未知 |
| 12 | age           | int(11)      | 是 | 年龄 |
| 13 | ageUnit      | varchar(6)   | 是 | 年龄单位，值：岁、月、天、时 |
| 14 | birthday      | datetime     | 否 | 出生日期，格式：YYYY-MM-DD |
| 15 | identityCard | varchar(25)  | 否 | 身份证号码 |
| 16 | patientPhone         | varchar(24)  | 否 | 病人电话号码 |
| 17 | deptName     | varchar(15)  | 否 | 申请科室名称，例如：耳鼻喉科 |
| 18 | deptId     | varchar(10)  | 否 | 申请科室代码，例如：mz0001。注：单据类型值为0时，该字段必填 |
| 19 | inpatientAreaName     | varchar(15)  | 否 | 病区名称，例如：产科一区 |
| 20 | inpatientAreaId     | varchar(10)  | 否 | 病区编码，例如：ck001 |
| 21 | bedNum           | varchar(15)  | 否 | 床号，例如：1床、+8床 |
| 22 | clinicalRemark          | varchar(400) | 否 | 临床诊断，例如：高血压、糖尿病等 |
| 23 | doctorName     | varchar(10)  | 否 | 申请医生名称 |
| 24 | doctorId     | varchar(10)  | 否 | 申请医生工号 |
| 25 | doctorPhone    | varchar(24)  | 否 | 申请医生手机号码 |
| 26 | requestTime       | datetime     | 是 | 开单时间，格式：YYYY-MM-DD HH:MM:SS |
| 27 | performedName  | varchar(30)  | 否 | 检验申请执行科室名称 |
| 28 | performedCode  | varchar(10)  | 否 | 检验申请执行科室编码 |
| 29 | requestPriority        | char(1)      | 否 | 急查标志，值：N-普通；Y-急查 |
| 30 | testItemQuantity        | int(11)      | 否 | 检验项目数量 |
| 31 | requestNo      | varchar(15)  | 是 | 检验申请流水号，标志唯一记录 |
| 32 | requestNote            | varchar(400) | 否 | 开单备注，例如：饭前、饭后一小时等 |
| 33 | barcode               | varchar(15)  | 否 | 条码号 |
| 34 | orderId              | varchar(32)  | 否 | 申请单id |
| 35 | orderType            | int(11)      | 是 | 单据类型，值：0-康华生产条码号，6-第三方系统生成条码号 |
| 36 | isConvertCode       | int(11)      | 是 | 项目对照标志位，值：0-需要对照项目，1-不需要对照项目 |
| 37 | testingStatus       | int(11)      | 是 | HIS执行状态，值：0-增加，1-修改 |
| 38 | testItems       | []  | 是 | 申请项目列表 |
| 39 | testItemName       | varchar(30)  | 是 | 申请项目名称,例如：血常规五分类 |
| 40 | testItemCode       | varchar(15)  | 是 | 申请项目编码，例如：A001 |
| 41 | testItemType       | varchar(6)   | 否 | 检验项目类型，值：组合、单项 |
| 42 | testItemPrice      | float        | 否 | 检验项目单价 |
| 43 | sampleTypeName         | varchar(30)  | 否 | 标本类型，例如：血清、尿液、粪便等 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "subjectNo": "9030687",
        "subjectNoType": "门诊就诊号",
        "treatmentTypeName": "门诊",
        "itemCount": "3",
        "subjectFeeType": "免费",
        "subjectName": "圣皇",
        "sexName": "男",
        "age": "27",
        "ageUnit": "岁",
        "birthday": "1990-02-14 00:00:00",
        "identityCard": "430324199002140001",
        "patientPhone": "13838383838",
        "deptName": "骨科",
        "deptId": "903804",
        "inpatientAreaName": "jskkdjflgj",
        "inpatientAreaId": "2345234",
        "bedNum": "35",
        "clinicalRemark": "接口洛杉矶地方",
        "doctorName": "和医生",
        "doctorId": "5892038940",
        "doctorPhone": "23838383838",
        "requestTime": "2017-05-11 00:00:00",
        "performedName": "了世界的符号",
        "performedCode": "lksdj",
        "requestPriority": "N",
        "testItemQuantity": "1",
        "requestNo": "20170505095301",
        "requestNote": "接受对方",
        "barcode": "20170505095301",
        "orderId": "asdg12345",
        "orderType": "0",
        "isConvertCode": "0",
        "testingStatus": "0",
        "testItems": [{
            "testItemName": "血常规",
            "testItemCode": "9230816",
            "testItemType": "组合",
            "testItemPrice": "12",
            "sampleTypeName": "静脉血"
        },
        ...
        {
            "testItemName": "血型鉴定",
            "testItemCode": "123456789",
            "testItemType": "组合",
            "testItemPrice": "13",
            "sampleTypeName": "静脉血"
        }]
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
  "success":true,
  "errorCode":null,
  "errorMsg":null,
  "data":"提交成功"
}
```


## 提供检验签收列表(已签收)
- 请求地址：/v3/api/his/request/tolislist
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
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
|:---:|--------|--------|:------:|---------|
| 1 | success | boolean | | 是否成功 |
| 2 | errorCode | string | | 错误编码 |
| 3 | errorMsg | string | | 错误信息 |
| 4 | data | string | | 返回数据 |
| 5 | requestNo | varchar(15) | 是 | 检验申请流水号，标志唯一记录 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": [{
        "requestNo": ""
    }]
}
```

