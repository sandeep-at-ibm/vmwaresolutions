---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight on IBM Cloud 概述
{: #caveonix_considerations}

Caveonix RiskForesight on {{site.data.keyword.cloud}} 服务可以通过主动监视和自动防御控制来管理网络和合规性风险，以防御威胁并满足行业或政府法规。

此服务仅可用于在 V2.9 和更高发行版中部署的 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 实例。
{:note}

## Caveonix RiskForesight on IBM Cloud 的技术规范 
{: #caveonix_considerations-specs}

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

### vCenter 资源
{: #caveonix_considerations-tech-specs-vcenter}

* CPU：8 个 vCPU
* RAM：32 GB
* 磁盘：80 GB

### 网络
{: #caveonix_considerations-tech-specs-network}

订购了具有 64 个 IP 地址的专用子网。

### 许可证和费用
{: #caveonix_considerations-tech-specs-license-fee}

为服务的每个实例订购了一个 Caveonix RiskForesight 许可证密钥。

## 安装 Caveonix RiskForesight on IBM Cloud 时的注意事项
{: #caveonix_considerations-install}

安装 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务之前，确保服务实例的缺省集群中的 CPU 和内存足够用于 Caveonix RiskForesight 虚拟机。

## 除去 Caveonix RiskForesight on IBM Cloud 时的注意事项
{: #caveonix_considerations-remove}

除去 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务之前，请查看以下注意事项：
* 除去 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务不会取消 Caveonix RiskForesight 许可证。必须从 {{site.data.keyword.vmwaresolutions_short}} 控制台的**资源**页面上的 **Caveonix RiskForesight 许可证**表中删除 Caveonix RiskForesight 许可证。
* 除去服务时，{{site.data.keyword.vmwaresolutions_short}} 自动化仅删除已部署的单个“一体化”Caveonix VM 以及为其订购的专用子网。因此，
   * 如果 Caveonix VM 已横向扩展为多个 VM，那么不会除去这些额外的 VM。
   * 如果在额外的 VM 上使用专用子网的 IP 地址，那么这些 VM 必须分配有新的 IP 地址才能继续正常运行。
   * 如果删除已安装了 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务的 vCenter Server 实例 A，并且您已使用在 vCenter Server 实例 B 中为该服务订购的专用子网的 IP 地址，那么在删除 vCenter Server 实例 A 时将取消该专用子网。

## 相关链接
{: #caveonix_considerations-related}

* [订购 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [管理 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
