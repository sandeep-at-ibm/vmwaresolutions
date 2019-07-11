---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: VMware HCX standalone, HCX on-premises, tech specs HCX

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 內部部署 VMware HCX on IBM Cloud 實例的考量
{: #standalone_considerations}

請先檢閱下列考量，再安裝或刪除您針對內部部署使用所訂購的 HCX on {{site.data.keyword.cloud}} 實例。

具有 HCX on {{site.data.keyword.cloud_notm}} 的 vCenter Server 實例限制為來自內部部署站台只能有三個同時連線。
{:note}

## 安裝內部部署 HCX on IBM Cloud 實例時的考量
{: #standalone_considerations-install}

HCX on {{site.data.keyword.cloud_notm}} 元件必須同時安裝在 {{site.data.keyword.cloud_notm}} 及內部部署 vSphere 環境中。建議您先將 HCX on {{site.data.keyword.cloud_notm}} 服務安裝至 {{site.data.keyword.cloud_notm}} 上的 vCenter Server with Hybridity Bundle 實例，再安裝內部部署 HCX on {{site.data.keyword.cloud_notm}} 實例。如需相關資訊，請參閱[安裝 HCX on {{site.data.keyword.cloud_notm}} 時的考量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-hcx_considerations#hcx_considerations-install)。

### IP 位址需求
{: #standalone_considerations-ip}

如需完整 HCX 功能，您至少需要五個可以存取網際網路的專用 IP 位址。

### 內部部署 HCX on IBM Cloud 實例的部署程序
{: #standalone_considerations-deploy}

您必須完成下列作業，才能順利安裝內部部署 HCX on {{site.data.keyword.cloud_notm}} 實例：
1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，訂購內部部署 HCX on {{site.data.keyword.cloud_notm}} 實例。如需相關資訊，請參閱[訂購內部部署 HCX 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances)。
2. 在 **HCX Cloud 主控台**中，完成下列步驟：
    1. 按一下**管理**標籤。
    2. 在**系統更新**標籤上，按一下**要求下載鏈結**。
    3. 按一下**複製鏈結**，然後使用此鏈結將 HCX Enterprise Client 下載至內部部署環境，而且可以存取您的內部部署 vSphere 環境。
3. 在 VMware vSphere Web Client 中，將 HCX Enterprise Client 當成 HCX Manager 虛擬應用裝置 (HCX Manager) 部署至內部部署環境。

   您必須在專用網路上部署內部部署 HCX Manager，並容許它存取公用網路。您可以使用 NSX Edge、Vyatta 或類似閘道，容許透過網際網路存取內部部署 HCX Manager。如果用於專用網路存取及公用網路存取的閘道不同，則建議您使用預設閘道來容許公用網路存取及內部部署 **HCX Manager 管理主控台**，以建立進行專用網路存取的靜態路徑。
   {:note}
4. 完成 HCX Manager 部署之後，請使用 **HCX Manager 管理主控台**來啟動內部部署 HCX Manager。若要取得內部部署 HCX Manager 的啟動金鑰，請在 {{site.data.keyword.vmwaresolutions_short}} 主控台中訂購內部部署 HCX on {{site.data.keyword.cloud_notm}} 實例。如需相關資訊，請參閱[訂購內部部署 HCX 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances)。
5. 如果您已在訂購 HCX on {{site.data.keyword.cloud_notm}} 服務時使用自簽 SSL 憑證，則必須完成下列步驟，將憑證匯入至內部部署 HCX Manager：
    1. 在內部部署 **HCX Manager 管理主控台**中，按一下**管理**標籤。
    2. 從左導覽窗格中，按一下**授信 CA 憑證**，然後按一下右側的**匯入**。
    3. 按一下 **URL**，然後輸入您要套用之憑證的 URL（即 **HCX Cloud IP** (``https://<cloud-side public IP>``)），而您可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台的 HCX on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到它。
    4. 按一下**套用**。

您現在已完成內部部署 HCX Manager 的基本設定。您可以繼續將內部部署 HCX on {{site.data.keyword.cloud_notm}} 站台與雲端 HCX 站台配對。

如需相關資訊，請參閱 [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)。

## 刪除內部部署 HCX on IBM Cloud 實例之前的考量
{: #standalone_considerations-delete}

請先檢閱下列考量，再刪除針對內部部署使用所訂購的 HCX on {{site.data.keyword.cloud_notm}} 實例：
1. 在 VMware vSphere Web Client 中，移至 HCX 使用者介面，然後檢查下列項目：
    1. 確定未執行 HCX 移轉或災難回復作業。
    2. 確定已移除所有延伸網路。
    3. 確定已移除具有配對雲端站台的所有交互連接元件。

   您必須先完成所有先前步驟，然後再繼續下一步。否則，會取消內部部署 HCX on {{site.data.keyword.cloud_notm}} 實例的授權。如果授權已取消，則無法執行移轉，而且 HCF 元件可能會發生錯誤。  
   {:important}
2. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，刪除已訂購的內部部署 HCX on {{site.data.keyword.cloud_notm}} 實例，以取得內部部署 HCX Manager 的啟動金鑰。請先確定主控台中不再有已刪除的實例，再繼續進行下一步。

   如需相關資訊，請參閱[刪除內部部署 HCX on {{site.data.keyword.cloud_notm}} 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_deletingserviceinstances)。
3. 在 VMware vSphere Web Client 中，刪除內部部署 HCX Manager。

## 相關鏈結
{: #standalone_considerations-related}

* [檢視內部部署 HCX on {{site.data.keyword.cloud_notm}} 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_viewingserviceinstances)
* [HCX 術語名詞解釋](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [VMware Hybrid Cloud Extension 文件](https://cloud.vmware.com/vmware-hcx/resources)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
