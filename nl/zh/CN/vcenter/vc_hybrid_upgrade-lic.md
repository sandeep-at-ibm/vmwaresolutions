---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: NSX license, upgrade license, Hybridity license

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 升级 vCenter Server with Hybridity Bundle 实例的 NSX 许可证
{: #vc_hybrid_upgrade-lic}

可以将实例的 VMware NSX 许可证升级到更高版本。不支持许可证版本降级。

## 升级 NSX 许可证的过程
{: #vc_hybrid_upgrade-lic-nsx}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要升级其 NSX 许可证的实例。
3. 在**摘要**页面上，验证是否所有实例详细信息都正确显示。然后在左侧导航窗格上，单击**基础架构**以验证**基础架构**页面上的详细信息。
   

   如果未显示详细信息，这可能指示由于防火墙规则或网络问题而导致 IBM CloudDriver 虚拟服务器实例 (VSI) 发生连接问题。请解决该问题后，再继续下一步，否则升级可能会失败。

4. 在左侧导航窗格上，单击**更新和补丁**，然后单击**升级**。在**升级 NSX 许可证修订版**窗口中，选择要升级到的修订版，然后单击**升级**。

   许可证升级将替换实例上的所有现有 NSX 许可证。如果在计费周期内进行升级，那么可能会因旧许可证与新许可证重叠而发生额外费用。为了避免发生额外费用，建议在计费周期结束时升级许可证。
   {:note}

## 相关链接
{: #vc_hybrid_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
