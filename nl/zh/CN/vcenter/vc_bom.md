---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 材料清单

查看 VMware vCenter Server 实例的材料清单 (BOM) 信息。

## vCenter Server 实例的 VLAN BOM

下表详细描述了 vCenter Server VLAN 的 BOM 信息。

表 1. vCenter Server 实例中 VLAN 的 BOM

|VLAN|类型|详细信息|
|:---------- |:---------- |:------------- |
|VLAN1|公用，主|分配给物理 ESXi 服务器以用于公用网络访问。在初始部署后未使用。可用于因特网访问。|
|VLAN2|专用 A，主|由 {{site.data.keyword.cloud}} 分配给物理 ESXi 服务器。通过管理界面用于 VMware vSphere 管理流量。<br><br>分配给充当管理组件的 VM（虚拟机）。<br><br>分配给 VMware NSX VTEP（VXLAN 隧道端点）|
|VLAN3|专用 B，可移植|分配给 VMware vSAN（如果使用）。<br><br>分配给 VMware NFS（如果使用）。<br><br>分配给 VMware vSphere vMotion。|

## vCenter Server 实例的软件 BOM

下表详细描述了 vCenter Server 软件组件的 BOM 信息。

表 2. vCenter Server 实例中软件组件的 BOM

|制造商|组件|版本|
|:------------- |:------------------------------ |:------------- |
|VMware|vSphere ESXi|6.5 Update P3（构建 6.5.0-10884925）|
|VMware|vCenter Server Appliance|6.5 U2d（构建 6.5.0-10964411）|
|VMware|Platform Services Controller|6.5 U2d（构建 6.5.0-10964411）|
|VMware|vSAN|6.6.1|
|VMware|NSX for vSphere|6.4.1|
|Microsoft|Windows Server Standard Edition|2012R2|

VMware vSAN 是可选组件。
{:note}

## ESXi 服务器的高级配置设置

查看下表以了解应用于 ESXi 服务器的高级配置设置的概述。这些设置取决于 vCenter Server 实例是部署在 V2.2 或更高版本中，还是从 V2.1 或更低版本升级到 V2.2 或更高版本。

这些设置会应用于新实例以及新实例 V2.2 或更高版本中的新集群。这些设置不会应用于 V2.1 或更低版本的现有实例中的新集群，也不会应用于升级到 V2.2 或更高版本的现有实例中的新集群。

表 3. vCenter Server 实例和集群的 ESXi 服务器高级配置设置

|配置设置|如果是新部署在 V2.2 或更高版本中|如果是从 V2.1 或更低版本升级|
|:------------- |:------------- |:------------- |
|最大卷数|**MaxVolumes** = 256|**/NFS/MaxVolumes** 和 **/NFS41/MaxVolumes** = 256|
|脉动信号最大故障数|**HeartbeatMaxFailures** = 10|未设置|
|脉动信号频率|**HeartbeatFrequency** = 12|未设置|
|脉动信号超时|**HeartbeatTimeout** = 5|未设置|
|最大队列深度|**MaxQueueDepth** = 64|未设置|
|队列已满样本大小|**QFullSampleSize** = 32|**/Disk/QFullSampleSize** = 32|
|队列已满阈值|**QFullThreshold** = 8|**/Disk/QFullThreshold** = 8|
|TCP/IP 堆大小|**TcpipHeapSize** = 32|未设置|
|最大 TCP/IP 堆大小|**TcpipHeapMax** = 1536|未设置|

