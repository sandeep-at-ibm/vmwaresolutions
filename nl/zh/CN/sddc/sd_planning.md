---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

# Cloud Foundation 实例的需求和规划

在订购 VMware Cloud Foundation 实例之前，请查看以下需求。根据 {{site.data.keyword.CloudDataCent}} 位置、工作负载容量需求和服务需求来规划实例。

## IBM Cloud 帐户需求

要使用的 {{site.data.keyword.cloud_notm}} 帐户必须满足特定需求。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} 帐户需求](../vmonic/slaccountrequirement.html)。

## IBM Cloud Data Center 可用性

Cloud Foundation 部署对物理基础架构有严格要求。因此，只能将实例部署在满足这些需求的 {{site.data.keyword.CloudDataCents_notm}} 中。以下 {{site.data.keyword.CloudDataCents_notm}} 可用于 Cloud Foundation 部署：

表 1. Cloud Foundation 实例的可用 {{site.data.keyword.CloudDataCents_notm}} 和 {{site.data.keyword.cloud_notm}} 裸机服务器配置

| {{site.data.keyword.CloudDataCent_notm}} |位置|区域|服务器配置|
|:----------------------|:---------|:-------|:----------------------|
|AMS03|阿姆斯特丹|欧洲|Skylake、Broadwell|
|CHE01|金奈|亚太地区|Skylake、Broadwell|
|DAL09|达拉斯|北美南部|Skylake、Broadwell|
|DAL10|达拉斯|北美南部|Skylake、Broadwell|
|DAL12|达拉斯|北美南部|Skylake、Broadwell|
|DAL13|达拉斯|北美南部|Skylake、Broadwell|
|FRA02|法兰克福|欧洲|Skylake、Broadwell|
|FRA04|法兰克福|欧洲|Skylake、Broadwell|
|HKG02|中国香港特别行政区|亚太地区|Skylake、Broadwell|
|LON02|伦敦|欧洲|Skylake、Broadwell|
|LON04|伦敦|欧洲|Skylake、Broadwell|
|LON06|伦敦|欧洲|Skylake、Broadwell|
|MEL01|墨尔本|亚太地区|Skylake、Broadwell|
|MEX01|克雷塔罗|北美南部|Skylake、Broadwell|
|MIL01|米兰|欧洲|Skylake、Broadwell|
|MON01|蒙特利尔|北美东部|Skylake、Broadwell|
|OSL01|奥斯陆|欧洲|Skylake、Broadwell|
|PAR01|巴黎|欧洲|Skylake、Broadwell|
|SAO01|圣保罗|南美|Skylake、Broadwell|
|SEO01|首尔|亚太地区|Skylake、Broadwell|
|SJC03|圣何塞|北美西部|Skylake、Broadwell|
|SJC04|圣何塞|北美西部|Skylake、Broadwell|
|SNG01|新加坡|亚太地区|Skylake、Broadwell|
|SYD01|悉尼|亚太地区|Skylake、Broadwell|
|SYD04|悉尼|亚太地区|Skylake、Broadwell|
|TOK02|东京|亚太地区|Skylake、Broadwell|
|TOR01|多伦多|北美东部|Skylake、Broadwell|
|WDC04|华盛顿|北美东部|Skylake、Broadwell|
|WDC06|华盛顿|北美东部|Skylake、Broadwell|
|WDC07|华盛顿|北美东部|Skylake、Broadwell|

根据可用性和库存供应，{{site.data.keyword.CloudDataCents_notm}} 可能会在 {{site.data.keyword.vmwaresolutions_short}} 控制台中显示状态指示符，以帮助您规划部署。

表 2. 订购 Cloud Foundation 实例时 {{site.data.keyword.CloudDataCents_notm}} 的状态指示符

|状态|状态详细信息|
|:------------------------------|:--------------------------------------------------|
|即将提供|{{site.data.keyword.CloudDataCent_notm}} 当前不可用。|
|暂时库存不足|{{site.data.keyword.CloudDataCent_notm}} 当前不可用。|
|有限库存|{{site.data.keyword.CloudDataCent_notm}} 具有有限可用性，并且订单可能未完成。|

## 备份管理组件

您负责维护和确保所有实例组件的可用性。建议您计划所有管理组件的备份或高可用性。有关更多信息，请参阅[备份组件](../archiref/solution/solution_backingup.html)。

## Cloud Foundation 实例的服务

您可以根据需要订购适用于实例的附加组件服务，例如灾难恢复。有关更多信息，请参阅[订购、查看和除去 Cloud Foundation 实例的服务](sd_addingremovingservices.html)。

## 容量注意事项

有关容量的更多信息，请参阅[扩展容量](../archiref/solution/solution_scaling.html)。

### 相关链接

* [Cloud Foundation 概述](sd_cloudfoundationoverview.html)
* [订购 Cloud Foundation 实例](sd_orderinginstance.html)
* [扩展和收缩 Cloud Foundation 实例的容量](sd_addingremovingservers.html)
* [订购、查看和除去 Cloud Foundation 实例的服务](sd_addingremovingservices.html)
