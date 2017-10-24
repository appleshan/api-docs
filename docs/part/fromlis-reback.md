section: fromlis
id: fromlis-reback
description: From LIS 退单报告单接口说明
icon: icon-book
filter: fromlis-reback
---

# From LIS 退单报告单

## 提供退单报告列表(已退单)
- 请求地址：/v3/api/fromlis/report/reback/list
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | token | daan_api_token |  |  | head参数 |
| 2 | 机构id | orgId | bigint(19) | 是 | 机构关键字对应orgs.id |
| 3 | 系统id | appId | bigint(19) | 是 | 功能点、菜单对应那个系统，对应applications.id |
| 4 | 提交数据 | data | string |  |  |  |

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
| 1 | 是否成功 | success | boolean |  |  |
| 2 | 错误编码 | errorCode | string |  |  |
| 3 | 错误信息 | errorMsg | string |  |  |
| 4 | 返回数据 | data | string |  |  |
| 5 | 机构id | orgId | bigint(19) | 是 | 送检机构id |
| 6 | 系统id | appId | bigint(19) | 是 | 系统id |
| 7 | 条码号 | barcode | varchar(15) | 否 | [条码号]—标本对应的条码号 |
| 8 | 就诊类型ID | treatmentTypeId | bigint(19) | 否 | [就诊类型ID] |
| 9 | 就诊类型名称 | treatmentTypeName | varchar(30) | 否 | [就诊类型名称]—就诊类型名称 |
| 10 | 受检者编号 | subjectNo | varchar(30) | 否 | [受检者编号]—病人所使用的那类id的编号，可以放诊疗卡号，门诊号，体检号。 |
| 11 | 病人ID类型 | subjectNoType | varchar(12) | 否 | [病人ID类型]—病人编号类型：诊疗卡号，门诊号，住院号,体检号 |
| 12 | 姓名 | subjectName | varchar(30) | 是 | [姓名]—受检人姓名 |
| 13 | 性别名称 | sexName | varchar(6) | 是 | [性别名称]—性别名称：男、女、未知 |
| 14 | 性别id | sexId | int(11) | 是 | [性别id]—男、女、未知。用于计算参考值及控制哪些项目可以录入到此标本中。1—男2—女3—未知 |
| 15 | 年龄 | age | varchar(17) | 是 | [年龄]—年龄说明，用于在界面上显示的年龄。格式如：1岁2月 |
| 16 | 计算年龄 | caculatedAge | int(11) | 是 | [计算年龄]—计算年龄，以小时为单位。将受检人的年龄转换为小时，用于后面业务计算参考值。 |
| 17 | 标本类型id | sampleTypeId | bigint(19) | 否 | [标本类型id] |
| 18 | 标本类型名称 | sampleTypeName | varchar(150) | 否 | [标本类型名称] |
| 19 | 临床诊断 | clinicalRemark | varchar(400) | 否 | [临床诊断]—医生给的临床诊断描述。 |
| 20 | 检查目的 | objectives | varchar(170) | 否 | [检查目的]—医生填的标本检查目的. |
| 21 | 申请医生id | doctorId | bigint(19) | 否 | [申请医生id]—医院开单医生ID |
| 22 | 申请医生名称 | doctorName | varchar(10) | 否 | [申请医生名称]—医院开单医生名称 |
| 23 | 开单科室id | deptId | bigint(19) | 否 | [开单科室id]—医院开单科室ID |
| 24 | 开单科室名称 | deptName | varchar(30) | 否 | [开单科室名称]—医院开单科室名称，例：不孕不育科 |
| 25 | 开单项目列表 | itemNames | varchar(2000) | 否 | [开单项目列表]，例子：血常规五分类,肝功四项,乙型肝炎检查定性,血脂四项 |
| 26 | 检查类型 | testType | int(11) | 否 | [检查类型]—检验类型标志，0—常规，1—急诊 |
| 27 | 标本备注 | remark | varchar(250) | 否 | [标本备注]—前处理的标本备注。 |
| 28 | 医嘱备注 | requestRemark | varchar(250) | 否 | [医嘱备注]—医生开单时填写的医嘱备注。 |
| 29 | 申请时间 | requestTime | datetime | 否 | [申请时间]—医嘱申请时间。 |
| 30 | 病区id | inpatientAreaId | bigint(19) | 否 | [病区id] |
| 31 | 病区名称 | inpatientAreaName | varchar(30) | 否 | [病区名称] |
| 32 | 床号 | bedNum | varchar(15) | 否 | [床号]—受检人是住院病人，病人的床号。 |
| 33 | 就诊次数 | timesInt | int(11) | 否 | [就诊次数]—就诊次数 |
| 34 | 单位代码 | subjectCompanyCode | varchar(15) | 否 | [单位代码]—受检人工作单位编码,有HIS传递过来或体检传递过来的code |
| 35 | 单位名称 | subjectCompanyName | varchar(30) | 否 | [单位名称]—受检人工作单位名称 |
| 36 | 费用类别 | costClasses | int(11) | 否 | [费用类别]—标志位：0—正常,1—免费 |
| 37 | 体检批号代码 | batchNo | varchar(15) | 否 | [体检批号代码]—体检批号：A01010011 |
| 38 | 采集时间 | collectTime | datetime | 否 | [采集时间]—标本的采集时间 |
| 39 | 接收时间 | takeTime | datetime | 否 | [接收时间]—标本接收时间. |
| 40 | 来源机构 | fromOrgId | bigint(19) | 否 | [来源机构]—标本来源的单位，来源单位有两种，一是自己医院的标本，一是外送进来的标本。 |
| 41 | 来源机构名称 | fromOrgName | varchar(35) | 否 | [来源机构名称]—标本来源机构名称，对应form_org_id的名称. |
| 42 | 标本来源申请单id | fromRequestId | bigint(19) | 否 | [标本来源申请单id]—平台内调度的标本需要记录下内部申请单id，以便结果回传。 |
| 43 | 外送单位id | toOrgId | bigint(19) | 否 | [外送单位id]—外送单位id,标本需要在调度过程前预先算出的外送单位。 |
| 44 | 外送机构名称 | toOrgName | varchar(35) | 否 | [外送机构名称]—外送机构名称对应to_org_id的名称。 |
| 45 | 外送机构条码 | toOrgBarcode | varchar(15) | 否 | [外送机构条码]—按照外送机构的系统格式的条码。可以预制也可以是系统生成。 |
| 46 | 录入时间 | inputTime | datetime | 否 | [录入时间]—验单录入时间 |
| 47 | 录入者id | inputBy | bigint(19) | 否 | [录入者id]—录入人id，对应users.id |
| 48 | 录入者名称 | inputByName | varchar(10) | 否 | [录入者名称]—标本录入人名称，对应users.name |
| 49 | 试管类型id | tubeTypeId | bigint(19) | 否 | [试管类型id]—试管类型id |
| 50 | 试管类型名称 | tubeTypeName | varchar(30) | 否 | [试管类型名称]—显示的试管类型名称 |
| 51 | 单据类型 | orderType | int(11) | 是 | [单据类型]—0—前处理申请单,1—手工外送单,2—外送单,4—送检单,6—不经前处理申请单。 |
| 52 | 分发人id | distributeBy | bigint(19) | 否 | [分发人id]—分发人id对应users.id |
| 53 | 分发人名称 | distributeName | varchar(10) | 否 | [分发人名称]—分发人名称。 |
| 54 | 分发时间 | distributeTime | datetime | 否 | [分发时间]—标本分发时间. |
| 55 | 提交标志 | submitFlag | int(11) | 否 | [提交标志]—标本提交标志位，0—未提交，1—已提交。 |
| 56 | 是否已扫描 | scanFlag | int(11) | 否 | [是否已扫描]—标志位，标记是否已经被扫描。0—未扫描,1—已扫描. |
| 57 | 送检日期 | submissionDate | datetime | 否 | [送检日期]—标本外送检验的日期，用于查询及主条件过滤。 |
| 58 | 执行条码 | execBarcode | varchar(15) | 否 | [执行条码]—标本使用的条码，由于前处理与外送的条码不一致。最终通过读这个字段来决定使用的条码。 |
| 59 | 界面流程配置id | uiWorkflowId | int(11) | 否 | [界面流程配置id]—标志位用于标示就诊类型的数据走那些流程,标志位的值如下：1—住院,2—门诊,3—体检。 |
| 60 | 扫描人id | scanBy | bigint(19) | 否 | [扫描人id]—扫描人id，对应users.id |
| 61 | 提交人id | submissionBy | bigint(19) | 否 | [提交人id]—提交人，对应users.id |
| 62 | 标本项目总数 | itemCount | int(11) | 否 | [标本项目总数]—标本检验项目总数，增加项目、删除项目要更新此字段。 |
| 63 | 样本状态id | sampleStateId | bigint(19) | 否 | [样本状态id]—样本状态id，表示标本溶血、止血等信息对应dict_codes.id |
| 64 | 样本状态名称 | sampleStateName | varchar(50) | 否 | [样本状态名称]—样本状态名称，对应dict_codes.name例：轻度溶血，末梢血（稀释法） |
| 65 | 出生日期 | birthday | datetime | 否 | [出生日期]—生日 |
| 66 | 提交时间 | releaseTime | datetime | 否 | [提交时间]—检验医师对标本的提交时间。 |
| 67 | 审核时间 | auditedTime | datetime | 否 | [审核时间]—审核时间 |
| 68 | 检验时间 | testTime | datetime | 否 | [检验时间]—标本的检验时间 |
| 69 | 接收者 | takeBy | bigint(19) | 否 | [接收者]—接收者id，对应users.id |
| 70 | 接收者名称 | takeByName | varchar(10) | 否 | [接收者名称]—标本接收人名称，对应users.name |
| 71 | 物流人员工号 | submittedByCode | varchar(25) | 否 | [物流人员工号]—标本对应的物流人员的工号. |
| 72 | 区域中心id | areaOrgId | bigint(19) | 否 | [区域中心id]—对应区域中心的id,对应ctr_orgs.id，org_type_id=3 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": [{
        "appId": "",
        "orgId": "",
        "barcode": "",
        "treatmentTypeId": "",
        "treatmentTypeName": "",
        "subjectNo": "",
        "subjectNoType": "",
        "subjectName": "",
        "sexName": "",
        "sexId": "",
        "age": "",
        "caculatedAge": "",
        "sampleTypeId": "",
        "sampleTypeName": "",
        "clinicalRemark": "",
        "objectives": "",
        "doctorId": "",
        "doctorName": "",
        "deptId": "",
        "deptName": "",
        "itemNames": "",
        "testType": "",
        "remark": "",
        "requestRemark": "",
        "requestTime": "",
        "inpatientAreaId": "",
        "inpatientAreaName": "",
        "bedNum": "",
        "timesInt": "",
        "subjectCompanyCode": "",
        "subjectCompanyName": "",
        "batchNo": "",
        "collectTime": "",
        "takeTime": "",
        "fromOrgId": "",
        "fromOrgName": "",
        "fromRequestId": "",
        "toOrgId": "",
        "toOrgName": "",
        "toOrgBarcode": "",
        "inputTime": "",
        "inputBy": "",
        "inputByName": "",
        "tubeTypeId": "",
        "tubeTypeName": "",
        "orderType": "",
        "distributeBy": "",
        "distributeName": "",
        "distributeTime": "",
        "submitFlag": "",
        "scanFlag": "",
        "submissionDate": "",
        "execBarcode": "",
        "uiWorkflowId": "",
        "scanBy": "",
        "submissionBy": "",
        "itemCount": "",
        "sampleStateId": "",
        "sampleStateName": "",
        "birthday": "",
        "releaseTime": "",
        "auditedTime": "",
        "testTime": "",
        "takeBy": "",
        "takeByName": "",
        "submittedByCode": "",
        "areaOrgId": ""
    }]
}
```


## 提供单个退单报告明细
- 请求地址：/v3/api/fromlis/report/reback/detail
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | token | daan_api_token |  |  | head参数 |
| 2 | 机构id | orgId | bigint(19) | 是 | 送检机构id |
| 3 | 系统id | appId | bigint(19) | 是 | 系统id |
| 4 | 提交数据 | data | string |  |  |  |

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
| 1 | 是否成功 | success | boolean |  |  |
| 2 | 错误编码 | errorCode | string |  |  |
| 3 | 错误信息 | errorMsg | string |  |  |
| 4 | 返回数据 | data | string |  |  |
| 5 | 条码号 | barcode | varchar(15) | 否 | [条码号]—标本对应的条码号 |
| 6 | 就诊类型ID | treatmentTypeId | bigint(19) | 否 | [就诊类型ID] |
| 7 | 就诊类型名称 | treatmentTypeName | varchar(30) | 否 | [就诊类型名称]—就诊类型名称 |
| 8 | 受检者编号 | subjectNo | varchar(30) | 否 | [受检者编号]—病人所使用的那类id的编号，可以放诊疗卡号，门诊号，体检号。 |
| 9 | 病人ID类型 | subjectNoType | varchar(12) | 否 | [病人ID类型]—病人编号类型：诊疗卡号，门诊号，住院号,体检号 |
| 10 | 姓名 | subjectName | varchar(30) | 是 | [姓名]—受检人姓名 |
| 11 | 性别名称 | sexName | varchar(6) | 是 | [性别名称]—性别名称：男、女、未知 |
| 12 | 性别id | sexId | int(11) | 是 | [性别id]—男、女、未知。用于计算参考值及控制哪些项目可以录入到此标本中。1—男2—女3—未知 |
| 13 | 年龄 | age | varchar(17) | 是 | [年龄]—年龄说明，用于在界面上显示的年龄。格式如：1岁2月 |
| 14 | 计算年龄 | caculatedAge | int(11) | 是 | [计算年龄]—计算年龄，以小时为单位。将受检人的年龄转换为小时，用于后面业务计算参考值。 |
| 15 | 标本类型id | sampleTypeId | bigint(19) | 否 | [标本类型id]—采集标本类型id对应dict_codes.id |
| 16 | 标本类型名称 | sampleTypeName | varchar(150) | 否 | [标本类型名称]—采集的标本类型名称，对应dict_codes.name |
| 17 | 临床诊断 | clinicalRemark | varchar(400) | 否 | [临床诊断]—医生给的临床诊断描述。 |
| 18 | 检查目的 | objectives | varchar(170) | 否 | [检查目的]—医生填的标本检查目的. |
| 19 | 申请医生id | doctorId | bigint(19) | 否 | [申请医生id]—医院开单医生ID |
| 20 | 申请医生名称 | doctorName | varchar(10) | 否 | [申请医生名称]—医院开单医生名称 |
| 21 | 开单科室id | deptId | bigint(19) | 否 | [开单科室id]—医院开单科室ID |
| 22 | 开单科室名称 | deptName | varchar(30) | 否 | [开单科室名称]—医院开单科室名称，例：不孕不育科 |
| 23 | 开单项目列表 | itemNames | varchar(2000) | 否 | [开单项目列表] 例子：血常规五分类,肝功四项,乙型肝炎检查定性,血脂四项 |
| 24 | 检查类型 | testType | int(11) | 否 | [检查类型]—检验类型标志，0—常规，1—急诊 |
| 25 | 标本备注 | remark | varchar(250) | 否 | [标本备注]—前处理的标本备注。 |
| 26 | 医嘱备注 | requestRemark | varchar(250) | 否 | [医嘱备注]—医生开单时填写的医嘱备注。 |
| 27 | 申请时间 | requestTime | datetime | 否 | [申请时间]—医嘱申请时间。 |
| 28 | 病区id | inpatientAreaId | bigint(19) | 否 | [病区id]—受检者所属病区id,关联inpatient_area.id |
| 29 | 病区名称 | inpatientAreaName | varchar(30) | 否 | [病区名称]—病区名称对应inpatient_area.name |
| 30 | 床号 | bedNum | varchar(15) | 否 | [床号]—受检人是住院病人，病人的床号。 |
| 31 | 就诊次数 | timesInt | int(11) | 否 | [就诊次数]—就诊次数 |
| 32 | 单位代码 | subjectCompanyCode | varchar(15) | 否 | [单位代码]—受检人工作单位编码,有HIS传递过来或体检传递过来的code |
| 33 | 单位名称 | subjectCompanyName | varchar(30) | 否 | [单位名称]—受检人工作单位名称 |
| 34 | 费用类别 | costClasses | int(11) | 否 | [费用类别]—标志位：0—正常,1—免费 |
| 35 | 体检批号代码 | batchNo | varchar(15) | 否 | [体检批号代码]—体检批号：A01010011 |
| 36 | 采集时间 | collectTime | datetime | 否 | [采集时间]—标本的采集时间 |
| 37 | 接收时间 | takeTime | datetime | 否 | [接收时间]—标本接收时间. |
| 38 | 来源机构 | fromOrgId | bigint(19) | 否 | [来源机构]—标本来源的单位，来源单位有两种，一是自己医院的标本，一是外送进来的标本。 |
| 39 | 来源机构名称 | fromOrgName | varchar(35) | 否 | [来源机构名称]—标本来源机构名称，对应form_org_id的名称. |
| 40 | 标本来源申请单id | fromRequestId | bigint(19) | 否 | [标本来源申请单id]—平台内调度的标本需要记录下内部申请单id，以便结果回传。 |
| 41 | 外送单位id | toOrgId | bigint(19) | 否 | [外送单位id]—外送单位id,标本需要在调度过程前预先算出的外送单位。 |
| 42 | 外送机构名称 | toOrgName | varchar(35) | 否 | [外送机构名称]—外送机构名称对应to_org_id的名称。 |
| 43 | 外送机构条码 | toOrgBarcode | varchar(15) | 否 | [外送机构条码]—按照外送机构的系统格式的条码。可以预制也可以是系统生成。 |
| 44 | 录入时间 | inputTime | datetime | 否 | [录入时间]—验单录入时间 |
| 45 | 录入者id | inputBy | bigint(19) | 否 | [录入者id]—录入人id，对应users.id |
| 46 | 录入者名称 | inputByName | varchar(10) | 否 | [录入者名称]—标本录入人名称，对应users.name |
| 47 | 试管类型id | tubeTypeId | bigint(19) | 否 | [试管类型id]—试管类型id |
| 48 | 试管类型名称 | tubeTypeName | varchar(30) | 否 | [试管类型名称]—显示的试管类型名称 |
| 49 | 单据类型 | orderType | int(11) | 是 | [单据类型]—0—前处理申请单,1—手工外送单,2—外送单,4—送检单,6—不经前处理申请单。 |
| 50 | 分发人id | distributeBy | bigint(19) | 否 | [分发人id]—分发人id对应users.id |
| 51 | 分发人名称 | distributeName | varchar(10) | 否 | [分发人名称]—分发人名称。 |
| 52 | 分发时间 | distributeTime | datetime | 否 | [分发时间]—标本分发时间. |
| 53 | 提交标志 | submitFlag | int(11) | 否 | [提交标志]—标本提交标志位，0—未提交，1—已提交。 |
| 54 | 是否已扫描 | scanFlag | int(11) | 否 | [是否已扫描]—标志位，标记是否已经被扫描。0—未扫描,1—已扫描. |
| 55 | 送检日期 | submissionDate | datetime | 否 | [送检日期]—标本外送检验的日期，用于查询及主条件过滤。 |
| 56 | 执行条码 | execBarcode | varchar(15) | 否 | [执行条码]—标本使用的条码，由于前处理与外送的条码不一致。最终通过读这个字段来决定使用的条码。 |
| 57 | 界面流程配置id | uiWorkflowId | int(11) | 否 | [界面流程配置id]—标志位用于标示就诊类型的数据走那些流程,标志位的值如下：1—住院,2—门诊,3—体检。 |
| 58 | 扫描人id | scanBy | bigint(19) | 否 | [扫描人id]—扫描人id，对应users.id |
| 59 | 提交人id | submissionBy | bigint(19) | 否 | [提交人id]—提交人，对应users.id |
| 60 | 标本项目总数 | itemCount | int(11) | 否 | [标本项目总数]—标本检验项目总数，增加项目、删除项目要更新此字段。 |
| 61 | 样本状态id | sampleStateId | bigint(19) | 否 | [样本状态id]—样本状态id，表示标本溶血、止血等信息对应dict_codes.id |
| 62 | 样本状态名称 | sampleStateName | varchar(50) | 否 | [样本状态名称]—样本状态名称，对应dict_codes.name例：轻度溶血，末梢血（稀释法） |
| 63 | 出生日期 | birthday | datetime | 否 | [出生日期]—生日 |
| 64 | 提交时间 | releaseTime | datetime | 否 | [提交时间]—检验医师对标本的提交时间。 |
| 65 | 审核时间 | auditedTime | datetime | 否 | [审核时间]—审核时间 |
| 66 | 检验时间 | testTime | datetime | 否 | [检验时间]—标本的检验时间 |
| 67 | 接收者 | takeBy | bigint(19) | 否 | [接收者]—接收者id，对应users.id |
| 68 | 接收者名称 | takeByName | varchar(10) | 否 | [接收者名称]—标本接收人名称，对应users.name |
| 69 | 物流人员工号 | submittedByCode | varchar(25) | 否 | [物流人员工号]—标本对应的物流人员的工号. |
| 70 | 区域中心id | areaOrgId | bigint(19) | 否 | [区域中心id]—对应区域中心的id,对应ctr_orgs.id，org_type_id=3 |
| 71 | 附加信息 | requestAdditions | {} | 否 | [附加信息] |
| 72 | 联系电话 | subjectPhone | varchar(24) | 否 | [联系电话]—受检人联系电话 |
| 73 | 糖尿病史 | diabetes | varchar(25) | 否 | [糖尿病史]—糖尿病史描述。 |
| 74 | 吸烟史 | smokingHistory | varchar(25) | 否 | [吸烟史]—吸烟史描述 |
| 75 | id卡号码 | idCard | varchar(32) | 否 | [id卡号码]—身份证号码，军人证，医保、社保号 |
| 76 | 体重 | weight | varchar(15) | 否 | [体重]—受检者体重(包含单位) |
| 77 | 身高 | height | varchar(15) | 否 | [身高]—受检者身高(包含单位) |
| 78 | 采集部位 | collectionSite | varchar(45) | 否 | [采集部位]—标本采样的部位描述 |
| 79 | B超孕周 | bultrasonic | varchar(15) | 否 | [B超孕周]—B超孕周(包含单位). |
| 80 | 24小时尿量 | urineVolume24h | varchar(15) | 否 | [24小时尿量]—24小时尿量(包含单位). |
| 81 | B超孕日 | pregnant | varchar(15) | 否 | [B超孕日]—B超孕日(包含单位). |
| 82 | LMP孕日 | lmpPregnant | varchar(15) | 否 | [LMP孕日]—LMP孕日(包含单位). |
| 83 | LMP孕周 | lmpBultrasonic | varchar(15) | 否 | [LMP孕周]—LMP孕周(包含单位). |
| 84 | 怀孕胎数 | babyCount | tinyint(4) | 否 | [怀孕胎数]—胎儿数量，一般1，2. |
| 85 | 精浆量 | seminalVolume | varchar(15) | 否 | [精浆量]—精浆量(包含单位). |
| 86 | 医嘱号 | requestNo | varchar(15) | 否 | [医嘱号]—医生开的医嘱号,从his获取的医嘱号。 |
| 87 | 末次月经 | lmpDate | varchar(25) | 否 | [末次月经]—文本内容。 |
| 88 | 是否社区报告 | isBbsReport | int(11) | 否 | [是否社区报告]--标志位复查标本，0ornull--否,1--是 |
| 89 | 是否复查 | isRecheck | int(11) | 否 | [是否复查]--是否是复查标本,0ornull--否,1--是 |
| 90 | 复查条码 | recheckBarcode | varchar(15) | 否 | [复查条码]--复查条码号 |
| 91 | 报告语言 | reportLang | int(11) | 否 | [报告语言]--标志为：null--中文报告,2--英文报告,3--中英文报告,中文报告为默认选项不需要设置 |
| 92 | 头臀径 | crl | varchar(12) | 否 | [头臀径]--单位mm |
| 93 | 双顶径 | bpd | varchar(12) | 否 | [双顶径]--单位mm |
| 94 | 颈项透明层厚度 | nt | varchar(12) | 否 | [颈项透明层厚度]--单位mm |
| 95 | 鼻骨 | nasalBone | varchar(12) | 否 | [鼻骨]--单位mm |
| 96 | 鼻骨状态 | nasalBoneState | int(11) | 否 | [鼻骨状态]--状态位:0ornull--缺失,1--可见 |
| 97 | 植入日期 | imbedDate | datetime | 否 | [植入日期]--日期内容 |
| 98 | 取卵日期 | eggRetrievalDate | datetime | 否 | [取卵日期]--日期内容 |
| 99 | 胰岛素依赖性糖尿病 | isIddm | int(11) | 否 | [胰岛素依赖性糖尿病]--标志为：0ornull--否,1--是 |
| 100 | 是否吸烟 | isSmoke | int(11) | 否 | [是否吸烟]--标志为:0--否,1--是,2--孕前戒,3--孕期戒 |
| 101 | 种族 | race | int(11) | 否 | [种族]--标志位0--黄种人,1--afro-caribbean,2--Asian,3--Caucasian,4--oriental,5--其他 |
| 102 | 种族名字 | raceName | varchar(25) | 否 | [种族名字]--种族为其他时的种族名称 |
| 103 | 受孕方式 | pregnantWay | int(11) | 否 | [受孕方式]--标志位:0--自然,1--克罗米芬2,--试验婴儿IVF,3-ICSI,4--增卵,5--供精,6--其他 |
| 104 | 其他受孕方式 | otherPregnantWay | varchar(25) | 否 | [其他受孕方式]-其他受孕方式名称 |
| 105 | 异常妊娠史 | exceptionPregnancy | int(11) | 否 | [异常妊娠史]--标志位:0--无,1--21三体,2--18三体,3--13三体,4,--神经管畸形,5--其他 |
| 106 | 其他异常妊娠史 | otherExceptionPregnancy | varchar(25) | 否 | [其他异常妊娠史]--其他异常妊娠史的内容 |
| 107 | 是否输血 | isTransfusion | int(11) | 否 | [是否输血]--标志位:0--否,1--是 |
| 108 | 是否有过移植手术 | isTransplantSurgery | int(11) | 否 | [是否有过移植手术]--标志位0--否,1--是 |
| 109 | 是否有过干细胞治疗 | stemCellTherapy | int(11) | 否 | [是否有过干细胞治疗]--标志位0--否,1--是 |
| 110 | 免疫治疗 | immuneTherapy | int(11) | 否 | [免疫治疗]--标志位0--否,1--是 |
| 111 | 集中送检医院 | centralizedHosp | varchar(35) | 否 | [集中送检医院]--无创集中送检医院 |
| 112 | 采样医院 | collectHosp | varchar(35) | 否 | [采样医院]--无创标本采样医院 |
| 113 | 体位 | bodyStyle | varchar(25) | 否 | [体位]--体位内容：立位、卧位... |
| 114 | 是否试管婴儿 | ivf | int(11) | 否 | [是否试管婴儿]—是否试管婴儿标志位0—否，1—是 |
| 115 | 恶性肿瘤未治愈或治愈未满一年 | cureCancer1 | int(11) | 否 | [恶性肿瘤未治愈或治愈未满一年]—标志位0—否,1—是 |
| 116 | 医生电话 | doctorPhone | varchar(25) | 否 | [医生电话]--医生电话内容 |
| 117 | B超检查日期 | bultrasonicDate | datetime | 否 | [B超检查日期]—B超检查日期 |
| 118 | 末次月经日期 | lastLmpDate | datetime | 否 | [末次月经日期]--末次月经日期(格式：yyyy-mm-dd) |
| 119 | 采血日期 | samplingDay | datetime | 否 | [采血日期]--采血日期(格式：yyyy-mm-dd) |
| 120 | 本次妊娠 | pregnancy | int(11) | 否 | [本次妊娠]--本次妊娠(1-单胎、2-双胎) |
| 121 | 超声检查日期 | examinationDay | datetime | 否 | [超声检查日期]--超声检查日期(格式：yyyy-mm-dd) |
| 122 | 超声检查 | examinationResultChild | int(11) | 否 | [超声检查]--超声检查(1-单胎、2-双胎) |
| 123 | 当日超声结果提示周 | examinationResultWeek | int(11) | 否 | [当日超声结果提示周]--当日超声结果提示周(正整数) |
| 124 | 当日超声结果提示天 | examinationResultDay | int(11) | 否 | [当日超声结果提示天]--当日超声结果提示天(正整数) |
| 125 | 检验项目组 | requestGroups | [] | 否 | [检验项目组] |
| 126 | 申请单 | requestFormId | bigint(19) | 是 | [申请单]—d对应request_forms.id |
| 127 | 检验项目id | testItemId | bigint(19) | 是 | [检验项目id]—项目id关联test_items.id |
| 128 | 英文简称 | testEnShortName | varchar(30) | 否 | [英文简称]，例：FRUC |
| 129 | 检验项目名称 | testItemName | varchar(55) | 是 | [检验项目名称]，例：血清果糖胺测定（糖化血清蛋白测定）(FRUC) |
| 130 | 顺序号 | displayOrder | int(11) | 否 | [顺序号]—显示的顺序号，用于排序显示。 |
| 131 | 对接HIS的医嘱号记录id | medicalOrderId | bigint(19) | 否 | [对接HIS的医嘱号记录id]—对应medical_orders.id |
| 132 | 价格 | price | decimal(10,2) | 否 | [价格]—项目价格 |
| 133 | 检验项目明细 | requestLines | [] | 否 | [检验项目明细] |
| 134 | 仪器工单对应的检验项目id | testingLineId | bigint(19) | 否 | [仪器工单对应的检验项目id]—关联testing_lines.id |
| 135 | 检验单id | requestFormId | bigint(19) | 是 | [检验单id]—d对应test_orders表的id |
| 136 | 检验项目名称 | testItemName | varchar(55) | 是 | [检验项目名称]，例：血清果糖胺测定（糖化血清蛋白测定）(FRUC) |
| 137 | 检验项目id | testItemId | bigint(19) | 是 | [检验项目id]—项目id关联testitems.id |
| 138 | 英文简称 | testEnShortName | varchar(30) | 否 | [英文简称]，例：FRUC |
| 139 | 开单项目id | testGroupId | bigint(19) | 否 | [开单项目id]—检验项目所属于哪个开单项目，对应testing_groups.test_item_id |
| 140 | 开单项目名称 | testGroupName | varchar(30) | 否 | [开单项目名称]—当前检验项目对应哪个开单项目。 |
| 141 | 顺序号 | displayOrder | int(11) | 否 | [顺序号]—细菌或抗生素显示的顺序号，用于排序显示。 |
| 142 | 检验方法id | testMethodId | bigint(19) | 否 | [检验方法id]—关联：dict_codes.id,对应基础字典表的dict_codes.type_key=2 |
| 143 | 检验方法名称 | testMethodName | varchar(30) | 否 | [检验方法名称]—项目对应的检验方法名称 |
| 144 | 标本类型id | sampleTypeId | bigint(19) | 否 | [标本类型id]—对应dictcodes.id |
| 145 | 标本类型名称 | sampleTypeName | varchar(30) | 否 | [标本类型名称] |
| 146 | 报告名称 | reportName | varchar(55) | 否 | [报告名称]—项目在报告上显示的名称. |
| 147 | 流水号 | sequenceNum | varchar(15) | 否 | [流水号]—样本准备的流水号,上机的流水号。 |
| 148 | 结果内容 | resultValue | varchar(150) | 否 | [结果内容]—项目的结果内容. |
| 149 | 结果备注 | resultComment | varchar(1000) | 否 | [结果备注]—结果备注,规则公式计算出的结果及仪器传输回来的结果备注（唐筛仪器） |
| 150 | 单位 | unit | varchar(30) | 否 | [单位]—项目单位例：μmol/L |
| 151 | 偏高偏低标志说明 | lowhighFlagName | varchar(10) | 否 | [偏高偏低标志说明]—记录偏高偏低标志位的说明内容。 |
| 152 | 参考值描述 | refDesc | varchar(320) | 否 | [参考值描述]-通过参考高低值及参考值方法计算出来如：[0.0-10.0] |
| 153 | 英文参考值备注 | engRefRemark | varchar(150) | 否 | [英文参考值备注] |
| 154 | 是否显示在报告单上 | isReport | int(11) | 否 | [是否显示在报告单上]—0或者null不显示,1显示在报告单上。 |
| 155 | 结果分类 | resultClassify | int(11) | 否 | [结果分类]—微生物的结果分类内容：1—阴性(-),2—阳性(+)。 |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": {
        "barcode": "",
        "treatmentTypeId": "",
        "treatmentTypeName": "",
        "subjectNo": "",
        "subjectNoType": "",
        "subjectName": "",
        "sexName": "",
        "sexId": "",
        "age": "",
        "caculatedAge": "",
        "sampleTypeId": "",
        "sampleTypeName": "",
        "clinicalRemark": "",
        "objectives": "",
        "doctorId": "",
        "doctorName": "",
        "deptId": "",
        "deptName": "",
        "itemNames": "",
        "testType": "",
        "remark": "",
        "requestRemark": "",
        "requestTime": "",
        "inpatientAreaId": "",
        "inpatientAreaName": "",
        "bedNum": "",
        "timesInt": "",
        "subjectCompanyCode": "",
        "subjectCompanyName": "",
        "costClasses": "",
        "batchNo": "",
        "collectTime": "",
        "takeTime": "",
        "fromOrgId": "",
        "fromOrgName": "",
        "fromRequestId": "",
        "toOrgId": "",
        "toOrgName": "",
        "toOrgBarcode": "",
        "inputTime": "",
        "inputBy": "",
        "inputByName": "",
        "tubeTypeId": "",
        "tubeTypeName": "",
        "orderType": "",
        "distributeBy": "",
        "distributeName": "",
        "distributeTime": "",
        "submitFlag": "",
        "scanFlag": "",
        "submissionDate": "",
        "execBarcode": "",
        "uiWorkflowId": "",
        "scanBy": "",
        "submissionBy": "",
        "itemCount": "",
        "sampleStateId": "",
        "sampleStateName": "",
        "birthday": "",
        "releaseTime": "",
        "auditedTime": "",
        "testTime": "",
        "takeBy": "",
        "takeByName": "",
        "submittedByCode": "",
        "areaOrgId": "",
        "requestAdditions": {
            "subjectPhone": "",
            "diabetes": "",
            "smokingHistory": "",
            "idCard": "",
            "weight": "",
            "height": "",
            "collectionSite": "",
            "bultrasonic": "",
            "urineVolume24h": "",
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
            "reportLang": "",
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
            "ivf": "",
            "cureCancer1": "",
            "doctorPhone": "",
            "bultrasonicDate": "",
            "lastLmpDate": "",
            "samplingDay": "",
            "pregnancy": "",
            "examinationDay": "",
            "examinationResultChild": "",
            "examinationResultWeek": "",
            "examinationResultDay": ""
        },
        "requestGroups": [{
            "requestFormId": "",
            "testItemId": "",
            "testEnShortName": "",
            "testItemName": "",
            "displayOrder": "",
            "medicalOrderId": "",
            "price": "",
            "requestLines": [{
                "testingLineId": "",
                "requestFormId": "",
                "testItemName": "",
                "testItemId": "",
                "testEnShortName": "",
                "testGroupId": "",
                "testGroupName": "",
                "displayOrder": "",
                "testMethodId": "",
                "testMethodName": "",
                "sampleTypeId": "",
                "sampleTypeName": "",
                "reportName": "",
                "sequenceNum": "",
                "resultValue": "",
                "resultComment": "",
                "unit": "",
                "lowhighFlagName": "",
                "refDesc": "",
                "engRefRemark": "",
                "isReport": "",
                "resultClassify": ""
            }]
        }]
    }
}
```


## 接收退单报告获取成功的通知
- 请求地址：/v3/api/fromlis/report/reback/success
- 请求方法：post
- 请求参数：

| 编号 | 字段名称 | 类型与长度 | 是否必须 | 字段说明 |
|:---:|--------|--------|:------:|---------|
| 1 | token | daan_api_token |  |  | head参数 |
| 2 | 机构id | orgId | bigint(19) | 是 | 送检机构id |
| 3 | 系统id | appId | bigint(19) | 是 | 系统id |
| 4 | 提交数据 | data | string |  |  |
| 5 | 条码号 | barcode | varchar(15) | 否 | [条码号]—标本对应的条码号 |

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
| 1 | 是否成功 | success | boolean |  |  |
| 2 | 错误编码 | errorCode | string |  |  |
| 3 | 错误信息 | errorMsg | string |  |  |
| 4 | 返回数据 | data | string |  |  |  |

样例：
```json
{
    "success": true,
    "errorCode": "",
    "errorMsg": "",
    "data": "修改成功"
}
```