**注：**
* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服务需要 **MaxVolumes** 设置，因为该服务可能会在 ESXi 服务器上使用超过缺省数量的 NFS 安装。
* 配置设置的**未设置**值指示不会自动应用新设置，因为这需要重新引导 ESXi 服务器，这样可能有破坏性。

  建议将**未设置**配置设置更改为新值，以实现在所有实例上的一致性，并为存储扩展提供充分支持。对于所有 {{site.data.keyword.vmwaresolutions_short}} V2.2 和更高发行版，IBM 计划仅测试这些新设置。

  有关更多信息，请参阅[增大定义 ESXi 主机上 NFS 最大安装数的缺省值](https://kb.vmware.com/s/article/2239)。

## NSX 和端口组配置设置

查看下表以了解 vCenter Server 实例的 VMware NSX 和端口组配置设置的概述，以及发行版之间的差异。

这些设置会应用于新实例以及新实例 V2.2 或更高版本中的新集群。这些设置不会应用于 V2.1 或更低版本的现有实例中的新集群，也不会应用于升级到 V2.2 或更高版本的现有实例中的新集群。

表 4. vCenter Server 实例的 NSX 和端口组配置设置

|配置设置|V2.1 或更低版本|V2.2 或更高版本|   
|:------------- |:------------- |:------------- |
|NSX VXLAN 集群合作策略|故障转移|负载均衡 - SRCID|
|NSX VXLAN 集群 VTEP|1|2|
|主实例的分段标识池|6000-8000|6000-7999|  
|后续辅助实例的分段标识池|6000-8000|多站点配置中前一个结束范围 + 1 到多站点配置中前一个结束范围 + 2000|  
|端口组 SDDC-DPortGroup-VSAN（如果适用）|**活动上行链路**设置为 **uplink1**，**备用上行链路**设置为 **uplink2**|**活动上行链路**设置为 **uplink2**，**备用上行链路**设置为 **uplink1**|  
|端口组 SDDC-DPortGroup-Mgmt|**端口绑定**设置为**临时 - 无绑定**，**负载均衡**设置为**基于发起虚拟端口进行路由**|**端口绑定**设置为**静态绑定**，**负载均衡**设置为**基于物理 NIC 负载进行路由**|  
|端口组 SDDC-DPortGroup-External|**端口绑定**设置为**临时 - 无绑定**|**端口绑定**设置为**静态绑定**|

## 网络 MTU 配置设置

vSphere 集群使用两个 vSphere 分布式交换机 (vDS)，一个用于公用网络连接，另一个用于专用网络连接。

专用网络连接配置为使用大小为 9000 的巨型帧 MTU（最大传输单元），这将提高存储和 VMware vMotion 等大型数据传输的性能。此值是 VMware 和 {{site.data.keyword.cloud_notm}} 中允许的最大 MTU。

在 V2.1 或更高版本中，公用网络连接使用标准以太网 MTU，即 1500。必须保留此设置 1500；对此设置的任何更改都可能导致因特网上发生包分段。

查看下表以了解应用于公用和专用分布式虚拟交换机 (DVS) 的网络 MTU 配置设置的概述，具体取决于 vCenter Server 实例是否部署在 V2.1 或更高版本中。

表 5. 基于实例版本的 vCenter Server 实例和集群的 MTU 配置设置

|vDS|V2.1 或更高版本|V2.0 或更低版本（或从 V2.0 或更低版本升级）|
|:-------------- |:-------------- |:------------- |
|公共交换机|1500（缺省值）|9000（巨型帧）|
|专用交换机|9000（巨型帧）|9000（巨型帧）|

这些设置会应用于新实例以及部署在 V2.1 或更高版本中的实例中的新集群。这些设置还会应用于已升级到 V2.1 或更高版本的实例中多个 {{site.data.keyword.CloudDataCents_notm}} 中的新集群。

对于 V2.0 或更低版本的现有实例，或者升级到 V2.1 或更高版本的现有实例，这些设置不会应用于同一 {{site.data.keyword.CloudDataCent_notm}} 中的新集群。

对于在 V2.0 或更低版本中部署的实例，建议将公共交换机 MTU 设置更新为 1500。

### 更新公共交换机 MTU 设置

要更新公共交换机的 MTU 设置，请在 VMware vSphere Web Client 中完成以下步骤：
1. 右键单击 vDS，然后单击**编辑设置**。
2. 在**属性**选项卡上，选择**高级**选项。
3. 确保将**最大 MTU** 值设置为 1500。

   **注**：更改 vDS 中的 MTU 大小后，连接的上行链路（物理 NIC）将停止，然后重新运行。这样一来，使用上行链路的 VM 会短暂中断。因此，建议在安排的停机时间内规划 MTU 设置更新。

### 相关链接

* [VMware ESXi 和 ESX 的构建号和版本 (2143832)](https://kb.vmware.com/s/article/2143832)
* [VMware vCenter Server 的构建号和版本 (2143838)](https://kb.vmware.com/s/article/2143838)
* [在虚拟分布式交换机上启用巨型帧](https://kb.vmware.com/s/article/1038827)
* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} 保护数据表](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040)
* [vCenter Server 概述](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html)
* [规划 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter/vc_planning.html)
