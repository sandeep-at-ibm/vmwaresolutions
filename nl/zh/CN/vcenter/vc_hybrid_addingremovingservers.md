---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vCenter Server Hybridity add host, add server vCenter Server Hybridity, remove host vCenter Server Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 扩展和收缩 vCenter Server with Hybridity Bundle 实例的容量
{: #vc_hybrid_addingremovingservers}

可以根据业务需求，通过添加或除去 ESXi 服务器，扩展或收缩 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 实例的容量。

从 V3.1 发行版开始，您可以通过选择现有配置或不同于集群中现有主机的替代配置，将新的 ESXi 服务器添加到现有集群。现有配置可用于在订购新服务器时进行即时选择。为了避免性能或稳定性问题，建议集群使用相同或类似的 CPU、RAM 和存储器配置。此功能对于同一集群中的硬件更新非常有用。一个集群只能有一种类型的存储器。

从 V2.9 发行版开始，您可以在集群处于维护模式时将新的 ESXi 服务器添加到集群。此外，您还可以跨多个集群同时添加或除去 ESXi 服务器。可同时进行以下操作：

* 向一个集群添加主机，并向其他集群添加主机。
* 从一个集群中除去主机，并从其他集群中除去主机。
* 向一个集群添加主机，并从其他集群除去主机。
* 从一个集群除去主机，并向其他集群添加主机。

由于初始集群将 vSAN 作为其存储器，因此在部署后添加一个或多个 ESXi 服务器可以增加集群存储容量。

## 向 vCenter Server with Hybridity Bundle 实例添加 ESXi 服务器
{: #vc_hybrid_addingremovingservers-adding}

### 在添加 ESXi 服务器之前
{: #vc_hybrid_addingremovingservers-adding-prereq}

* 尽可能使用 {{site.data.keyword.vmwaresolutions_full}} 控制台添加 ESXi 服务器，因为在 VMware vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_short}} 控制台同步。因此，将 ESXi 服务器添加到 vCenter Server 仅适用于内部部署 ESXi 服务器，或者无法或不会在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理的 ESXi 服务器。
* vSAN 存储器至少需要 4 个 ESXi 服务器。

## 添加 ESXi 服务器的过程
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要扩展容量的实例。
3. 在左侧导航窗格上，单击**基础架构**。
4. 在**集群**表中，单击要在其中添加 ESXi 服务器的集群。
5. 在 **ESXi 服务器**表中，单击**添加**。
6. 在**添加服务器**窗口中，输入要添加的服务器数。
7. (可选）选中此复选框以在维护模式下添加服务器。缺省情况下，选中了此复选框。

   当您供应新的 ESXi 服务器时，如果未选中**维护方式**复选框，那么虚拟机 (VM) 会立即迁移到新服务器。在迁移开始之前，您不会收到确认消息。
{:important}

8. 填写裸机配置。
   * 从集群中的现有主机选择配置。
   * 选择新的 {{site.data.keyword.baremetal_short_sing}} 配置并指定 CPU 型号和 RAM 大小。
9. 填写存储配置。指定容量和高速缓存磁盘的磁盘类型、磁盘数和 vSAN 许可证版本。如果需要更多存储器，请选中**高性能 Intel Optane** 框。
10. 查看估算成本并单击**添加**。

  您还可以通过单击**添加到估算**来将供应的资源添加到 {{site.data.keyword.cloud_notm}} 估算工具**。如果要与您可能考虑购买的其他 {{site.data.keyword.cloud_notm}} 资源一起估算所选 {{site.data.keyword.vmwaresolutions_short}} 资源的成本，那么这非常有用。

### 添加 ESXi 服务器后的结果
{: #vc_hybrid_addingremovingservers-adding-results}

1. 当实例状态从**可供使用**变为**正在修改**时，您在控制台上可能会遇到轻微延迟。在对实例进行更多更改之前，请允许该操作完全完成。
2. 系统将通过电子邮件通知您，正在处理添加 ESXi 服务器的请求。在控制台上，与 ESXi 服务器关联的集群的状态会更改为**正在修改**。
3. 如果在集群中看不到添加到列表中的新 ESXi 服务器，请检查电子邮件或控制台通知以查找有关该故障的更多详细信息。

如果要在维护模式下添加 ESXi 服务器，那么在除去集群的维护方式之前，虚拟机 (VM) 不会迁移到新服务器。   
{:important}

## 从 vCenter Server with Hybridity Bundle 实例中除去 ESXi 服务器
{: #vc_hybrid_addingremovingservers-removing}

### 在除去 ESXi 服务器之前
{: #vc_hybrid_addingremovingservers-removing-prereq}

* 尽可能使用 {{site.data.keyword.vmwaresolutions_full}} 控制台除去 ESXi 服务器，因为在 vSphere Web Client 上所做的更改不会与 {{site.data.keyword.vmwaresolutions_short}} 控制台同步。因此，从 vCenter Server 中除去 ESXi 服务器仅适用于内部部署 ESXi 服务器，或者无法或不会在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理的 ESXi 服务器。
* vSAN 存储器至少需要 4 个 ESXi 服务器。
* 在除去安装有 F5 on {{site.data.keyword.cloud_notm}} 或 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务的 ESXi 服务器之前，必须将 F5 BIG-IP 和 FortiGate VM 迁移到与托管 VM 的 ESXi 服务器不同的 ESXi 服务器。
* 在除去安装了 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服务的 ESXi 服务器之前，请确保没有任何活动（失败或正在进行）的备份或复原操作，因为这些活动的操作可能会阻止除去 ESXi 服务器。
* 除去 ESXi 服务器时，会将这些服务器置于维护模式，接着会迁移在这些服务器上运行的所有虚拟机 (VM)，然后从 vCenter Server 中除去这些服务器。为了最大程度地控制 VM 的重新定位，建议您先将要除去的 ESXi 服务器置于维护模式，然后使用 VMware vSphere Web Client 来手动迁移在这些 ESXi 服务器上运行的 VM。在此之后，使用 {{site.data.keyword.vmwaresolutions_short}} 控制台来除去 ESXi 服务器。

## 除去 ESXi 服务器的过程
{: #vc_hybrid_addingremovingservers-removing-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要压缩容量的实例。
3. 在左侧导航窗格上，单击**基础架构**。
4. 在**集群**表中，单击要从中除去 ESXi 服务器的集群。
5. 在 **ESXi 服务器**表中，选择要除去的服务器，然后单击**除去**。

### 除去 ESXi 服务器后的结果
{: #vc_hybrid_addingremovingservers-removing-results}

1. 当实例状态从**可供使用**变为**正在修改**时，您在控制台上可能会遇到轻微延迟。在对实例进行其他更改之前，请允许该操作完全完成。
2. 系统将通过电子邮件通知您，正在处理除去 ESXi 服务器的请求。在控制台上，与 ESXi 服务器关联的集群的状态会更改为**正在修改**。
3. {{site.data.keyword.cloud_notm}} 基础架构将在 {{site.data.keyword.cloud_notm}} 基础架构计费周期（通常为 30 天）结束时完全回收 ESXi 服务器。

   在所除去 ESXi 服务器的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。
   {:note}

## 相关链接
{: #vc_hybrid_addingremovingservers-related}

* [vCenter Server 材料清单](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [针对 vCenter Server with Hybridity Bundle 实例的需求和规划](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [添加、查看和删除 vCenter Server with Hybridity Bundle 实例的集群](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [将主机置于维护模式](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:external}
* [Enhanced vMotion Compatibility (EVC) 处理器支持](https://kb.vmware.com/s/article/1003212){:external}
