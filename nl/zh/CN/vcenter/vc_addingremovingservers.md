---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# 扩展和收缩 vCenter Server 实例的容量

可以根据业务需求，通过添加或除去 ESXi 服务器，扩展或收缩 VMware vCenter Server 实例的容量。

如果初始集群将 vSAN 作为其存储器，那么在部署后添加一个或多个 ESXi 服务器可以增加集群存储容量。

## 开始之前

* 不要通过 VMware vSphere Web Client 来添加或除去 ESXi 服务器。在 vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_short}} 控制台同步。
* 使用 NFS 存储器的 vCenter Server 实例必须至少具有 2 个 ESXi 服务器。对于在 V2.1 或更高版本中部署的实例，可以将缺省集群扩展为最多具有 51 个 ESXi 服务器。每个非缺省集群可以扩展为最多具有 59 个 ESXi 服务器。
* 使用 vSAN 存储器的 vCenter Server 实例必须至少具有 4 个 ESXi 服务器。
* 在除去安装有 F5 on {{site.data.keyword.cloud_notm}} 或 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的 ESXi 服务器之前，必须将 F5 BIG-IP 和 FortiGate VM 迁移到与当前托管 VM 的 ESXi 服务器不同的 ESXi 服务器。
* 在除去安装了 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服务的 ESXi 服务器之前，请确保没有任何活动（失败或正在进行）的备份或复原操作，因为这些活动的操作可能会阻止除去 ESXi 服务器。
* 除去 ESXi 服务器时，这些服务器会置于维护模式，接着会迁移在这些服务器上运行的所有虚拟机 (VM)，然后从 vCenter Server 中除去这些服务器。为了最大程度地控制 VM 的重新定位，建议您先将要除去的 ESXi 服务器置于维护模式，然后使用 VMware vSphere Web Client 来手动迁移在这些 ESXi 服务器上运行的 VM。在此之后，使用 {{site.data.keyword.vmwaresolutions_full}} 控制台来除去 ESXi 服务器。
* 对于在 V2.0 或更低版本中部署的 vCenter Server 实例，可以将每个集群扩展为最多具有 32 个 ESXi 服务器。一次可以添加的 {{site.data.keyword.baremetal_short}} 数量如下：
   * 对于**小型**、**中型**和**大型**配置，一次可以添加 1 到 10 个 ESXi 服务器。
   * 对于**定制**配置，一次可以添加 1 到 20 个 ESXi 服务器。有关最少 ESXi 服务器数的更多信息，请参阅[双节点 vCenter Server 实例具有高可用性吗？](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## 过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在 **vCenter Server 实例**表中，单击要扩展或收缩其容量的实例。
3. 在左侧导航窗格上，单击**基础架构**。
4. 在**集群**表中，单击要在其中添加或除去 ESXi 服务器的集群。
5. 要添加 ESXi 服务器，请完成以下步骤：
   1. 在 **ESXi 服务器**部分中，单击**添加**。
   2. 在**添加服务器**窗口中，输入要添加的服务器数，复查估算成本，然后单击**添加**。
6. 要除去 ESXi 服务器，请在 **ESXi 服务器**部分中选择要除去的服务器，然后单击**除去**。

## 结果

启动添加或除去操作后，在实例状态从**可供使用**更改为**正在修改**时，可能会略有延迟。在对实例进行其他更改之前，请允许该操作完全完成。

系统将通过电子邮件通知您，正在处理添加或除去 ESXi 服务器的请求。与 ESXi 服务器关联的集群的状态会更改为**正在修改**。除去服务器时，请注意，{{site.data.keyword.cloud_notm}} 基础架构将在 {{site.data.keyword.cloud_notm}} 基础架构计费周期（通常为 30 天）结束时才会完全回收 ESXi 服务器。

**注意**：在所除去 ESXi 服务器的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。

如果在集群中看不到添加到列表中的新 ESXi 服务器，请检查电子邮件或控制台通知以查找有关该故障的更多详细信息。

## 相关链接

* [vCenter Server 材料清单](vc_bom.html)
* [针对 vCenter Server 实例的需求和规划](vc_planning.html)
* [添加、查看和删除 vCenter Server 实例的集群](vc_addingviewingclusters.html)
* [将主机置于维护模式](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) 处理器支持](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
