---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmware-solutions


---

# 产品比较图表
{: #inst_comp_chart}

查看以下图表，以了解 VMware vCenter Server 实例、VMware vCenter Server with Hybridity Bundle 实例和 VMware vSphere 集群在功能支持方面的差异。

表 1. vCenter Server、vCenter Server with Hybridity Bundle 和 vSphere 集群支持的功能

|功能|vCenter Server| vCenter Server with Hybridity|VMware vSphere|
|:--- |:--- |:--- |:--- |
|基于 {{site.data.keyword.IBM}} 高级自动化技术<sup>1</sup>|是|是|否。自行构建和配置|
|存储选项|vSAN 或共享文件级别存储器 (NFS)| vSAN 或 NFS <sup>2</sup> | vSAN 或 NFS |
|初始集群中的 ESXi 服务器数| 对于 vSAN 为 4 个，对于 NFS 最少为 2 个（建议 3 个） |4|1 个用于扩展现有集群，4 个用于新的 vSAN 集群，至少 3 个用于使用 NFS 的新集群|
| 最大 ESXi 服务器数 <sup>3</sup> |每个集群 59 个|每个集群 59 个|每个集群 60 个|
|云自动化多站点部署|支持在 V2.0 或更高版本中部署的新实例|支持|支持。不包含自动化配置|
|添加 ESXi 服务器|支持|支持|支持。不包含自动化配置|
|除去 ESXi 服务器|支持|支持|支持。不包含自动化配置|
|多集群支持|最大数量取决于 VMware 大小调整准则|最大数量取决于 VMware 大小调整准则|支持。不包含自动化配置|
|客户机管理的 VMware 堆栈更新和修补|客户机管理的更新：<br/>本机 VMware Tools (VMware Update Manager)|客户机管理的更新：<br/>本机 VMware Tools (VMware Update Manager)|客户机管理的更新：<br/>本机 VMware Tools (VMware Update Manager)|
|备份与复原|手动使用 IBM Spectrum Protect Plus 或 Veeam|手动使用 IBM Spectrum Protect Plus 或 Veeam|不包含备份和复原解决方案|
|软件定义的联网|NSX Base、Advanced 或 Enterprise|NSX Advanced 或 Enterprise|NSX Standard、Base 或 Enterprise。不包含自动化配置|
|vSphere 和 vSAN 的 BYOL|每个集群完全支持|不支持|支持|
|vCenter 和 NSX 的 BYOL|每个实例完全支持|不支持|支持|
|NSX 许可证升级选项|可从 NSX Base 升级到 Advanced 或 Enterprise，也可从 NSX Advanced 升级到 Enterprise。可升级到 vCenter Server with Hybridity Bundle。|可从 NSX Advanced 升级到 Enterprise|无|
|vSAN 许可证版本|vSAN Advanced 或 Enterprise|vSAN Advanced 或 Enterprise|vSAN Advanced 或 Enterprise|
|附加组件服务|支持，不包括 HCX on {{site.data.keyword.cloud_notm}}。可升级到 vCenter Server with Hybridity Bundle。|支持，包括 HCX on {{site.data.keyword.cloud_notm}}。|此解决方案的自动化不支持，但您可以使用并安装自己的软件。|

## 注释
{: #inst_comp_chart-notes}

<sup>1</sup> 根据经过验证的设计并在部署期间进行过验证。

<sup>2</sup> vSAN 仅适用于新的 vCenter Server with Hybridity 实例和集群。部署后，可以添加 NFS 存储器。

<sup>3</sup> 可以将 vSAN 集群中的 ESXi 服务器数增大到最大值 64 个。有关更多信息，请参阅[关于 ESXi 服务器的常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi)中的_可以向集群添加多少个 ESXi 服务器？_。

## 相关链接
{: #inst_comp_chart-related}

* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [vCenter Server 概述](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [vCenter Server Hybridity 概述](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [VMware vSphere 概述](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)
* [vCenter Server BOM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [VMware vSphere BOM](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
