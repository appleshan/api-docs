section: tolis
id: tolis-request
description: To LIS 申请单接口说明
icon: icon-book
filter: tolis-request
---

# To LIS 申请单

## 提供申请单列表(待签收)
- 请求地址：/v3/api/tolis/request/formlislist
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | orgId | bigint(19) | 是 | 检测机构ID |
| 3 | appId | bigint(19) | 是 | 系统ID |
| 4 | data | string | | | |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "29349238492834922323",
    "appId": "2",
    "data": null
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | success | boolean | | 是否成功 |
| 2 | errorCode | string | | 错误编码 |
| 3 | errorMsg | string | | 错误信息 |
| 4 | data | string | | 返回数据 |
| 5 | barcode | varchar(15)   | 是 | 返回数据 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": [{
        "barcode": "123"
    },
    {
        "barcode": "456"
    },
    {
        "barcode": "789"
    }]
}
```


## 提供单个申请单明细
- 请求地址：/v3/api/tolis/request/detail
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | orgId | bigint(19) | 是 | 检测机构ID |
| 3 | appId | bigint(19) | 是 | 系统ID |
| 4 | data | string | | |
| 5 | barcode       | varchar(15) | 是 | 条码号 |

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
| 1 | success | boolean | | 是否成功 |
| 2 | errorCode | string | | 错误编码 |
| 3 | errorMsg | string | | 错误信息 |
| 4 | data | string | | 返回数据 |
| 5 | barcode | varchar(15)   | 是 | 条码号 |
| 6 | subjectName | varchar(30)   | 是  | 姓名 |
| 7 | sexName | varchar(6)    | 是  | 性别，值：男、女、未知 |
| 8 | age | varchar(17)   | 是  | 年龄，例：1岁2月 |
| 9 | birthday | datetime      | 否 | 出生日期，格式：YYYY-MM-DD |
| 10 | fromOrgId          | bigint(19)    | 否 | 送检医院编码 |
| 11 | fromOrgName        | varchar(35)   | 否 | 送检医院名称 |
| 12 | treatmentTypeName  | varchar(30)   | 否 | 就诊类型，例如：门诊、住院、体检 |
| 13 | subjectNo           | varchar(30)   | 否 | 病人编号，唯一标识病人 |
| 14 | inpatientAreaName  | varchar(30)   | 否 | 病区名称 |
| 15 | doctorName          | varchar(10)   | 否 | 申请医生 |
| 16 | deptName            | varchar(30)   | 否 | 开单科室 |
| 17 | bedNum              | varchar(15)   | 否 | 床号 |
| 18 | remark               | varchar(250)  | 否 | 标本备注 |
| 19 | clinicalRemark      | varchar(400)  | 否 | 临床诊断 |
| 20 | requestRemark       | varchar(250)  | 否 | 医嘱备注 |
| 21 | requestTime         | datetime      | 是 | 申请时间，格式：YYYY-MM-DD HH:MM:SS |
| 22 | sampleTypeName     | varchar(150)  | 否 | 标本类型，例：血清、尿液、粪便等 |
| 23 | collectTime         | datetime      | 否 | 采集时间，格式：YYYY-MM-DD HH:MM:SS |
| 24 | requestAdditions     | {}  | 否 | 附加信息 |
| 25 | doctorPhone              | varchar(25) | 否 | 医生电话 |
| 26 | subjectPhone             | varchar(24) | 否 | 病人电话 |
| 27 | diabetes             | varchar(25) | 否 | 糖尿病史 |
| 28 | smokingHistory           | varchar(25) | 否 | 吸烟史 |
| 29 | idCard                   | varchar(32) | 否 | id卡号码 |
| 30 | weight                    | varchar(15) | 否 | 体重，例：70kg |
| 31 | height                    | varchar(15) | 否 | 身高，例：173cm |
| 32 | collectionSite           | varchar(45) | 否 | 采集部位，例：伤口切面等 |
| 33 | urineVolume24h          | varchar(15) | 否 | 24小时尿量，例：1200ml |
| 34 | pregnant                  | varchar(15) | 否 | B超孕日，例：5天 |
| 35 | bultrasonic               | varchar(15) | 否 | B超孕周，例：4周 |
| 36 | lmpPregnant              | varchar(15) | 否 | LMP孕日，例：5天 |
| 37 | lmpBultrasonic           | varchar(15) | 否 | LMP孕周，例：4周 |
| 38 | babyCount                | tinyint(4)  | 否 | 怀孕胎数，胎儿数量，一般 1，2 . |
| 39 | seminalVolume            | varchar(15) | 否 | 精浆量，例：23ml |
| 40 | lmpDate                  | varchar(25) | 否 | 末次月经，格式：YYYY-MM-DD |
| 41 | crl                       | varchar(12) | 否 | 头臀径，例：8.3mm |
| 42 | bpd                       | varchar(12) | 否 | 双顶径，例：8.3mm |
| 43 | nt                        | varchar(12) | 否 | 颈项透明层厚度，例：8.3mm |
| 44 | nasalBone                | varchar(12) | 否 | 鼻骨，例：8.3mm |
| 45 | nasalBoneState          | int(11)     | 否 | 鼻骨状态，值: 0-缺失，1-可见 |
| 46 | imbedDate                | datetime    | 否 | 植入日期，格式：YYYY-MM-DD |
| 47 | eggRetrievalDate        | datetime    | 否 | 取卵日期，格式：YYYY-MM-DD |
| 48 | isIddm                   | int(11)     | 否 | 胰岛素依赖性糖尿病，值: 0-缺失，1-可见 |
| 49 | isSmoke                  | int(11)     | 否 | 是否吸烟，值: 0-否，1-是，2-孕前戒，3-孕期戒 |
| 50 | race                      | int(11)     | 否 | 种族，值:0-黄种人，1-afro-caribbean，2-Asian，3-Caucasian，4-oriental，5-其他 |
| 51 | raceName                 | varchar(25) | 否 | 种族名字，种族为其他时的种族名称 |
| 52 | pregnantWay              | int(11)     | 否 | 受孕方式，值: 0-自然，1-克罗米芬，2-试验婴儿IVF，3-ICSI，4-增卵，5-供精，6-其他 |
| 53 | otherPregnantWay        | varchar(25) | 否 | 其他受孕方式，其他受孕方式名称 |
| 54 | exceptionPregnancy       | int(11)     | 否 | 异常妊娠史，值: 0-无，1-21三体，2-18三体，3-13三体，4-神经管畸形，5-其他 |
| 55 | otherExceptionPregnancy | varchar(25) | 否 | 其他异常妊娠史，其他异常妊娠史的内容 |
| 56 | isTransfusion            | int(11)     | 否 | 是否输血，值: 0-否，1-是 |
| 57 | isTransplantSurgery     | int(11)     | 否 | 移植手术，值: 0-否，1-是 |
| 58 | stemCellTherapy         | int(11)     | 否 | 干细胞治疗，值: 0-否，1-是 |
| 59 | immuneTherapy            | int(11)     | 否 | 免疫治疗，值: 0-否，1-是 |
| 60 | centralizedHosp          | varchar(35) | 否 | 集中送检医院，无创集中送检医院 |
| 61 | collectHosp              | varchar(35) | 否 | 采样医院，无创标本采样医院 |
| 62 | bodyStyle                | varchar(25) | 否 | 体位，例：立位、卧位等 |
| 63 | bultrasonicDate          | datetime    | 否 | B超检查日期，格式：YYYY-MM-DD |
| 64 | cureCancer1             | int(11)     | 否 | 恶性肿瘤未治愈或治愈未满一年，值: 0-否，1-是 |
| 65 | pregnancy                 | int(11)     | 否 | 本次妊娠，值：1-单胎、2-双胎 |
| 66 | examinationDay           | datetime    | 否 | 超声检查日期，格式：YYYY-MM-DD |
| 67 | examinationResultChild  | int(11)     | 否 | 超声检查，值：1-单胎、2-双胎 |
| 68 | examinationResultWeek   | int(11)     | 否 | 当日超声结果提示周，例如：4周 |
| 69 | examinationResultDay    | int(11)     | 否 | 当日超声结果提示天，例如：5天 |
| 70 | requestGroups     | []  | 否 | 申请项目信息 |
| 71 | testItemCode       | bigint(19)    | 是  | 申请项目编码，例如：A001 |
| 72 | testItemName     | varchar(55)   | 是  | 申请项目名称，例如：血型鉴定 |
| 73 | testEnShortName | varchar(30)   | 否 | 英文简称，例：ABO |
| 74 | displayOrder      | int(11)       | 否 | 顺序号 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": {
        "barcode": "",
        "subjectName": "",
        "sexName": "",
        "age": "",
        "birthday": "",
        "fromOrgId": "",
        "fromOrgName": "",
        "treatmentTypeName": "",
        "subjectNo": "",
        "inpatientAreaName": "",
        "doctorName": "",
        "deptName": "",
        "bedNum": "",
        "remark": "",
        "clinicalRemark": "",
        "requestRemark": "",
        "requestTime": "",
        "sampleTypeName": "",
        "collectTime": "",
        "requestAdditions": {
            "doctorPhone": "",
            "subjectPhone": "",
            "diabetes": "",
            "smokingHistory": "",
            "idCard": "",
            "weight": "",
            "height": "",
            "collectionSite": "",
            "urineVolume24h": "",
            "pregnant": "",
            "bultrasonic": "",
            "lmpPregnant": "",
            "lmpBultrasonic": "",
            "babyCount": "",
            "seminalVolume": "",
            "lmpDate": "",
            "crl": "",
            "bpd": "",
            "nt": "",
            "nasalBone": "",
            "nasalBoneState": "",
            "imbedDate": "",
            "eggRetrievalDate": "",
            "isIddm": "",
            "isSmoke": "",
            "race": "",
            "raceName": "",
            "pregnantWay": "",
            "otherPregnantWay": "",
            "exceptionPregnancy": "",
            "otherExceptionPregnancy": "",
            "isTransfusion": "",
            "isTransplantSurgery": "",
            "stemCellTherapy": "",
            "immuneTherapy": "",
            "centralizedHosp": "",
            "collectHosp": "",
            "bodyStyle": "",
            "bultrasonicDate": "",
            "cureCancer1": "",
            "pregnancy": "",
            "examinationDay": "",
            "examinationResultChild": "",
            "examinationResultWeek": "",
            "examinationResultDay": ""
        },
        "requestGroups": [{
            "testItemCode": "",
            "testItemName": "",
            "testEnShortName": "",
            "displayOrder": ""
        }]
    }
}
```


## 接收申请单检验签收的通知
- 请求地址：/v3/api/tolis/request/success
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | orgId | bigint(19) | 是 | 检测机构ID |
| 3 | appId | bigint(19) | 是 | 系统ID |
| 4 | data | string | | |
| 5 | barcode | varchar(15) | 是 | 条码号 |

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
    "data": "修改成功"
}
```

