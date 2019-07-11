---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

# 更新 vSAN 叢集
{: #vum-updating-vsan}

vSAN 會產生系統基準線及基準線群組以與 VUM 搭配使用，您可以使用這些建議的基準線，在您的 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 實例中使用 vSAN 來更新 vSphere ESXi 主機的軟體、修補程式及延伸規格。vSAN 6.6.1 以及更新版本會針對 vSAN 叢集產生自動化建置建議。vSAN 會結合《VMware 相容性手冊》及「vSAN 版本」型錄中的資訊與已安裝 vSphere ESXi 版本的相關資訊。

這些建議的更新提供最佳可用版本，讓您的硬體保持支援狀態。
* **vSAN 系統基準線** - 透過 VUM 的 vSAN 系統基準線提供 vSAN 建置建議。vSAN 會為每個 vSAN 叢集產生一個基準線群組，並列在「基準線」及「群組」標籤的「基準線」窗格中。VUM 會自動掃描每個 vSAN 叢集，以檢查是否符合基準線群組標準。不過，若要升級 vSAN 叢集，您必須透過 VUM 手動重新修補系統基準線，而且您可以在單一主機或整個叢集上重新修補 vSAN 系統基準線。
* **vSAN 版本型錄** - vSAN 版本型錄會維護可用版本、版本之喜好設定順序以及每個版本所需之重要修補程式的相關資訊。vSAN 需要網際網路連線功能才能存取版本型錄。您不需要在「客戶體驗改進計畫 (CEIP)」中登記，即可讓 vSAN 存取版本型錄。
* 使用 **vSAN 建置建議** - VUM 會根據《VMware 相容性手冊》之『硬體相容性清單 (HCL)』中的資訊來檢查已安裝的 vSphere ESXi 版本。它會根據現行「vSAN 版本」型錄，判斷每個 vSAN 叢集的正確升級路徑。vSAN 也會包括其系統基準線中建議版本的必要驅動程式及修補程式更新。vSAN 建置建議可確保每個 vSAN 叢集都保持為現行硬體相容性狀態或更好的狀態。如果 HCL 上不包括 vSAN 叢集裡的硬體，則 vSAN 會建議升級至最新版本。

vSAN 叢集升級會依下列作業序列執行：
* **啟用 vSAN 線上性能工作流程** - 此工作流程會在 VUM 中啟用 vSAN 基準線，以檢閱及重新修補更新。一開始只需要執行它，即可使用 VUM 來啟用 vSAN
* **必要條件** - 瞭解必要條件、處理程序及限制
* **升級 vCenter Server Appliance**。如需相關資訊，請參閱 [VCSA 更新及 SSO 鏈結的 vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa)。
* **升級 vSphere ESXi 主機** - 如需相關資訊，請參閱[建立基準線並連接至庫存物件](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines)。
* **升級 vSAN 磁碟格式** - 請參閱「升級 vSAN 磁碟格式」。升級磁碟格式是選用作業，但若要獲得最佳的結果，請升級物件以使用最新版本。磁碟內存格式會向完整 vSAN 特性集公開您的環境。

## 啟用 vSAN 線上性能工作流程
{: #vum-updating-vsan-enable-vsan-workflow}

使用下節中的作業，讓 vSAN 基準線可在 VUM 中使用。vSAN 6.6.1 以及更新版本會提供無縫自動更新處理程序，以確保 vSAN 叢集保持最新的可用版本，讓 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 實例維持在受支援狀態下，並提供：
* **vSAN 版本建議** - 使用《VMware 相容性手冊》、「vSAN 版本型錄」及基礎硬體配置狀態提示中的資訊自動產生。這也包括其系統基準線中建議版本的必要驅動程式及修補程式更新。
* **vSAN 建置建議** - 確保叢集維持現行硬體相容性狀態或更好的狀態。

確定 VCSA 是 vCenter 6.5 Patch 2 或更新版本，再繼續執行，因為這會修正一些 Proxy 使用問題。如需相關資訊，請參閱 [VCSA 更新及 SSO 鏈結的 vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa)。

若要查看 VUM 中的 vSAN 更新，請遵循 vSAN 線上性能工作流程。因此，「vSAN 線上性能」需要連接至 `vcsa.vmware.com` 和 `vmware.com` 站台，才能執行這些線上性能檢查。為了啟用「vSAN 線上性能工作流程」，我們需要：
* 配置 VCSA 來使用 Proxy。
* 配置 vSAN 來使用 Proxy。
* 啟用「客戶體驗改進計畫 (CEIP)」。
* 執行上傳測試，並驗證上傳有效。

首要步驟是將 my.vmware.com 認證新增至「vSAN 建置建議引擎」。成功登入之後，vSAN 會針對每個 vSAN 叢集產生建議更新的基準線群組。vSAN 系統基準線會列在「基準線」及「群組」標籤的「基準線」窗格中。

### 配置 VCSA 來使用 Proxy
{: #vum-updating-vsan-config-vcsa-proxy}

1.	從跳躍伺服器 Web 瀏覽器中，連接至「VCSA 管理介面」`https://<vCenter ip>:5480`
2.	使用 IBM Cloud for VMware Solutions 主控台中的認證，以 root 使用者身分登入 VCSA 管理介面。
3.	在「vCenter Server Appliance 管理介面」中，按一下**網路**，然後按一下**管理**。
4.	若要配置 Proxy 伺服器，請在「Proxy 設定」窗格中按一下**編輯**。
5.	選取**使用 Proxy 伺服器**，輸入 Proxy 伺服器設定，然後按一下**確定**。

已報告只針對 HTTP 設定 Proxy 資訊，但未針對 HTTPS。若要同時配置 HTTPS 資料流量的 Proxy 資訊，必須先啟用它。在您透過 SSH 登入 VCSA 之後，請使用 proxy.get 指令來檢視配置，並確認未設定 HTTPS 參數。

如果未設定 HTTPS 參數，則請使用下列指令：`proxy.set --protocol https --server ``<proxy ip>`` --port 3128`

### 配置 vSAN 來使用 Proxy
{: #vum-updating-vsan-config-vsan-proxy}

1. 導覽至**首頁** > **主機及叢集**，選取「導覽」窗格中的 **vSAN 叢集**，然後選取**配置**標籤並導覽至 **vSAN**，再選取**一般**。捲動至**網際網路連線功能**區段，然後按一下**編輯**。
2. 輸入 Proxy 的 IP 位址及埠號，然後按一下**確定**。

### 啟用客戶體驗改進計畫 (CEIP)
{: #vum-updating-vsan-enable-ceip}

這是選用步驟。使用 vSphere Web Client，導覽至**首頁** > **管理** > **客戶體驗改進計畫**，然後按一下**加入**。

### 完成測試上傳，並驗證上傳已作用
{: #vum-updating-vsan-complete-upload}

1. 使用 vSphere Web Client，導覽至**首頁** > **主機及叢集**。選取必要的叢集，並選取**監視**標籤及 **vSAN** 頁面，然後按一下**性能**。按一下**啟用線上性能**。
2. 按一下**重新測試**，並等待處理程序完成。
3. 新的檢查會出現在稱為 _Online health connectivity_ 的「性能」中，而且**啟用線上性能**會變更為**使用線上性能重新測試**。
4. 按一下**使用線上性能重新測試**來開始第一次上傳，並等待處理程序完成，方法是檢閱「最近作業」窗格中的狀態。「測試名稱」會變更為 Online health (Last check: just now)。
5. 完成時，請在「性能」視窗中捲動並展開「vSAN 建置建議」，然後按一下 **vSAN 建置建議引擎性能**。
6. 按一下**登入 my.vmware.com**，然後輸入您的認證。處理程序完成時，**測試結果**會變更為**通過**狀態。
7. 按一下 **Update Manager** 標籤，「vSAN 叢集」即會新增至「基準線」。

## 必要條件
{: #vum-updating-vsan-prereq}

啟動 vSAN 升級處理程序之前，請確定滿足下列需求：
* 檢閱 VMware 知識庫文章，並檢閱現行 vSAN 版本與所需目標 vSAN 版本之間的任何已知相容性問題
* **vSphere 環境是最新的**：
  - VCSA 的修補程式層次必須等於或高於 vSphere ESXi 主機的修補程式層次。更新 VCSA（如有必要）
  - 所有主機都必須執行相同的 ESXi 建置。如果不符合 vSphere ESXi 主機版本，則更新
* **所有 vSAN 磁碟都應該性能良好**：
  - 沒有磁碟故障或不存在。這可以透過 vSphere Web Client 中的 **vSAN 磁碟管理**視圖來決定。**首頁** > **主機及叢集**，選取 **vSAN 叢集**，然後按一下 **vSAN** 標籤，再按一下**實體磁碟**。捲動所有磁碟，並檢閱「vSAN 性能狀態」。
  - 沒有無法存取的 vSAN 物件。這可以使用 **vSAN 性能服務**進行驗證，方法是按一下**首頁** > **主機及叢集**，然後選取 **vSAN 叢集**。按一下**監視**標籤，並按一下 **vSAN**，然後按一下**性能**。檢閱「測試結果」。
  - 在升級處理程序開始時，沒有任何作用中重新同步，方法是按一下**首頁** > **主機及叢集**，選取 **vSAN 叢集**，然後依序按一下 **vSAN** 標籤及**重新同步元件**。_「重新同步元件」計數應該為 0_。在升級處理程序期間，預期會有一些重新同步活動，因為在主機重新啟動之後需要同步處理資料。
* **vSphere ESXi 主機準備** - 當您將主機移至 vSAN 叢集裡的維護模式時，有三個選項可供選擇：
  - **無資料移轉** - 如果您選取這個選項，vSAN 不會從此主機撤除任何資料。如果您關閉主機電源，或從叢集中移除主機，則部分虛擬機器 (VM) 可能變成無法存取。
  - **確保可用性** - 如果您選取這個選項，則 vSAN 容許您將主機移至維護模式的速度比「完整資料移轉」更快，並容許存取環境中的 VM。
  - **完整資料移轉**
* **結束維護模式及重新同步** - vSphere ESXi 主機已升級並移出維護模式後，會發生重新同步。您可以透過 Web 用戶端來查看此項目。請先確定此作業已完成，再移至下一部主機。已更新的主機現在可以再次提出至 vSAN 資料儲存庫時，會進行重新同步。請務必要等到此重新同步完成，以確保不會遺失任何資料。
* **啟動「vSAN 叢集」升級之後**：
  - 請不要嘗試藉由將新的版本引入叢集以及移轉工作負載，來升級叢集。
  - 如果引進新的主機，請確定它們具有相同的起始版本，並升級它們與叢集的其餘部分。
  - 如果您在升級期間新增或取代磁碟，請確定它們已使用適當的舊式磁碟內存格式版本（適用時）進行格式化。
  - 因此，某些 vSAN 行為變更是由磁碟內存格式所控制。重要的是，較新的磁碟內存格式版本並不會引入混合版本的叢集。

## 升級 vCenter Server Appliance
{: #vum-updating-vsan-upgrade-vcsa}

如需相關資訊，請參閱 [VCSA 更新及 SSO 鏈結的 vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa)。

##	升級 vSphere ESXi 主機
{: #vum-updating-vsan-upgrade-hosts}

如需相關資訊，請參閱[建立基準線並連接至庫存物件](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines)。

##	升級 vSAN 磁碟格式
{: #vum-updating-vsan-upgrade-vsan}

「Ruby vSphere 主控台 (RVC)」是 vSphere 的 Ruby 型指令行介面，可以用來管理 VMware vSphere ESXi 及 vCenter。vSphere 庫存會以樹狀結構呈現，可讓您針對 vCenter 物件導覽及執行指令。

許多基本管理作業的執行效率都遠優於按一下 vSphere Client。RVC 在 VCSA 中完全實作，且由應用裝置的 SSH 連線進行。
1. SSH 到 VCSA，並使用「ICVS 主控台」上提供的 root 及密碼登入。
2. 在提示時，鍵入：`rvc Administrator@vsphere.local@localhost`，然後按 **Enter** 鍵。
3. 輸入「ICVS 主控台」上提供的「管理者」密碼。您現在將位於虛擬檔案系統的根目錄中，鍵入 ls，然後按 **Enter** 鍵，您會看到：
  `0 /
  1 localhost/``

5. 鍵入 `cd 1` 並按 Enter 鍵，然後鍵入 `ls` 並按 **Enter** 鍵。您會看到：
  `0 / datacenter1 (datacenter)`

6. 鍵入 `cd 0` 並按 Enter 鍵，然後鍵入 `ls` 並按 **Enter** 鍵。您會看到：

  `0 storage/
  1 computers [host]/
  2 networks [network]/
  3 datastores [datastore]/
  4 vms [vm]/`

7. 鍵入 `cd 1` 並按 **Enter** 鍵，然後鍵入 `ls` 並按 **Enter** 鍵。您會看到叢集：
  `0 cluster1 (cluster)``

8. 針對此叢集使用 VSAN 指令。若要檢查磁碟狀態，請鍵入 `vsan.disks_stats 0`，然後按 **Enter** 鍵。

9. 確定所有磁碟的「性能狀態」都是「正常」。然後，鍵入 `vsan.ondisk_upgrade 0` 並按 **Enter** 鍵以開始升級。

10. 根據 vSAN 大小，此作業可能需要一些時間。完成時，請鍵入 `vsan.objstatusreport 0` 並按 **Enter** 鍵，以驗證物件版本已升級為新的磁碟內存格式。

11. VSAN 叢集升級現在已完成。鍵入 `exit` 並按 **Enter** 鍵，以離開 RVC。

## 相關鏈結
{: #vum-updating-vsan-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware)（示範）
