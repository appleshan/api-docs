section: tolis
id: tolis-report
description: To LIS 检验报告单接口说明
icon: icon-book
filter: tolis-report
---

# To LIS 检验报告单

## 接收检验结果信息与PDF报告
- 请求地址：/v3/api/tolis/report/success/commit
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | orgId | bigint(19) | 是 | 检测机构ID |
| 3 | appId | bigint(19) | 是 | 系统ID |
| 4 | data | string | | |
| 5 | testingForm | string | | 检验结果信息 |
| 6 | reportTemplateId   | bigint(19)    | 是 | 报告单模板编码 |
| 7 | barcode              | varchar(15)   | 是 | 条码号 |
| 8 | sequenceNum         | varchar(15)   | 否 | 样本号 |
| 9 | treatmentTypeName  | varchar(30)   | 否 | 就诊类型，例如：门诊、住院、体检 |
| 10 | subjectNo           | varchar(30)   | 否 | 病人ID编号，唯一标识病人 |
| 11 | subjectName         | varchar(30)   | 是 | 姓名 |
| 12 | sexName             | varchar(6)    | 是 | 性别，值：男、女、未知 |
| 13 | age                  | varchar(17)   | 是 | 年龄，例如：1岁3月 |
| 14 | sampleTypeName     | varchar(150)  | 否 | 标本类型，例如：尿液、粪便 |
| 15 | sampleStateName    | varchar(50)   | 否 | 样本状态，例如：正常、轻度溶血 |
| 16 | clinicalRemark      | varchar(400)  | 否 | 临床诊断 |
| 17 | objectives           | varchar(170)  | 否 | 检查目的 |
| 18 | requestDoctorName  | varchar(10)   | 否 | 申请医生 |
| 19 | requestDeptName    | varchar(30)   | 否 | 开单科室 |
| 20 | collectTime         | datetime      | 否 | 采集时间，格式：YYYY-MM-DD HH:MM:SS |
| 21 | takeTime            | datetime      | 否 | 接收时间,格式：YYYY-MM-DD HH:MM:SS |
| 22 | testByName         | varchar(10)   | 是 | 检验医师 |
| 23 | testTime            | datetime      | 是 | 检验时间，格式：YYYY-MM-DD HH:MM:SS |
| 24 | releaseByName      | varchar(10)   | 是 | 初审医师 |
| 25 | releaseTime         | datetime      | 是 | 初审时间,格式：YYYY-MM-DD HH:MM:SS |
| 26 | auditedByName      | varchar(10)   | 是 | 审核医师 |
| 27 | auditedTime         | datetime      | 是 | 审核时间,格式：YYYY-MM-DD HH:MM:SS |
| 28 | reportEvaluation    | varchar(250)  | 否 | 报告评价 |
| 29 | reportRemark        | varchar(250)  | 否 | 建议解释 |
| 30 | itemNames           | varchar(2000) | 否 | 开单项目列表，例：血常规五分类+血型鉴定 |
| 31 | mdr                  | int(11)       | 否 | 多重耐药，值：0—无，1—多重耐药。 |
| 32 | testingStatus       | int(11)       | 否 | 订单状态字段 |
| 33 | reportKey           | varchar(45)   | 是 | 外送报告key，标识报告单唯一性 |
| 34 | testingAdditions     | {}  | 否 | 附加信息组 |
| 35 | idCard              | varchar(32) | 否 | id卡号码 |
| 36 | height               | varchar(15) | 否 | 身高，例如：170cm |
| 37 | weight               | varchar(15) | 否 | 体重，例如：73kg |
| 38 | collectionSite      | varchar(45) | 否 | 采集部位，例如：伤口切面 |
| 39 | urineVolume24h     | varchar(15) | 否 | 24小时尿量，例：120ml |
| 40 | pregnant             | varchar(15) | 否 | B超孕日，例：5天 |
| 41 | bultrasonic          | varchar(15) | 否 | B超孕周，例：4周 |
| 42 | lmpPregnant         | varchar(15) | 否 | LMP孕日，例：5天 |
| 43 | lmpBultrasonic      | varchar(15) | 否 | LMP孕周，例：4周 |
| 44 | babyCount           | tinyint(4)  | 否 | 怀孕胎数，胎儿数量，一般 1，2 . |
| 45 | seminalVolume       | varchar(15) | 否 | 精浆量，例：23ml |
| 46 | requestNo           | varchar(15) | 否 | 医嘱号 |
| 47 | inpatientAreaName  | varchar(30) | 否 | 病区名称 |
| 48 | bedNum              | varchar(15) | 否 | 床号 |
| 49 | timesInt            | int(11)     | 否 | 就诊次数 |
| 50 | requestTime         | datetime    | 否 | 申请时间，格式：YYYY-MM-DD HH:MM:SS |
| 51 | notifyTime          | datetime    | 否 | 送检时间，格式：YYYY-MM-DD HH:MM:SS |
| 52 | arrivalTime         | datetime    | 否 | 送达时间，格式：YYYY-MM-DD HH:MM:SS |
| 53 | subjectPhone        | varchar(24) | 否 | 病人电话 |
| 54 | subjectCompanyName | varchar(30) | 否 | 病人单位名称 |
| 55 | batchNo             | varchar(15) | 否 | 体检批号代码 |
| 56 | costClasses         | int(11)     | 否  | 费用类别，值：0—正常，1—免费 |
| 57 | diabetes             | varchar(25) | 否 | 糖尿病史 |
| 58 | smokingHistory      | varchar(25) | 否 | 吸烟史 |
| 59 | lmpDate             | varchar(25) | 否 | 末次月经，格式：YYYY-MM-DD |
| 60 | testingGroups     | []  |  | 检验组合项目组 |
| 61 | testItemCode       | bigint(19)  | 是 | 检验项目代码，例：A001 |
| 62 | testItemName     | varchar(55) | 是  | 检验项目名称，例：血型鉴定 |
| 63 | testEnShortName | varchar(30) | 否 | 英文简称，例：ABO |
| 64 | displayOrder      | int(11)     | 否 | 顺序号 |
| 65 | testingLines     | []  |  | 检验单项项目组 |
| 66 | testItemCode       | bigint(19)    | 是 | 报告项目代码，例：GELT000001 |
| 67 | testItemName     | varchar(55)   | 是  | 报告项目名称，例：ABO血型 |
| 68 | testEnShortName | varchar(30)   | 否 | 英文简称，例：ABO |
| 69 | resultValue       | varchar(150)  | 是 | 结果内容 |
| 70 | resultComment     | varchar(1000) | 是 | 结果备注 |
| 71 | unit               | varchar(30)   | 否 | 单位 |
| 72 | lowhighFlagName  | varchar(10)   | 否 | 高低标志。 |
| 73 | refDesc           | varchar(320)  | 否 | 参考范围，例：0.0-10.0 |
| 74 | engRefRemark     | varchar(150)  | 否 | 英文参考值备注  |
| 75 | displayOrder      | int(11)       | 否 | 打印次序  |
| 76 | isReport          | int(11)       | 否 | 是否显示在报告单上，值：0-不显示，1-显示 |
| 77 | sampleTypeName   | varchar(30)   | 否 | 标本类型 |
| 78 | testMethodName   | varchar(30)   | 否 | 检验方法名称 |
| 79 | resultClassify    | int(11)       | 否 | 结果分类，值：1—阴性(-)，2—阳性(+) |
| 80 | testingOrganisms     | []  |  | 细菌组 |
| 81 | organismName          | varchar(50) | 是  | 细菌名称 |
| 82 | organismEnShortName | varchar(30) | 否 | 英文简称 |
| 83 | displayOrder          | int(11)     | 否 | 顺序号 |
| 84 | tips                   | varchar(30) | 否 | 提示 |
| 85 | quantityComment       | varchar(45) | 否 | 落菌计算 |
| 86 | mdr                    | int(11)     | 否 | 多重耐药值：0-否，1-多重耐药。 |
| 87 | testingAntibiotics     | []  |  | 抗生素组 |
| 88 | antibioticName          | varchar(50) | 是  | 抗生素名称 |
| 89 | antiboiticEnShortName | varchar(30) | 否 | 英文简称 |
| 90 | displayOrder            | int(11)     | 否 | 顺序号 |
| 91 | zoneS                   | varchar(12) | 否 | Zone敏感参考值 |
| 92 | zoneM                   | varchar(12) | 否 | Zone中介参考值 |
| 93 | zoneR                   | varchar(12) | 否 | Zone耐药参考值 |
| 94 | zoneValue               | varchar(12) | 否 | Zone结果值 |
| 95 | zoneResult              | varchar(10) | 否 | Zone结果，值：敏感、耐药、中介 |
| 96 | micS                    | varchar(12) | 否 | MIC敏感参考值 |
| 97 | micM                    | varchar(12) | 否 | MIC中介参考值 |
| 98 | micR                    | varchar(12) | 否 | MIC耐药参考值 |
| 99 | micValue                | varchar(12) | 否 | Mic结果值 |
| 100 | micResult               | varchar(10) | 否 | Mic结果，值：敏感、耐药、中介 |
| 101 | micMethod               | int(11)     | 否 | 微生物检验方法，值：1—MIC方法，2-KB方法。 |
| 102 | reportFile | string | | 如果检测机构无法提供PDF报告，则为空。 |
| 103 | barcode         | varchar(15)  | 是 | 条码号 |
| 104 | reportKey | varchar(45) | 是 | 外送报告key |
| 105 | landscape       | int(11)      | 否  | 打印方向，值：0—纵向，1—横向. |
| 106 | paperSize      | int(11)      | 否  | 纸张类型，值：0—A5，1—A4，2—A3 |
| 107 | pageCount      | int(11)      | 否  | 报告单页数 |
| 108 | file       | varchar(15000) | 是 | 报告单文件的base64文本 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "testingForm": {
            "barcode": "",
            "sequenceNum": "",
            "treatmentTypeName": "",
            "subjectNo": "",
            "subjectName": "",
            "sexName": "",
            "age": "",
            "sampleTypeName": "",
            "sampleStateName": "",
            "clinicalRemark": "",
            "objectives": "",
            "requestDoctorName": "",
            "requestDeptName": "",
            "collectTime": "",
            "takeTime": "",
            "testByName": "",
            "testTime": "",
            "releaseByName": "",
            "releaseTime": "",
            "auditedByName": "",
            "auditedTime": "",
            "reportEvaluation": "",
            "reportRemark": "",
            "itemNames": "",
            "mdr": "",
            "testingStatus": "",
            "reportKey": "",
            "reportTemplateId": "",
            "testingAdditions": {
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
                "requestNo": "",
                "inpatientAreaName": "",
                "bedNum": "",
                "timesInt": "",
                "requestTime": "",
                "notifyTime": "",
                "arrivalTime": "",
                "subjectPhone": "",
                "subjectCompanyName": "",
                "batchNo": "",
                "costClasses": "",
                "diabetes": "",
                "smokingHistory": "",
                "lmpDate": ""
            },
            "testingGroups": [{
                "testItemCode": "",
                "testItemName": "",
                "testEnShortName": "",
                "displayOrder": "",
                "testingLines": [{
                    "testItemCode": "",
                    "testItemName": "",
                    "testEnShortName": "",
                    "resultValue": "",
                    "resultComment": "",
                    "unit": "",
                    "lowhighFlagName": "",
                    "refDesc": "",
                    "engRefRemark": "",
                    "displayOrder": "",
                    "isReport": "",
                    "sampleTypeName": "",
                    "testMethodName": "",
                    "resultClassify": "",
                    "testingOrganisms": [{
                        "organismName": "",
                        "organismEnShortName": "",
                        "displayOrder": "",
                        "tips": "",
                        "quantityComment": "",
                        "mdr": "",
                        "testingAntibiotics": [{
                            "antibioticName": "",
                            "antiboiticEnShortName": "",
                            "displayOrder": "",
                            "zoneS": "",
                            "zoneM": "",
                            "zoneR": "",
                            "zoneValue": "",
                            "zoneResult": "",
                            "micS": "",
                            "micM": "",
                            "micR": "",
                            "micValue": "",
                            "micResult": "",
                            "micMethod": ""
                        }]
                    }]
                }]
            }]
        },
        "reportFile": {
            "barcode": "",
            "reportKey": "",
            "landscape": "",
            "paperSize": "",
            "pageCount": "",
            "file": ""
        }
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
    "data": "保存成功"
}
```


## 接收检验结果信息
- 请求地址：/v3/api/tolis/report/success/commit/testing_form
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | orgId | bigint(19) | 是 | 检测机构ID |
| 3 | appId | bigint(19) | 是 | 系统ID |
| 4 | data | string | | |
| 5 | reportTemplateId   | bigint(19)    | 是 | 报告单模板编码 |
| 6 | barcode              | varchar(15)   | 是 | 条码号 |
| 7 | sequenceNum         | varchar(15)   | 否 | 样本号 |
| 8 | treatmentTypeName  | varchar(30)   | 否 | 就诊类型，例如：门诊、住院、体检 |
| 9 | subjectNo           | varchar(30)   | 否 | 病人ID编号，唯一标识病人 |
| 10 | subjectName         | varchar(30)   | 是 | 姓名 |
| 11 | sexName             | varchar(6)    | 是 | 性别，值：男、女、未知 |
| 12 | age                  | varchar(17)   | 是 | 年龄，例如：1岁3月 |
| 13 | sampleTypeName     | varchar(150)  | 否 | 标本类型，例如：尿液、粪便 |
| 14 | sampleStateName    | varchar(50)   | 否 | 样本状态，例如：正常、轻度溶血 |
| 15 | clinicalRemark      | varchar(400)  | 否 | 临床诊断 |
| 16 | objectives           | varchar(170)  | 否 | 检查目的 |
| 17 | requestDoctorName  | varchar(10)   | 否 | 申请医生 |
| 18 | requestDeptName    | varchar(30)   | 否 | 开单科室 |
| 19 | collectTime         | datetime      | 否 | 采集时间，格式：YYYY-MM-DD HH:MM:SS |
| 20 | takeTime            | datetime      | 否 | 接收时间,格式：YYYY-MM-DD HH:MM:SS |
| 21 | testByName         | varchar(10)   | 是 | 检验医师 |
| 22 | testTime            | datetime      | 是 | 检验时间，格式：YYYY-MM-DD HH:MM:SS |
| 23 | releaseByName      | varchar(10)   | 是 | 初审医师 |
| 24 | releaseTime         | datetime      | 是 | 初审时间,格式：YYYY-MM-DD HH:MM:SS |
| 25 | auditedByName      | varchar(10)   | 是 | 审核医师 |
| 26 | auditedTime         | datetime      | 是 | 审核时间,格式：YYYY-MM-DD HH:MM:SS |
| 27 | reportEvaluation    | varchar(250)  | 否 | 报告评价 |
| 28 | reportRemark        | varchar(250)  | 否 | 建议解释 |
| 29 | itemNames           | varchar(2000) | 否 | 开单项目列表，例：血常规五分类+血型鉴定 |
| 30 | mdr                  | int(11)       | 否 | 多重耐药，值：0—无，1—多重耐药。 |
| 31 | testingStatus       | int(11)       | 否 | 订单状态字段 |
| 32 | reportKey           | varchar(45)   | 是 | 外送报告key，标识报告单唯一性 |
| 33 | testingAdditions     | {}  | 否 | 附加信息组 |
| 34 | idCard              | varchar(32) | 否 | id卡号码 |
| 35 | height               | varchar(15) | 否 | 身高，例如：170cm |
| 36 | weight               | varchar(15) | 否 | 体重，例如：73kg |
| 37 | collectionSite      | varchar(45) | 否 | 采集部位，例如：伤口切面 |
| 38 | urineVolume24h     | varchar(15) | 否 | 24小时尿量，例：120ml |
| 39 | pregnant             | varchar(15) | 否 | B超孕日，例：5天 |
| 40 | bultrasonic          | varchar(15) | 否 | B超孕周，例：4周 |
| 41 | lmpPregnant         | varchar(15) | 否 | LMP孕日，例：5天 |
| 42 | lmpBultrasonic      | varchar(15) | 否 | LMP孕周，例：4周 |
| 43 | babyCount           | tinyint(4)  | 否 | 怀孕胎数，胎儿数量，一般 1，2 . |
| 44 | seminalVolume       | varchar(15) | 否 | 精浆量，例：23ml |
| 45 | requestNo           | varchar(15) | 否 | 医嘱号 |
| 46 | inpatientAreaName  | varchar(30) | 否 | 病区名称 |
| 47 | bedNum              | varchar(15) | 否 | 床号 |
| 48 | timesInt            | int(11)     | 否 | 就诊次数 |
| 49 | requestTime         | datetime    | 否 | 申请时间，格式：YYYY-MM-DD HH:MM:SS |
| 50 | notifyTime          | datetime    | 否 | 送检时间，格式：YYYY-MM-DD HH:MM:SS |
| 51 | arrivalTime         | datetime    | 否 | 送达时间，格式：YYYY-MM-DD HH:MM:SS |
| 52 | subjectPhone        | varchar(24) | 否 | 病人电话 |
| 53 | subjectCompanyName | varchar(30) | 否 | 病人单位名称 |
| 54 | batchNo             | varchar(15) | 否 | 体检批号代码 |
| 55 | costClasses         | int(11)     | 否  | 费用类别，值：0—正常，1—免费 |
| 56 | diabetes             | varchar(25) | 否 | 糖尿病史 |
| 57 | smokingHistory      | varchar(25) | 否 | 吸烟史 |
| 58 | lmpDate             | varchar(25) | 否 | 末次月经，格式：YYYY-MM-DD |
| 59 | testingGroups     | []  |  | 检验组合项目组 |
| 60 | testItemCode       | bigint(19)  | 是 | 检验项目代码，例：A001 |
| 61 | testItemName     | varchar(55) | 是  | 检验项目名称，例：血型鉴定 |
| 62 | testEnShortName | varchar(30) | 否 | 英文简称，例：ABO |
| 63 | displayOrder      | int(11)     | 否 | 顺序号 |
| 64 | testingLines     | []  |  | 检验单项项目组 |
| 65 | testItemCode       | bigint(19)    | 是 | 报告项目代码，例：GELT000001 |
| 66 | testItemName     | varchar(55)   | 是  | 报告项目名称，例：ABO血型 |
| 67 | testEnShortName | varchar(30)   | 否 | 英文简称，例：ABO |
| 68 | resultValue       | varchar(150)  | 是 | 结果内容 |
| 69 | resultComment     | varchar(1000) | 是 | 结果备注 |
| 70 | unit               | varchar(30)   | 否 | 单位 |
| 71 | lowhighFlagName  | varchar(10)   | 否 | 高低标志。 |
| 72 | refDesc           | varchar(320)  | 否 | 参考范围，例：0.0-10.0 |
| 73 | engRefRemark     | varchar(150)  | 否 | 英文参考值备注  |
| 74 | displayOrder      | int(11)       | 否 | 打印次序  |
| 75 | isReport          | int(11)       | 否 | 是否显示在报告单上，值：0-不显示，1-显示 |
| 76 | sampleTypeName   | varchar(30)   | 否 | 标本类型 |
| 77 | testMethodName   | varchar(30)   | 否 | 检验方法名称 |
| 78 | resultClassify    | int(11)       | 否 | 结果分类，值：1—阴性(-)，2—阳性(+) |
| 79 | testingOrganisms     | []  |  | 细菌组 |
| 80 | organismName          | varchar(50) | 是  | 细菌名称 |
| 81 | organismEnShortName | varchar(30) | 否 | 英文简称 |
| 82 | displayOrder          | int(11)     | 否 | 顺序号 |
| 83 | tips                   | varchar(30) | 否 | 提示 |
| 84 | quantityComment       | varchar(45) | 否 | 落菌计算 |
| 85 | mdr                    | int(11)     | 否 | 多重耐药值：0-否，1-多重耐药。 |
| 86 | testingAntibiotics     | []  |  | 抗生素组 |
| 87 | antibioticName          | varchar(50) | 是  | 抗生素名称 |
| 88 | antiboiticEnShortName | varchar(30) | 否 | 英文简称 |
| 89 | displayOrder            | int(11)     | 否 | 顺序号 |
| 90 | zoneS                   | varchar(12) | 否 | Zone敏感参考值 |
| 91 | zoneM                   | varchar(12) | 否 | Zone中介参考值 |
| 92 | zoneR                   | varchar(12) | 否 | Zone耐药参考值 |
| 93 | zoneValue               | varchar(12) | 否 | Zone结果值 |
| 94 | zoneResult              | varchar(10) | 否 | Zone结果，值：敏感、耐药、中介 |
| 95 | micS                    | varchar(12) | 否 | MIC敏感参考值 |
| 96 | micM                    | varchar(12) | 否 | MIC中介参考值 |
| 97 | micR                    | varchar(12) | 否 | MIC耐药参考值 |
| 98 | micValue                | varchar(12) | 否 | Mic结果值 |
| 99 | micResult               | varchar(10) | 否 | Mic结果，值：敏感、耐药、中介 |
| 100 | micMethod               | int(11)     | 否 | 微生物检验方法，值：1—MIC方法，2-KB方法。 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "barcode": "",
        "sequenceNum": "",
        "treatmentTypeName": "",
        "subjectNo": "",
        "subjectName": "",
        "sexName": "",
        "age": "",
        "sampleTypeName": "",
        "sampleStateName": "",
        "clinicalRemark": "",
        "objectives": "",
        "requestDoctorName": "",
        "requestDeptName": "",
        "collectTime": "",
        "takeTime": "",
        "testByName": "",
        "testTime": "",
        "releaseByName": "",
        "releaseTime": "",
        "auditedByName": "",
        "auditedTime": "",
        "reportEvaluation": "",
        "reportRemark": "",
        "itemNames": "",
        "mdr": "",
        "testingStatus": "",
        "reportKey": "",
        "reportTemplateId": "",
        "testingAdditions": {
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
            "requestNo": "",
            "inpatientAreaName": "",
            "bedNum": "",
            "timesInt": "",
            "requestTime": "",
            "notifyTime": "",
            "arrivalTime": "",
            "subjectPhone": "",
            "subjectCompanyName": "",
            "batchNo": "",
            "costClasses": "",
            "diabetes": "",
            "smokingHistory": "",
            "lmpDate": ""
        },
        "testingGroups": [{
            "testItemCode": "",
            "testItemName": "",
            "testEnShortName": "",
            "displayOrder": "",
            "testingLines": [{
                "testItemCode": "",
                "testItemName": "",
                "testEnShortName": "",
                "resultValue": "",
                "resultComment": "",
                "unit": "",
                "lowhighFlagName": "",
                "refDesc": "",
                "engRefRemark": "",
                "displayOrder": "",
                "isReport": "",
                "sampleTypeName": "",
                "testMethodName": "",
                "resultClassify": "",
                "testingOrganisms": [{
                    "organismName": "",
                    "organismEnShortName": "",
                    "displayOrder": "",
                    "tips": "",
                    "quantityComment": "",
                    "mdr": "",
                    "testingAntibiotics": [{
                        "antibioticName": "",
                        "antiboiticEnShortName": "",
                        "displayOrder": "",
                        "zoneS": "",
                        "zoneM": "",
                        "zoneR": "",
                        "zoneValue": "",
                        "zoneResult": "",
                        "micS": "",
                        "micM": "",
                        "micR": "",
                        "micValue": "",
                        "micResult": "",
                        "micMethod": ""
                    }]
                }]
            }]
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
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": "保存成功"
}
```

- 处理逻辑：


## 接收检验结果的PDF报告
- 请求地址：/v3/api/tolis/report/success/commit/report_pdf
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | orgId | bigint(19) | 是 | 检测机构ID |
| 3 | appId | bigint(19) | 是 | 系统ID |
| 4 | data | string | | |
| 5 | barcode         | varchar(15)  | 是 | 条码号 |
| 6 | reportKey | varchar(45) | 是 | 外送报告key |
| 7 | landscape       | int(11)      | 否  | 打印方向，值：0—纵向，1—横向. |
| 8 | paperSize      | int(11)      | 否  | 纸张类型，值：0—A5，1—A4，2—A3 |
| 9 | pageCount      | int(11)      | 否  | 报告单页数 |
| 10 | file       | varchar(15000) | 是 | 报告单文件的base64文本 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "barcode": "",
        "reportKey": "",
        "landscape": "",
        "paperSize": "",
        "pageCount": "",
        "file": ""
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
    "data": "保存成功"
}
```

- 处理逻辑：

