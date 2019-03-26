---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 扩展和收缩 vCenter Server with NSX-T 实例的容量
{: #vc_nsx-t_addingremovingservers}

可以根据业务需求，通过添加或除去 ESXi 服务器或网络文件系统 (NFS) 存储器，扩展或收缩 VMware vCenter Server with NSX-T 实例的容量。

您可以在集群处于维护模式时将新的 ESXi 服务器添加到集群。此外，您还可以跨多个集群同时添加或除去 ESXi 服务器。可同时进行以下操作：

* 将主机添加到 **cluster1**，并将主机添加到其他集群。
* 从 **cluster1** 中除去主机，并从其他集群中除去主机。
* 将主机添加到 **cluster1**，并从其他集群除去主机。
* 从 **cluster1** 中除去主机，并将主机添加到其他集群。

可以在现有 NFS 或 vSAN vCenter Server with NSX-T 集群中添加或除去 NFS 存储共享。
{:note}

如果初始集群将 vSAN 作为其存储器，那么在部署后添加一个或多个 ESXi 服务器可以增加集群存储容量。

## 向 vCenter Server with NSX-T 实例添加 ESXi 服务器
{: #vc_nsx-t_addingremovingservers-adding}

### 在添加 ESXi 服务器之前
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* 不要通过 VMware vSphere Web Client 来添加 ESXi 服务器。在 vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_full}} 控制台同步。
* 使用 NFS 存储器的 vCenter Server with NSX-T 实例必须至少具有 3 个 ESXi 服务器。可以将缺省集群扩展为最多具有 51 个 ESXi 服务器。每个非缺省集群可以扩展为最多具有 59 个 ESXi 服务器。
* 使用 vSAN 存储器的 vCenter Server with NSX-T 实例必须至少具有 4 个 ESXi 服务器。

### 添加 ESXi 服务器的过程
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要扩展容量的实例。
3. 在左侧导航窗格上，单击**基础架构**。
4. 在**集群**表中，单击要在其中添加 ESXi 服务器的集群。
5. 在 **ESXi 服务器**部分中，单击**添加**。
6. 在**添加服务器**窗口中，输入要添加的服务器数。
7. (可选）选中此复选框以在维护模式下添加服务器。
8. 查看估算成本并单击**添加**。

### 添加 ESXi 服务器后的结果
{: #vc_nsx-t_addingremovingservers-adding-results}

1. 当实例状态从**可供使用**变为**正在修改**时，您在控制台上可能会遇到轻微延迟。在对实例进行更多更改之前，请允许该操作完全完成。
2. 系统将通过电子邮件通知您，正在处理添加 ESXi 服务器的请求。在控制台上，与 ESXi 服务器关联的集群的状态会更改为**正在修改**。
3. 如果在集群中看不到添加到列表中的新 ESXi 服务器，请检查电子邮件或控制台通知以查找有关该故障的更多详细信息。

如果要在维护模式下添加 ESXi 服务器，那么在除去集群的维护方式之前，虚拟机 (VM) 不会迁移到新服务器。   
{:important}

## 从 vCenter Server with NSX-T 实例中除去 ESXi 服务器
{: #vc_nsx-t_addingremovingservers-removing}

### 在除去 ESXi 服务器之前
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* 不要通过 VMware vSphere Web Client 来除去 ESXi 服务器。在 vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_short}} 控制台同步。
* 使用 NFS 存储器的 vCenter Server with NSX-T 实例必须至少有 3 个 ESXi 服务器，使用 vSAN 存储器的 vCenter Server with NSX-T 实例必须至少有 4 个 ESXi 服务器。
* 除去 ESXi 服务器时，会将这些服务器置于维护模式，接着会迁移在这些服务器上运行的所有 VM，然后从 vCenter Server 中除去这些服务器。为了最大程度地控制 VM 的重新定位，建议您先将要除去的 ESXi 服务器置于维护模式，然后使用 VMware vSphere Web Client 来手动迁移在这些 ESXi 服务器上运行的 VM。在此之后，使用 {{site.data.keyword.vmwaresolutions_short}} 控制台来除去 ESXi 服务器。

### 除去 ESXi 服务器的过程
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要压缩容量的实例。
3. 在左侧导航窗格上，单击**基础架构**。
4. 在**集群**表中，单击要从中除去 ESXi 服务器的集群。
5. 在 **ESXi 服务器**部分中，选择要除去的服务器，然后单击**除去**。

### 除去 ESXi 服务器后的结果
{: #vc_nsx-t_addingremovingservers-removing-results}

1. 当实例状态从**可供使用**变为**正在修改**时，您在控制台上可能会遇到轻微延迟。在对实例进行更多更改之前，请允许该操作完全完成。
2. 系统将通过电子邮件通知您，正在处理除去 ESXi 服务器的请求。在控制台上，与 ESXi 服务器关联的集群的状态会更改为**正在修改**。
3. {{site.data.keyword.cloud_notm}} 基础架构将在 {{site.data.keyword.cloud_notm}} 基础架构计费周期（通常为 30 天）结束时完全回收 ESXi 服务器。

   在所除去 ESXi 服务器的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。
   {:note}

## 向 vCenter Server with NSX-T 实例添加 NFS 存储器
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### 添加 NFS 存储器之前
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

不要通过 VMware vSphere Web Client 来添加 NFS 存储器。在 vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_short}} 控制台同步。IBM 不会管理手动添加到实例的 NFS 文件共享。

