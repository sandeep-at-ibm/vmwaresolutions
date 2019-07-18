---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vCenter Server delete instance, delete vCenter Server, delete multi-site

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 刪除多站台配置中的 vCenter Server 實例
{: #vc_deletinginstance_multi}

在規劃刪除屬於多站台配置的 vCenter Server 實例之前，請注意下列特殊考量。

當您刪除 vCenter Server 實例時，會循序釋出下列元件：
1. 所有已部署的服務
2. 支援與服務費用
3. VMware 產品授權
4. ESXi 伺服器
5. 子網路
6. VLAN

由於資源相依關係，當您刪除實例時，不會立即釋放實例中的元件。例如，在 {{site.data.keyword.cloud}} 基礎架構完全收回 ESXi 伺服器（這發生在 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束時）之前，無法刪除子網路及 VLAN。當 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束（通常是 30 天），就會刪除子網路和 VLAN，並且完成實例刪除。

將針對已刪除的實例，向您收取到 {{site.data.keyword.cloud_notm}} 基礎架構計費週期結束為止的費用。
{:note}

## 在多站台配置中刪除 vCenter Server 實例的程序
{: #vc_deletinginstance_multi-procedure}

1. 從次要 vCenter Server 實例移除所有服務。
2. 確定未將任何 NSX 物件擴充至您要刪除的次要實例。
3. 從主要 SSO（單一登入）網域刪除次要 vCenter Server。如需相關資訊，請參閱 [Unregister vCenter Server from Single Sign-On](https://kb.vmware.com/s/article/2106736){:external}。
4. 將本端網域控制站 VSI（虛擬服務實例）降級。如需相關資訊，請參閱 [Demoting domain controllers and domains](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:external}。
5. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台刪除次要 vCenter Server 實例。
6. 針對多站台配置中的所有次要 vCenter Server 實例，重複步驟 1 - 5。
7. 刪除所有次要實例之後，您也可以從 {{site.data.keyword.vmwaresolutions_short}} 主控台刪除主要實例。

## 相關鏈結
{: #vc_deletinginstance_multi-related}

* [刪除 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance)
* [訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [取消虛擬伺服器](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)
