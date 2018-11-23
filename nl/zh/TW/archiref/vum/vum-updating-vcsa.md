---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

# VCSA 更新及 SSO 鏈結的 vCenter

## VCSA 更新

VUM 未更新 VCSA，因此本節說明更新此應用裝置的處理程序。VMware vCenter Server on {{site.data.keyword.cloud}} 實例中所部署的 VCSA 沒有網際網路存取，因此應該先將更新組合下載至跳躍伺服器。

透過應用裝置管理主控台來更新 VCSA，而非 vSphere Web Client。使用瀏覽器、VCSA IP 位址及埠 5480 來存取 VCSA 應用裝置管理主控台。

您應該在更新之前起始應用裝置的 Snapshot 或 VCSA 備份。請確定所有工作都如預期般運作，然後在幾天內移除 Snapshot，以避免效能降低。此外，在嘗試任何升級之前，請先檢閱版本注意事項。

若要更新 VCSA，請遵循下列步驟：
1. 您可以移至 VMware 修補程式[下載中心](https://my.vmware.com/group/vmware/patch#search)、登入並從**依產品搜尋**功能表中選擇 VC，來下載更新。選取適當的修補程式，然後按一下**下載**。
2. 使用 vSphere Web Client，將 ISO 檔案上傳至 vCenter 資料儲存庫。
3. 將更新 ISO 檔案裝載至 vCenter Server。
4. 建立 vCenter Server 的 Snapshot。
5. 登入 vCenter 應用裝置管理主控台，網址為：`https://vcenterip:5480`
6. 移至**更新**區段，選取**檢查更新**，然後選取**檢查 CDROM**。應該會列出更新。
7. 選取**安裝更新**及**接受** EULA。即會安裝更新。
8. 更新完成之後，您必須返回應用裝置管理主控台，並選擇重新啟動主控台。
9. 重新登入 vSphere Web Client，檢查以尋找所有錯誤。請執行手動掃描 VUM、**首頁** > **主機及叢集**，選取資料中心或叢集，然後選取 **Update Manager** 標籤，再按一下**掃描更新**。如果這會導致錯誤，請參閱 [Resetting VMware Update Manager database on a vCenter Server appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284)。
10. 測試之後，如果您需要取消，請回復為 Snapshot，或使用先前的備份來還原 vCenter。

## SSO 鏈結的 vCenter

如果您具有主要及次要 vCenter Server 實例，則 VCSA 配置為處在單一 vCenter Single Sign-On (SSO) 網域中。每個 VCSA 都會有已部署的 VUM 實例。您修改的配置內容只會套用至您指定的 VUM 實例，而且不會延伸到群組中的其他實例。

您可以藉由從導覽列選取用於登錄 VUM 實例的 VCSA 名稱，來指定 VUM 實例。您也可以管理基準線及基準線群組，以及僅掃描及重新修補用於登錄 VUM 實例之 VCSA 所管理的庫存物件。

### 相關鏈結

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) 上的 VMware 解決方案（示範）
