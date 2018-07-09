---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# 针对 VMware vSphere on IBM Cloud 的需求和规划

在订购 VMware vSphere on {{site.data.keyword.cloud}} 之前，请查看以下需求。根据 {{site.data.keyword.CloudDataCent_notm}} 位置以及工作负载容量需求来规划 VMware vSphere 集群。

**注**：部署 ESXi 服务器后，您负责设置环境、安装和配置各种 VMware 组件。此类组件包括：VMware vCenter Server、VMware NSX 和 VMware vSAN。

## IBM Cloud 帐户需求

要使用的 {{site.data.keyword.cloud_notm}} 帐户必须满足特定需求。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} 帐户需求](../vmonic/slaccountrequirement.html)。

## IBM Cloud Data Center 可用性

vSphere 部署对物理基础架构有严格要求。因此，只能将集群部署在满足这些需求的 {{site.data.keyword.CloudDataCents_notm}} 中。以下 {{site.data.keyword.CloudDataCent_notm}} 可用于 vSphere 部署。

**注**：如果选择的是 vSAN 组件，那么位置列表将按 SSD（固态磁盘）可用性进行过滤。

表 1. 可用于 vSphere 集群的 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |位置|区域|
|:----------------------|:---------|:-------|
|AMS03|阿姆斯特丹|欧洲|
|CHE01|金奈|亚太地区|
|DAL09|达拉斯|北美南部|
|DAL10|达拉斯|北美南部|
|DAL12|达拉斯|北美南部|
|DAL13|达拉斯|北美南部|
|FRA02|法兰克福|欧洲|
|FRA04|法兰克福|欧洲|
|HKG02|中国香港特别行政区|亚太地区|
|LON02|伦敦|欧洲|
|LON04|伦敦|欧洲|
|LON06|伦敦|欧洲|
|MEL01|墨尔本|亚太地区|
|MEX01|克雷塔罗|北美南部|
|MIL01|米兰|欧洲|
|MON01|蒙特利尔|北美东部|
|OSL01|奥斯陆|欧洲|
|PAR01|巴黎|欧洲|
|SAO01|圣保罗|南美|
|SEO01|首尔|亚太地区|
|SJC03|圣何塞|北美西部|
|SJC04|圣何塞|北美西部|
|SNG01|新加坡|亚太地区|
|SYD01|悉尼|亚太地区|
|SYD04|悉尼|亚太地区|
|TOK02|东京|亚太地区|
|TOR01|多伦多|北美东部|
|WDC04|华盛顿|北美东部|
|WDC06|华盛顿|北美东部|
|WDC07|华盛顿|北美东部|

## 相关链接

* [订购新的 vSphere 集群](vs_orderinginstances.html)
* [扩展现有集群](vs_scalingexistingclusters.html)
* [扩展在控制台外部创建的现有集群](vs_orderingforclustersoutside.html)
