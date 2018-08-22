---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-18"

---

# VMware vSphere on IBM Cloud 概述

VMware vSphere on {{site.data.keyword.cloud}} 是一个经过简化和优化的 VMware 订购平台，支持您根据所选 VMware 组件来定制和订购与 VMware 兼容的硬件，从而构建自己的 IBM 托管的 VMware 环境。

{{site.data.keyword.vmwaresolutions_short}} 控制台会基于您选择的 VMware 组件自动过滤硬件。例如，创建新的全闪存 VMware vSAN 集群时，仅提供根据 [VMware 兼容性指南](https://www.vmware.com/resources/compatibility/search.php)验证过的硬件，并且至少需要 4 个 ESXi 服务器。

VMware vSphere on {{site.data.keyword.cloud_notm}} 不会自动安装、配置和启动可选的 VMware 组件，但支持以最大的灵活性设计和构建托管的 VMware 环境，同时包含与 VMware 兼容的硬件。

使用此产品可创建新的 ESXi 服务器集群，也可以向外扩展 {{site.data.keyword.CloudDataCent_notm}} 中现有的 ESXi 服务器集群。根据您选择的 VMware 组件，一开始可以只有一个 ESXi 服务器，日后根据需要再对集群进行扩展。

## VMware vSphere on IBM Cloud 集群的技术规范

复查 VMware vSphere on {{site.data.keyword.cloud_notm}} 的组件。

**注**：标准化硬件配置的可用性和定价可能会因选择用于部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。

### VMware 组件

用于以下 VMware 组件的许可证（IBM 提供或 BYOL）：
* VMware vSphere Enterprise Plus 6.0u2 或 6.5u1
* 可选 VMware 组件：
   * VMware vCenter Server Standard
   * VMware NSX（Base、Advanced 或 Enterprise）
   * VMware vSAN（Advanced 或 Enterprise）
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### 裸机服务器

一个或多个 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}，具有所选 CPU 型号和 RAM 大小：
* 2 个 Intel Broadwell 代 CPU（Intel Xeon E5-2600 V4 系列）
* 2 个 Intel Skylake 代 CPU（Intel Xeon 4100/5100/6100 系列）

可用的选项取决于是否选择了 VMware vSAN 组件。

此外，还有以下磁盘和联网规范：
* 10 Gbps 双公用和专用网络上行链路
* 一个 RAID 磁盘控制器

### 联网

* 三个 VLAN（虚拟 LAN）：一个公用 VLAN 和两个专用 VLAN
* （可选）FortiGate Security Appliance 设备的 HA 对

### 存储

选择 VMware vSAN 组件时用于 vSAN 配置的用户定制存储器：
* 存储磁盘选项：960 GB SSD SED、1.9 TB SSD SED 或 3.8 TB SSD SED
* 磁盘数量选项：2、4、6 或 8 个

**注**：3.8 TB SSD（固态磁盘）驱动器在数据中心内基本可用后就会受到支持。

## vSphere 集群扩展节点的技术规范

每个 vSphere 集群扩展节点将在您的 {{site.data.keyword.slportal}} 帐户中部署以下组件并收取相应费用。

### 扩展节点的硬件

一个 {{site.data.keyword.cloud_notm}} 裸机服务器，其硬件配置在 [VMware vSphere on {{site.data.keyword.cloud_notm}} 的组件](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)中提供。

### 扩展节点的联网

一个 {{site.data.keyword.cloud_notm}} 裸机服务器，其联网配置在 [VMware vSphere on {{site.data.keyword.cloud_notm}} 的组件](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)中提供。

### 扩展节点的 VMware 组件

* 一个 {{site.data.keyword.cloud_notm}} 裸机服务器，带 VMware vSphere Enterprise Plus 6.0u2 或 6.5u1  
* 可选的 VMware 组件，在 [VMware vSphere on {{site.data.keyword.cloud_notm}} 的组件](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)中提供。

**重要信息**：您只能在 {{site.data.keyword.slportal}} 中管理订购并交付给您的 {{site.data.keyword.cloud_notm}} 帐户的 ESXi 服务器、可选 VMware 组件以及其他硬件。在 {{site.data.keyword.vmwaresolutions_short}} 控制台中创建新集群后，可以返回到控制台以使用保存的配置扩展新集群。有关更多信息，请参阅[扩展现有 vSphere 集群](vs_scalingexistingclusters.html)。

### 相关链接

* [VMware vSphere 软件材料清单](vs_bom.html)
* [规划 vSphere 集群](vs_planning.html)
* [订购 vSphere 集群](vs_orderinginstances.html)
* [扩展现有 vSphere 集群](vs_scalingexistingclusters.html)
