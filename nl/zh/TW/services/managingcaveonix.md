---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Caveonix console, Caveonix RiskForesight license, login Caveonix console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix}

## 存取 Caveonix RiskForesight 主控台
{: #managingcaveonix-access-console}

若要管理 Caveonix RiskForesight on {{site.data.keyword.cloud}} 服務，您必須完成下列步驟來存取 Caveonix RiskForesight 主控台：

1. 使用 IBM Cloud 基礎架構 VPN 或跳躍伺服器來容許存取 Caveonix RiskForesight 虛擬機器 (VM) 的 IP 位址。您可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台的 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 的服務詳細資料頁面上找到 IP 位址。具體方法如下：
   1. 從 {{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站建立 VPN 密碼。
   2. 使用 {{site.data.keyword.cloud_notm}} 基礎架構 VPN 認證登入資料中心 VPN 入口網站。
   3. 從本端電腦將 IP 位址和主機名稱對映新增至 `hosts` 檔。請使用下列格式：

      ```javascript
      RiskForesight_VM_IP_Address      RiskForesight_FQDN
      ```
2. 若要存取 Caveonix RiskForesight 主控台，請按一下 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上的**檢視 RiskForesight 主控台**，然後使用相同服務詳細資料頁面上列出的認證進行登入。

## 將更新套用至 Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix-update}

您要負責維護 Caveonix RiskForesight，以保持更新至最新版本。您可以從 [Caveonix 服務提供者入口網站](https://support.caveonix.com){:external}下載必要更新。

## 更新 Caveonix RiskForesight 授權

Caveonix RiskForesight 授權的有效期間為一年。您可以在到期時使用下列程序來更新 Caveonix RiskForesight 授權：
1. 訂購新的 Caveonix RiskForesight 授權並複製至 Caveonix RiskForesight 主控台。如需相關資訊，請參閱[訂購 Caveonix RiskForesight 授權的程序](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure)。
2. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台的 **Caveonix RiskForesight 授權**表格中刪除過期的授權。如需相關資訊，請參閱[刪除 Caveonix RiskForesight 授權的程序](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete)。

## 相關鏈結
{: #managingcaveonix-related}

* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [訂購 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
