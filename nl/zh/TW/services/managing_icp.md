---

copyright:

  years:  2016, 2019

lastupdated: "2018-09-27"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# 要求 IBM Cloud Private Hosted - 已淘汰

本主題中的資訊即將淘汰。如需 IBM Cloud Private Hosted 的最新資訊，請參閱 [IBM Cloud Private Hosted 概觀](icp_overview.html)。
{:deprecated}

vCenter Server on {{site.data.keyword.cloud_notm}} 的 {{site.data.keyword.cloud}} Private Hosted 會自動在您的 VMware vCenter Server 實例上部署 {{site.data.keyword.cloud_notm}} Private Hosted。

{{site.data.keyword.cloud_notm}} Private Hosted 為您在 {{site.data.keyword.cloud_notm}} 上的 VMware 環境帶來微服務及容器的功能。使用此服務，您可以將熟悉的相同 VMware 與 {{site.data.keyword.cloud_notm}} Private 作業模型和工具，從內部部署延伸到 {{site.data.keyword.cloud_notm}}。

## IBM Cloud Private Hosted 的技術規格

以下是要求 {{site.data.keyword.cloud_notm}} Private Hosted 服務的最低需求：

* VMware vCenter Server on {{site.data.keyword.cloud_notm}}。**附註：**不支援 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle。
* VMware NSX Advanced 或 Enterprise 版本
* 三個 {{site.data.keyword.baremetal_long}}
* 雙重 Intel Xeon Gold 5120 處理器 / 總計 28 核心，2.2 GHz
* 每部伺服器 384 GB RAM
* 共用的 NFS 儲存空間的一個檔案共用，具有 8,000 GB 及 4 IOPS/GB
* 33 份 IBM Cloud Private 虛擬處理器核心授權
* 以資料備份而言，建議使用 Veeam on IBM Cloud 服務。

## 要求 IBM Cloud Private Hosted 的程序

1. 遵循[訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)中的步驟來訂購新的 vCenter Server 實例。您也可以針對現有的實例來要求 IBM Cloud Private Hosted。
  **重要事項：**確定您的環境符合上述最低需求。
2. 確定您具有 IBM Cloud Private 授權。
3. 收到 vCenter Server 實例可備妥可用的確認之後，請繼續進行下列步驟來要求 IBM Cloud Private Hosted。
4. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**開始使用**。
5. 向下捲動頁面，並在**訂購其他服務**之下按一下 **IBM Cloud Private Hosted** 服務卡。
6. 在 **IBM Cloud Private Hosted on vCenter Server on IBM Cloud** 頁面的**與 IBM Cloud Private Hosted DevOps 團隊聯絡**方框中，輸入需求的說明，並按一下**要求商議**。

一位 {{site.data.keyword.cloud_notm}} Private Hosted DevOps 服務代表會透過您的 {{site.data.keyword.cloud_notm}} 聯絡資訊與您聯絡，協助您入門。
