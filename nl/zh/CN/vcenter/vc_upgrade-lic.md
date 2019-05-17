---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 升级 vCenter Server 实例的许可证
{: #vc_upgrade-lic}

仅当 VMware vCenter Server 实例处于 V2.3 或更高版本时，才能将相应实例升级到 vCenter Server with Hybridity Bundle。

IBM 业务合作伙伴用户无法选择升级到 Hybridity Bundle。
{:note}

## 将许可证升级到 Hybridity Bundle 之前
{: #vc_upgrade-lic-upgrade-prereq}

查看升级到 Hybridity Bundle 时执行的以下操作：

* 如果 vCenter Server 实例已安装 VMware NSX Base Edition，那么 NSX 许可证将自动升级到 NSX Advanced Edition。
* 如果 vCenter Server 实例具有 NFS 存储器，那么不会对 VMware vSAN 存储器收费。但是，Hybridity Bundle 随附的 vSAN 许可证要收费。


## 升级到 Hybridity Bundle 的过程（V2.3 或更高版本的实例）
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要升级到 Hybridity Bundle 的实例。
3. 在**摘要**页面上，验证是否所有实例详细信息都正确显示。然后在左侧导航窗格上，单击**基础架构**以验证**基础架构**页面上的详细信息。
   

   如果未显示详细信息，这可能指示由于防火墙规则或其他网络问题而导致 IBM CloudDriver VSI 发生连接问题。请解决该问题后，再继续下一步，否则升级可能会失败。

4. 在左侧导航窗格上，单击**更新和补丁**。
5. 要应用 Hybridity Bundle 许可证升级，请在**许可证升级**表中，单击**操作**列中的**升级**。复查估算成本，然后单击**升级**。
6. （可选）可以部署 VMware HCX on {{site.data.keyword.cloud_notm}} 服务。在**许可证升级**表中启用了 Hybridity Bundle 时，请完成以下步骤：
  1. 在**许可证升级**表中，单击**操作**列中的**部署 HCX on {{site.data.keyword.cloud_notm}}**。
  2. 滚动到 **HCX on {{site.data.keyword.cloud_notm}}** 卡，然后单击**选择服务**。
  3. 向下滚动并指定服务的必需设置，然后单击**下一步**。
  4. 查看服务的适用条款，复查估算成本，然后单击**下订单**。

## 升级 NSX 许可证的过程（V2.1 或更高版本实例）
{: #vc_upgrade-lic-nsx}

此过程适用于在 V2.1 或更高版本中部署的实例。对于在 V2.0 和更低版本中部署的实例，必须手动升级 NSX 许可证。

可以将实例的 NSX 许可证升级到更高版本。不支持许可证版本降级。

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要升级其 NSX 许可证的实例。
3. 在**摘要**页面上，验证是否所有实例详细信息都正确显示。然后在左侧导航窗格上，单击**基础架构**以验证**基础架构**页面上的详细信息。
   

   如果未显示详细信息，这可能指示由于防火墙规则或网络问题而导致 IBM CloudDriver 虚拟服务器实例 (VSI) 发生连接问题。请解决该问题后，再继续下一步，否则升级可能会失败。

4. 在左侧导航窗格上，单击**更新和补丁**，然后单击**升级**。在**升级 NSX 许可证修订版**窗口中，选择要升级到的修订版，然后单击**升级**。

   许可证升级将替换实例上的所有现有 NSX 许可证。如果在计费周期内进行升级，那么可能会因旧许可证与新许可证重叠而发生额外费用。为了避免发生额外费用，建议在计费周期结束时升级许可证。
   {:note}

## 相关链接
{: #vc_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
