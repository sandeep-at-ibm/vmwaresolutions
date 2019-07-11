---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: set credentials, user credentials, set notifications

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理使用者帳戶及設定
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}} 透過 {{site.data.keyword.slapi_short}} 呼叫，與 {{site.data.keyword.cloud_notm}} 基礎架構進行通訊。若要安全地存取 {{site.data.keyword.slapi_short}}，您必須將 {{site.data.keyword.cloud_notm}} 基礎架構帳戶的認證鏈結至 {{site.data.keyword.cloud_notm}} 帳戶。

您也可以指定是否要接收各種事件的電子郵件及主控台通知。

## 開始之前
{: #useraccount-reqs}

* 您只能將一個 {{site.data.keyword.cloud_notm}} 基礎架構帳戶鏈結至一個 {{site.data.keyword.cloud_notm}} 使用者帳戶。
* 您使用的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶必須符合特定需求。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 基礎架構帳戶需求](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)。
* 如果 {{site.data.keyword.cloud_notm}} 基礎架構帳戶的 API 金鑰變更，則您必須在 {{site.data.keyword.vmwaresolutions_short}} 主控台的**設定**頁面上更新金鑰。

   您負責確保**設定**頁面上儲存的 API 金鑰正確且最新。否則，需要 API 金鑰驗證的作業可能會失敗。
   {:important}

## 設定通知的程序
{: #useraccount-set-notif}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**設定**。
2. 如果您要在事件發生時透過電子郵件通知您，請按一下**啟用電子郵件通知**。
3. 如果您要在事件發生時透過主控台通知您，請按一下**啟用主控台通知**。

## 設定使用者帳戶認證的程序
{: #useraccount-set-cred}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**設定**。
2. 在 **IBM Cloud 基礎架構認證**區域中，檢閱您需要執行之步驟的資訊。
3. 如果您同時有鏈結在一起的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶和 {{site.data.keyword.cloud_notm}} 帳戶，請按一下**擷取**以自動填寫認證。
4. 如果您同時有未鏈結在一起的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶和 {{site.data.keyword.cloud_notm}} 帳戶，則必須進行鏈結。按照[鏈結 IBM ID 帳戶](/docs/account?topic=account-unifyingaccounts#link_accounts)中的指示進行操作，然後按一下**擷取**以自動填寫認證。
5. 如果您沒有 {{site.data.keyword.cloud_notm}} 基礎架構帳戶，且您沒有計費 {{site.data.keyword.cloud_notm}} 帳戶，請先[升級帳戶](/docs/account?topic=account-upgrading-account)，然後[建立標準基礎架構 API 金鑰](/docs/iam?topic=iam-classic_keys)。
6. 如果您沒有 {{site.data.keyword.cloud_notm}} 基礎架構帳戶，且您有計費 {{site.data.keyword.cloud_notm}} 帳戶，則必須[建立標準基礎架構 API 金鑰](/docs/iam?topic=iam-classic_keys)。
7. 按一下**儲存認證**。

## 結果
{: #useraccount-results}

鏈結 {{site.data.keyword.cloud_notm}} 帳戶與 {{site.data.keyword.cloud_notm}} 基礎架構帳戶之後，主控台會自動擷取 {{site.data.keyword.cloud_notm}} 基礎架構帳戶認證，以與 {{site.data.keyword.cloud_notm}} 上的 VMware 環境通訊。

所儲存的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶認證用於需要與 {{site.data.keyword.cloud_notm}} 基礎架構互動的未來作業。

如果針對某些實例事件啟用電子郵件或主控台通知，則會在發生這些事件時透過電子郵件或主控台訊息通知您。

## 相關鏈結
{: #useraccount-related}

* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [通知](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [SoftLayer API](/docs/customer-portal?topic=customer-portal-customerportal_api)
