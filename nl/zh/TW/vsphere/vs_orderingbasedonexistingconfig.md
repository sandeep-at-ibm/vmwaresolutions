---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 根據現有配置來訂購 vSphere 叢集

您可以根據您儲存的配置範本來訂購 VMware vSphere 叢集。您可以使用此程序，根據現有的叢集配置來定義新的叢集配置。

## 需求

請確定您已完成下列作業：
*  您已在**設定**頁面上配置 {{site.data.keyword.cloud}} 基礎架構認證。如需相關資訊，請參閱[使用者帳戶及設定](../vmonic/useraccount.html)。
*  您已檢閱 [vSphere 叢集的需求及規劃](vs_planning.html)中的需求及考量。
*  您已建立要重複使用的配置範本。

## 根據現有配置來訂購 vSphere 叢集的程序

1. 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格上的 **VMware**，然後按一下**虛擬資料中心**區段中的 **VMware vSphere**。
2. 在 **VMware vSphere on IBM Cloud** 頁面上，按一下**建立**。  
3. 按一下**建立新的項目**標籤，然後從**叢集配置**清單中選取配置範本。
4. 輸入新的叢集名稱。
5. 檢閱自動完成的叢集設定，並根據您的需要更新設定。如需設定的相關資訊，請參閱[訂購新的 vSphere 叢集](vs_orderinginstances.html)。
6. 在**訂單摘要**窗格中，驗證實例配置及預估成本。
   * 若要將配置儲存為範本而不下訂單，請按一下**儲存配置**。
   * 若要下訂單，請確定要收費的帳戶正確，請檢閱並接受條款，然後按一下**佈建**。

   僅安裝 {{site.data.keyword.baremetal_short}}。您負責在叢集部署之後安裝及配置各種元件，例如 VMware vCenter、VMware NSX、VMware vSAN。{:note}

## 結果

如果您將叢集配置儲存為範本，則會收到主控台通知，指出已儲存配置。然後，您可以在**叢集配置**清單中找到該範本。

如果您已下訂單，則會自動啟動叢集的部署。您會收到電子郵件確認，指出正在處理該訂單。當叢集已備妥可供使用時，也會透過電子郵件通知您。

vSphere 叢集與 vCenter Server 及 Cloud Foundation 實例不同，並不會顯示在**已部署的實例**頁面上。{:note}

### 相關鏈結

* [訂購新的 vSphere 叢集](vs_orderinginstances.html)
* [擴充現有的 vSphere 叢集](vs_scalingexistingclusters.html)
* [擴充在主控台以外建立的叢集](vs_orderingforclustersoutside.html)
