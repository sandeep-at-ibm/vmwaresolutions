---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: IBM Spectrum Protect Plus, SPP configuration, order SPP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# 訂購 IBM Spectrum Protect Plus on IBM Cloud
{: #spp_ordering}

您可以在訂購包含服務的新實例時，同時訂購 {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服務，或將服務新增至現有實例。

## 為新實例訂購 IBM Spectrum Protect Plus on IBM Cloud
{: #spp_ordering-new}

您可以使用下列其中一種方法，訂購含 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的新實例：
* 當您從 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購新實例時，請選取**服務**區段中的 **IBM Spectrum Protect Plus on IBM Cloud**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格上的 **VMware** 圖示，然後按一下 **VMware Services** 區段中的 **IBM Spectrum Protect Plus on IBM Cloud** 卡。指定服務設定，然後選取**新增至新實例**。

## 為現有實例訂購 IBM Spectrum Protect Plus on IBM Cloud
{: #spp_ordering-existing}

您可以使用下列其中一種方法，將 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務新增至現有實例：
* 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，檢視您要為其新增服務的實例，按一下左導覽窗格上的**服務**，然後按一下**新增**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格上的 **VMware** 圖示，然後按一下 **VMware Services** 區段中的 **IBM Spectrum Protect Plus on IBM Cloud** 卡。指定服務設定，然後選取**新增至現有實例**。

## IBM Spectrum Protect Plus on IBM Cloud 服務配置
{: #spp_ordering-config}

當您訂購此服務時，請提供下列設定。

### 儲存空間磁區數目
{: #spp_ordering-config-number-vol}

符合儲存空間需求的磁區數目。

### 每個磁區的儲存空間大小
{: #spp_ordering-config-size}

每個磁區的儲存空間容量。

### 儲存空間效能
{: #spp_ordering-config-performance}

根據工作負載需求的每 GB IOPS（每秒輸入/輸出作業數）。
* 如果您要訂購 IBM Spectrum Protect Plus 的授權，請在**訂購授權**標籤上指定**要授權的 VM 數目**。
* 如果您要「自帶授權 (BYOL)」，請按一下 **IBM Spectrum Protect Plus 授權**標籤，然後按一下**新增授權檔**以上傳您擁有的 IBM Spectrum Protect Plus 授權檔。

## IBM Spectrum Protect Plus on IBM Cloud 的部署處理程序
{: #spp_ordering-deploy}

自動部署 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}。不論您要訂購包含此服務的實例，還是稍後將服務部署至實例，下列步驟都會透過 {{site.data.keyword.vmwaresolutions_short}} 自動化處理程序完成：

1. 根據您指定的設定，從 IBM Spectrum Protect Plus 備份儲存庫的 {{site.data.keyword.cloud_notm}} 基礎架構訂購耐久性 NFS 儲存空間。
2. 根據您指定的設定，從 {{site.data.keyword.cloud_notm}} 基礎架構訂購一些 IBM Spectrum Protect Plus 授權。根據您指定要在訂購 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務時授權的 VM 數目，來訂購授權，且增量為 10 個虛擬機器 (VM) 授權套件。如果您要攜帶現有 IBM Spectrum Protect Plus 授權，則不會從 {{site.data.keyword.cloud_notm}} 基礎架構訂購授權。
3. 將針對此服務訂購的 NFS 儲存空間裝載至實例預設叢集裡的所有 ESXi 伺服器（包括將每一部 ESXi 伺服器上的正確靜態路徑新增至儲存空間專用子網路）。
4. 針對裝載至 ESXi 伺服器的所有 NFS 儲存空間磁區，在 vCenter Server 中建立 NFS 資料儲存庫。
5. 在實例的預設叢集裡，部署、啟動及配置 IBM Spectrum Protect Plus VM。
6. 將針對此服務訂購的 NFS 儲存空間附加至 IBM Spectrum Protect Plus VM，並且配置備份儲存庫。
7. 向實例的 DNS 伺服器，登錄 IBM Spectrum Protect Plus VM 的主機名稱及 IP 位址。

## 相關鏈結
{: #spp_ordering-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 預防性服務規劃](https://www-01.ibm.com/support/docview.wss?uid=swg22012650){:external}
* [管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp)
* [訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [IBM Spectrum Protect Plus 文件](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html){:external}
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
