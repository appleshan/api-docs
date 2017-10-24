section: fromlis
id: fromlis-request
description: From LIS 申请单接口说明
icon: icon-book
filter: fromlis-request
---

# From LIS 申请单

## 接收提交的申请单
- 请求地址：/v3/api/fromlis/request/commit
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token |  |  | head参数 |
| 2 | orgId | bigint(19) | 是 | 机构ID |
| 3 | appId | bigint(19) | 是 | 系统ID |
| 4 | data | [] |  | 提交数据: 检验申请单列表大小不能超出 50 个条码的申请单信息. |
| 5 | barcode | varchar(15) | 是 | 条码号 |
| 6 | treatmentTypeName | varchar(30) | 否 | 就诊类型 |
| 7 | subjectNo | varchar(30) | 否 | 病人ID号 |
| 8 | subjectNoType | varchar(12) | 否 | 病人ID类型 |
| 9 | subjectName | varchar(30) | 是 | 姓名 |
| 10 | sexName | varchar(6) | 是 | 性别，值：男、女、未知 |
| 11 | age | varchar(17) | 是 | 年龄 |
| 12 | ageUnit | varchar(6) | 是 | 年龄单位，值：岁；月；天；小时。 |
| 13 | birthday | datetime | 否 | 出生日期，格式：YYYY-MM-DD |
| 14 | doctorName | varchar(10) | 否 | 开单医生 |
| 15 | deptName | varchar(30) | 否 | 开单科室 |
| 16 | inpatientAreaName | varchar(30) | 否 | 病区名称 |
| 17 | bedNum | varchar(15) | 否 | 床号 |
| 18 | requestTime | datetime | 否 | 申请时间，格式：YYYY-MM-DD HH:MM:SS |
| 19 | inputTime | datetime | 否 | 录入时间，格式：YYYY-MM-DD HH:MM:SS |
| 20 | collectTime | datetime | 否 | 采集时间，格式：YYYY-MM-DD HH:MM:SS |
| 21 | clinicalRemark | varchar(400) | 否 | 临床诊断 |
| 22 | objectives | varchar(170) | 否 | 检查目的 |
| 23 | remark | varchar(250) | 否 | 标本备注 |
| 24 | requestRemark | varchar(250) | 否 | 医嘱备注 |
| 25 | subjectCompanyName | varchar(30) | 否 | 病人单位名称 |
| 26 | submissionDate | datetime | 否 | 送检日期，格式：YYYY-MM-DD HH:MM:SS |
| 27 | takeTime | datetime | 否 | 接收时间，格式：YYYY-MM-DD HH:MM:SS |
| 28 | inputByName | varchar(10) | 否 | 录入者 |
| 29 | tubeTypeName | varchar(30) | 否 | 试管类型 |
| 30 | sampleTypeName | varchar(150) | 否 | 标本类型 |
| 31 | itemCount | int(11) | 否 | 标本项目总数 |
| 32 | sampleStateName | varchar(50) | 否 | 样本状态 |
| 33 | subjectPhone | varchar(24) | 否 | 联系电话 |
| 34 | diabetes | varchar(25) | 否 | 糖尿病史 |
| 35 | smokingHistory | varchar(25) | 否 | 吸烟史 |
| 36 | idCard | varchar(32) | 否 | id卡号码，例如：身份证号码，军人证，医保、社保号 |
| 37 | weight | varchar(15) | 否 | 体重，例如：80kg |
| 38 | height | varchar(15) | 否 | 身高，例如：173cm |
| 39 | collectionSite | varchar(45) | 否 | 采集部位，例如：伤口切面等 |
| 40 | urineVolume24h | varchar(15) | 否 | 24小时尿量，例如：1200ml |
| 41 | bultrasonic | varchar(15) | 否 | B超孕周 |
| 42 | pregnant | varchar(15) | 否 | B超孕日 |
| 43 | lmpPregnant | varchar(15) | 否 | LMP孕日 |
| 44 | lmpBultrasonic | varchar(15) | 否 | LMP孕周 |
| 45 | babyCount | tinyint(4) | 否 | 怀孕胎数，例如：1、2、3 |
| 46 | seminalVolume | varchar(15) | 否 | 精浆量，例如：23ml |
| 47 | requestNo | varchar(15) | 否 | 医嘱号 |
| 48 | lmpDate | varchar(25) | 否 | 末次月经，格式：YYYY-MM-DD |
| 49 | isBbsReport | int(11) | 否 | 是否社区报告,值：0：否，1：是 |
| 50 | isRecheck | int(11) | 否 | 是否复查，值：0：否，1：是 |
| 51 | recheckBarcode | varchar(15) | 否 | 复查条码 |
| 52 | crl | varchar(12) | 否 | 头臀径，例如：8.9mm |
| 53 | bpd | varchar(12) | 否 | 双顶径，例如：13mm |
| 54 | nasalBone | varchar(12) | 否 | 鼻骨，例如：9.4mm |
| 55 | nt | varchar(12) | 否 | 颈项透明层厚度，例如：8.1mm |
| 56 | nasalBoneState | int(11) | 否 | 鼻骨状态，值：0：缺少，1：可见 |
| 57 | imbedDate | datetime | 否 | 植入日期，格式：YYYY-MM-DD |
| 58 | eggRetrievalDate | datetime | 否 | 取卵日期，格式：YYYY-MM-DD |
| 59 | isIddm | int(11) | 否 | 胰岛素依赖性糖尿病，值：0：否，1：是  |
| 60 | race | int(11) | 否 | 种族，值：0：黄种人,1：afro-caribbean,2：Asian，3：Caucasian,4：oriental,5：其他 |
| 61 | isSmoke | int(11) | 否 | 是否吸烟，值：0：否，1：是  |
| 62 | pregnantWay | int(11) | 否 | 受孕方式，值：0：自然,1：克罗米芬，2：试验婴儿IVF,3：ICSI,4：增卵,5：供精,6：其他 |
| 63 | exceptionPregnancy | int(11) | 否 | 异常妊娠史，值：0：无,1：21三体,2：18三体,3：13三体,4：神经管畸形,5：其他  |
| 64 | isTransplantSurgery | int(11) | 否 | 是否有过移植手术，值：0：否，1：是  |
| 65 | isTransfusion | int(11) | 否 | 是否输血，值：0：否，1：是  |
| 66 | stemCellTherapy | int(11) | 否 | 是否有过干细胞治疗，值：0：否，1：是   |
| 67 | immuneTherapy | int(11) | 否 | 免疫治疗，值：0：否，1：是 |
| 68 | centralizedHosp | varchar(35) | 否 | 集中送检医院 |
| 69 | collectHosp | varchar(35) | 否 | 采样医院 |
| 70 | bodyStyle | varchar(25) | 否 | 体位，例如：立位、卧位等 |
| 71 | requestGroups | [] | 否 | 申请项目组 |
| 72 | testEnShortName | varchar(30) | 否 | 英文简称，例：CBC+DIFF、ABO等 |
| 73 | testItemCode | varchar(15) | 是 | 申请项目代码，例如：xcg001、A001等 |
| 74 | testItemName | varchar(55) | 是 | 申请项目名称，例：血常规五分类、血型鉴定等 |
| 75 | displayOrder | int(11) | 否 | 顺序号 |

