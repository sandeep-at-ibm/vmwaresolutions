---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# 關於 IBM Cloud for VMware Solutions

{{site.data.keyword.vmwaresolutions_full}} 可讓您使用可擴充、安全且高效能的 {{site.data.keyword.cloud_notm}} 基礎架構及領先業界的 VMware 混合式虛擬化技術，來快速且無縫地將您的內部部署 VMware 工作負載整合或移轉至 {{site.data.keyword.cloud_notm}}。

{{site.data.keyword.vmwaresolutions_short}} 可讓您輕鬆部署 VMware 虛擬環境，及管理 {{site.data.keyword.cloud_notm}} 上的基礎架構資源。同時，您仍然可以使用熟悉的原生 VMware 產品主控台來管理 VMware 工作負載。

## IBM Cloud for VMware Solutions 的優點

{{site.data.keyword.vmwaresolutions_short}} 提供下列主要優點：
* **全球觸角**：可讓您擴大混合式雲端覆蓋範圍至全球多達 30 個企業級 {{site.data.keyword.CloudDataCents_notm}}。
* **無縫整合**：在混合式雲端上使用 {{site.data.keyword.cloud_notm}} 基礎架構來進行無縫整合。
* **快速佈建**：將 VMware 環境的部署和配置自動化，可讓您利用隨需應變的 {{site.data.keyword.cloud_notm}}{{site.data.keyword.baremetal_short}} 和虛擬伺服器，快速部署企業級 VMware 環境。
* **簡化**：可讓您使用 VMware 雲端平台時不需要識別、採購、部署及管理實體基礎架構（運算、儲存空間及網路）和軟體授權。
* **擴充及縮減的彈性**：可讓您根據商業需要，輕鬆擴充及縮減 VMware 工作負載。
* **單一管理主控台**：提供單一主控台，在 {{site.data.keyword.cloud_notm}} 上部署、存取及管理 VMware 環境。

## 部署供應項目

{{site.data.keyword.vmwaresolutions_short}} 提供 VMware 虛擬環境的標準化及可自訂的部署選項。提供了下列部署類型：
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}}**：vCenter Server 供應項目可讓您使用自訂運算、儲存空間及網路資源來部署 VMware 虛擬環境，以充分配合您的商業需要。
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle**：vCenter Server with Hybridity 供應項目是一種受管理的專用雲端，有助於快速且輕鬆地將內部部署基礎架構延伸到雲端。VMware 環境根據 IBM 提供的「VMware 軟體定義資料中心」授權，並包括 VMware Hybrid Cloud Extension (HCX)。使用 HCX，您可以透過內部部署方式安全地連接 vSphere 5.0+ 環境與 IBM Cloud 站台，來獲得無縫的基礎架構混合及實際應用程式行動性。
* **VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}**：Cloud Foundation 供應項目使用每一個使用者部署專用的標準 {{site.data.keyword.cloud_notm}} 運算、儲存空間及網路資源，來提供統一的 VMware 虛擬環境。
* **VMware vSphere on {{site.data.keyword.cloud_notm}}**：vSphere on {{site.data.keyword.cloud_notm}} 供應項目提供可自訂的虛擬化服務，結合 VMware 相容的 {{site.data.keyword.baremetal_short}}、硬體元件及授權，來建置您自己的 IBM 管理 VMware 環境。
* **NetApp ONTAP Select**：NetApp ONTAP Select 供應項目可讓您部署軟體定義的儲存叢集，以根據 NetApp ONTAP Select 來處理您對於專用及高可用性儲存應用裝置的需要。
* **VMware Federal on {{site.data.keyword.cloud_notm}}**：VMware Federal on {{site.data.keyword.cloud_notm}} 供應項目除了提供選項來保護已部署實例的安全，同時移除機密性資訊及用於持續存取實例以使用管理功能的開啟管理連線之外，還支援訂購基本 vCenter Server 實例。

## 其他服務

{{site.data.keyword.vmwaresolutions_short}} 可讓您在訂購實例時或實例部署之後新增各種服務。提供了下列服務：

### FortiGate Security Appliance on IBM Cloud

此服務會部署一組 HA 的 FortiGate Security Appliance (FSA) 300 系列裝置，其可提供防火牆、遞送、NAT 及 VPN 服務，以維護公用網路與您環境之連線的安全。

只有在 1.8 版或更新版本中部署的實例，才能使用此服務。

如需相關資訊，請參閱[管理 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html)。

### FortiGate Virtual Appliance on IBM Cloud

此服務會部署一組 HA 的 FortiGate Virtual Appliance，讓您可以在虛擬基礎架構內實作重要安全控制來降低風險。

只有在 2.0 版或更新版本中部署的實例，才能使用此服務。

如需相關資訊，請參閱[管理 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html)。

### F5 on IBM Cloud

此服務可讓效能最佳化，並使用 F5 BIG-IP Virtual Edition (VE) 確保應用程式的可用性和安全性。

只有在 1.9 版或更新版本中部署的實例，才能使用此服務。

如需相關資訊，請參閱[管理 F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html)。

### IBM Spectrum Protect Plus on IBM Cloud

此服務提供有效率且可調式解決方案，以進行虛擬環境的資料保護、資料重複使用及資料回復。您可以將它當成獨立式解決方案來實作，或與 IBM Spectrum Protect&trade; Plus 環境整合以卸載副本，進行長期儲存及資料控管。

**附註**：
* 只有部署在（或升級至）2.2 版或更新版本的實例，才能使用此服務。
* 對於部署在 2.3 版或更新版本的實例，IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 會自動提供管理 VM 的備份。
* 對於部署在 2.2 版的實例，此服務僅為工作負載 VM 提供資料保護。

如需相關資訊，請參閱[管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/managingspp.html)。

### Veeam on IBM Cloud

此服務與 VMware 環境無縫整合，以協助您管理環境中所有虛擬機器 (VM) 的備份及還原，包括管理元件的備份及還原。在配置您的資料時，它可提供少於 15 分鐘的回復點目標 (RPO)。

此服務是配置成在部署實例之後立即備份管理 VM。

只有在 1.8 版或更新版本中部署的實例，才能使用此服務。

如需相關資訊，請參閱[管理 Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html)。

### Zerto on IBM Cloud

此服務提供抄寫及災難回復功能，以協助保護工作負載。如需相關資訊，請參閱[管理 Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html)。

### 來自 IMI 的受管理服務

這些服務可讓 IBM Integrated Managed Infrastructure (IMI) 為各種不同雲端基礎架構提供動態遠端管理服務。

只有 Cloud Foundation 實例，才能使用這些服務。

如需相關資訊，請參閱[從 IMI 要求受管理服務](../services/managing_imi.html)。

## 相關鏈結

* [開始使用](../index.html)
* [Cloud Foundation 概觀](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 概觀](../vcenter/vc_vcenterserveroverview.html)
* [vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [NetApp ONTAP Select](../netapp/np_netappoverview.html)