### 添加 NFS 存储器的过程
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要扩展容量的实例。
3. 在左侧导航窗格上，单击**基础架构**。
4. 在**集群**表中，单击要在其中添加 NFS 存储器的集群。
5. 在**存储**部分中，单击**添加**。
6. 在**存储**窗口中，填写存储配置。
   * 如果要向所有文件共享添加和配置相同设置，请指定**共享数**、**性能**和**大小 (GB)**。
   * 如果要单独添加和配置文件共享，请选择**单独配置共享**，单击**添加共享存储器**标签旁边的 **+** 图标，然后为每个单独的文件共享选择**性能**和**大小 (GB)**。必须至少选择一个文件共享。
7. 单击**添加 NFS 存储器**。

### 添加 NFS 存储器后的结果
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. 当实例状态从**可供使用**变为**正在修改**时，您在控制台上可能会遇到轻微延迟。在对实例进行更多更改之前，请允许该操作完全完成。
2. 系统将通过电子邮件通知您，正在处理添加 NFS 存储器的请求。在控制台上，与 NFS 存储器关联的集群的状态会更改为**正在修改**。
3. 如果在集群中看不到添加到列表中的新 NFS 存储器，请检查电子邮件或控制台通知以查找有关该故障的更多详细信息。

## 从 vCenter Server with NSX-T 实例除去 NFS 存储器
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### 除去 NFS 存储器之前
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* 不要通过 VMware vSphere Web Client 来除去 NFS 存储器。在 vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_short}} 控制台同步。
* 除去 NFS 存储器之前，请确保已除去位于该存储器上的所有 VM。
* 确保计划除去的共享与正确的 vCenter Server 实例相关联。
* 该集群必须处于**可供使用**状态。

### 除去 NFS 存储器的过程
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要压缩容量的实例。
3. 在左侧导航窗格上，单击**基础架构**。
4. 在**集群**表中，单击要从中除去 NFS 存储器的集群。
5. 在**存储**部分中，选择要除去的存储共享，然后单击**删除**。
6. 单击**除去存储器**窗口中的**除去**。

### 除去 NFS 存储器后的结果
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. 当实例状态从**可供使用**变为**正在修改**时，您在控制台上可能会遇到轻微延迟。在对实例进行更多更改之前，请允许该操作完全完成。
2. 系统将通过电子邮件通知您，正在处理除去 NFS 存储器的请求。在控制台上，与 NFS 存储器关联的集群的状态会更改为**正在修改**。
3. {{site.data.keyword.cloud_notm}} 基础架构将在 {{site.data.keyword.cloud_notm}} 基础架构计费周期（通常为 30 天）结束时完全回收 NFS 存储器。

   在所除去 NFS 存储器的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。
{:note}

## 相关链接
{: #vc_nsx-t_addingremovingservers-related}

* [vCenter Server 材料清单](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [针对 vCenter Server 实例的需求和规划](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [订购 vCenter Server with NSX-T 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [添加、查看和删除 vCenter Server with NSX-T 实例的集群](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
* [将主机置于维护模式](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) 处理器支持](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
