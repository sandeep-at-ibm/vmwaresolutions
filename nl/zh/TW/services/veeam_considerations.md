---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud 概觀
{: #veeam_considerations}

Veeam on {{site.data.keyword.cloud}} 服務與 VMware Hypervisor 無縫整合，以協助您的企業達到高可用性。此服務提供您應用程式及資料的回復點及時間目標。完成配置之後，可以在 15 分鐘以內提供回復點及時間目標。使用此服務，您可以從 Veeam 主控台直接控制基礎架構之所有虛擬機器 (VM) 的備份及還原。

只有在 1.8 版或更新版本中部署的實例，才能使用此服務。目前安裝的 Veeam 版本為 9.5u3。
{:note}

## Veeam on IBM Cloud 的技術規格
{: #technical-specifications-for-veeam-on-ibm-cloud}

下列元件已訂購並包含在 Veeam on {{site.data.keyword.cloud_notm}} 服務中：

### VSI
{: #veeam_considerations-specs-vsi}

* 具有 Veeam Backup and Replication 9.5 OS 附加程式的單一 VSI
* Windows Server 2016 Standard Edition（64 位元）
* 4 x 2.0 GHz 核心
* 8 GB RAM
* 1 Gbps 專用網路上行鏈路
* 100 GB 磁碟 (SAN)

### 用於備份的儲存空間
{: #veeam_considerations-specs-storage}

* 耐久性 iSCSI 儲存空間（2000、4000、8000 或 12000 GB）
* 儲存空間效能（0.25、2 或 4 IOPS/GB）

### 網路
{: #veeam_considerations-specs-networking}

一個主要專用 IP 位址。

### 授權及費用
{: #veeam_considerations-specs-licenses}

Veeam Backup and Replication 9.5 Enterprise Plus（10、25、50、100 或 200 份 VM 授權）。

### 管理
{: #veeam_considerations-specs-mgmt}

依預設，最多配置 5 部 VM 及 2000 GB 儲存空間的管理備份。

## 安裝 Veeam on IBM Cloud 時的考量
{: #veeam_considerations-install}

儲存空間儲存庫及 Veeam 伺服器位在原始 Pod 及資料中心內。因此，遠端叢集的備份作業效能可能會降低。

## 移除 Veeam on IBM Cloud 時的考量
{: #veeam_considerations-remove}

移除 Veeam on {{site.data.keyword.cloud_notm}} 服務會停止所有備份並刪除所有先前的備份。管理 VM 的備份會停止，而且刪除先前的備份是無法逆轉的。如果管理 VM 毀損，則無法予以還原。

## 相關鏈結
{: #veeam_considerations-related}

* [訂購 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [要求 Veeam on {{site.data.keyword.cloud_notm}} 的受管理服務](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam 網站](https://www.veeam.com/){:new_window}
* [Veeam 說明中心](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
