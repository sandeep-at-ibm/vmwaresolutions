---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-18"

keywords: KMIP for VMware, KMIP stand-alone, tech specs KMIP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud 概觀
{: #kmip_standalone_considerations}

KMIP for VMware on {{site.data.keyword.cloud}} 服務提供全年無休高可性服務，以管理 {{site.data.keyword.cloud_notm}} 中 VMware 所使用的加密金鑰。此服務提供運行環境功能，以容許客戶建立、擷取、啟動、撤銷及毀損加密金鑰。同時提供管理功能來維護用戶端認證與加密金鑰之間的關聯。

在未關聯至 VMware 實例的情況下，KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務提供為獨立式服務。每個服務實例都可以提供一個以上的 vCenter Server 實例或 vSphere 叢集。

## KMIP for VMware on IBM Cloud 的技術規格
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務隨附下列規格：

* VMware 相容的「金鑰管理交互作業通訊協定 (KMIP)」
* 兩個受管理服務：[Key Protect](https://cloud.ibm.com/catalog/services/key-protect){:external} 及 [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services){:external}
* 可在全球多個地理區域使用
* 每個地區提供兩個 KMIP 服務端點，以獲得高可用性

## 安裝 KMIP for VMware on IBM Cloud 實例時的考量
{: #kmip_standalone_considerations-install}

請先檢閱下列考量，再安裝 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例：

* KMIP for VMware on {{site.data.keyword.cloud_notm}} 使用 IBM Key Protect 服務或 Hyper Protect Crypto Services (HPCS) 服務來建立、加密及解密加密金鑰。因此，在安裝 KMIP for VMware on {{site.data.keyword.cloud_notm}} 之前，請先確定下列項目：
   * 您已在要於其中管理 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例的 {{site.data.keyword.cloud_notm}} 地區中訂購可用的 Key Protect 或 HPCS 服務實例。
      * 如需建立 Key Protect 實例的相關資訊，請參閱[佈建服務](/docs/services/key-protect?topic=key-protect-provision)。
      * 如需建立 HPCS 實例的相關資訊，請參閱[佈建服務](/docs/services/hs-crypto?topic=hs-crypto-provision#provision)。除了佈建 HPCS 服務之外，您還必須[起始設定加密實例](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm)，以讓 HPCS 可以提供金鑰相關功能。
   * 已遵循[建立服務 ID](/docs/iam?topic=iam-serviceids) 中的步驟建立 {{site.data.keyword.cloud_notm}} 服務 ID。此服務 ID 用來存取您所建立的 Key Protect 或 HPCS 服務實例。
   * 已為服務 ID 授與下列存取層次：
      * 在平台存取層次：Key Protect 或 HPCS 服務實例的「檢視者」權限
      * 在服務存取層次：Key Protect 或 HPCS 服務實例的「管理員」權限
   * 您具有適用於所建立服務 ID 的 API 金鑰。當您訂購服務時，需要此金鑰。
   * 您已使用 Key Protect 或 HPCS 的 GUI 或 API 建立至少一個客戶根金鑰 (CRK)：
      * 如需使用 Key Protect GUI 或 API 建立根金鑰的相關資訊，請參閱[建立根金鑰](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)或 [IBM Key Protect API](https://cloud.ibm.com/apidocs/key-protect){:external}。
      * 如需使用 HPCS GUI 或 API 建立根金鑰的相關資訊，請參閱[建立根金鑰](/docs/hs-crypto/get-started?topic=hs-crypto-create-root-keys)或 [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto){:external}。

     **重要事項：**沒有 CRK 就無法訂購服務。強烈建議您使用下列方法：使用現有金鑰資料建立 CRK，並備份您要建立的金鑰資料。這樣做，即可確保您可在套用 Key Protect 或 HPCS 以儲存您 CRK 的資料中心故障時回復金鑰。
* 請確定啟用 {{site.data.keyword.cloud_notm}} 基礎架構帳戶來進行「虛擬遞送及轉遞 (VRF)」以及連接至「服務端點」。如需相關資訊，請參閱：
   * [IBM Cloud 上的虛擬遞送及轉遞 (VRF) 概觀](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [啟用服務端點](/docs/account?topic=account-vrf-service-endpoint#service-endpoint)
* 因為僅支援專用連線，所以您不需要針對從 vCenter Server 到 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例端點的網路連線功能，在 vCenter Server 中配置任何防火牆或 SNAT 規則。

如需相關資訊，請參閱 [KMIP for VMware on IBM Cloud 解決方案架構](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)。

## 刪除 KMIP for VMware on IBM Cloud 實例時的考量
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

在您移除 KMIP for VMware on IBM Cloud 服務之後，無法解密該服務保護的所有資料（包括已加密備份）。

## 相關鏈結
{: #kmip_standalone_considerations-related}

* [訂購 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [新增、檢視及刪除 KMIP for VMware on IBM Cloud 實例的憑證](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [檢視 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [刪除 KMIP for VMware on {{site.data.keyword.cloud_notm}} 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker 事件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
