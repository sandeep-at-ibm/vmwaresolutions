---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Veeam on IBM Cloud 概觀

Veeam on {{site.data.keyword.cloud}} 服務與 VMware Hypervisor 無縫整合，以協助您的企業達到高可用性。此服務提供您應用程式及資料的回復點及時間目標。完成配置之後，可以在 15 分鐘以內提供回復點及時間目標。使用此服務，您可以從 Veeam 主控台直接控制基礎架構之所有虛擬機器 (VM) 的備份及還原。

**可用性：**只有部署在 1.8 版或更新版本中的實例，才能使用此服務。

## Veeam on IBM Cloud 的技術規格

下列元件已訂購並包含在 Veeam on {{site.data.keyword.cloud_notm}} 服務中：

### VSI

* 具有 Veeam Backup and Replication 9.5 OS 附加程式的單一 VSI
* Windows Server 2016 Standard Edition（64 位元）
* 4 x 2.0 GHz 核心
* 8 GB RAM
* 1 Gbps 專用網路上行鏈路
* 100 GB 磁碟 (SAN)

### 用於備份的儲存空間

* 耐久性 iSCSI 儲存空間（2000、4000、8000 或 12000 GB）
* 儲存空間效能（0.25、2 或 4 IOPS/GB）

### 網路

一個主要專用 IP 位址。

### 授權及費用

Veeam Backup and Replication 9.5 Enterprise Plus（10、25、50、100 或 200 份 VM 授權）。

### 管理

依預設，最多配置 5 部 VM 及 2000 GB 儲存空間的管理備份。

## 安裝 Veeam on IBM Cloud 時的考量

儲存空間儲存庫及 Veeam 伺服器位在原始 Pod 及資料中心內。因此，遠端叢集的備份作業效能可能會降低。

## 移除 Veeam on IBM Cloud 時的考量

移除 Veeam on {{site.data.keyword.cloud_notm}} 服務會停止所有備份並刪除所有先前的備份。管理 VM 的備份會停止，而且刪除先前的備份是無法逆轉的。如果管理 VM 毀損，則無法予以還原。

### 相關鏈結

* [訂購 Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [要求 Veeam on {{site.data.keyword.cloud_notm}} 的受管理服務](managing_veeam_services.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [常見問題](../vmonic/faq.html)
* [Veeam 網站](https://www.veeam.com/){:new_window}
* [Veeam 說明中心](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
