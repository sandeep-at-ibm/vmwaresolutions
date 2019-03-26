---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-01"

---

# 更新 NSX
{: #vum-updating-nsx}

下列資訊是 NSX 更新處理程序的範例。請參閱 VMware 手冊，以瞭解您要升級至之 NSX 版本的更新處理程序。

如果需要同時升級 NSX 及 vSphere，VMware 建議您先完成 NSX 升級，然後再完成 vSphere 升級，因為 NSX VIB 是主機上所安裝的 ESXi 版本特有的。不過，如果手動使用下列工作流程完成，則建議如本文件所記載地使用 VUM（一次一部主機）：

1. **升級 ESXi** - ESXi 升級完成之後，主機會結束維護模式，不過，除非下一步完成，否則您無法將連接至邏輯交換器的 VM 移至主機。
2. **升級 NSX VIB** - 升級 VOB 並將主機移出維護模式之後，您可以將連接至邏輯交換器的 VM 移至主機。

使用 _my.vmware.com_ 中的下載，透過更新 NSX Manager 來更新 NSX。因此，您需要一個帳戶來下載更新。如果您搭配使用 {{site.data.keyword.cloud}} 訂閱授權與 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 實例，將無法使用 **my.vmware.com** 帳戶來下載更新項目。因此，您需要[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。

開始升級之前，請檢查升級問題及暫行解決方法的 NSX 注意事項。使用版本注意事項，驗證 vCenter 滿足 NSX 的新系統需求。

如果您已安裝來自 VMware 事業夥伴的任何其他軟體，請參閱事業夥伴文件，以取得相容性及升級詳細資料。如果您已部署 vCenter Server 主要實例及次要實例，且具有跨 vCenter NSX 環境，請參閱版本注意事項中的正確升級處理程序。

在跨 vCenter NSX 環境中，會先更新「主要 NSX Manager」應用裝置，接著再更新所有次要 NNSX Manager 應用裝置。
**不支援降級**，因此，請先備份 NSX Manager，再繼續升級，在 NSX Manager 備份期間，會備份所有 NSX Edge 配置、邏輯路由器及 Edge Services Gateway。

順利升級 NSX Manager 之後，就無法降級 NSX。建議在協議的維護時間內執行所有維護活動，因此，請遵循您的企業指引。建議在單一運作中斷時間範圍內升級所有 NSX 元件，以讓關閉時間降到最少，並減少功能問題。NSX 升級處理程序可能需要一些時間，因此，請務必瞭解 NSX 部署升級順序：
* NSX Manager
* NSX Controller 叢集
* NSX Host 叢集
* 在 NSX Manager 升級之後隨時可以升級 Edge Services Gateway
* 來賓內部檢查（如果已使用），請遵循版本注意事項中的指示

工作流程如下：
1. 登入跳躍伺服器，然後開啟瀏覽器。
2. 使用 _my.vmware.com_ 認證，導覽至下載區段，並搜尋 _NSX for vSphere_。
3. 選取您需要的版本。
4. 在下載頁面上，選取**升級組合、立即下載**。
5. 下載至適當的資料夾。
6. **升級 NSX Manager**：
  - 使用「IC4VS 主控台」中所記載的 IP 位址及認證登入「NSX Manager 虛擬應用裝置」，然後按一下首頁上的「升級」按鈕。
  - 登入 NSX Manager。
  - 在**應用裝置管理**下，按一下**備份及還原**。
  - 按一下「備份」，然後輸入適當的檔名。VMware 建議您先重新安裝 NSX Manager 應用裝置，再還原 NSX Manager 資料。雖然現有 NSX Manager 應用裝置上的還原作業可能有作用，但未正式予以支援。最佳作法是記下 NSX Manager 應用裝置的 IP 設定，因此可以使用它們來指定新部署 NSX Manager 應用裝置的 IP 資訊及備份位置資訊。
  - 在右上方，按一下**上傳組合**，然後上傳您從 _my.vmware.com_ 下載的檔案。
  - 閱讀升級資訊，並選取是否要啟用 SSH 並參與「VMware 客戶體驗改進計畫」。
  - 按一下**升級**。
  - 上傳完成時，系統會將您重新導向至 NSX Manager 登入頁面。重新登入，並驗證現行軟體版本顯示正確無誤。
7. **升級 NSX Controller 叢集**：
  - 開啟 vSphere Web Client，並登入 VCSA。
  - 導覽至**首頁** > **網路及安全** > **安裝**，選取**管理**標籤，然後按一下「控制器叢集狀態」直欄中的**升級可用**。
  - 逐一升級並重新啟動環境中的控制器。在您起始升級之後，系統會下載升級檔案、升級每個控制器、重新啟動每個控制器，以及更新每個控制器的升級狀態。
8. **升級 NSX Host 叢集**：
  - 升級 NSX Manager 及 NSX Controller 之後，NSX VIB 會在 vSphere ESXi 主機上更新主機叢集。
  - 在 vSphere Web Client 中，導覽至**首頁** > **網路及安全** > **安裝**，然後選取**主機準備**標籤。對於您要升級的每個叢集，按一下**升級可用**。「安裝狀態」會顯示「安裝中」。
  - 叢集「安裝狀態」會顯示_未備妥_。按一下**未備妥**以顯示相關資訊，然後按一下**全部解決**來嘗試完成 VIB 安裝。主機會進入維護模式，並在必要時重新開機，以完成升級。「安裝狀態」直欄會顯示「安裝中」。升級完成之後，「安裝狀態」直欄會顯示綠色勾號及已升級的 NSX 版本。
9. **Edge Services Gateway**：
  - 在升級處理程序期間，會一起部署新的邊緣虛擬應用裝置與現有的邊緣虛擬應用裝置。新的 Edge 備妥時，會中斷舊 Edge vNIC 的連線，並且會連接新的 Edge vNIC。新的 Edge 接著會傳送無償 ARP (GARP) 封包，以更新已連接交換器的 ARP 快取。部署 HA 時，升級處理程序會執行兩次。此處理程序可能會暫時影響封包轉遞。
  - 在 vSphere Web Client 中，選取**網路及安全** > **NSX Edge**。對於每個 NSX Edge 實例，選取**動作**功能表中的**升級版本**。
  - 順利升級 NSX Edge 之後，「狀態」為「已部署」，而且「版本」直欄會顯示新的 NSX 版本。如果 Edge 無法升級且未回復至舊版本，請按一下**重新部署 NSX Edge** 圖示，然後重試升級。

## 相關鏈結
{: #vum-updating-nsx-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware)（示範）
