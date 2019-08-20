---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-16"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware 實作及管理
{: #kmip-implementation}

## 連接金鑰管理伺服器
{: #kmip-implementation-connecting-kms}

若要使用 KMIP for VMware on {{site.data.keyword.cloud_notm}} 來啟用 vSphere 加密或 vSAN 加密，您需要完成下列作業：

1. [在帳戶中啟用服務端點](/docs/account?topic=account-vrf-service-endpoint#service-endpoint)。
2. 使用 [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial) 或 [IBM Cloud Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) 來建立金鑰管理程式實例。如果您是使用 Hyper Protect Crypto Services，請務必[起始設定您的加密實例](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm)，讓 Hyper Protect Crypto Services 可以提供金鑰相關功能。
3. 在金鑰管理程式實例內建立客戶根金鑰 (CRK)。
4. 建立 Identity and Access Management (IAM) [服務 ID 及 API 金鑰](/docs/iam?topic=iam-serviceidapikeys)，以與 KMIP for VMware 搭配使用。將此服務 ID 平台檢視者存取權及服務寫入權授與金鑰管理程式實例。
5. 從 {{site.data.keyword.cloud_notm}} 型錄，建立 [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering) 實例。
6. 在 VMware vCenter 內，建立具有兩部伺服器的金鑰管理伺服器 (KMS) 叢集，所選擇地區中的每個 KMIP for VMware 端點都有一個。
7. 選取其中一種 VMware 方法，以在 vCenter 中產生或安裝 KMS 用戶端憑證。
8. 匯出公用版本的憑證，並將它配置為 KMIP for VMware 實例中容許的用戶端憑證。

## 啟用加密
{: #kmip-implementation-enable-encrypt}

若要使用 vSAN 加密，請編輯 vCenter 叢集中的 vSAN 一般設定，並選取加密勾選框。

vSAN 性能檢查可能會定期發出警告，指出它無法從您的一部以上 vSphere 主機連接至 KMS 叢集。這些警告發生的原因是 vSAN 性能檢查連線太快逾時。您可以忽略這些警告。如需相關資訊，請參閱 [因出現「SSL 信號交換逾時」錯誤，而發生 vSAN KMS 性能檢查間歇性失敗](https://kb.vmware.com/s/article/67115){:new_window}。
{:note}

若要使用 vSphere 加密，請編輯虛擬機器儲存空間原則，以要求磁碟加密。

## 金鑰替換
{: #kmip-implementation-key-rotation}

使用 {{site.data.keyword.cloud_notm}} 主控台或 API，替換您的 [Key Protect](/docs/services/key-protect?topic=key-protect-rotate-keys#rotate-keys) 或 [Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-rotating-keys) 客戶根金鑰 (CRK)。

對於 VMware vSAN 加密，透過 vCenter 叢集中的 vSAN 一般設定來替換 VMware 金鑰的加密金鑰 (KEK) 以及選擇性地替換資料加密金鑰 (DEK)。

對於 VMware vSphere 加密，使用 **Set-VMEncryptionKey** PowerShell 指令來替換 VMware KEK 及 DEK（選擇性）。

## 金鑰撤銷
{: #kmip-implementation-key-revocation}

您可以藉由從金鑰管理程式中刪除選擇的 CRK，來撤銷 KMIP for VMware 正在使用的所有金鑰。

撤銷金鑰時，此方法會以加密方式清除受這些金鑰及 KMIP for VMware 實例所保護的所有資料。VMware 會保留部分金鑰，同時開啟 ESXi 主機的電源，因此，您需要重新啟動 vSphere 叢集，確定無法再使用所有已加密資料。
{:important}

KMIP for VMware 會使用與 VMware 已知之金鑰 ID 相關聯的名稱，將個別包裝的 KEK 儲存在 Key Protect 或 Hyper Protect Crypto Services 實例中。您可以刪除個別金鑰，以撤銷個別磁碟或磁碟機的加密。

從庫存中移除具有已加密磁碟的 VM 時，VMware 不會刪除 KMS 中的金鑰。這樣可容許從備份回復該 VM，或將它還原至庫存。如果您要收回這些金鑰，並以加密方式讓所有備份都失效，則需要在刪除 VM 之後從金鑰管理程式實例中刪除金鑰。
{:note}

## 相關鏈結
{: #kmip-implementation-related}

* [解決方案概觀](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)
* [解決方案設計](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)
* [IBM Cloud Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)
