---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# 产品比较图表

查看以下图表，以了解 VMware Cloud Foundation 实例、VMware vCenter Server 实例、VMware vCenter Server with Hybridity Bundle 实例和 VMware vSphere 集群在功能支持方面的差异。

表 1. Cloud Foundation、vCenter Server、vCenter Server with Hybridity Bundle 和 vSphere 集群支持的功能

|功能|Cloud Foundation|vCenter Server| vCenter Server with Hybridity|VMware vSphere|
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
|基于 {{site.data.keyword.IBM}} 高级自动化技术<sup>1</sup>|是|是|是|否。自行构建和配置|
|存储选项|vSAN|vSAN 或共享文件级别存储器 (NFS)|vSAN|vSAN 或共享文件级别存储器 (NFS)|
|初始集群中的 ESXi 服务器数|4|对于 vSAN 为 4 个，对于 NFS 至少为 2 个（强烈建议使用 3 个）|4|1 个用于扩展现有集群，4 个用于新的 vSAN 集群，至少 3 个用于使用 NFS 的新集群|
|最大 ESXi 服务器数<sup>2</sup>|每个集群 32 个|每个集群 59 个|每个集群 59 个|每个集群 60 个|
|云自动化多站点部署|支持 V2.0 或更高版本中部署的新实例|支持 V2.0 或更高版本中部署的新实例|支持|支持。不包含自动化配置|
|添加 ESXi 服务器|支持|支持|支持|支持。不包含自动化配置|
|除去 ESXi 服务器|支持|支持|支持|支持。不包含自动化配置|
|多集群支持|5 个集群|10 个集群|10 个集群|支持。不包含自动化配置|
|客户机管理的 VMware 堆栈更新和修补|IBM CloudDriver 和 VMware 更新|IBM CloudDriver|IBM CloudDriver|不包含自动化修补|
|备份与复原|支持|支持|支持|不包含自动化备份解决方案配置|
|软件定义的联网|NSX Enterprise|NSX Base、Advanced 或 Enterprise|NSX Advanced 或 Enterprise|NSX Standard、Base 或 Enterprise。不包含自动化配置|
|vSphere 和 vSAN 的 BYOL|每个集群完全支持|每个集群完全支持|不支持|支持|
|vCenter 和 NSX 的 BYOL|每个实例完全支持|每个实例完全支持|不支持|支持|
|NSX 许可证升级选项|无|可从 NSX Base 升级到 Advanced 或 Enterprise，也可从 NSX Advanced 升级到 Enterprise。可升级到 vCenter Server with Hybridity Bundle。|可从 NSX Advanced 升级到 Enterprise|无|
|vSAN 许可证版本|vSAN Advanced 或 Enterprise|vSAN Advanced 或 Enterprise|vSAN Advanced 或 Enterprise|vSAN Advanced 或 Enterprise|
|附加组件服务|支持，不包括 HCX on {{site.data.keyword.cloud_notm}}。|支持，不包括 HCX on {{site.data.keyword.cloud_notm}}。可升级到 vCenter Server with Hybridity Bundle。|支持，包括 HCX on {{site.data.keyword.cloud_notm}}。|支持。不包含自动化配置|

**注**：

<sup>1</sup> 根据经过验证的设计并在部署期间进行过验证。

<sup>2</sup> 可以将 vSAN 集群中的 ESXi 服务器数增大到最大值 64 个。有关更多信息，请参阅[关于 ESXi 服务器的常见问题](faq_esxi.html)中的_可以向集群添加多少个 ESXi 服务器？_。

### 相关链接

* [常见问题](faq.html)
* [Cloud Foundation 概述](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 概述](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server Hybridity 概述](../vcenter/vc_hybrid_overview.html)
* [Vmware vSphere 概述](../vsphere/vs_vsphereclusteroverview.html)
* [Cloud Foundation BOM](../sddc/sd_bom.html)
* [vCenter Server BOM](../vcenter/vc_bom.html)
* [Vmware vSphere BOM](../vsphere/vs_bom.html)
