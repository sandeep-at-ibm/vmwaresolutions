---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-04"

---

# 擴充現有的 vSphere 叢集

您可以橫向擴充已訂購或儲存在 {{site.data.keyword.vmwaresolutions_full}} 主控台中的 VMware vSphere 叢集。若要這樣做，請新增 ESXi 伺服器，或為叢集訂購 FortiGate 300 系列 Security Appliance HA 配對。

## 需求

請確定您已完成下列作業：
*  您已在**設定**頁面上配置 {{site.data.keyword.cloud_notm}} 基礎架構認證。如需相關資訊，請參閱[使用者帳戶及設定](../vmonic/useraccount.html)。
*  您已檢閱 [vSphere 叢集的需求及規劃](vs_planning.html)中的需求及考量。
*  您已收到電子郵件，內含您想要擴充之叢集已經可以使用的確認。

## 擴充現有叢集的程序

1. 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格上的 **VMware**，然後按一下**虛擬資料中心**區段中的 **VMware vSphere**。
2. 在 **VMware vSphere on IBM Cloud** 頁面上，按一下**建立**。  
3. 按一下**擴充現有項目**標籤，並從**叢集配置**清單中選取您要擴充的叢集。
4. 檢閱自動完成的叢集設定。
5. 在 **{{site.data.keyword.baremetal_short}}** 區段中，指定您要新增至叢集的 {{site.data.keyword.baremetal_short}} 數目。
6. 如果該叢集在其公用 VLAN 上不包括「FortiGate 300 系列 Security Appliance HA 配對」，則您可以訂購應用裝置。若要這樣做，請選取 **FortiGate Physical Appliance 300 系列 HA 對組**下的**購買隨附**勾選框。
7. 在**訂單摘要**窗格中，驗證實例配置及預估成本。
   * 若要將配置儲存為範本而不下訂單，請按一下**儲存配置**。
   * 若要下訂單，請確定要收費的帳戶正確，請檢閱並接受條款，然後按一下**佈建**。

### 結果

自動啟動叢集擴充。您會收到電子郵件確認，指出正在處理該訂單。當叢集已備妥可供使用時，會透過電子郵件通知您。

如果您擴充的叢集尚無法使用，則您可能會收到錯誤訊息。

**附註：**vSphere 叢集與 vCenter Server 及 Cloud Foundation 實例不同，並不會顯示在**已部署的實例**頁面上。

### 相關鏈結

* [訂購新的 vSphere 叢集](vs_orderinginstances.html)
* [根據現有配置來訂購 vSphere 叢集](vs_orderingbasedonexistingconfig.html)
* [擴充在主控台以外建立的叢集](vs_orderingforclustersoutside.html)
