---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-13"

---

# 訂購 IBM Spectrum Protect Plus on IBM Cloud

您可以在訂購包含服務的新實例時，同時訂購 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務，或將服務新增至現有實例。

## 為新實例訂購 IBM Spectrum Protect Plus on IBM Cloud

您可以使用下列其中一種方法，訂購含 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的新實例：
* 當您從 {{site.data.keyword.vmwaresolutions_full}} 主控台訂購新實例時，請選取**服務**區段中的 **IBM Spectrum Protect Plus on IBM Cloud**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，選取 **IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務**，指定服務設定，然後選取**新增至新實例**。

## 為現有實例訂購 IBM Spectrum Protect Plus on IBM Cloud

您可以使用下列其中一種方法，將 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務新增至現有實例：
* 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，檢視您要為其新增服務的實例，按一下左導覽窗格上的**服務**，然後按一下**新增服務**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，選取 **IBM Spectrum Protect Plus on IBM Cloud 服務**，指定服務設定，然後選取**新增至現有實例**。

## IBM Spectrum Protect Plus on IBM Cloud 服務配置

當您訂購此服務時，請提供下列設定。

### 儲存空間磁區數目

符合儲存空間需求的磁區數目。

### 每個磁區的儲存空間大小

每個磁區的儲存空間容量。每個磁區至少需要 500 GB 以用於管理。

### 儲存空間效能

根據工作負載需求的每 GB IOPS（每秒輸入/輸出作業數）。
* 如果您要訂購 IBM Spectrum Protect Plus 的授權，請在**訂購授權**標籤上指定**要授權的 VM 數目**。至少需要 10 部 VM 以用於授權管理。
* 如果您要「自帶授權 (BYOL)」，請按一下 **IBM Spectrum Protect Plus 授權**標籤，然後按一下**新增授權檔**以上傳您擁有的 IBM Spectrum Protect Plus 授權檔。

## IBM Spectrum Protect Plus on IBM Cloud 的部署處理程序

自動部署 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}。不論您要訂購包含此服務的實例，還是稍後將服務部署至實例，下列步驟都會透過 {{site.data.keyword.vmwaresolutions_short}} 自動化處理程序完成：

1. 根據使用者輸入，從 IBM Spectrum Protect Plus 備份儲存庫的 {{site.data.keyword.cloud_notm}} 基礎架構訂購「耐久性 NFS」儲存空間。
2. 根據使用者輸入，從 {{site.data.keyword.cloud_notm}} 基礎架構訂購特定數目的 IBM Spectrum Protect Plus 授權。根據使用者指定要在訂購 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務時授權的 VM 數目，來訂購授權，且增量為 10 個 VM 授權套件。如果使用者選擇攜帶現有 IBM Spectrum Protect Plus 授權，則不會從 {{site.data.keyword.cloud_notm}} 基礎架構訂購授權。
3. 將針對此服務所訂購的所有 NFS 儲存空間裝載至實例預設叢集中的所有 ESXi 伺服器（包括將每一部 ESXi 伺服器上的正確靜態路徑新增至儲存空間專用子網路）。
4. 針對裝載至 ESXi 伺服器的所有 NFS 儲存空間磁區，在 vCenter Server 中建立 NFS 資料儲存庫。
5. 在實例的預設叢集中，部署、啟動及配置 IBM Spectrum Protect Plus 虛擬機器。
6. 將針對此服務所訂購的所有 NFS 儲存空間連接至 IBM Spectrum Protect Plus 虛擬機器，並配置備份儲存庫。
7. 向實例的 DNS 伺服器，登錄 IBM Spectrum Protect Plus 虛擬機器的主機名稱及 IP 位址。
8. （針對 2.3 版及更新版本的實例）在 IBM Spectrum Protect Plus 中建立預設管理備份工作。如需相關資訊，請參閱[管理 IBM Spectrum Protect Plus on IBM Cloud](managingspp.html)。

## 相關鏈結

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 概觀](spp_considerations.html)
* [IBM Spectrum Protect Plus on IBM Cloud 預防性服務規劃](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [訂購、檢視及移除 Cloud Foundation 實例的服務](../sddc/sd_addingremovingservices.html)
* [訂購、檢視及移除 vCenter Server 實例的服務](../vcenter/vc_addingremovingservices.html)
* [訂購、檢視及移除 vCenter Server with Hybridity Bundle 實例的服務](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Spectrum Protect Plus 文件](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
