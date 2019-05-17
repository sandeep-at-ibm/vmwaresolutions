---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

# 针对 vCenter Server with Hybridity Bundle 实例的需求和规划
{: #vc_hybrid_planning}

在订购 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 实例之前，请查看以下需求。根据 {{site.data.keyword.CloudDataCent_notm}} 位置、工作负载容量需求和其他服务需求来规划实例。

## IBM Cloud 帐户需求
{: #vc_hybrid_planning-account-req}

要使用的 {{site.data.keyword.cloud_notm}} 帐户必须满足特定需求。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} 帐户需求](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement)。

## IBM Cloud Data Center 可用性
{: #vc_hybrid_planning-dc-availability}

vCenter Server with Hybridity Bundle 部署对物理基础架构有严格要求。因此，只能将实例部署在满足这些需求的 {{site.data.keyword.CloudDataCents_notm}} 中。以下 {{site.data.keyword.CloudDataCents_notm}} 可用于 vCenter Server with Hybridity Bundle 部署：

表 1. 可用于 vCenter Server with Hybridity Bundle 实例的 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |位置|区域|
|:----------------------|:---------|:---------------|
|AMS03|阿姆斯特丹|欧洲|
|CHE01|金奈|亚太地区|
|DAL09|达拉斯|北美南部|
|DAL10|达拉斯|北美南部|
|DAL12|达拉斯|北美南部|
|DAL13|达拉斯|北美南部|
|FRA02|法兰克福|欧洲|
|FRA04|法兰克福|欧洲|
|FRA05|法兰克福|欧洲|
|HKG02|中国香港特别行政区|亚太地区|
|LON02|伦敦|欧洲|
|LON04|伦敦|欧洲|
|LON05|伦敦|欧洲|
|LON06|伦敦|欧洲|
|MEL01|墨尔本|亚太地区|
|MEX01|克雷塔罗|北美南部|
|MIL01|米兰|欧洲|
|MON01|蒙特利尔|北美东部|
|OSL01|奥斯陆|欧洲|
|PAR01|巴黎|欧洲|
|SAO01|圣保罗|南美洲|
|SEO01|首尔|亚太地区|
|SJC03|圣何塞|北美西部|
|SJC04|圣何塞|北美西部|
|SNG01|新加坡|亚太地区|
|SYD01|悉尼|亚太地区|
|SYD04|悉尼|亚太地区|
|TOK02|东京|亚太地区|
|TOK04|东京|亚太地区|
|TOR01|多伦多|北美东部|
|WDC04|华盛顿|北美东部|
|WDC06|华盛顿|北美东部|
|WDC07|华盛顿|北美东部|

根据可用性和库存供应，{{site.data.keyword.CloudDataCents_notm}} 可能会在 {{site.data.keyword.vmwaresolutions_short}} 控制台中显示状态指示符，以帮助您规划部署。

表 2. 订购 vCenter Server with Hybridity Bundle 实例时 {{site.data.keyword.CloudDataCents_notm}} 的状态指示符

|状态|状态详细信息|
|:------------------------------|:--------------------------------------------------|
|即将提供|{{site.data.keyword.CloudDataCent_notm}} 当前不可用。|
|暂时库存不足|{{site.data.keyword.CloudDataCent_notm}} 当前不可用。|
|有限库存|{{site.data.keyword.CloudDataCent_notm}} 具有有限可用性，并且订单可能未完成。|

## 备份管理组件
{: #vc_hybrid_planning-backup-mgmt-components}

您负责维护和确保所有实例组件的可用性。强烈建议您计划所有管理组件的备份或高可用性。有关更多信息，请参阅[备份组件](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)。

## vCenter Server with Hybridity Bundle 实例的服务
{: #vc_hybrid_planning-addon-services}

vCenter Server with Hybridity Bundle 实例包含授权您使用 VMware HCX on {{site.data.keyword.cloud_notm}} 服务的 VMware Hybrid Cloud Extension (HCX) 许可。此服务可以将内部部署数据中心的网络无缝扩展到 {{site.data.keyword.cloud_notm}}，这允许虚拟机 (VM) 在不进行任何转换或更改的情况下，迁移到 {{site.data.keyword.cloud_notm}} 或从中迁移出来。

部署此服务时，请完成以下设置：
* 通过选择下列其中一个选项来指定 **HCX 互连类型**：
  * **公用网络**：HCX 通过公用网络在站点之间创建加密连接。
  * **专用网络**：HCX 通过专用网络在站点之间创建加密连接。
* 指定**公共端点证书类型**。如果选择 **CA 证书**，请配置以下设置：
  * **证书内容**：输入 CA 证书的内容。
  * **专用密钥**：输入 CA 证书的专用密钥。
  * （可选）**密码**：输入专用密钥的密码（如果对专用密钥进行了加密）。
  * （可选）**重新输入密码**：重新输入专用密钥的密码。
  * （可选）**主机名**：输入要映射到 CA 证书的公共名称 (CN) 的主机名。HCX on {{site.data.keyword.cloud_notm}} 需要 CA 证书采用 NSX Edge 接受的格式。有关 NSX Edge 证书格式的更多信息，请参阅[导入 SSL 证书](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html)。

您可以根据需要订购适用于实例的其他附加组件服务，例如灾难恢复。有关更多信息，请参阅[订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)。

## 容量注意事项
{: #vc_hybrid_planning-capacity-considerations}

有关容量注意事项的更多信息，请参阅[缩放容量](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling)。

## 相关链接
{: #vc_hybrid_planning-related}

* [vCenter Server with Hybridity Bundle 概述](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [订购 vCenter Server with Hybridity Bundle 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [扩展和收缩 vCenter Server with Hybridity Bundle 实例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
