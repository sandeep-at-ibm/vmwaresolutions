---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 升級 vCenter Server 實例的授權
{: #vc_upgrade-lic}

只有在您的實例是 2.3 版或更新版本時，才能將您的 VMware vCenter Server 實例升級至 vCenter Server with Hybridity Bundle。

「IBM 事業夥伴」使用者沒有升級至 Hybridity Bundle 的選項。
{:note}

## 將授權升級至 Hybrik Bundle 之前
{: #vc_upgrade-lic-upgrade-prereq}

檢閱您升級至 Hybich Bundle 時所採取的下列動作：

* 如果您的 vCenter Server 實例已安裝 VMware NSX Base 版本，則您的 NSX 授權將自動升級至 NSX Advanced 版本。
* 如果您的 vCenter Server 實例具有 NFS 儲存空間，則不會向您收取 VMware vSAN 儲存空間的費用。不過，會向您收取 Hybridity Bundle 隨附之 vSAN 授權的費用。

## 升級至 Hybridity Bundle 的程序（2.3 版或更新版本的實例）
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下要升級至 Hybridity Bundle 的實例。
3. 在**摘要**頁面上，驗證所有實例詳細資料都已正確顯示。然後，按一下左導覽窗格上的**基礎架構**，以驗證**基礎架構**頁面上的詳細資料。
   

   如果未顯示詳細資料，這可能表示因為防火牆規則或其他網路問題的緣故，而有 IBM CloudDriver VSI 連線問題。請先解決問題，再繼續下一步，否則升級可能會失敗。

4. 在左導覽窗格上，按一下**更新及修補程式**。
5. 若要套用 Hybridity Bundle 授權升級，請在**授權升級**表格中，按一下**動作**直欄中的**升級**。檢閱預估成本，然後按一下**升級**。
6. 您可以選擇性地部署 VMware HCX on {{site.data.keyword.cloud_notm}} 服務。在**授權升級**表格中啟用 Hybridity Bundle 後，請完成下列步驟：
  1. 在**授權升級**表格中，按一下**動作**直欄中的**部署 HCX on {{site.data.keyword.cloud_notm}}**。
  2. 捲動至 **HCX on {{site.data.keyword.cloud_notm}}** 卡片，然後按一下**選取服務**。
  3. 向下捲動，並指定服務的必要設定，然後按**下一步**。
  4. 檢閱適用於服務的條款、檢閱預估成本，然後按一下**下訂單**。

## 升級 NSX 授權的程序（2.1 版或更新版本的實例）
{: #vc_upgrade-lic-nsx}

此程序適用於已部署在 2.1 版或更新版本的實例。對於部署在 2.0 版及更早版本的實例，您必須手動升級 NSX 授權。

您可以將實例的 NSX 授權升級至更新版本。不支援授權版本降級。

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下要升級其 NSX 授權的實例。
3. 在**摘要**頁面上，驗證所有實例詳細資料都已正確顯示。然後，按一下左導覽窗格上的**基礎架構**，以驗證**基礎架構**頁面上的詳細資料。
   

   如果未顯示詳細資料，這可能表示因為防火牆規則或網路問題的緣故，而有 IBM CloudDriver 虛擬伺服器實例 (VSI) 連線問題。請先解決問題，再繼續下一步，否則升級可能會失敗。

4. 在左導覽窗格上，按一下**更新及修補程式**，然後按一下**升級**。在**升級 NSX 授權版本**視窗中，選取您要升級至的版本，然後按一下**升級**。

   授權升級會取代實例上的所有現有 NSX 授權。如果您在計費週期中途進行升級，則可能因為新舊授權重疊而產生其他費用。為了避免產生其他費用，建議在計費週期結束時升級授權。
   {:note}

## 相關鏈結
{: #vc_upgrade-lic-related}

* [vCenter Server with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
