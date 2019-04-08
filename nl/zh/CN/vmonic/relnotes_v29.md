---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-25"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V2.9 发行说明
{: #relnotes_v29}

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VMware vCenter Server on IBM Cloud with NSX-T
{: #relnotes_v29-vcs-nsx-t}

本发行版引入了 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T 产品作为概念验证或沙箱测试产品。vCenter Server with NSX-T 是私有托管云，允许您试用 VMware 下一代联网平台 NSX-T。

有关更多信息，请参阅以下主题：

* [vCenter Server with NSX-T 概述](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview)
* [订购 vCenter Server with NSX-T 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## 对 VMware Cloud Foundation on IBM Cloud 的支持结束 
{: #relnotes_v29-vcf-eos}

为了整合我们的产品以获得更好的客户体验，从 2019 年 5 月 13 日起，{{site.data.keyword.cloud_notm}} 将不再提供对 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 的支持。此后，所有客户将定向到
VMware vCenter Server on {{site.data.keyword.cloud_notm}}，它将在存储和许可选项方面提供更大的灵活性。
在 2019 年 5 月 13 日结束支持之前，使用 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 的现有客户将在支持人员的协助下迁移到 VMware vCenter Server on {{site.data.keyword.cloud_notm}}。

在 5 月 13 日之后，将从 {{site.data.keyword.vmwaresolutions_short}} 控制台中除去 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 的管理功能。可以通过 IBM Cloud 基础架构控制台访问尚未迁移到
VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的实例。

{{site.data.keyword.cloud_notm}} 支持人员将在 2019 年 3 月 25 日之前联系客户，开始迁移 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}。有关现有客户的迁移选项的更多信息，请参阅 [{{site.data.keyword.vmwaresolutions_short}} wiki 页面](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/Wf58c4c538dbf_45b4_b7a7_5003d0ceb79b/page/IBM%20Cloud%20for%20VMware%20Solutions){:new_window}。
客户可以在 [{{site.data.keyword.vmwaresolutions_short}} 控制台](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted)上查看其现有 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 实例。

## VMware vSphere 6.7 Update 1 支持
{: #relnotes_v29-vsphere}

您现在可以选择与 VMware vCenter Server、VMware vCenter Server with Hybridity Bundle 和 VMware vSphere on {{site.data.keyword.cloud_notm}} 实例一起订购 VMware vSphere version 6.7 Update 1。

此外，Migration and App Modernization 的单节点试用版实例现在随 vSphere Enterprise Plus 6.7u1 一起订购。

vSphere Enterprise Plus 6.7u1 仅可用于 Broadwell 和 Skylake {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}。

有关更多信息，请参阅以下内容中的_许可证设置_部分：

* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [订购 vCenter Server with Hybridity Bundle 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## 结束对 VLAN 生成的支持
{: #relnotes_v29-vlan}

从 2019 年 8 月起，{{site.data.keyword.vmwaresolutions_short}} 不再支持 VLAN 生成。到 2019 年 7 月底，您必须将 {{site.data.keyword.cloud_notm}} 基础架构帐户转换为虚拟路由和转发 (VRF) 并为您的帐户启用服务端点。

有关更多信息，请参阅：

* [IBM Cloud 上的虚拟路由和转发 (VRF) 概述](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [使用 IBM Cloud CLI 支持帐户使用服务端点](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)

## 支持应用程序编程接口
{: #relnotes_v29-api}

应用程序编程接口 (API) 现在可用于部署实例，删除实例以及添加和除去 ESXi 服务器和集群。

现在，用户文档的*参考*部分中还提供了 REST API 文档。有关更多信息，请参阅 [{{site.data.keyword.vmwaresolutions_short}} API](https://cloud.ibm.com/apidocs/vmware-solutions)。

## 对 VMware vCenter Server 实例的更新
{: #relnotes_v29-vcs}

本发行版应用了以下升级和改进：

* vSphere ESXi 6.7 Update 1（构建 6.7.0-11675023）
* vSphere ESXi 6.5 Update 2（构建 6.5.0-11925212）
* vSphere 6.7 Distributed vSwitch 6.6.0
* vSphere 6.5 Distributed vSwitch 6.5.0
* vCenter Server Appliance 6.7 U1（构建 6.7.0-10244745）
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4（构建 11197766）
* NSX-T for vSphere 2.4

有关选择 VMware 组件的更多信息，请参阅 [vCenter Server 材料清单](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)。

### 对数据中心的更新
{: #relnotes_v29-dc}

以下新的数据中心可用于部署：**FRA-05 - 法兰克福**和 **LON-05 - 伦敦**。 有关更多信息，请参阅[针对 vCenter Server 实例的需求和规划](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)。

### ESXi 服务器增强功能
{: #relnotes_v29-vcs-esxi}

* 现在，在交付实例之前，已针对 ESXi 服务器禁用安全 Shell (SSH) 协议。
* 从 V2.9 发行版开始，以下 ESXi 服务器操作可用：

   * 在服务器处于维护模式时，向现有集群添加新的 ESXi 服务器。在您除去虚拟机的维护模式之前，这些虚拟机不会迁移到新服务器。
   * 同时在实例中的多个集群中添加或除去 ESXi 服务器。

有关更多信息，请参阅[扩展和收缩 vCenter Server 实例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)。

### 网络文件系统存储器大小
{: #relnotes_v29-vcs-nfs}

对于 vCenter Server 实例订单，现在可以为性能级别 0.25、2 和 4 IOPS/GB 添加最多 24 TB 的网络文件系统 (NFS) 共享存储器。

此 10 IOPS/GB 性能级别仍限制为每个文件共享的最大容量为 4 TB。
{:note}

## 对附加组件服务的更新
{: #relnotes_v29-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v29-services-caveonix}

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务现在可用于部署或升级到 V2.9 或更高发行版的 VMware vCenter Server 实例。此服务可以通过主动监视和自动防御控制来管理网络和合规性风险，以防御威胁并且满足行业或政府法规。

您可以订购包含 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务的 vCenter Server 实例，或者以后从实例详细信息页面上的**服务**选项卡上将此服务添加到现有 vCenter Server 实例。

您还可以订购单机的 Caveonix RiskForesight 许可证，而不将其与任何 VMware 实例关联，以对内部部署工作负载进行许可和激活。

有关更多信息，请参阅：
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 的注意事项](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [订购 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [ Caveonix 许可证的注意事项](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_considerations)
* [订购 Caveonix 许可证](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

在当前发行版中，F5-BigIP VE V14.1.0.2 安装在所有新部署的实例上。有关 F5-BigIP VE V14.1.0.2 中新功能的更多信息，请参阅 [Release Note: BIG-IP 14.1.0 New and Installation](https://support.f5.com/kb/en-us/products/big-ip_ltm/releasenotes/product/relnote-bigip-14-1-0.html){:new_window}。

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

在当前发行版中，HyTrust CloudControl 5.4.2 安装在所有新部署的实例上。有关 HyTrust CloudControl 5.4.2 中新功能的更多信息，请参阅
[HyTrust CloudControl 发行说明 V5.4.2](https://docs.hytrust.com/CloudControl/5.4.2/Online/index.html#HTCC_Admin_Guide/_FrontMatter/Whats-New.html%3FTocPath%3D_____2){:new_window}。

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

现在，在悉尼有可用于 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务的两个新端点。有关更多信息，请参阅 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务配置](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config)。

### Veeam on IBM Cloud
{: #relnotes_v29-services-veeam}

在当前发行版中，Veeam Backup and Replication 9.5 Update 4 安装在所有新部署的实例上。有关 Veeam 9.5u4 中新功能的更多信息，请参阅 [Release Information for Veeam Backup & Replication 9.5 Update 4](https://www.veeam.com/kb2878){:new_window}。

### Zerto on IBM Cloud
{: #relnotes_v29-services-zerto}

在当前发行版中，Zerto Virtual Replication 6.5 update 3 安装在所有新部署的实例上。有关 Zerto Virtual Replication 6.5 update 3 中新功能的更多信息，请参阅 [Release notes for Zerto Virtual Replication V6.5 Update 3](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Release%20Notes.pdf){:new_window}。

## 用户界面更新和增强功能
{: #relnotes_v29-ui}

用户界面已更新，并提供了以下增强功能：

* 在**基础架构**页面上，新的**网络接口**表提供集群的 VLAN、子网和 IP 地址详细信息。
* 提供了各种错误消息和工具提示增强功能，以帮助您在用户界面上选择相应的设置。
