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

# 升級 vCenter Server with Hybridity Bundle 實例的 NSX 授權
{: #vc_hybrid_upgrade-lic}

您可以將實例的 VMware NSX 授權升級至更新版本。不支援授權版本降級。

## 升級 NSX 授權的程序
{: #vc_hybrid_upgrade-lic-nsx}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下要升級其 NSX 授權的實例。
3. 在**摘要**頁面上，驗證所有實例詳細資料都已正確顯示。然後，按一下左導覽窗格上的**基礎架構**，以驗證**基礎架構**頁面上的詳細資料。
   

   如果未顯示詳細資料，這可能表示因為防火牆規則或網路問題的緣故，而有 IBM CloudDriver 虛擬伺服器實例 (VSI) 連線問題。請先解決問題，再繼續下一步，否則升級可能會失敗。

4. 在左導覽窗格上，按一下**更新及修補程式**，然後按一下**升級**。在**升級 NSX 授權版本**視窗中，選取您要升級至的版本，然後按一下**升級**。

   授權升級會取代實例上的所有現有 NSX 授權。如果您在計費週期中途進行升級，則可能因為新舊授權重疊而產生其他費用。為了避免產生其他費用，建議在計費週期結束時升級授權。
   {:note}

## 相關鏈結
{: #vc_hybrid_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
