---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware 概觀
{: #kmip-overview}

此解決方案架構說明用於保護 VMware on {{site.data.keyword.cloud_notm}} 實例的 KMIP on VMware 架構。有許多儲存空間加密選項可用來保護 VMware 工作負載。KMIP for VMware 與 VMware 原生 vSphere 加密及 vSAN 加密一起使用，以同時提供簡化的儲存空間加密管理以及 {{site.data.keyword.cloud_notm}} Key Protect 或 {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services 客戶管理之金鑰的安全和彈性。

此解決方案被視為 {{site.data.keyword.cloud_notm}} 上 vCenter Server 供應項目的額外元件及延伸。因此，此文件未涵蓋 {{site.data.keyword.cloud_notm}} 上這些基礎解決方案的現有配置。若要深入瞭解基礎解決方案架構，請參閱 [VMware on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)。

## 主要優點
{: #kmip-overview-benefits}

當有許多儲存空間加密解決方案可用於 VMware 工作負載時，KMIP for VMware 提供下列優點：

* 與 VMware vSAN 加密及 vSphere 加密整合，兩者都是在 Hypervisor 層實作，而非儲存空間或虛擬機器層。此方式容許輕鬆管理及瞭解儲存空間解決方案及應用程式。
* 在許多 {{site.data.keyword.cloud_notm}} 多區域地區 (MZR) 中提供完全受管理金鑰管理伺服器。
* 整合 VMWare 叢集和 {{site.data.keyword.cloud_notm}} Key Protect 或 {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services 可提供您可以隨時撤銷且完全由客戶管理的金鑰。

## 相關鏈結
{: #kmip-overview-related}

* [解決方案設計](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [實作及管理](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-implementation)
