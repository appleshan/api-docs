section: his
id: his-report
description: HIS 检验报告接口说明
icon: icon-book
filter: his-report
---

# HIS 检验报告

## 提供检验报告列表(根据患者编号)
- 请求地址：/v3/api/his/report/success/listBySubjectNo
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
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 7 | testTime           | datetime      | YES | [检验日期] — 标本检验日期                                                                                             |
| 8 | instrumentId       | bigint(19)    | NO  | [仪器id]  —  在那台仪器上检验。对应instruments.id                                                                        |
| 9 | instrumentTypeId  | int(11)       | NO  | [仪器分类] — 标记仪器属于种类别的仪器, 0 — 常规仪器, 1— 微生物仪器 , 2—文字描述，3— 酶标。此字段决定仪器读那些表。                                       |
| 10 | testType           | int(11)       | YES | [检查类型]— 检验类型标志，0—常规，1— 急诊                                                                                   |
| 11 | barcode             | varchar(15)   | YES | [条码号] — 标本对应的条码号                                                                                            |
| 12 | treatmentTypeId   | bigint(19)    | YES | [就诊类型ID] — 部门关联就诊ID，当获取标本时就可以知道该病人的就诊类型, 对应 dict_codes.id的“就诊类型”的分类                                         |
| 13 | treatmentTypeName | varchar(30)   | YES | [就诊类型名称] — 就诊类型名称                                                                                           |
| 14 | subjectNo          | varchar(30)   | YES | [受检者编号]— 病人所使用的那类id的编号，可以放诊疗卡号，门诊号，体检号。                                                                     |
| 15 | subjectNoType     | varchar(12)   | YES | [病人类型] —  病人编号类型：诊疗卡号，门诊号，住院号, 体检号                                                                          |
| 16 | subjectName        | varchar(30)   | YES | [姓名] — 受检人姓名                                                                                                |
| 17 | sexId              | int(11)       | YES | [性别id ] — 男、女、未知。用于计算参考值及控制哪些项目可以录入到此标本中。1— 男;2— 女;3— 未知                                                    |
| 18 | sexName            | varchar(6)    | YES | [性别名称] —  性别名称： 男、女、未知                                                                                      |
| 19 | age                 | varchar(17)   | YES | [年龄] — 年龄说明，用于在界面上显示的年龄。 格式如： 1岁2月                                                                          |
| 20 | birthday            | datetime      | YES | [出生日期]                                                                                                      |
| 21 | sampleTypeId      | bigint(19)    | YES | [标本类型id] — 标本类型id 对应dict_codes.id                                                                           |
| 22 | sampleTypeName    | varchar(150)  | YES | [标本类型名称] — 标本类型名称， 对应 dict_codes.name                                                                       |
| 23 | clinicalRemark     | varchar(400)  | YES | [临床诊断] — 医生给的临床诊断描述。                                                                                        |
| 24 | objectives          | varchar(170)  | YES | [检查目的] — 医生填的标本检查目的.                                                                                        |
| 25 | requestDoctorId   | bigint(19)    | YES | [申请医生id] — 医院开单医生ID， 对应doctors.id                                                                           |
| 26 | requestDoctorName | varchar(10)   | YES | [申请医生名称] — 医院开单医生名称，对应doctors.name                                                                          |
| 27 | requestDeptId     | bigint(19)    | YES | [开单科室id] — 医院开单科室ID ，对应hosp_departments.id                                                                  |
| 28 | requestDeptName   | varchar(30)   | YES | [开单科室名称] — 医院开单科室名称对应hosp_departments.name ，例： 不孕不育科                                                        |
| 29 | releaseBy          | bigint(19)    | YES | [标本的提交人], 对应user.id                                                                                          |
| 30 | releaseByName     | varchar(10)   | YES | [提交人的名称]。users.name                                                                                           |
| 31 | releaseTime        | datetime      | YES | [提交时间] — 检验医师对标本的提交时间。                                                                                      |
| 32 | auditedBy          | bigint(19)    | YES | [审核医师id] — 标本审核人id， 对应user.id                                                                               |
| 33 | auditedByName     | varchar(10)   | YES | [审核医师名称]— 审核人名称。 对应users.name                                                                               |
| 34 | auditedTime        | datetime      | YES | [审核时间]— 审核时间                                                                                                |
| 35 | reportEvaluation   | varchar(250)  | YES | [报告评价] —  显示在报告评价栏的描述。                                                                                      |
| 36 | reportRemark       | varchar(250)  | YES | [建议解释] — 标本的建议解释描述。                                                                                         |
| 37 | itemNames          | varchar(2000) | YES | [开单项目列表] — 用于冗余开单项目字符串，在界面显示时不需再访问数据库。检验项目描述 ， 例子： 血常规五分类 + 肝功四项 + 乙型肝炎检查定性 + 血脂四项                          |
| 38 | hasAddition        | int(11)       | NO  | [是否有附加信息] — 是否有附加信息标志位，有则需在业务使用中读取附加信息表的内容。 0— 无， 1— 有。                                                     |
| 39 | inputBy            | bigint(19)    | YES | [录入者id] — 录入人id ，对应users.id                                                                                 |
| 40 | inputTime          | datetime      | YES | [录入时间] — 验单录入时间                                                                                             |
| 41 | inputByName       | varchar(10)   | YES | [录入者名称] — 标本录入人名称， 对应users.name                                                                             |
| 42 | reportId           | bigint(19)    | YES | [报告单id] — 仪器工单对应的报告单，对应 report_pdfs.id                                                                      |
| 43 | createTime         | datetime      | NO  | [创建时间] — 在insert的时候记录创建时间，用于表分区。                                                                            |
| 44 | timeVersion        | timestamp     | NO  | [时间版本] — 时间版本，当新增、修改都需要把当前服务器时间写入次字段，用于同步数据用。                                                              |
| 45 | fromOrgId         | bigint(19)    | YES | [来源机构] — 标本来源的单位，来源单位有两种， 一是自己医院的标本（如果是非内部lis转过来的标本来源机构也是自己）， 一是外送进来的标本可以查dispatch_orgs 中的机构单位查出那家机构送进来的标本。 |
| 46 | fromOrgName       | varchar(35)   | YES | [来源机构名称] — 标本来源机构名称，对应form_org_id的名称.                                                                       |
| 47 | fromOrgAddress    | varchar(35)   | YES | [送检机构地址] — 实验室、机构的地址。                                                                                       |
| 48 | testBy             | bigint(19)    | YES | [检验医师id] — 检验人id对应user.id                                                                                   |
| 49 | testByName        | varchar(10)   | YES | [检验医师名称] — 检验人名称。                                                                                           |
| 50 | requestTime        | datetime      | YES | [申请时间] — 医嘱申请时间。                                                                                            |
| 51 | reportTitle        | varchar(120)  | YES | [报告抬头] — 报告抬头内容                                                                                             |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": [{
        "orgId": "864819130673397760",
        "appId": "2",
        "testTime": "2017-08-11 14:13:33",
        "instrumentId": "895474187953770496",
        "instrumentTypeId": 0,
        "testType": 0,
        "barcode": "36",
        "treatmentTypeId": "871561705443037184",
        "treatmentTypeName": "体检",
        "subjectNo": "9170501322",
        "subjectNoType": "体检号",
        "subjectName": "陈浩",
        "sexId": 1,
        "sexName": "男",
        "age": "29岁",
        "sampleTypeId": "738646604084547586",
        "sampleTypeName": "氟化钠抗凝血浆",
        "requestDoctorId": "895467392665391104",
        "requestDoctorName": "谢帮国",
        "requestDeptId": "871562182083743744",
        "requestDeptName": "健康管理科A区",
        "releaseBy": "864819957483962368",
        "releaseByName": "管理员",
        "releaseTime": "2017-08-11 14:13:33",
        "auditedBy": "864819957483962368",
        "auditedByName": "管理员",
        "auditedTime": "2017-08-11 14:18:43",
        "itemNames": "血葡萄糖测定(Glu),血清丙氨酸氨基转移酶测定(ALT)",
        "hasAddition": 1,
        "inputBy": "864819957483962368",
        "inputTime": "2017-08-11 14:13:50",
        "inputByName": "管理员",
        "reportId": "895892229932531712",
        "createTime": "2017-08-11 14:14:26",
        "timeVersion": "2017-08-11 14:19:23",
        "fromOrgId": "864819130673397760",
        "fromOrgName": "蕉岭第二人民医院",
        "testBy": "864819957483962368",
        "testByName": "管理员",
        "requestTime": "2017-08-11 10:43:23"
    }]
}
```


## 提供单个检验报告明细(根据患者编号)
- 请求地址：/v3/api/his/report/success/detail_by_subject_no
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 4 | data | string | | 提交数据 |
| 5 | treatmentTypeName | varchar(30) | 是 | 就诊类型 |
| 6 | subjectNo | varchar(30) | 是 | 受检者编号 |
| 7 | isConverted | int(1) | 是 | 项目对照标志位，值：0-不需要对照项目，1-需要对照项目 |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "treatmentTypeName": "",
        "subjectNo": "",
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
| 5 | requestFormId      | bigint(19)    | 否 | [检验单id] — 仪器工单对应那张检验单，对应request_forms.id                                           |
| 6 | testTime            | datetime      | 否 | [检验日期] — 标本检验日期                                                                    |
| 7 | barcode              | varchar(15)   | 否 | [条码号] — 标本对应的条码号                                                                   |
| 8 | sequenceNum         | varchar(15)   | 否 | [流水号] — 样本准备的流水号, 上机的流水号。                                                          |
| 9 | treatmentTypeName  | varchar(30)   | 否 | [就诊类型名称] — 就诊类型名称                                                                  |
| 10 | subjectNo           | varchar(30)   | 否 | [受检者编号]— 病人所使用的那类id的编号，可以放诊疗卡号，门诊号，体检号。                                            |
| 11 | subjectName         | varchar(30)   | 否 | [姓名] — 受检人姓名                                                                       |
| 12 | sexName             | varchar(6)    | 否 | [性别名称] —  性别名称： 男、女、未知                                                             |
| 13 | age                  | varchar(17)   | 否 | [年龄] — 年龄说明，用于在界面上显示的年龄。 格式如： 1岁2月                                                 |
| 14 | sampleTypeName     | varchar(150)  | 否 | [标本类型名称] — 标本类型名称， 对应 dict_codes.name                                              |
| 15 | sampleStateName    | varchar(50)   | 否 | [样本状态名称] — 样本状态名称， 对应dict_codes.name例：轻度溶血，末梢血（稀释法）                                |
| 16 | clinicalRemark      | varchar(400)  | 否 | [临床诊断] — 医生给的临床诊断描述。                                                               |
| 17 | objectives           | varchar(170)  | 否 | [检查目的] — 医生填的标本检查目的.                                                               |
| 18 | requestDoctorName  | varchar(10)   | 否 | [申请医生名称] — 医院开单医生名称，对应doctors.name                                                 |
| 19 | requestDeptName    | varchar(30)   | 否 | [开单科室名称] — 医院开单科室名称对应hosp_departments.name ，例： 不孕不育科                               |
| 20 | collectTime         | datetime      | 否 | [采集时间] — 标本的采集时间                                                                   |
| 21 | takeTime            | datetime      | 否 | [接收时间] —  标本接收时间.                                                                  |
| 22 | releaseByName      | varchar(10)   | 否 | [检验医师名称]  — 提交人的名称。users.name                                                      |
| 23 | releaseTime         | datetime      | 否 | [提交时间] — 检验医师对标本的提交时间。                                                             |
| 24 | auditedByName      | varchar(10)   | 否 | [审核医师名称]— 审核人名称。 对应users.name                                                      |
| 25 | auditedTime         | datetime      | 否 | [审核时间]— 审核时间                                                                       |
| 26 | labGroupId         | bigint(19)    | 否 | [检验科室id] — 检验科室id  , 对应lab_groups.id                                               |
| 27 | reportEvaluation    | varchar(250)  | 否 | [报告评价] —  显示在报告评价栏的描述。                                                             |
| 28 | reportRemark        | varchar(250)  | 否 | [建议解释] — 标本的建议解释描述。                                                                |
| 29 | itemNames           | varchar(2000) | 否 | [开单项目列表] — 用于冗余开单项目字符串，在界面显示时不需再访问数据库。检验项目描述 ， 例子： 血常规五分类 + 肝功四项 + 乙型肝炎检查定性 + 血脂四项 |
| 30 | hasAddition         | int(11)       | 是  | [是否有附加信息] — 是否有附加信息标志位，有则需在业务使用中读取附加信息表的内容。 0— 无， 1— 有。                            |
| 31 | inputByName        | varchar(10)   | 否 | [录入者名称] — 标本录入人名称， 对应users.name                                                    |
| 32 | mdr                  | int(11)       | 否 | [多重耐药] — 多重耐药标记 0 or null — 无，1 —多重耐药。                                             |
| 33 | reportId            | bigint(19)    | 否 | [报告单id] — 仪器工单对应的报告单，对应 report_pdfs.id                                             |
| 34 | testByName         | varchar(10)   | 否 | [检验人名称] — 检验人名称。                                                                   |
| 35 | testingAdditions     | {}  | 否 | [附加信息] |
| 36 | idCard              | varchar(32) | 否 | [id卡号码] — 身份证号码，军人证，医保、社保号               |
| 37 | height               | varchar(15) | 否 | [身高] — 受检者身高(包含单位)                       |
| 38 | weight               | varchar(15) | 否 | [体重] —  受检者体重(包含单位)                      |
| 39 | collectionSite      | varchar(45) | 否 | [采集部位] — 标本采样的部位描述                       |
| 40 | urineVolume24h     | varchar(15) | 否 | [24小时尿量] — 24小时尿量(包含单位).                 |
| 41 | pregnant             | varchar(15) | 否 | [B超孕日] — B超孕日(包含单位).                     |
| 42 | bultrasonic          | varchar(15) | 否 | [B超孕周] — B超孕周(包含单位).                     |
| 43 | lmpPregnant         | varchar(15) | 否 | [LMP孕日] — LMP孕日(包含单位).                   |
| 44 | lmpBultrasonic      | varchar(15) | 否 | [LMP孕周] — LMP孕周(包含单位).                   |
| 45 | babyCount           | tinyint(4)  | 否 | [怀孕胎数] — 胎儿数量，一般 1，2 .                   |
| 46 | seminalVolume       | varchar(15) | 否 | [精浆量] — 精浆量(包含单位).                       |
| 47 | requestNo           | varchar(15) | 否 | [医嘱号] — 医生开的医嘱号,从his获取的医嘱号。              |
| 48 | inpatientAreaId    | bigint(19)  | 否 | [病区id] — 受检者所属病区id , 关联inpatient_area.id |
| 49 | inpatientAreaName  | varchar(30) | 否 | [病区名称] —  病区名称对应inpatient_area.name      |
| 50 | bedNum              | varchar(15) | 否 | [床号] — 受检人是住院病人，病人的床号。                   |
| 51 | timesInt            | int(11)     | 否 | [就诊次数] — 就诊次数                            |
| 52 | requestTime         | datetime    | 否 | [申请时间] — 验单申请日期                          |
| 53 | notifyTime          | datetime    | 否 | [送检时间] — 标本送检时间。                         |
| 54 | arrivalTime         | datetime    | 否 | [送达时间] — 配置人员送达时间，用于存医院内调度送达的时间。         |
| 55 | subjectPhone        | varchar(24) | 否 | [联系电话] — 受检人联系电话                         |
| 56 | subjectCompanyCode | varchar(15) | 否 | [单位代码] — 受检人工作单位编码 ,有HIS传递过来或体检传递过来的code |
| 57 | subjectCompanyName | varchar(30) | 否 | [单位名称] — 受检人工作单位名称                       |
| 58 | batchNo             | varchar(15) | 否 | [体检批号代码] — 体检批号：A01010011                |
| 59 | costClasses         | int(11)     | 是  | [费用类别] —标志位： 0 — 正常, 1— 免费               |
| 60 | diabetes             | varchar(25) | 否 | [糖尿病史] — 糖尿病史描述。                         |
| 61 | smokingHistory      | varchar(25) | 否 | [吸烟史] — 吸烟史描述                            |
| 62 | lmpDate             | varchar(25) | 否 | [末次月经] — 文本内容。                           |
| 63 | testingGroups     | []  | 否 | [检验项目组] |
| 64 | testingFormId    | bigint(19)  | 是  | [申请单] — d 对应request_forms.id       |
| 65 | testItemId       | bigint(19)  | 否 | [检验项目id] — 项目id关联test_items.id    |
| 66 | testEnShortName | varchar(30) | 否 | [英文简称]， 例： FRUC                      |
| 67 | testItemName     | varchar(55) | 是  | [检验项目名称]， 例： 血清果糖胺测定（糖化血清蛋白测定）(FRUC)
| 68 | displayOrder      | int(11)     | 否 | [顺序号] — 显示的顺序号，用于排序显示。             |
| 69 | testingLines     | []  | 否 | [检验项目明细] |
| 70 | testingFormId    | bigint(19)    | 是  | [仪器工单id]— 关联testing_forms.id                 |
| 71 | testItemId       | bigint(19)    | 否 | [检验项目id] — 项目id关联testitems.id                |
| 72 | testItemName     | varchar(55)   | 是  | [检验项目名称]， 例： 血清果糖胺测定（糖化血清蛋白测定）(FRUC)           |
| 73 | testEnShortName | varchar(30)   | 否 | [英文简称]， 例： FRUC                                |
| 74 | sequenceNum       | varchar(15)   | 否 | [流水号] — 样本准备的流水号, 上机的流水号。                    |
| 75 | resultValue       | varchar(150)  | 否 | [结果内容] — 项目的结果内容.                            |
| 76 | resultComment     | varchar(1000) | 否 | [结果备注] — 结果备注, 规则公式计算出的结果及仪器传输回来的结果备注（唐筛仪器）  |
| 77 | unit               | varchar(30)   | 否 | [单位] — 项目单位 例： μmol/L                        |
| 78 | lowhighFlag  | varchar(10)   | 否 | [偏高偏低标志说明] — 记录偏高偏低标志位的说明内容。                 |
| 79 | refDesc           | varchar(320)  | 否 | [参考值描述] - 通过参考高低值及参考值方法计算出来如： [0.0-10.0]        |
| 80 | engRefRemark     | varchar(150)  | 否 | [英文参考值备注]                                      |
| 81 | displayOrder      | int(11)       | 否 | [报告显示顺序号] — 项目在报告中显示的顺序号, 控制报告中的排序           |
| 82 | isReport          | int(11)       | 否 | [是否显示在报告单上] — 0 或者null 不显示,  1显示在报告单上。       |
| 83 | sampleTypeName   | varchar(30)   | 否 | [标本类型名称]                                       |
| 84 | testingGroupId   | bigint(19)    | 否 | [开单项目id] — 检验项目所属于哪个开单项目，对应testing_groups.id |
| 85 | testingGroupName | varchar(55)   | 否 | [开单项目名称] — 当前检验项目对应哪个开单项目。                   |
| 86 | testMethodName   | varchar(30)   | 否 | [检验方法名称] — 项目对应的检验方法名称                       |
| 87 | resultClassify    | int(11)       | 否 | [结果分类] — 微生物的结果分类内容：1— 阴性(-) , 2 — 阳性(+) 。   |
| 88 | reportName        | varchar(55)   | 否 | [报告名称] — 项目在报告上显示的名称.                        |
| 89 | testingOrganisms     | []  | 否 | [细菌结果] |
| 90 | testingFormId        | bigint(19)  | 是  | [仪器工单id] — 关联testing_forms.id             |
| 91 | testingLineId        | bigint(19)  | 是  | [工单项目id] — 细菌对应哪个工单的项目 对应testing_lines.id |
| 92 | organismId            | bigint(19)  | 否 | [细菌id] — 对应mic_items.id                   |
| 93 | organismName          | varchar(50) | 是  | [中文名称] — 细菌或抗生素的中文名称.                     |
| 94 | organismEnShortName | varchar(30) | 否 | [英文简称] — 细菌或康盛素的英文简称                      |
| 95 | displayOrder          | int(11)     | 否 | [顺序号] — 细菌或抗生素显示的顺序号，用于排序显示。              |
| 96 | tips                   | varchar(30) | 否 | [提示] — 细菌提示                               |
| 97 | quantityComment       | varchar(45) | 否 | [落菌计算] — 细菌落菌计算结果.                        |
| 98 | organismGroupId      | bigint(19)  | 否 | [细菌分组id] — 细菌对应的细菌分组  对应mic_groups.id     |
| 99 | mdr                    | int(11)     | 否 | [多重耐药] — 细菌是否多重耐药标记， 0 — 否， 1 — 多重耐药。     |
| 100 | testingAntibiotics     | []  | 否 | [标本药敏信息] |
| 101 | testingFormId          | bigint(19)  | 是  | [仪器工单id] — 关联testing_forms.id               |
| 102 | testingLineId          | bigint(19)  | 是  | [仪器工单id]，关联work_orders.id                   |
| 103 | testingOrganismId      | bigint(19)  | 是  | [细菌id] — 药敏对应条细菌id 关联 testing_organisms.id  |
| 104 | antibioticGroupId      | bigint(19)  | 否 | [抗生素分组id] — 对应mic_groups.id                 |
| 105 | antibioticId            | bigint(19)  | 否 | [细菌id] — 对应mic_items.id                     |
| 106 | antibioticName          | varchar(50) | 是  | [中文名称] — 细菌或抗生素的中文名称.                       |
| 107 | antiboiticEnShortName | varchar(30) | 否 | [英文简称] — 细菌或康盛素的英文简称                        |
| 108 | displayOrder            | int(11)     | 否 | [顺序号] — 细菌或抗生素显示的顺序号，用于排序显示。                |
| 109 | zoneS                   | varchar(12) | 否 | [Zone敏感参考值] — Zone敏感参考值                     |
| 110 | zoneM                   | varchar(12) | 否 | [Zone中介参考值] — Zone中介参考值                     |
| 111 | zoneR                   | varchar(12) | 否 | [Zone耐药参考值] — Zone耐药参考值                     |
| 112 | zoneValue               | varchar(12) | 否 | [Zone结果值] — Zone结果值                         |
| 113 | zoneResult              | varchar(10) | 否 | [Zone结果] — Zone结果： 敏感、耐药、中介                 |
| 114 | micS                    | varchar(12) | 否 | [MIC敏感参考值] — MIC敏感参考值                       |
| 115 | micM                    | varchar(12) | 否 | [MIC中介参考值] — MIC中介参考值                       |
| 116 | micR                    | varchar(12) | 否 | [MIC耐药参考值] —MIC耐药参考值                        |
| 117 | micValue                | varchar(12) | 否 | [Mic结果值] — Mic结果值                           |
| 118 | micResult               | varchar(10) | 否 | [Mic结果] — Zone结果: 敏感、耐药、中介                  |
| 119 | micMethod               | int(11)     | 否 | [微生物检验方法] — 微生物检验方法标志， 1— mic 方法, 2 — kb方法。 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": {
        "requestFormId": "",
        "testTime": "",
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
        "releaseByName": "",
        "releaseTime": "",
        "auditedByName": "",
        "auditedTime": "",
        "labGroupId": "",
        "reportEvaluation": "",
        "reportRemark": "",
        "itemNames": "",
        "hasAddition": "",
        "inputByName": "",
        "mdr": "",
        "reportId": "",
        "testByName": "",
        "testingAdditions": {
            "idCard": "",
            "height": "",
            "weight": "",
            "collectionSite": "",
            "urineVolume24h": "",
            "pregnant": "",
            "bultrasonic": "",
            "lmpPregnant": "",
            "lmpBultrasonic": "",
            "babyCount": "",
            "seminalVolume": "",
            "requestNo": "",
            "inpatientAreaId": "",
            "inpatientAreaName": "",
            "bedNum": "",
            "timesInt": "",
            "requestTime": "",
            "notifyTime": "",
            "arrivalTime": "",
            "subjectPhone": "",
            "subjectCompanyCode": "",
            "subjectCompanyName": "",
            "batchNo": "",
            "costClasses": "",
            "diabetes": "",
            "smokingHistory": "",
            "lmpDate": ""
        },
        "testingGroups": [{
            "testingFormId": "",
            "testItemId": "",
            "testEnShortName": "",
            "testItemName": "",
            "displayOrder": "",
            "testingLines": [{
                "testingFormId": "",
                "testItemId": "",
                "testItemName": "",
                "testEnShortName": "",
                "sequenceNum": "",
                "resultValue": "",
                "resultComment": "",
                "unit": "",
                "lowhighFlagName": "",
                "refDesc": "",
                "engRefRemark": "",
                "displayOrder": "",
                "isReport": "",
                "sampleTypeName": "",
                "testingGroupId": "",
                "testingGroupName": "",
                "testMethodName": "",
                "resultClassify": "",
                "reportName": "",
                "testingOrganisms": [{
                    "testingFormId": "",
                    "testingLineId": "",
                    "organismId": "",
                    "organismName": "",
                    "organismEnShortName": "",
                    "displayOrder": "",
                    "tips": "",
                    "quantityComment": "",
                    "organismGroupId": "",
                    "mdr": "",
                    "testingAntibiotics": [{
                        "testingFormId": "",
                        "testingLineId": "",
                        "testingOrganismId": "",
                        "antibioticGroupId": "",
                        "antibioticId": "",
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


## 接收检验报告获取成功的通知(根据检验工单id)
- 请求地址：/v3/api/his/report/success/feedback
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | daan_api_token | | | head 参数 |
| 2 | appId | bigint(19) | 是 | 系统id |
| 3 | orgId | bigint(19) | 是 | 机构id |
| 4 | data | string | | 提交数据 |
| 5 | testingFormId | bigint(19) | 是 | 检验工单id |

样例：
```json
{
    "daan_api_token": "",
    "orgId": "",
    "appId": "",
    "data": {
        "testingFormId": ""
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
    "data": "状态更新成功"
}
```

