---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vSphere upgrade, NSX upgrade, PSC upgrade

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 將 vCenter Server vSphere 軟體從 VMware vSphere 6.5 升級至 6.7
{: #vc_vsphere_upgrade}

{{site.data.keyword.cloud}} 供應項目上的 vCenter Server 是 VMware vSphere SDDC 堆疊的全自動化部署解決方案，包括 vSphere、NSX 及選用的 vSAN 產品。雖然 vCenter Server 會將部署、擴充及縮減 VMware SDDC 型基礎架構最具挑戰性的部分自動化，但它不是受管理服務。由於 vCenter Server 的原則是支援 N-1 範圍內的 VMware SDDC 軟體版本的自動化，因此，如果您想要繼續從 {{site.data.keyword.vmwaresolutions_short}} 自動化中得益，則必須升級 vCenter Server 的現有實例。

根據 VMware 支援原則的要求，繼續支援自動化支援所需之層次外的 vCenter Server 版本，但不再使用 {{site.data.keyword.vmwaresolutions_short}} 自動化。您必須在 vCenter Server 實例的生命週期內執行 VMware 軟體的定期修補及升級。這包括視需要將 VMware SDDC 軟體升級至 {{site.data.keyword.vmwaresolutions_short}} 自動化支援的版本。

下列程序提供將 vCenter Server VMware vSphere 6.5 型實例轉換為 vCenter Server VMware vSphere 6.7 型實例所需的步驟。這些步驟可讓您一開始升級至最新 6.7 層次的 vSphere、NSX 及 vSAN。在此升級之後，您可能需要使用一般 vSphere 功能，來升級虛擬機器 (VM) 硬體層次及工具。

vCenter Server 的設計旨在容許「漸進式」升級。亦即，如果您完成下列程序，則目前運作中的 VM 工作負載會繼續運作，而不會中斷。企業必須使用其變更管理原則來啟用結構化和通訊的升級，並提供應急方案。不過，在某些管理功能（例如，vCenter 及 NSX Manager）的升級過程中，管理功能的暫時中斷、配置變更、關閉及開啟 VM 電源，可能會受到影響。
{:note}

## 開始之前
{: #vc_vsphere_upgrade-prereq}

執行升級的估計時間不明。可能需要數個維護時間，才能完整升級環境。在升級過程中，VMWare 支援執行上層及下層的 SDDC 軟體版本。不過，在此過程中，部分功能（例如 vMotion）可能受到限制。

開始升級之前，請完成下列需求：  
* 您必須負責在 vCenter Server 環境內升級任何延伸規格或嵌入式管理單元。在計劃升級之前，請檢閱下列文件：
  * [VMware vCenter Server 6.7 Update 1b 版本注意事項](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:external}
  * [關於 VMware ESXi 升級](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:external}
* 在 vCenter Server 實例內設定 vSphere Update Manager (VUM)，從 VMware vSphere 下載最新的更新。如需相關資訊，請參閱 [VMware Update Manager 簡介](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro)。
* 向 {{site.data.keyword.vmwaresolutions_short}} 團隊開立支援問題單，以通知他們正在執行升級。在於 {{site.data.keyword.vmwaresolutions_short}} 主控台的已升級層次中登錄實例之前，問題單會保持開立狀態。
* 確認您所升級的 vCenter Server 實例是否鏈結至另一個 vCenter Server 實例，作為 {{site.data.keyword.vmwaresolutions_short}} 主控台中的主要或次要實例。在升級特定站台時，所有鏈結的實例首先必須升級其「平台服務控制器 (PSU)」。
* 對於 vSAN 型實例確認下列情況：
  * 確定「vSAN 性能」工具已啟用，且未報告任何嚴重錯誤。如果出現嚴重錯誤，請聯絡「IBM 支援中心」團隊，並附上升級支援問題單 ID。
  * 確定每一個節點上都有空間，以在 ESXi 主機於升級期間無法重新啟動時，處理 SAN 物件的重建備援。您可能需要在升級之前減少磁碟用量或新增其他 ESXi 主機。  
  * 驗證整體 vSAN 磁區的使用量是否已超過 70%。您可能需要在升級之前減少磁碟用量或新增其他 ESXi 主機。
* 如果您的 vCenter Server 實例已啟動為 {{site.data.keyword.vmwaresolutions_short}} 2.5 版或更新版本，則必須與「IBM 支援中心」聯絡，以取得 PSC 及 vCenter 的 **root** 使用者 ID 密碼，因為入口網站上只能看到具有 **customerroot** 存取權的服務帳戶。如果可以看到 PSC 及 vCenter **root** 使用者 ID 與其密碼，則不需要此步驟。
* 確認您具有 https://my.vmware.com 使用者 ID，以下載必要的升級二進位檔。如果沒有，請聯絡「IBM 支援中心」，並附上升級支援問題單 ID。
* 確認已將 VUM 配置為連接 https://www.vmware.com，以下載修補程式。如果因為安全原則而無法配置，則您必須手動下載最新的修補程式集，並將它們上傳至 VUM。如需相關資訊，請參閱 [VMware Update Manager 簡介](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro)。

### 準備 jumpbox
{: #vc_vsphere_upgrade-prereq-jumpbox}

由於 {{site.data.keyword.cloud_notm}} 用戶端存取 VPN 受限於 512 Kbps，建議您在相同的 {{site.data.keyword.CloudDataCent_notm}} 內，佈建 {{site.data.keyword.cloud_notm}} Windows 2012-2016 伺服器的「虛擬伺服器實例 (VSI)」，或在個別的 vSphere vCenter Server 環境上設定類似的 Windows VM。這用來作為要升級的 vCenter Server 實例中的 jumpbox，並容許從 https://my.vmware.com 快速下載二進位檔。雖然可以將此 VM 置於要升級的 vCenter Server 實例上，但不建議這樣做。

請完成下列步驟來訂購 VSI jumpbox。

如果您的環境中已有 VSI jumpbox，請跳過第一個步驟。
{:note}

1. 從 [IBM Cloud 基礎架構客戶入口網站](https://control.softlayer.com/){:external}訂購每小時或每月 VSI。請訂購下列屬性：
  * Windows 2012 或 2016 Server Standard
  * 2 個 CPU
  * 16 GB 記憶體
  * 100 G 磁碟
  * 1 Gbps 公用及專用上行鏈路
2. 佈建 VSI 時，請在控制面板內配置「{{site.data.keyword.cloud_notm}} 存取控制清單 (ACL)」，以容許來自專用鏈結的所有 Ingress 及 Egress，以及僅來自公用鏈結的 Egress。您必須使用 {{site.data.keyword.cloud_notm}} 用戶端存取 VPN，「遠端桌面通訊協定 (RDP)」階段作業才能進入 Windows VSI。
3. RDP 進入 Windows VSI。在專用網路配接卡上修改其「網域名稱系統 (DNS)」設定，以僅指向要升級之 vCenter Server 實例內的 Windows AD 伺服器。
4. 下載並安裝 Google Chrome 瀏覽器。您可以使用 Mozilla Firefox，但在使用 vCenter 使用者介面內的 VUM 畫面時，會有快取問題。
5. 下載偏好的 SSH 終端機軟體。例如，Putty。
6. 使用 Google Chrome 來存取要升級的 vCenter Server 實例。請使用 **administratorivere.local**，並確定您可以檢視使用者介面。  
7. 如前一節所述，檢查 vSphere 環境的錯誤及問題。
8. 使用 SSH 終端機軟體，藉由入口網站存取 PSC 及 vCenter，或支援提供給 **root** 的密碼。
9. 選擇性地使用 SL 控制面板中註明的 **root** 使用者 ID 和密碼，來存取每一部 ESXi 主機，以驗證 **root** 密碼。

#### 下載二進位檔
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

使用 Windows VSI 跳板，並登入到您的 https://my.vmware.com 帳戶，以下載下列二進位檔：

* VMware vSphere 6.7u1 Hypervisor (ESXi ISO) 映像檔（包括 VMware Tools）
* vCenter 6.7u1b 應用裝置 ISO。不是更新組合。
* NSX for vSphere 6.4.4 升級組合

若為 Intel Optane 磁碟機，請下載下列檔案，以作為利用 VMware Update Manager 之後置升級修補程序的一部分。

對於 Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA（750 GB，HHHL），在 https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742 上找出 Intel NVMe 驅動程式的 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 檔案。

#### 備份元件

開始升級之前，請備份每個元件。

* 如需備份 vCenter Server 及 PDS 的相關資訊，請參閱 [vCenter Server 6.x 中備份及還原選項的概觀 (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:external}。
* 如需有關備份 vCenter Server 及 PSC 的其他考量及資訊，請參閱 [vCenter 檔案型備份](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter)。
* 如需備份 NSX 的相關資訊，請參閱[備份 NSX Manager 資料](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:external}。

建議使用以檔案為基礎的備份。VMware VSphere 6.7 不支援以映像檔為基礎的備份（使用 vSphere Data Protection)。
{:note}

## 將 IBM vCenter Server vSphere 軟體從 6.5 升級至 6.7 的程序
{: #vc_vsphere_upgrade-procedure}

只要您在升級過程中的任何時候遇到問題，請使用您在過程開始時開立的 {{site.data.keyword.vmwaresolutions_short}} 升級問題單，與「IBM 支援中心」聯絡。「IBM 支援中心」會視需要開立具有 VMware 支援的問題單。

**重要事項**：

* 您必須使用此路徑，以確保 {{site.data.keyword.vmwaresolutions_short}} 為 VMware 支援中心提供他們所需的所有 vCenter Server 設計、設定相關資訊，以及 {{site.data.keyword.cloud_notm}} 資訊。遵循此處理程序以確保與 VMware 支援中心分享正確的資訊，縮短支援體驗。在「IBM 支援中心」提供必要資訊給 VMware 支援中心之後，您可以視需要直接與 VMware 支援中心互動。
* 務必記錄此升級程序中建立的所有新密碼和認證。IBM 支援中心在升級程序結束時，需要這些認證以便更新其內部資料庫。

### 升級 VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx}

升級 VMware NSX 可能需要一些時間，因為升級程序會更新 ESXi 主機上的「vSphere 安裝組合」，而且需要重新啟動每部主機。請相應地計劃您的維護時間。

#### 升級 VMware NSX 之前
{: #vc_vsphere_upgrade-procedure-nsx-before}

* 如果您的環境上已安裝 Zerto for {{site.data.keyword.cloud_notm}}，請使用 Zto 使用者介面來關閉每部主機上的 zVRA VM。在 Zerto 使用者介面的 Zerto 站台設定、原則區段中，選取**容許 Zerto 在補救期間一律讓主機進入維護模式**。否則，Zerto 會啟動 zVRA，並阻止升級繼續進行，因為不容許升級 ESXi 主機以進入維護模式。
* 對於未安裝 VMware Tools 的 VM，請在 NSX ESXi 主機模組安裝之前手動關閉或強制關閉電源。這些 VM 會阻止目標 ESXi 主機進入維護模式。

#### 升級 VMware NSX 的程序
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

如需下列程序的相關詳細資料，請參閱 [NSX 升級手冊](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external}。

1. 閱讀 NSX 6.4.4 的版本注意事項，以確保與您的特定環境配置相容。如需相關資訊，請參閱 [VMware NSX Data Center for vSphere 6.4.4 版本注意事項](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}。
2. 首先升級 NSX Manager。如果您有多個使用交叉 vCenter 鏈結模式的 NSX 環境，請升級所有 NSX Manager，再升級 NSX 使用者介面**升級協調程式**中的元件。
3. 在 vCenter 使用者介面內的 NSX 使用者介面中，使用**升級協調程式**來升級 NSX 元件。
4. 繼續檢閱並監視 vCenter 使用者介面內的 NSX 升級使用者介面，因為可能問題會獲得解決，以確保升級繼續進行，直到所有元件都已升級。

### 升級 Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc}

如果您有 vCenter Server 鏈結實例，則必須升級 vCenter Server 主要及次要站台中的所有 PSC 實例。因為鏈結的 vCenter Server 實例會建立中心及分支 PSC 抄寫拓蹼，並以主要 vCenter Server 實例作為中心，所以建議從升級主要 vCenter Server 實例 PSC 開始，然後升級每個次要站台 PSC。

#### 升級 Platform Services Controller 之前
{: #vc_vsphere_upgrade-procedure-psc-before}

* 具備可供下列程序使用的 vCenter 及 PSC root 密碼。請使用 {{site.data.keyword.vmwaresolutions_short}} 主控台，以注意您的 vCenter Server 實例版本是否已從 2.4 版或更早版本升級至 2.7 版或更新版本。
* 在 {{site.data.keyword.vmwaresolutions_short}} 主控台上，顯示 PSC 和 vCenter 兩者的單一 root 密碼。不過，這只是 vCenter 密碼。您必須[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)，以取得 root PSC 密碼。
* 為了避免衝突，請使用 vCenter 及 PSC 目前正在使用之相同子網路上半部的 IP 位址。您必須使用暫時 IP 位址來進行新的應用裝置部署。

#### 升級 Platform Services Controller 的程序
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. 同時登入 PSC (`https://<psc-fqdn>:5480`) 及 vCenter 應用裝置管理使用者介面，以確認 root 密碼是否過期。如果密碼到期日是 **1970**，則它已過期，且您必須在 PSC 應用裝置管理使用者介面中啟用 SSH 和 Bash Shell。
    1. 使用 root ID 及密碼 SSH 至 PSC。即使密碼過期，它仍可讓您登入。
    2. 使用 Shell **passwd** 指令，為 PSC 及 vCenter 設定新的 root 密碼。
    3. 儲存顯示在 {{site.data.keyword.vmwaresolutions_short}} 主控台的密碼，或「IBM 支援中心」提供給您的密碼。稍後在您升級應用裝置時會重複使用這些密碼。
2. 使用內建 Windows ISO 裝載功能，在 jumpbox 內裝載 vCenter 6.7u1b ISO。
3. 遵循首先升級所有 PSC 的 VMware 指示。如需相關資訊，請參閱 [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}。

**您必須從與要升級之應用裝置位於相同網路的 Windows、Linux 或 Mac 機器執行 GUI 升級**，此陳述需求適用於您帳戶中 {{site.data.keyword.cloud_notm}} 內的任何子網路。
{:note}

建議您使用 vCenter 作為升級的來源和目標。

### 升級 vCenter
{: #vc_vsphere_upgrade-procedure-vcenter}

對於 vCenter Server 鏈結實例，雖然建議升級 vCenter Server 主要次要站台中的所有 vCenter 實例，但這不是必要的。

#### 升級 vCenter 之前
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* 具備可供下列程序使用的 vCenter 及 PSC root 密碼。請使用 {{site.data.keyword.vmwaresolutions_short}} 主控台，以注意您的 vCenter Server 實例版本是否已從 2.4 版或更早版本升級至 2.7 版或更新版本。
* 為了避免衝突，請使用 vCenter 及 PSC 目前正在使用之相同子網路上半部的 IP 位址。您必須使用暫時 IP 位址來進行新的應用裝置部署。

#### 升級 vCenter 的程序
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. 同時登入 PSC (``https://<psc-fqdn>:5480``) 及 vCenter 應用裝置管理使用者介面，以確認 root 密碼是否過期。如果密碼到期日是 **1970**，則它已過期，且您必須在 PSC 應用裝置管理使用者介面中啟用 SSH 和 Bash Shell。
    1. 使用 root ID 及密碼 SSH 至 PSC。即使密碼過期，它仍可讓您登入。
    2. 使用 Shell **passwd** 指令，為 PSC 及 vCenter 設定新的 root 密碼。
    3. 儲存顯示在 {{site.data.keyword.vmwaresolutions_short}} 主控台的密碼，或「IBM 支援中心」提供給您的密碼。稍後在您升級應用裝置時會重複使用這些密碼。
2. 使用內建 Windows ISO 裝載功能，在 jumpbox 內裝載 vCenter 6.7u1b ISO。
3. 遵循 VMware 指示以升級 vCenter。如需相關資訊，請參閱 [Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}。VMware 指示類似於 PSC 的升級程序。但是，對於升級程序，請指向 vCenter FQDN/IP，而不是指向 PSC。

**附註**：
* **您必須從與要升級之應用裝置位於相同網路的 Windows、Linux 或 Mac 機器執行 GUI 升級**，此陳述需求適用於您帳戶中 {{site.data.keyword.cloud_notm}} 內的任何子網路。

* 建議您使用 vCenter 作為升級的來源和目標。

#### 將 PSC 功能合併至 vCenter

1. 在順利完成 PSC 及 vCenter 升級之後，請登入 vCenter FLEX 型使用者介面，檢查**系統配置**區段中與 vCenter 及 PSC 相關之所有服務的性能。  
2. 備份您的 PSC。建議使用以檔案為基礎的備份。如需相關資訊，請參閱 [vSphere 6.7 中以檔案為基礎的備份](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:external}。
3. 導覽至 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge`` 目錄。
4. 將 ``converge.json`` 檔案複製到 jump VM 上的本端磁碟機。
  * 如果這是您要合併的第一個 PSC，則必須從 ``json`` 檔案中移除 **replication** 區段。
  * 如果這是後續鏈結的 PSC，則必須填寫 ``json`` 檔案的 **replication** 區段中要求的屬性。
5. 導覽至 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission`` 目錄。
6. 將 ``decommission_psc.json`` 檔複製到 jump VM 上的本端磁碟機。
7. 編輯 ``converge.json`` 及 ``decommission_psc.json`` 檔案。如何編輯欄位的指示在 ``json`` 檔案內。建議您在 **managing_esx_or_vc** 區段中使用包含 PSC 的 ESXi 主機，而不是 vCenter。
8. 導覽至指令視窗中的 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` 目錄。
9. 執行 ``vcsa-util.exe``，搭配 **converge** 參數，以及先前編輯之 ``converge.json`` 檔案的路徑。例如，``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``。
   1. 鍵入 **Y**，確認已備份 PSC 以繼續。
   2. 處理程序完成時，請鍵入 **Y** 來確認重新啟動 vCenter。

   如果聚合程序失敗，且顯示 ``ERROR converge Failed to get vecs users and permissions`` 訊息，請參閱 [Converge to embedded failed!](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:external}，以取得解決此錯誤的步驟。
   {:note}

10. 在重新啟動 vCenter 之後，請登入 vCenter 使用者介面來驗證作業正常。
11. 導覽至指令視窗中的 ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` 目錄。
12. 執行 ``vcsa-util.exe``，搭配 **decommission** 參數，以及先前編輯之 ``decommission_psc.json`` 檔案的路徑。例如，``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``。
13.	指令順利完成時，請登入 vCenter flex 型使用者介面，驗證 vCenter 應用裝置是非鏈結環境中列出的唯一應用裝置，且所有服務都健全。
14. 刪除舊的 PSC、vCenter 及未用的合併 PSC VM。
15. 將 vCenter 使用者介面內的 vCenter Server 重新命名為 **<instancename>_vc_separate**。例如，如果您的 vCenter Server 實例名稱是 **production**，則 vCenter 使用者介面名稱是 **production_vc_separate**。這是必要的，因此，自動化可能會回復它對此 vCenter Server 實例的功能。  

### 升級 ESXi 主機
{: #vc_vsphere_upgrade-procedure-esxi}

vCenter 內的 VMware Update Manager 功能是用來升級及修補 ESXi 主機至 6.7u1 層次。與本文件的 NSX 升級一節類似，任何無法 vMotion 至另一部主機的 VM，都必須在沒有問題的情況下關閉，否則可能會導致升級程序停滯。
{:note}

#### 將 ESXi ISO 上傳至 VUM
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. 確定您已配置 VUM，從 https://www.vmware.com 下載修補程式。如需相關資訊，請參閱 [VMware Update Manager 簡介](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction)。
2. 使用 Flex 或 HTML 來開啟 vCenter 使用者介面，然後導覽至 **VUM 管理視圖**。
3. 從 **VIUM 管理視圖**中，選取 **ESXi 映像檔**標籤，然後選取**匯入 ESXi 映像檔**。
4. 瀏覽已從 VMware 下載的 **ESXi 6.7u1iso** 映像檔，並將它匯入至 VUM 儲存庫。

#### 升級 ESXi 主機的程序
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. 在 vCenter 使用者介面中，導覽至包含要升級之 ESXi 主機的叢集。
2. 按一下導覽畫面中的**更新**標籤。移至主機更新並按一下**連接**。
3. 選取已上傳到 VUM 的基準線（適用於 ESXi 升級的 ISO 映像檔）並按一下**重新修補**。
4. 接受「一般使用者授權合約」並按一下**確定**。
5. 檢閱要重新修補的主機並確認預先補救檢查結果。

   您必須將連接到 VM 的任何 CD 或 DVD 分離，否則包含該 VM 的主機不容許進入維護模式。
   {:note}

6. 預先補救檢查成功後，按一下**重新修補**。使用重新修補實體作業監視升級程序。
7. 升級完成後，檢閱主機的摘要區段以確認是否顯示了 ``VMware ESXi, 6.7.0``。

如果升級程序立即失敗，並顯示**主機無法進入維護模式**錯誤訊息，請關閉 Zvand ZVA，然後再試一次。ZVRA VM 會在每部伺服器停止補救時自動啟動。如需在升級過程中繼續 Zins 抄寫的相關資訊，請參閱 [How to Place a Host with an Associated VRA into Maintenance Mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:external}。
{:note}

#### 將 Intel NVME 驅動程式修補程式新增至 VUM 儲存庫
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

如二進位下載一節所述，您必須將 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 檔案的內容匯入至儲存庫。然後，在後續小節中將它套用為非重要 ESXi 主機延伸。

1. 將 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` 檔案解壓縮至 jump VM 上的本端磁碟機。
2. 使用 Flex 或 HTML 來開啟 vCenter 使用者介面，然後導覽至 **VUM 管理視圖**。
3. 從 **VIUM 管理視圖**中，選取**修補程式儲存庫**標籤，然後選取**匯入修補程式**。
4. 瀏覽 ``VMW-ESX-6.7.0 - intel-nvme-vmmd-1.4.0.1016-8733247.zip`` 目錄的解壓縮內容，然後選取 ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip`` 檔案。此檔案會立即匯入至 VUM 儲存庫。

在修補程式儲存庫中找出作為**重要**「主機延伸」的映像檔。

#### 修補 ESXi 主機
{: #vc_vsphere_upgrade-procedure-esxi-patch}

在升級後，建議您套用所有重要及非重要 ESXi 主機修補程式。

1. 從 vCenter 使用者介面，選取包含要修補之主機的叢集。
2. 按一下導覽畫面中的**更新**標籤，然後選取**主機更新**標籤。選取**重要主機修補程式（預先定義）**。重複升級 ESXi 主機的程序。
3. 按一下導覽畫面中的**更新**標籤，然後選取**主機更新**標籤。選取**非重要主機修補程式（預先定義）**。重複升級 ESXi 主機的程序。

在此過程中，您可能需要再次關閉 Zerto zVRA VM。
{:note}

### 升級其他項目
{: #vc_vsphere_upgrade-procedure-addtl}

#### 升級 vSAN On Disk Format 版本
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

將 vSAN Disk Format 版本升級至第 7 版。

1. 導覽至包含要在 vCenter 使用者介面中升級之 vSAN 的叢集。
2. 從叢集物件中，選取**配置 > vSAN > 一般**。
3. 按一下**事先檢查升級**，以檢查升級相容性和可能的問題。等待檢查傳回**備妥以升級...**。
4. 按一下**升級**。因為升級一次處理一個磁碟群組，所以可能需要一些時間才能完成，視叢集的大小而定。在此過程中，可以選擇性地選取**減少的備援**。儘管這可大幅減少升級所需的時間，但若升級過程中發生磁碟故障，則可能會導致資料流失。

#### 升級虛擬分散式交換器
{: #vc_vsphere_upgrade-procedure-addtl-vds}

將「虛擬分散式交換器 (VDS)」升級至 6.6.0 版也會升級「網路 I/O」控制，並新增加強的「鏈結聚集控制通訊協定 (LACP)」支援。

1.	如果已部署 CHX，則在升級其所在的 VDS 之前，您必須解除部署 HCX 的「雲端閘道」部分。請確定在重新部署「雲端閘道」之前，HCX 已更新為最新版本。
2.	從 vCenter 使用者介面中，導覽至**網路**標籤。
3.	在要升級的分散式交換器（**SDDC-Dswitch-Private** 或 **SDDC-Dswitch-Public**）上按一下滑鼠右鍵，然後選取**升級分散式交換器**。

#### 升級 vCenter 使用者介面延伸及外掛程式
{: #vc_vsphere_upgrade-procedure-addtl-extension}

您必須負責在 vCenter Server 環境內升級任何延伸規格或嵌入式管理單元。從 vCenter 使用者介面中，按一下**首頁 > 管理 > 解決方案**，以檢視狀態並啟用或停用 vCenter 延伸及外掛程式。

#### 升級 VMware Tools
{: #vc_vsphere_upgrade-procedure-addtl-tools}

使用 vCenter 使用者介面來執行 VMware 來賓工具升級。部分較舊的 VM 可能需要某些 VMware Tools，這些 VM 已移轉至 vCenter Server 環境。  

#### 升級虛擬機器硬體層次
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

與 VMware 來賓工具類似，vCenter Server 環境升級可能導致舊的 VM 處於其現行硬體層次不支援的狀態。請視需要使用 vCenter 使用者介面來尋找並更新這些 VM。  

#### 將「增強 vMotion 相容性」模式設定為 Intel Skylake
{: #vc_vsphere_upgrade-procedure-addtl-evc}

您可以使用 Intel Skylake 世代設定主機，以便叢集在升級後進入 Skylake「增強 vMotion 相容性 (EVC)」模式。請使用下列步驟來更新 EVC 模式：

1. 從包含主機的叢集，按一下**配置**。
2. 從 **VMware EVC** 按一下**編輯**，並將 EVC 模式變更為 **Intel Skylake 世代**。

如需相關資訊，請參閱 [Enhanced vMotion Compatibility (EVC) processor support (1003212)](https://kb.vmware.com/s/article/1003212){:external}。

#### 重新配置 NSX Manager 和 HCX Manager 以指向 PSC

1. 從 Web 瀏覽器，導覽至 NSX Manager 應用裝置使用者介面，網址為 ``https://<nsx-manager-ip>`` 或 ``https://<nsx-manager-hostname>``。使用認證登入。
2. 從起始位置按一下**管理 vCenter 登錄**。
3. 編輯**查閱服務 URL** 以指向 vCenter IP。使用內嵌式 **PSC doesn’t exist anymore** PSC 單機。

## 升級 vCenter Server vSphere 軟體之後的結果
{: #vc_vsphere_upgrade-results}

升級完成之後執行 vSAN 性能檢查可能會對 IBM Cloud 提供的 RAID 及網路控制器產生有關韌體更新的警告。在判定需要韌體更新的主機之後，請向「IBM 支援中心」開立問題單，以將韌體更新至建議的版本。

1. 從 vCenter 使用者介面中，選取包含要檢查其性能之 vSAN 的叢集。
2. 選取**監視**標籤，然後選取 **vSAN** 標籤。
3. 選取**性能**，並注意所有顯示的警告。
4. 如果顯示**硬體相容性**警告，請展開警告，若處於警告狀態，則按一下**控制器韌體已獲 VMware 認證**訊息。
5. 記下列出的主機及韌體更新建議。
6. 向「IBM 支援中心」開立問題單，來排定讓每部主機停止服務的時間，以容許進行韌體更新。

升級完成時，請向「IBM 支援中心」更新您的支援問題單。請提供在此升級程序中建立的新密碼。例如，在支援問題單中提供密碼以部署應用裝置管理服務 -PSC 和 vCenter。然後，IBM 支援中心會更新 {{site.data.keyword.vmwaresolutions_short}} 主控台和內部資料庫，以在 6.7 層次繼續 {{site.data.keyword.vmwaresolutions_short}} 自動化。這包括新增及移除服務、主機、叢集及次要 vCenter Server 實例。

## 相關鏈結
{: #vc_vsphere_upgrade-related}

* [VMware NSX Data Center for vSphere 6.4.4 版本注意事項](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}
* [NSX 升級手冊](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external}
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
