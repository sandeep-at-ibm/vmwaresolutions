---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Veeam on IBM Cloud 概觀

Veeam on {{site.data.keyword.cloud}} 服務與 VMware Hypervisor 無縫整合，以協助您的企業達到高可用性。此服務可以提供您應用程式及資料的回復點及時間目標。完成配置之後，可以在 15 分鐘以內提供回復點及時間目標。使用此服務，即可從 Veeam 主控台直接控制基礎架構之所有虛擬機器的備份及還原。

**可用性**：只有部署在 1.8 版或更新版本中的實例，才能使用此服務。

## Veeam on IBM Cloud 的元件

下列元件已訂購並包含在 Veeam on {{site.data.keyword.cloud_notm}} 服務中：
* 一個具有主要專用 IP 位址及 1 GbE 介面的 Windows Server 2016 VSI
* 您在訂購服務時選取之大小及效能的「{{site.data.keyword.cloud_notm}} 耐久性」區塊儲存空間

## 安裝 Veeam on IBM Cloud 時的考量

* 此服務會備份下列管理元件：
  - VMware vCenter Server
  - Platform Services Controller (PSC)
  - IBM CloudDriver
  - **僅限 Cloud Foundation 實例**：VMware SDDC Manager
  - **僅限含 HA AD/DNS 的 vCenter Server 實例**：AD/DNS 伺服器的高可用性配對

* Veeam on {{site.data.keyword.cloud_notm}} 服務不會備份 ESXi 伺服器的配置。

* 依預設，會使用最多有 14 個還原點的 NSX Manager 每日備份 NSX Controller 及 NSX Edge 的配置。若要完整還原 NSX 配置，您必須建立 {{site.data.keyword.cloud_notm}} 支援問題單，因為 NSX 配置的備份儲存在 {{site.data.keyword.vmwaresolutions_full}} 內部的儲存空間上。如需使用 NSX Manager 來管理 NSX 配置備份的相關資訊，請參閱 [VMware 技術指示](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html)。
* 儲存空間及 Veeam 伺服器的儲存庫位在原始 Pod 及資料中心內。因此，遠端叢集的備份作業效能可能會降低。

## 移除 Veeam on IBM Cloud 時的考量

移除 Veeam on {{site.data.keyword.cloud_notm}} 服務之前，請注意，移除此服務會停止所有備份（包括管理 VM 的備份），並刪除所有先前的備份（刪除是不可逆轉的）。如果管理 VM 之後毀損，則無法予以還原。

## 相關鏈結

* [訂購 Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [要求 Veeam on {{site.data.keyword.cloud_notm}} 的受管理服務](managing_veeam_services.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [常見問題](../vmonic/faq.html)
* [Veeam 網站](https://www.veeam.com/){:new_window}
* [Veeam 說明中心](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
