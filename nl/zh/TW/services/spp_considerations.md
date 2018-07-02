---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# IBM Spectrum Protect Plus on IBM Cloud 概觀

IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} 服務提供有效且可調式解決方案，以進行虛擬環境的資料保護、資料重複使用及資料回復。您可以將服務當成獨立式解決方案來實作，或與 IBM Spectrum Protect Plus 環境整合以卸載副本，進行長期儲存及資料控管。

**可用性**：只有部署在（或升級至）2.2 版或更新版本的實例，才能使用此服務。

**附註：**
* 如果您針對部署在 2.4 版或更新版本的實例接受預設服務選擇，則會安裝 IBM Spectrum Protect Plus 10.1.1 版 Patch 1。此服務自動提供管理虛擬機器 (VM) 的回復支援。
* 如果您針對部署在 2.3 版的實例接受預設服務選擇，則會安裝 IBM Spectrum Protect Plus 10.1.1 版。此服務自動提供管理 VM 的備份。
* 如果您針對部署在 2.2 版的實例安裝服務，則會安裝 IBM Spectrum Protect Plus 10.1.0 版。此服務僅為工作負載 VM 提供資料保護。


## IBM Spectrum Protect Plus on IBM Cloud 的元件

下列元件已訂購並包含在 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務中：

### vCenter 資源

* 執行 IBM Spectrum Protect Plus 伺服器的單一虛擬機器 (VM)
* 4 x 2.0 GHz 核心
* 32 GB RAM
* 370 GB 磁碟

### 用於備份的儲存空間

使用下列選項之備份的可自訂儲存空間：
* 檔案儲存空間數目：1、2、3 或 4
* 每一個耐久性檔案儲存空間：500、1000、2000、4000、8000 或 12000 GB
* 儲存空間效能：0.25、2 或 4 IOPS/GB

### 用於管理的儲存空間

一個耐久性檔案儲存空間（500 GB、2 IOPS/GB），可管理 IBM Spectrum Protect Plus 虛擬機器，並在與針對服務所訂購之備份儲存空間相同的子網路上執行。

### 網路

一個可攜式專用 IP 位址。

### 授權及費用

在 {{site.data.keyword.vmwaresolutions_short}} 主控台中可以授權 IBM Spectrum Protect Plus 用於 10 部到最多 1000 部 VM，而增量為 10。您也可以在安裝處理程序期間「自帶授權 (BYOL)」及上傳授權檔。

## 安裝 IBM Spectrum Protect Plus on IBM Cloud 時的考量

請先檢閱下列考量，再安裝 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務。

* 確定實例預設叢集中的 CPU 及記憶體足夠用於 IBM Spectrum Protect Plus 虛擬機器。
* 根據 ESXi 伺服器的版本，確定 ESXi 伺服器上可用的 NFS 裝載足夠。

  在 VMware 中，部署或升級至 2.2 版或更新版本的 Cloud Foundation 實例及 vCenter Server 實例具有 `NFS.MaxVolumes` 參數設定。此參數定義 ESXi 伺服器的 NFS 裝載數目上限，而且可以設為 ESXi 伺服器版本特有的上限 256。如需相關資訊，請參閱[增加 ESXi/ESX 主機上定義 NFS 裝載數目上限的預設值](https://kb.vmware.com/s/article/2239)。

  在實例預設叢集的每一部 ESXi 伺服器上，IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務最多會使用五個 NFS 磁區。此外，此服務還會建立暫時性 NFS 裝載來進行備份及還原。因此，您必須將 NFS 裝載數目設為至少 64，確保服務可以順利安裝及運作。

## 移除 IBM Spectrum Protect Plus on IBM Cloud 時的考量

請先檢閱下列考量，再移除 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務：
* 確定已移除所有備份工作配置，而且沒有作用中備份或還原作業。
* 當您移除此服務時，會從 IBM Spectrum Protect Plus VM 中移除備份儲存庫的儲存空間，並取消儲存空間訂單，以永久地刪除備份儲存庫資料。
* 當您移除此服務時，也會移除針對此服務所訂購的備份儲存空間。因此，在移除服務期間，所有備份都會變成無法存取。

## 相關鏈結

* [IBM Spectrum Protect Plus on IBM Cloud 預防性服務規劃](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [訂購 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [IBM Spectrum Protect Plus 文件](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
