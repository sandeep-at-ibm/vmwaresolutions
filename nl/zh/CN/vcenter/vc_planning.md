---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# 针对 vCenter Server 实例的需求和规划

在订购 VMware vCenter Server 实例之前，请查看以下需求。根据 {{site.data.keyword.CloudDataCent}} 位置、工作负载容量需求和其他服务需求来规划实例。

## IBM Cloud 帐户需求

要使用的 {{site.data.keyword.cloud_notm}} 帐户必须满足特定需求。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} 帐户需求](../vmonic/slaccountrequirement.html)。

## IBM Cloud Data Center 可用性

vCenter Server 部署对物理基础架构有严格要求。因此，只能将实例部署在满足这些需求的 {{site.data.keyword.CloudDataCents_notm}} 中。以下 {{site.data.keyword.CloudDataCents_notm}} 可用于 vCenter Server 部署：

表 1. 可用于 vCenter Server 实例的 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |位置|区域|服务器选项|
|:----------------------|:---------|:-------|:---------------|
|AMS03|阿姆斯特丹|欧洲|定制|
|CHE01|金奈|亚太地区|定制|
|DAL09|达拉斯|北美南部|定制|
|DAL10|达拉斯|北美南部|定制、小型、中型、大型|
|DAL12|达拉斯|北美南部|定制|
|DAL13|达拉斯|北美南部|定制|
|FRA02|法兰克福|欧洲|定制、小型、中型、大型|
|FRA04|法兰克福|欧洲|定制|
|HKG02|中国香港特别行政区|亚太地区|定制|
|LON02|伦敦|欧洲|定制|
|LON04|伦敦|欧洲|定制|
|LON06|伦敦|欧洲|定制、小型、中型、大型|
|MEL01|墨尔本|亚太地区|定制|
|MEX01|克雷塔罗|北美南部|定制|
|MIL01|米兰|欧洲|定制|
|MON01|蒙特利尔|北美东部|定制|
|OSL01|奥斯陆|欧洲|定制|
|PAR01|巴黎|欧洲|定制|
|SAO01|圣保罗|南美|定制|
|SEO01|首尔|亚太地区|定制|
|SJC03|圣何塞|北美西部|定制、小型、中型、大型|
|SJC04|圣何塞|北美西部|定制|
|SNG01|新加坡|亚太地区|定制|
|SYD01|悉尼|亚太地区|定制|
|SYD04|悉尼|亚太地区|定制|
|TOK02|东京|亚太地区|定制|
|TOR01|多伦多|北美东部|定制、小型、中型、大型|
|WDC04|华盛顿|北美东部|定制、小型、中型、大型|
|WDC06|华盛顿|北美东部|定制|
|WDC07|华盛顿|北美东部|定制|

一小部分 IBM Cloud {{site.data.keyword.CloudDataCents_notm}} 提供预配置的**小型**、**中型**和**大型**裸机服务器选项。根据可用性和库存供应，{{site.data.keyword.CloudDataCents_notm}} 可能会在 {{site.data.keyword.vmwaresolutions_full}} 控制台中显示状态指示符，以帮助您规划部署。

表 2. 订购 vCenter Server 实例时 {{site.data.keyword.CloudDataCents_notm}} 的状态指示符

|状态|状态详细信息|
|:------------------------------|:--------------------------------------------------|
|即将提供|{{site.data.keyword.CloudDataCent_notm}} 当前不可用。|
|暂时库存不足|此时 {{site.data.keyword.CloudDataCent_notm}} 不具有可用性。|
|有限库存|{{site.data.keyword.CloudDataCent_notm}} 具有有限可用性，并且订单可能未完成。|

## vCenter Server 实例的服务

您可以根据需要订购适用于实例的附加组件服务，例如灾难恢复。有关更多信息，请参阅[订购、查看和除去 vCenter Server 实例的服务](vc_addingremovingservices.html)。

<!-- ## Capacity considerations

For capacity information and considerations, see the _Bill of
Materials_ document on the [Virtual reference architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page. -->

## 相关链接

* [vCenter Server 概述](vc_vcenterserveroverview.html)
* [订购 vCenter Server 实例](vc_orderinginstance.html)
* [扩展和收缩 vCenter Server 实例的容量](vc_addingremovingservers.html)
* [订购、查看和除去 vCenter Server 实例的服务](vc_addingremovingservices.html)
