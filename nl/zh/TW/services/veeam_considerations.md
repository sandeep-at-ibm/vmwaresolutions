---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-02"

keywords: Veeam, Veeam install, tech specs Veeam

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud 概觀
{: #veeam_considerations}

Veeam on {{site.data.keyword.cloud}} 服務與 VMware Hypervisor 無縫整合，以協助您的企業達到高可用性。此服務提供您應用程式及資料的回復點及時間目標。完成配置之後，可以在 15 分鐘以內提供回復點及時間目標。使用此服務，您可以從 Veeam 主控台直接控制基礎架構之所有虛擬機器 (VM) 的備份及還原。

只有在 1.8 版或更新版本中部署的實例，才能使用此服務。現行安裝的 Veeam 版本為 9.5u4b。
{:note}

## Veeam on IBM Cloud 的技術規格
{: #veeam_considerations-specs}

下列元件已訂購並包含在 Veeam on {{site.data.keyword.cloud_notm}} 服務中：

### VSI
{: #veeam_considerations-specs-vsi}

* 具有 Veeam Backup and Replication 9.5 附加程式和 Veeam Availability Suite 9.5 的單一 VSI
* Windows Server 2016 Standard Edition（64 位元）
* 4 x 2.0 GHz 核心
* 8 個 vCPU，32 GB RAM
* 1 Gbps 專用網路上行鏈路
* 100 GB 磁碟 (SAN)

### 用於備份的儲存空間
{: #veeam_considerations-specs-storage}

* 耐久性 iSCSI 儲存空間（2,000、4,000、8,000 或 12,000 GB）
* 儲存空間效能（0.25、2 或 4 IOPS/GB）

作為 Veeam 服務安裝和配置的一部分，將建立下列儲存庫：
* 對於 Veeam 配置備份檔：名為 `IC4V 預設配置備份儲存庫`的儲存庫。儲存 Veeam 備份的資料夾的路徑為 `<Drive>:\ConfigBackup\`。
* 對於橫向擴充：名為 `IC4V 橫向擴充儲存庫`的儲存庫。如需相關資訊，請參閱[新增橫向擴充儲存庫](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icos_ordering#icos_ordering-scale-repo)。
* 對於虛擬機器 (VM) 備份：名為 ``IC4V 預設 VM 備份儲存庫``的儲存庫。儲存 VM 備份的資料夾的路徑為 ``<Drive>:\VMBackup\`。此儲存庫作為範圍新增到 ``IC4V 橫向擴充儲存庫`。

### 網路
{: #veeam_considerations-specs-networking}

一個主要專用 IP 位址。

### 授權及費用
{: #veeam_considerations-specs-licenses}

* Veeam Availability Suite 9.5（10、25、50、100 或 200 VM 授權）

## 安裝 Veeam on IBM Cloud 時的考量
{: #veeam_considerations-install}

儲存空間儲存庫及 Veeam 伺服器位在原始 Pod 及資料中心內。因此，遠端叢集的備份作業效能可能會降低。

## 移除 Veeam on IBM Cloud 時的考量
{: #veeam_considerations-remove}

移除 Veeam on {{site.data.keyword.cloud_notm}} 服務會停止所有備份並刪除所有先前的備份。管理 VM 的備份將停止，而且刪除先前的備份是無法逆轉的。如果管理 VM 毀損，則無法予以還原。

## 相關鏈結
{: #veeam_considerations-related}

* [訂購 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Managed Services for Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam 網站](https://www.veeam.com/){:external}
* [Veeam 說明中心](https://www.veeam.com/documentation-guides-datasheets.html){:external}
