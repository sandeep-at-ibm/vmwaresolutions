---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware 實作及管理

**附註**：在此版本中，KMIP for VMware on {{site.data.keyword.cloud_notm}} 僅限進行 vSphere 加密。

## 連接金鑰管理伺服器

若要使用 KMIP for VMware on {{site.data.keyword.cloud_notm}} 來啟用 vSphere 加密或 vSAN 加密，您需要完成下列作業：

1. [針對服務端點啟用帳戶](/docs/services/service-endpoint/enable-servicepoint.html#getting-started)。
2. 建立 [IBM Key Protect](/docs/services/key-protect/index.html) 實例。
3. 在 IBM Key Protect 內建立客戶主要金鑰 (CRK)。
4. 建立 Identity and Access Management (IAM) [服務 ID 及 API 金鑰](/docs/iam/serviceid_keys.html)，以與 KMIP for VMware 搭配使用。將此服務 ID 平台檢視者存取權及服務寫入權授與 Key Protect 實例。
5. 從 {{site.data.keyword.cloud_notm}} 型錄，建立 [KMIP for VMware](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html) 實例。
6. 在 VMware vCenter 內，建立具有兩部伺服器的金鑰管理伺服器 (KMS) 叢集，所選擇地區中的每個 KMIP for VMware 端點都有一個。
7. 選取其中一種 VMware 方法，以在 vCenter 中產生或安裝 KMS 用戶端憑證。
8. 匯出公用版本的憑證，並將它配置為 KMIP for VMware 實例中容許的用戶端憑證。

## 啟用加密

若要使用 vSAN 加密，請編輯 vCenter 叢集中的 vSAN 一般設定，並選取加密勾選框。

若要使用 vSphere 加密，請編輯虛擬機器儲存空間原則，以要求磁碟加密。

## 金鑰替換

使用 {{site.data.keyword.cloud_notm}} 主控台或 API，以[替換 Key Protect 客戶主要金鑰 (CRK)](/docs/services/key-protect/rotate-keys.html)。

對於 VMware vSAN 加密，透過 vCenter 叢集中的 vSAN 一般設定來替換 VMware 金鑰的加密金鑰 (KEK) 以及選擇性地替換資料加密金鑰 (DEK)。

對於 VMware vSphere 加密，使用 **Set-VMEncryptionKey** PowerShell 指令來替換 VMware KEK 及 DEK（選擇性）。

## 金鑰撤銷

您可以從 Key Protect 刪除選擇的 CRK，來撤銷 KMIP for VMware 正在使用的所有金鑰。

撤銷金鑰時，此方法會以加密方式清除受這些金鑰及 KMIP for VMware 實例所保護的所有資料。VMware 會保留部分金鑰，同時開啟 ESXi 主機的電源，因此，您需要重新啟動 vSphere 叢集，確定無法再使用所有已加密資料。
{:important}

KMIP for VMware 會使用與 VMware 已知之金鑰 ID 相關聯的名稱，將個別包裝的 KEK 儲存至 Key Protect 實例。您可以刪除個別金鑰，以撤銷個別磁碟或磁碟機的加密。

從庫存中移除具有已加密磁碟的 VM 時，VMware 不會刪除 KMS 中的金鑰。這樣可容許從備份回復該 VM，或將它還原至庫存。如果您要收回這些金鑰，並以加密方式讓所有備份都失效，則需要在刪除 VM 之後從 Key Protect 中刪除金鑰。
{:note}

### 相關鏈結

* [解決方案概觀](/docs/services/vmwaresolutions/archiref/kmip/overview.html)
* [解決方案設計](/docs/services/vmwaresolutions/archiref/kmip/design.html)
* [IBM Key Protect](/docs/services/key-protect/index.html)