样例：
```json
{
    "orgId": "",
    "appId": "",
    "data": [{
        "barcode": "20170505095301",
        "treatmentTypeName": "门诊",
        "subjectNo": "",
        "subjectNoType": "",
        "subjectName": "陈阳",
        "sexName": "男",
        "age": "21",
        "ageUnit": "岁",
        "birthday": "1990-02-14 00:00:00",
        "doctorName": "张文涛医生",
        "deptName": "内科",
        "inpatientAreaName": "",
        "bedNum": "",
        "requestTime": "2017-05-05 09:53:01",
        "inputTime": "",
        "collectTime": "",
        "clinicalRemark": "临床诊断",
        "objectives": "",
        "remark": "",
        "requestRemark": "医嘱备注",
        "subjectCompanyName": "",
        "submissionDate": "",
        "takeTime": "",
        "inputByName": "",
        "tubeTypeName": "",
        "sampleTypeName": "静脉血",
        "itemCount": "",
        "sampleStateName": "",
        "subjectPhone": "23838383838",
        "diabetes": "",
        "smokingHistory": "",
        "idCard": "430324199002140001",
        "weight": "",
        "height": "",
        "collectionSite": "",
        "urineVolume24h": "",
        "bultrasonic": "",
        "pregnant": "",
        "lmpPregnant": "",
        "lmpBultrasonic": "",
        "babyCount": "",
        "seminalVolume": "",
        "requestNo": "",
        "lmpDate": "",
        "isBbsReport": "",
        "isRecheck": "",
        "recheckBarcode": "",
        "crl": "",
        "bpd": "",
        "nasalBone": "",
        "nt": "",
        "nasalBoneState": "",
        "imbedDate": "",
        "eggRetrievalDate": "",
        "isIddm": "",
        "race": "",
        "isSmoke": "",
        "pregnantWay": "",
        "exceptionPregnancy": "",
        "isTransplantSurgery": "",
        "isTransfusion": "",
        "stemCellTherapy": "",
        "immuneTherapy": "",
        "centralizedHosp": "",
        "collectHosp": "",
        "bodyStyle": "",
        "requestGroups": [
            {
                "testEnShortName": "FKJC",
                "testItemCode": "243",
                "testItemName": "妇科检查",
                "displayOrder": 1
            },
            {
                "testEnShortName": "HPVJC",
                "testItemCode": "245",
                "testItemName": "HPV检查",
                "displayOrder": 2
            },
            {
                "testEnShortName": "YDJJC",
                "testItemCode": "244",
                "testItemName": "阴道镜检查",
                "displayOrder": 3
            }
        ]
    }]
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | success | boolean |  | 是否成功 |
| 2 | errorCode | string |  | 错误编码 |
| 3 | errorMsg | string |  | 错误信息 |
| 4 | data | string |  | 每一条申请单的处理状态 |
| 5 | success | boolean |  | 是否成功 |
| 6 | errorCode | string |  | 错误编码 |
| 7 | errorMsg | string |  | 错误信息 |
| 8 | data | string |  |  条码号 |

样例：
```json
{
    "success": false,
    "errorCode": null,
    "errorMsg": "检验申请单列表大小不能超出 50 个条码的申请单信息.",
    "data": null
}
```
或者
```json
{
    "success": true,
    "errorCode": null,
    "errorMsg": null,
    "data": [
        {
            "success": false,
            "errorCode": "403",
            "errorMsg": "[barcode - 条形码] 不能为空",
            "data": null
        },
        {
            "success": false,
            "errorCode": "403",
            "errorMsg": "条形码:20170505095301,记录已经存在",
            "data": "20170505095301"
        },
        {
            "success": false,
            "errorCode": "410",
            "errorMsg": "[sex_name] 字段超出数据库字段设定长度",
            "data": "285937663"
        },
        {
            "success": true,
            "errorCode": null,
            "errorMsg": null,
            "data": "469409078"
        }
    ]
}
```


## 提供物流核收列表(已核收)
- 请求地址：/v3/api/fromlis/request/logisticslist
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token |  |  | head参数 |
| 2 | orgId | bigint(19) | 是 | 送检机构id |
| 3 | appId | bigint(19) | 是 | 系统id |
| 4 | data | string |  |  |  |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": ""
}
```

- 返回结果：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | success | boolean |  | 是否成功 |
| 2 | errorCode | string |  | 错误编码 |
| 3 | errorMsg | string |  | 错误信息 |
| 4 | data | string |  | 返回数据 |
| 5 | barcode | varchar(15) | 是 | 条码号 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": [{
        "barcode": "20170505095301"
    },
    {
        "barcode": "20170505095302"
    }]
}
```


