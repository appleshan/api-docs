section: fromlis
id: fromlis-report
description: From LIS 检验报告单接口说明
icon: icon-book
filter: fromlis-report
---

# From LIS 检验报告单

## 提供检验报告列表(已审核)
- 请求地址：/v3/api/fromlis/report/success/list
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token |  |  | head参数 |
| 2 | orgId | bigint(19) | 是 | 送检机构id |
| 3 | appId | bigint(19) | 是 | 系统id |
| 4 | data | string |  |  |
| 5 | isFullAmount | int(1) | 是 | 是否全量，值：0-全量，1-增量 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "isFullAmount": 0
    }
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
    "errorCode": null,
    "errorMsg": null,
    "data": [
        {
            "barcode": "441733129900"
        },
        {
            "barcode": "441535022300"
        }
    ]
}
```


## 提供单个检验报告明细
- 请求地址：/v3/api/fromlis/report/success/detail
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token |  |  | head参数 |
| 2 | orgId | bigint(19) | 是 | 送检机构id |
| 3 | appId | bigint(19) | 是 | 系统id |
| 4 | data | string |  | 提交数据 |
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
| 1 | success | boolean |  | 是否成功 |
| 2 | errorCode | string |  | 错误编码 |
| 3 | errorMsg | string |  | 错误信息 |
| 4 | data | string |  | 返回数据 |
| 5 | barcode | varchar(15) | 是 | 条码号 |
| 6 | treatmentTypeName | varchar(30) | 否 | 就诊类型，例如：门诊、住院、体检 |
| 7 | subjectNo | varchar(30) | 否 | 病人ID，病人唯一标识 |
| 8 | subjectName | varchar(30) | 是 | 病人姓名 |
| 9 | sexName | varchar(6) | 是 | 病人性别，男、女、未知 |
| 10 | age | varchar(17) | 是 | 病人年龄，例如：1岁2月  |
| 11 | sampleTypeName | varchar(150) | 否 | 标本类型，例如：血清、尿液等 |
| 12 | clinicalRemark | varchar(400) | 否 | 临床诊断 |
| 13 | objectives | varchar(170) | 否 | 检查目的 |
| 14 | requestDoctorName | varchar(10) | 否 | 申请医生 |
| 15 | requestDeptName | varchar(30) | 否 | 开单科室 |
| 16 | inpatientAreaName | varchar(30) | 否 | 病区名称 |
| 17 | bedNum | varchar(15) | 否 | 床号 |
| 18 | requestTime | datetime | 否 | 申请时间，格式：YYYY-MM-DD HH:MM:SS |
| 19 | collectTime | datetime | 否 | 采集时间，格式：YYYY-MM-DD HH:MM:SS |
| 20 | notifyTime | datetime | 否 | 送检时间，格式：YYYY-MM-DD HH:MM:SS |
| 21 | takeTime | datetime | 否 | 接收时间，格式：YYYY-MM-DD HH:MM:SS |
| 22 | idCard | varchar(32) | 否 | ID卡号码，身份证、军人证等 |
| 23 | height | varchar(15) | 否 | 身高，例如：173cm |
| 24 | weight | varchar(15) | 否 | 体重，例如：80kg |
| 25 | collectionSite | varchar(45) | 否 | 标本采集部位 |
| 26 | urineVolume24h | varchar(15) | 否 | 24小时尿量，例如：1200ml |
| 27 | pregnant | varchar(15) | 否 | B超孕日 |
| 28 | bultrasonic | varchar(15) | 否 | B超孕周 |
| 29 | lmpPregnant | varchar(15) | 否 | LMP孕日 |
| 30 | lmpBultrasonic | varchar(15) | 否 | LMP孕周 |
| 31 | babyCount | tinyint(4) | 否 | 怀孕胎数，例如：1、2、3. |
| 32 | seminalVolume | varchar(15) | 否 | 精浆量，例如：20ml |
| 33 | requestNo | varchar(15) | 否 | 医嘱号，医生开的医嘱号 |
| 34 | timesInt | int(11) | 否 | 就诊次数 |
| 35 | subjectPhone | varchar(24) | 否 | 联系电话 |
| 36 | subjectCompanyName | varchar(30) | 否 | 单位名称 |
| 37 | batchNo | varchar(15) | 否 | 体检批号代码 |
| 38 | costClasses | int(11) | 是 | 费用类别，例如：免费、医保等 |
| 39 | diabetes | varchar(25) | 否 | 糖尿病史 |
| 40 | smokingHistory | varchar(25) | 否 | 吸烟史 |
| 41 | lmpDate | varchar(25) | 否 | 末次月经，格式：YYYY-MM-DD |
| 42 | testingReports | [] | 否 | 检验报告组 |
| 43 | reportId | bigint(19) | 是 | 报告单id |
| 44 | testByName | varchar(10) | 是 | 检验医师 |
| 45 | testTime | datetime | 是 | 检验时间，格式：YYYY-MM-DD HH:MM:SS |
| 46 | releaseByName | varchar(10) | 是 | 初审医师 |
| 47 | releaseTime | datetime | 是 | 初审时间，格式：YYYY-MM-DD HH:MM:SS |
| 48 | auditedByName | varchar(10) | 是 | 审核医师 |
| 49 | auditedTime | datetime | 是 | 审核时间，格式：YYYY-MM-DD HH:MM:SS |
| 50 | reportEvaluation | varchar(250) | 否 | 报告评价 |
| 51 | reportRemark | varchar(250) | 否 | 建议解释 |
| 52 | sequenceNum | varchar(15) | 否 | 样本号 |
| 53 | sampleStateName | varchar(50) | 否 | 样本状态，例如：正常、轻度溶血等 |
| 54 | mdr | int(11) | 否 | 多重耐药 |
| 55 | reportPDF | string | 是 | PDF 报告单(Base64) |
| 56 | testingGroups | [] | 否 | 检验项目组 |
| 57 | testItemCode | bigint(19) | 否 | 申请项目代码 |
| 58 | testItemName | varchar(55) | 是 | 申请项目名称，例如：血常规五分类 |
| 59 | testEnShortName | varchar(30) | 否 | 英文简称，例如：CBC+DIFF |
| 60 | displayOrder | int(11) | 否 | 顺序号 |
| 61 | testingLines | [] | 否 | 检验项目明细 |
| 62 | testItemCode | bigint(19) | 否 | 检验项目代码 |
| 63 | testItemName | varchar(55) | 是 | 检验项目名称，例如：白细胞计数 |
| 64 | testEnShortName | varchar(30) | 否 | 英文简称，例如：WBC |
| 65 | resultValue | varchar(150) | 是 | 结果内容 |
| 66 | resultComment | varchar(1000) | 否 | 结果备注 |
| 67 | unit | varchar(30) | 否 | 单位 |
| 68 | lowhighFlagName | varchar(10) | 否 | 高低标志 |
| 69 | refDesc | varchar(320) | 否 | 参考范围，例如：12.30-23.45 |
| 70 | displayOrder | int(11) | 否 | 打印次序 |
| 71 | testMethodName | varchar(30) | 否 | 检验方法，例如：微柱凝集法、电化学发光法等 |
| 72 | resultClassify | int(11) | 否 | 微生物结果分类，值：1-阴性，2-阳性 |
| 73 | testingOrganisms | [] | 否 | 细菌检验结果组 |
| 74 | organismName | varchar(50) | 是 | 细菌名称 |
| 75 | organismEnShortName | varchar(30) | 否 | 英文简称 |
| 76 | displayOrder | int(11) | 否 | 顺序号 |
| 77 | tips | varchar(30) | 否 | 提示 |
| 78 | quantityComment | varchar(45) | 否 | 落菌计算 |
| 79 | mdr | int(11) | 否 | 多重耐药，值：0—否，1—多重耐药。 |
| 80 | testingAntibiotics | [] | 否 | 药敏检验结果组 |
| 81 | antibioticName | varchar(50) | 是 | 抗生素名称 |
| 82 | antiboiticEnShortName | varchar(30) | 否 | 英文简称 |
| 83 | displayOrder | int(11) | 否 | 顺序号 |
| 84 | zoneS | varchar(12) | 否 | Zone敏感参考值 |
| 85 | zoneM | varchar(12) | 否 | Zone中介参考值 |
| 86 | zoneR | varchar(12) | 否 | Zone耐药参考值 |
| 87 | zoneValue | varchar(12) | 否 | Zone结果值 |
| 88 | zoneResult | varchar(10) | 否 | Zone结果，值：敏感、耐药、中介 |
| 89 | micS | varchar(12) | 否 | MIC敏感参考值 |
| 90 | micM | varchar(12) | 否 | MIC中介参考值 |
| 91 | micR | varchar(12) | 否 | MIC耐药参考值 |
| 92 | micValue | varchar(12) | 否 | Mic结果值 |
| 93 | micResult | varchar(10) | 否 | Mic结果，值：敏感、耐药、中介 |
| 94 | micMethod | int(11) | 否 | 微生物检验方法，值：1—mic方法,2—kb方法。 |
| 95 | testingText | {} | 否 | 病理检验结果组 |
| 96 | resultText | varchar(3000) | 否 | 描述报告结果内容 |
| 97 | isPositive | int(11) | 否 | 是否阳性标志，值：0— 阴性, 1 — 阳性. |

样例：
```json
{
    "success": true,
    "errorCode": null,
    "errorMsg": null,
    "data": {
        "barcode": "441733129900",
        "treatmentTypeName": null,
        "subjectNo": "106732561200",
        "subjectName": "冯丽菲",
        "sexName": "女",
        "age": "35岁",
        "sampleTypeName": null,
        "clinicalRemark": null,
        "objectives": null,
        "requestDoctorName": null,
        "requestDeptName": "病理科",
        "collectTime": "2017-10-10 14:46:43",
        "takeTime": null,
        "requestTime": "2017-10-10 14:46:43",
        "bedNum": null,
        "timesInt": null,
        "subjectCompanyName": null,
        "costClasses": null,
        "batchNo": null,
        "notifyTime": "2017-10-10 14:48:31",
        "inpatientAreaName": null,
        "idCard": null,
        "height": null,
        "weight": null,
        "collectionSite": null,
        "urineVolume24h": null,
        "pregnant": null,
        "bultrasonic": null,
        "lmpPregnant": null,
        "lmpBultrasonic": null,
        "babyCount": null,
        "seminalVolume": null,
        "requestNo": null,
        "subjectPhone": null,
        "diabetes": null,
        "smokingHistory": null,
        "lmpDate": null,
        "testingReports": [{
            "reportId": null,
            "testByName": "管理员",
            "testTime": 1507686479000,
            "releaseByName": "管理员",
            "releaseTime": 1507686479000,
            "auditedByName": "管理员",
            "auditedTime": "2017-10-11 09:48:12",
            "reportEvaluation": null,
            "reportRemark": null,
            "sequenceNum": "1",
            "sampleStateName": null,
            "mdr": null,
            "reportPdf": null,
            "testingGroups": [{
                "testItemName": "肝功五项",
                "testEnShortName": "gg5",
                "displayOrder": 5,
                "testItemCode": null,
                "testingLines": [{
                    "testItemName": "血清丙氨酸氨基转移酶测定(ALT)",
                    "testEnShortName": "ALT",
                    "resultValue": "12",
                    "resultComment": null,
                    "unit": null,
                    "refDesc": null,
                    "displayOrder": 0,
                    "testMethodName": "速率法",
                    "resultClassify": 0,
                    "testItemCode": "CECA1000001012",
                    "lowhighFlagName": "1",
                    "testingOrganisms": []
                },
                {
                    "testItemName": "血清天门冬氨酸氨基转移酶测定(AST)",
                    "testEnShortName": "AST",
                    "resultValue": "1",
                    "resultComment": null,
                    "unit": null,
                    "refDesc": null,
                    "displayOrder": 0,
                    "testMethodName": "速率法",
                    "resultClassify": 0,
                    "testItemCode": "CECB1000001012",
                    "lowhighFlagName": "1",
                    "testingOrganisms": []
                },
                {
                    "testItemName": "血清直接胆红素测定(D-Bil)",
                    "testEnShortName": "DBIL",
                    "resultValue": "12",
                    "resultComment": null,
                    "unit": null,
                    "refDesc": null,
                    "displayOrder": 0,
                    "testMethodName": "钒酸盐法",
                    "resultClassify": 0,
                    "testItemCode": "CELB1000001055",
                    "lowhighFlagName": "1",
                    "testingOrganisms": []
                },
                {
                    "testItemName": "间接胆红素(IBIL)",
                    "testEnShortName": "IBIL",
                    "resultValue": "12",
                    "resultComment": null,
                    "unit": null,
                    "refDesc": null,
                    "displayOrder": 0,
                    "testMethodName": "计算值",
                    "resultClassify": 0,
                    "testItemCode": "CELC1000001030",
                    "lowhighFlagName": "1",
                    "testingOrganisms": []
                },
                {
                    "testItemName": "血清总胆红素测定(T-Bil)",
                    "testEnShortName": "TBIL",
                    "resultValue": "1",
                    "resultComment": null,
                    "unit": null,
                    "refDesc": null,
                    "displayOrder": 0,
                    "testMethodName": "钒酸盐法",
                    "resultClassify": 0,
                    "testItemCode": "CELA1000001055",
                    "lowhighFlagName": "1",
                    "testingOrganisms": []
                }]
            }]
        }],
        "testingText": {
            "resultText": "",
            "isPositive": 0
        }
    }
}
```


## 接收检验报告获取成功的通知
- 请求地址：/v3/api/fromlis/report/success/success
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token |  |  | head参数 |
| 2 | orgId | bigint(19) | 是 | 机构id |
| 3 | appId | bigint(19) | 是 | 系统id |
| 4 | data | string |  | 提交数据 |
| 5 | reportId | bigint(19) | 否 | 报告单id |

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
| 1 | success | boolean |  | 是否成功 |
| 2 | errorCode | string |  | 错误编码 |
| 3 | errorMsg | string |  | 错误信息 |
| 4 | data | string |  | 返回数据 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": "修改成功"
}
```


