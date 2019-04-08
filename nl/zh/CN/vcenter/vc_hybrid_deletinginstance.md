---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 删除 vCenter Server with Hybridity Bundle 实例
{: #vc_hybrid_deletinginstance}

要释放在 VMware vCenter Server with Hybridity Bundle 实例中订购的组件，请删除该实例。

删除 vCenter Server with Hybridity Bundle 实例时，会按顺序释放以下组件：
1. 所有部署的服务
2. 支持和服务费用
3. VMware 产品许可证
4. ESXi 服务器
5. 子网
6. VLAN

由于资源依赖关系，删除实例后，不会立即释放该实例中的组件。例如，在 {{site.data.keyword.cloud}} 基础架构完全回收 ESXi 服务器（在 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束时发生）后，才能删除子网和 VLAN。在 {{site.data.keyword.cloud_notm}} 基础架构计费周期（通常为 30 天）结束时，将删除子网和 VLAN，此时实例删除操作完成。

在所删除实例的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。
   {:note}

## 在资源页面中删除实例的过程
{: #vc_hybrid_deletinginstance-procedure1}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，找到要删除的实例。
3. 在**操作**列中，单击“删除”图标。
   实例的状态会更改为**正在删除**。成功删除实例后，会释放该实例的组件，并且实例的状态会更改为**已删除**。
4. 如果要在 {{site.data.keyword.vmwaresolutions_short}} 控制台中除去实例记录，请完成以下步骤：
   1. 在**操作**列中，再次单击“删除”图标。
   2. 在**删除实例**窗口中，单击**确定**。

## 在实例详细信息页面中删除实例的过程
{: #vc_hybrid_deletinginstance-procedure2}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要删除的实例。
3. 单击 **vCenter 控制台**旁边的溢出菜单图标，然后单击**删除实例**。
   实例的状态会更改为**正在删除**。成功删除实例后，会释放该实例的组件，并且实例的状态会更改为**已删除**。
4. 如果要在 {{site.data.keyword.vmwaresolutions_short}} 控制台中除去实例记录，请完成以下步骤：
   1. 再次单击 **vCenter 控制台**旁边的溢出菜单图标，然后单击**删除实例**。
   2. 在**删除实例**窗口中，单击**确定**。

## 相关链接
{: #vc_hybrid_deletinginstance-related}

* [删除多站点配置中的 vCenter Server with Hybridity Bundle 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance_multi)
* [订购 vCenter Server with Hybridity Bundle 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [查看 vCenter Server with Hybridity Bundle 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [扩展和收缩 vCenter Server with Hybridity Bundle 实例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
