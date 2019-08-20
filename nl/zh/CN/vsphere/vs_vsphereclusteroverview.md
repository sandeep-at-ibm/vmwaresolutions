---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-26"

keywords: vSphere, vSphere component, tech specs vSphere

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware vSphere on IBM Cloud 概述
{: #vs_vsphereclusteroverview}

VMware vSphere on {{site.data.keyword.cloud}} 是经过简化和优化的 VMware 订购平台。利用此平台，可以构建您自己的由 IBM 托管的 VMware 环境，方法是根据所选的 VMware 组件定制和订购与 VMware 兼容的硬件。

{{site.data.keyword.vmwaresolutions_short}} 控制台会基于您选择的 VMware 组件自动过滤硬件。例如，创建新的全闪存 VMware vSAN 集群时，仅显示针对 [VMware 兼容性指南](https://www.vmware.com/resources/compatibility/search.php){:external}验证过的硬件。此外，至少需要四个 ESXi 服务器。

VMware vSphere on {{site.data.keyword.cloud_notm}} 不会自动安装、配置、启动可选 VMware 组件。利用此平台可实现最大的灵活性，在包含与 VMware 兼容的硬件的同时，设计并构建托管的 VMware 环境。

使用此产品可创建新的 ESXi 服务器集群，也可以向外扩展 {{site.data.keyword.CloudDataCent_notm}} 中现有的 ESXi 服务器集群。根据您选择的 VMware 组件，一开始可以只有一个 ESXi 服务器，日后根据需要再对集群进行扩展。

## VMware vSphere on IBM Cloud 集群的技术规范
{: #vs_vsphereclusteroverview-specs}

复查 VMware vSphere on {{site.data.keyword.cloud_notm}} 的组件。

标准化硬件配置的可用性和定价可能会因选择用于部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。
{:note}

### VMware 组件
{: #vs_vsphereclusteroverview-specs-vmware-components}

选择用于以下 VMware 组件的许可证（IBM 提供或 BYOL）：
* VMware vSphere Enterprise Plus 6.7 U2 或 6.5 U2
* 以下 VMware 组件是可选的：
   * VMware vCenter Server Standard
   * VMware NSX（Base、Advanced 或 Enterprise）
   * VMware vSAN（Advanced 或 Enterprise）
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### 裸机服务器
{: #vs_vsphereclusteroverview-specs-bare-metal}

可以使用下列其中一个配置来订购一个或更多 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}：
* **Skylake**：具有所选 CPU 型号和 RAM 大小的 2 个 CPU Intel Skylake 代服务器（Intel Xeon 4100/5100/6100 系列）。
* **Cascade**：具有所选 CPU 型号和 RAM 大小的 2 个 CPU Intel Cascade 代服务器（Intel Xeon 4200/5200/6200 系列）。
* **SAP 认证**：具有所选 CPU 型号的 Intel Skylake 或 Intel Broadwell 代服务器（Intel Xeon 6140/E5-2690/E7-8890 系列）。
* **Broadwell**：具有所选 CPU 型号和 RAM 大小的 4 个 CPU 的 Intel Broadwell 代服务器（Intel Xeon E7-4800 系列）。

可用的选项取决于是否选择了 VMware vSAN 组件。

此外，还有以下磁盘和联网规范：
* 10 Gbps 双公用和专用网络上行链路
* 一个 RAID 磁盘控制器

### 联网
{: #vs_vsphereclusteroverview-specs-network}

* 一个公用 VLAN（虚拟 LAN）和两个专用 VLAN
* （可选）FortiGate Security Appliance 设备的 HA 对

### 存储
{: #vs_vsphereclusteroverview-specs-storage}

选择 VMware vSAN 组件时用于 vSAN 配置的用户定制存储器：
* 存储磁盘选项：960 GB SSD SED、1.9 TB SSD SED 或 3.8 TB SSD SED
* 磁盘数量选项：2、4、6 或 8 个

  此外，每个主机还会订购两个 960 GB 高速缓存磁盘。

  3.8 TB SSD（固态磁盘）驱动器在数据中心内普遍可用后就会受到支持。
  {:note}
* 高性能 Intel Optane 选项，用于提供两个额外的容量磁盘托架，总共可容纳 10 个容量磁盘。此选项取决于 CPU 型号。

## vSphere 集群扩展节点的技术规范
{: #vs_vsphereclusteroverview-expansion-node-specs}

每个 vSphere 集群扩展节点将在您的 {{site.data.keyword.slportal}} 帐户中部署以下组件并收取相应费用。

### 扩展节点的硬件
{: #vs_vsphereclusteroverview-expansion-node-specs-hardware}

一个 {{site.data.keyword.cloud_notm}} 裸机服务器，其硬件配置在 [VMware vSphere on {{site.data.keyword.cloud_notm}} 集群的技术规范](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs)中显示。

### 扩展节点的联网
{: #vs_vsphereclusteroverview-expansion-node-specs-network}

一个 {{site.data.keyword.cloud_notm}} 裸机服务器，其联网配置在 [VMware vSphere on {{site.data.keyword.cloud_notm}} 集群的技术规范](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs)中显示。

### 扩展节点的 VMware 组件
{: #vs_vsphereclusteroverview-expansion-node-specs-vmware-components}

* 一个 {{site.data.keyword.cloud_notm}} 裸机服务器，带 VMware vSphere Enterprise Plus 6.7u2 或 6.5u2。  
* 可选的 VMware 组件在 [VMware vSphere on {{site.data.keyword.cloud_notm}} 集群的技术规范](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs)中显示。

您只能在 {{site.data.keyword.slportal}} 中管理订购并交付给您的 {{site.data.keyword.cloud_notm}} 帐户的 ESXi 服务器、可选 VMware 组件以及其他硬件。在 {{site.data.keyword.vmwaresolutions_short}} 控制台中创建新集群后，可以返回到控制台并使用保存的信息扩展新集群。有关更多信息，请参阅[缩放现有 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)。
{:important}

## 相关链接
{: #vs_vsphereclusteroverview-related}

* [VMware vSphere 软件材料清单](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
* [规划 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [订购 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [缩放现有 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
