section: his
id: his-report
description: HIS 检验报告接口说明
icon: icon-book
filter: his-report
---

# HIS 检验报告

## 提供检验报告列表(已审核)
- 请求地址：/v3/api/his/report/success/list
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
| 5 | barcode | varchar(15)   | 是 | [条码号] — 标本对应的条码号 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": [{
        "barcode": "2156890036"
    }]
}
```


## 提供单个检验报告明细
- 请求地址：/v3/api/his/report/success/detail
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 4 | data | string | | 提交数据 |
| 5 | barcode | varchar(15) | 是 | 条码号 |
| 6 | isConverted | int(1) | 是 | 项目对照标志位，值：0-不需要对照项目，1-需要对照项目 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "barcode": "",
        "isConverted": 1
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
| 5 | barcode              | varchar(15)   | 是 | 条码号 |
| 6 | sequenceNum         | varchar(15)   | 否 | 样本号 |
| 7 | treatmentTypeName  | varchar(30)   | 是 | 就诊类型，例如：门诊、住院、体检等 |
| 8 | subjectNo           | varchar(30)   | 否 | 病人编号 |
| 9 | subjectName         | varchar(30)   | 是 | 病人姓名 |
| 10 | sexName             | varchar(6)    | 是 | 性别，值：男、女、未知 |
| 11 | age                  | varchar(17)   | 是 | 年龄，例如：1岁2月 |
| 12 | sampleTypeName     | varchar(150)  | 是 | 标本类型，例如：血清、尿液、粪便等 |
| 13 | sampleStateName    | varchar(50)   | 否 | 样本状态，例如：正常、轻度溶血等 |
| 14 | clinicalRemark      | varchar(400)  | 否 | 临床诊断 |
| 15 | objectives           | varchar(170)  | 否 | 检查目的 |
| 16 | requestDoctorName  | varchar(10)   | 否 | 申请医生，例如：李时珍 |
| 17 | requestDeptName    | varchar(30)   | 否 | 开单科室，例如：中医科 |
| 18 | collectTime         | datetime      | 否 | 采集时间，格式：YYYY-MM-DD HH:MM:SS |
| 19 | takeTime            | datetime      | 否 | 接收时间，格式：YYYY-MM-DD HH:MM:SS |
| 20 | testByName         | varchar(10)   | 是 | 检验医师 |
| 21 | testTime            | datetime      | 是 | 检验时间，格式：YYYY-MM-DD HH:MM:SS |
| 22 | releaseByName      | varchar(10)   | 是 | 初审医师 |
| 23 | releaseTime         | datetime      | 是 | 初审时间，格式：YYYY-MM-DD HH:MM:SS |
| 24 | auditedByName      | varchar(10)   | 是 | 审核医师 |
| 25 | auditedTime         | datetime      | 是 | 审核时间，格式：YYYY-MM-DD HH:MM:SS |
| 26 | reportEvaluation    | varchar(250)  | 否 | 报告评价 |
| 27 | reportRemark        | varchar(250)  | 否 | 建议解释 |
| 28 | mdr                  | int(11)       | 否 | 多重耐药，值：0 — 无，1 — 多重耐药。 |
| 29 | instrumentName | varchar(30) | 是 | 仪器名称 |
| 30 | reportType | int(11) | 是 | 报告单类型，值：1 — 常规报告单，2 — 微生物药敏报告单，3 — 病理报告单。 |
| 31 | reportId            | bigint(19)    | 是 | 报告单id |
| 32 | reportPDF            | string | 是 | PDF 报告单(Base64) |
| 33 | testingAdditions     | {}  | 否 | [附加信息] |
| 34 | idCard              | varchar(32) | 否 | id卡号码 |
| 35 | height               | varchar(15) | 否 | 身高 |
| 36 | weight               | varchar(15) | 否 | 体重 |
| 37 | collectionSite      | varchar(45) | 否 | 采集部位，例如：伤口切面 |
| 38 | urineVolume24h     | varchar(15) | 否 | 24小时尿量，例如：1200ml |
| 39 | pregnant             | varchar(15) | 否 | B超孕日 |
| 40 | bultrasonic          | varchar(15) | 否 | B超孕周 |
| 41 | lmpPregnant         | varchar(15) | 否 | LMP孕日 |
| 42 | lmpBultrasonic      | varchar(15) | 否 | LMP孕周 |
| 43 | babyCount           | tinyint(4)  | 否 | 怀孕胎数 |
| 44 | seminalVolume       | varchar(15) | 否 | 精浆量 |
| 45 | requestNo           | varchar(15) | 否 | 医嘱号 |
| 46 | inpatientAreaName  | varchar(30) | 否 | 病区名称 |
| 47 | bedNum              | varchar(15) | 否 | 床号 |
| 48 | timesInt            | int(11)     | 否 | 就诊次数 |
| 49 | requestTime         | datetime    | 否 | 申请时间，格式：YYYY-MM-DD HH:MM:SS |
| 50 | notifyTime          | datetime    | 否 | 送检时间，格式：YYYY-MM-DD HH:MM:SS |
| 51 | subjectPhone        | varchar(24) | 否 | 病人电话 |
| 52 | subjectCompanyName | varchar(30) | 否 | 病人单位名称 |
| 53 | batchNo             | varchar(15) | 否 | 体检批号代码 |
| 54 | costClasses         | int(11)     | 是  | 费用类别 |
| 55 | diabetes             | varchar(25) | 否 | 糖尿病史 |
| 56 | smokingHistory      | varchar(25) | 否 | 吸烟史 |
| 57 | lmpDate             | varchar(25) | 否 | 末次月经，格式：YYYY-MM-DD |
| 58 | testingGroups     | [] | 否 | [检验项目组] |
| 59 | testItemCode       | bigint(19)  | 是 | 检验项目编码,例如：A001 |
| 60 | testItemName     | varchar(55) | 是  | 检验项目名称，例：血型鉴定 |
| 61 | testEnShortName | varchar(30) | 否 | 英文简称，例如：ABO |
| 62 | displayOrder      | int(11)     | 否 | 顺序号 |
| 63 | testingLines     | []  | 否 | [检验项目明细] |
| 64 | testItemCode       | bigint(19)    | 是 | 报告项目编码，例如：GELT00000001 |
| 65 | testItemName     | varchar(55)   | 是  | 报告项目名称 |
| 66 | testEnShortName | varchar(30)   | 否 | [英文简称]， 例： FRUC |
| 67 | resultValue       | varchar(150)  | 是 | 结果内容 |
| 68 | resultComment     | varchar(1000) | 否 | 结果备注 |
| 69 | unit               | varchar(30)   | 否 | 单位 |
| 70 | lowhighFlag  | varchar(10)   | 否 | 高低标志 |
| 71 | refDesc           | varchar(320)  | 否 | 参考范围，例如：0.0-10.0 |
| 72 | displayOrder      | int(11)       | 否 | 打印次序 |
| 73 | testMethodName   | varchar(30)   | 否 | 检验方法 |
| 74 | resultClassify    | int(11)       | 否 | 结果分类 |
| 75 | testingOrganisms     | []  | 否 | 细菌结果组 |
| 76 | organismCode          | varchar(50) | 是  | 细菌编码 |
| 77 | organismName          | varchar(50) | 是  | 细菌名称 |
| 78 | organismEnShortName | varchar(30) | 否 | 英文简称 |
| 78 | organismEnName | varchar(55) | 否 | 英文名称 |
| 78 | organismWhonetCode | varchar(15) | 否 | whonet编码 |
| 79 | displayOrder          | int(11)     | 否 | 顺序号 |
| 80 | tips                   | varchar(30) | 否 | 提示 |
| 81 | quantityComment       | varchar(45) | 否 | 落菌计算 |
| 82 | mdr                    | int(11)     | 否 | 多重耐药 |
| 83 | testingAntibiotics     | []  | 否 | [标本药敏信息] |
| 84 | antibioticCode          | varchar(50) | 是  | 抗生素编码 |
| 85 | antibioticName          | varchar(50) | 是  | 抗生素名称 |
| 86 | antiboiticEnShortName | varchar(30) | 否 | 英文简称 |
| 87 | antiboiticEnName | varchar(55) | 否 | 英文名称 |
| 88 | antiboiticWhonetCode | varchar(15) | 否 | whonet编码 |
| 89 | displayOrder            | int(11)     | 否 | 顺序号 |
| 90 | zoneS                   | varchar(12) | 否 | Zone敏感参考值 |
| 91 | zoneM                   | varchar(12) | 否 | Zone中介参考值 |
| 92 | zoneR                   | varchar(12) | 否 | Zone耐药参考值 |
| 93 | zoneValue               | varchar(12) | 否 | Zone结果值 |
| 94 | zoneResult              | varchar(10) | 否 | Zone结果 |
| 95 | micS                    | varchar(12) | 否 | MIC敏感参考值 |
| 96 | micM                    | varchar(12) | 否 | MIC中介参考值 |
| 97 | micR                    | varchar(12) | 否 | MIC耐药参考值 |
| 98 | micValue                | varchar(12) | 否 | Mic结果值 |
| 99 | micResult               | varchar(10) | 否 | Mic结果 |
| 100 | micMethod              | int(11)     | 否 | 微生物检验方法 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": [
        {
            "barcode": "201709100001",
            "sequenceNum": "1",
            "treatmentTypeName": "门诊",
            "subjectNo": "mz00001",
            "subjectName": "张弘毅",
            "sexName": "男",
            "age": "23岁",
            "sampleTypeName": "全血",
            "sampleStateName": "正常",
            "clinicalRemark": "高血压",
            "objectives": "",
            "requestDoctorName": "王聪聪",
            "requestDeptName": "外科门诊",
            "collectTime": "2017-09-10 09:12:54",
            "takeTime": "2017-09-10 12:34:05",
            "testByName": "赵大海",
            "testTime": "2017-09-10 12:36:05",
            "releaseByName": "赵大海",
            "releaseTime": "2017-09-13 12:36:05",
            "auditedByName": "杨超",
            "auditedTime": "2017-09-13 15:36:05",
            "reportEvaluation": "报告评价内容",
            "reportRemark": "检验解释内容",
            "mdr": 0,
            "instrumentName": "TAB细菌仪",
            "reportType": 2,
            "reportId": "8231213292342423",
            "reportPDF": "PDF(Base64)",
            "testingAdditions": {
                "idCard": "4414251970090212112",
                "height": "170cm",
                "weight": "60kg",
                "collectionSite": "",
                "urineVolume24h": "",
                "pregnant": "",
                "bultrasonic": "",
                "lmpPregnant": "",
                "lmpBultrasonic": "",
                "babyCount": "",
                "seminalVolume": "",
                "requestNo": "",
                "inpatientAreaName": "",
                "bedNum": "",
                "timesInt": "",
                "requestTime": "",
                "notifyTime": "",
                "subjectPhone": "",
                "subjectCompanyName": "",
                "batchNo": "",
                "costClasses": "",
                "diabetes": "",
                "smokingHistory": "",
                "lmpDate": ""
            },
            "testingGroups": [
                {
                    "testItemCode": "100001",
                    "testItemName": "血培养鉴定",
                    "testEnShortName": "xpy",
                    "displayOrder": "1",
                    "testingLines": [
                        {
                            "testItemCode": "ETAE000988738E81",
                            "testItemName": "血培养鉴定(需氧)",
                            "testEnShortName": "xpyjd",
                            "resultValue": "阳性",
                            "resultComment": "",
                            "unit": "",
                            "lowhighFlag": "",
                            "refDesc": "",
                            "displayOrder": "1",
                            "testMethodName": "",
                            "resultClassify": "",
                            "testingOrganisms": [
                                {
                                    "organismCode": "1000000865",
                                    "organismName": "金黄色葡萄球菌金黄亚种",
                                    "organismEnShortName": "SAU",
                                    "organismEnName": "Staphylococcus aureus",
                                    "organismWhonetCode": "SAU",
                                    "displayOrder": "1",
                                    "tips": "ERSA",
                                    "quantityComment": "5E+08",
                                    "mdr": "0",
                                    "testingAntibiotics": [
                                        {
                                            "antibioticCode": "100002",
                                            "antibioticName": "两性霉素B",
                                            "antiboiticEnShortName": "AMB",
                                            "antiboiticEnName": "Amphotericin B",
                                            "antiboiticWhonetCode": "AMB",
                                            "displayOrder": "1",
                                            "zoneS": "<8",
                                            "zoneM": "9-10",
                                            "zoneR": ">=11",
                                            "zoneValue": ">89/11",
                                            "zoneResult": "耐药",
                                            "micS": "",
                                            "micM": "",
                                            "micR": "",
                                            "micValue": "",
                                            "micResult": "",
                                            "micMethod": "KB法"
                                        },
                                        {
                                            "antibioticCode": "2000000006",
                                            "antibioticName": "阿莫西林",
                                            "antiboiticEnShortName": "AMX",
                                            "antiboiticEnName": "Amoxicillin",
                                            "antiboiticWhonetCode": "AMX",
                                            "displayOrder": "2",
                                            "zoneS": "<12",
                                            "zoneM": "13-20",
                                            "zoneR": ">=21",
                                            "zoneValue": "10",
                                            "zoneResult": "敏感",
                                            "micS": "",
                                            "micM": "",
                                            "micR": "",
                                            "micValue": "",
                                            "micResult": "",
                                            "micMethod": "KB法"
                                        },
                                        {
                                            "antibioticCode": "2000000019",
                                            "antibioticName": "阿奇霉素",
                                            "antiboiticEnShortName": "AZM",
                                            "antiboiticEnName": "Azithromycin",
                                            "antiboiticWhonetCode": "AZM",
                                            "displayOrder": "3",
                                            "zoneS": "",
                                            "zoneM": "",
                                            "zoneR": "",
                                            "zoneValue": "",
                                            "zoneResult": "",
                                            "micS": "<10",
                                            "micM": "10-20",
                                            "micR": ">=21",
                                            "micValue": "10",
                                            "micResult": "中介",
                                            "micMethod": "MIC法"
                                        }
                                    ]
                                },
                                {
                                    "organismCode": "1000000215",
                                    "organismName": "大肠埃希菌",
                                    "organismEnShortName": "ECO",
                                    "organismEnName": "Escherichia coli",
                                    "organismWhonetCode": "ECO",
                                    "displayOrder": "2",
                                    "tips": "ERSA",
                                    "quantityComment": "5E+08",
                                    "mdr": "0",
                                    "testingAntibiotics": [
                                        {
                                            "antibioticCode": "2000000001",
                                            "antibioticName": "两性霉素B",
                                            "antiboiticEnShortName": "AMB",
                                            "antiboiticEnName": "Amphotericin B",
                                            "antiboiticWhonetCode": "AMB",
                                            "displayOrder": "1",
                                            "zoneS": "<8",
                                            "zoneM": "9-10",
                                            "zoneR": ">=11",
                                            "zoneValue": ">89/11",
                                            "zoneResult": "耐药",
                                            "micS": "",
                                            "micM": "",
                                            "micR": "",
                                            "micValue": "",
                                            "micResult": "",
                                            "micMethod": "KB法"
                                        }
                                    ]
                                }
                            ]
                        },
                        {
                            "testItemCode": "ETAE000988738E82",
                            "testItemName": "血培养鉴定(厌氧)",
                            "testEnShortName": "xpyjd",
                            "resultValue": "无细菌生长",
                            "resultComment": "",
                            "unit": "",
                            "lowhighFlag": "",
                            "refDesc": "",
                            "displayOrder": "",
                            "testMethodName": "",
                            "resultClassify": "",
                            "testingOrganisms": null
                        }
                    ]
                }
            ]
        }
    ]
}
```


## 接收检验报告获取成功的通知
- 请求地址：/v3/api/his/report/success/success
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 4 | data | string | | 提交数据 |
| 5 | reportId | bigint(19) | 是 | 报告单id |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "reportId": ""
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

