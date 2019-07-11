---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

keywords: Caveonix, Caveonix RiskForesight, tech specs Caveonix

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight on IBM Cloud 概觀
{: #caveonix_considerations}

Caveonix RiskForesight on {{site.data.keyword.cloud}} 服務可以透過主動監視和自動化防禦控制來防範威脅及因應業界或政府規章，以協助管理網路和法規遵循風險。

只有部署在 2.9 版及更新版本中的 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 實例，才能使用此服務。
現行安裝的 Caveonix RiskForesight 版本為 2.2.1。
{:note}

## Caveonix RiskForesight on IBM Cloud 的技術規格
{: #caveonix_considerations-specs}

下列元件已完成訂購並包含在 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服務中。

### vCenter 資源
{: #caveonix_considerations-tech-specs-vcenter}

* CPU：8 個 vCPU
* RAM：32 GB
* 磁碟：80 GB

### 網路
{: #caveonix_considerations-tech-specs-network}

已訂購具有 64 個 IP 位址的專用子網路。

### 授權及費用
{: #caveonix_considerations-tech-specs-license-fee}

每個服務實例都要訂購一個 Caveonix RiskForesight 授權碼。

## 安裝 Caveonix RiskForesight on IBM Cloud 時的考量
{: #caveonix_considerations-install}

安裝 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服務之前，請確定您的服務實例的預設叢集中的 CPU 和記憶體足夠用於 Caveonix RiskForesight 虛擬機器。

## 移除 Caveonix RiskForesight on IBM Cloud 時的考量
{: #caveonix_considerations-remove}

請先檢閱下列考量，然後再移除 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服務：
* 移除 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服務並不會取消 Caveonix RiskForesight 授權。您必須從 {{site.data.keyword.vmwaresolutions_short}} 主控台的**資源**頁面中的 **Caveonix RiskForesight Licenses** 表格刪除 Caveonix RiskForesight 授權。
* 當您移除服務時，{{site.data.keyword.vmwaresolutions_short}} 自動化只會刪除已部署的單一「全功能」的 Caveonix VM，以及針對其訂購的專用子網路。因此，
   * 如果您將 Caveonix VM 擴充為多部 VM，額外的 VM 不會被移除。
   * 如果您已使用額外 VM 上的專用子網路的 IP 位址，必須對那些 VM 指派新的 IP 位址，才能夠繼續運作。
   * 如果您刪除已安裝 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服務的 vCenter Server 實例 A，而且您使用針對 vCenter Server 實例 B 中的服務所訂購的專用子網路的 IP 位址，則專用子網路會在刪除 vCenter Server 實例 A 時立即被取消。

## 相關鏈結
{: #caveonix_considerations-related}

* [訂購 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [管理 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
