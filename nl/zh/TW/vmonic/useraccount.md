---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# 管理使用者帳戶及設定

{{site.data.keyword.vmwaresolutions_full}} 透過 {{site.data.keyword.slapi_short}} 呼叫，與 {{site.data.keyword.cloud_notm}} 基礎架構進行通訊。若要安全地存取 {{site.data.keyword.slapi_short}}，您必須將 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶的認證鏈結至 {{site.data.keyword.cloud_notm}} 帳戶。

**附註：**{{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶先前稱為 IBM SoftLayer 帳戶。

您也可以指定是否要接收各種事件的電子郵件及主控台通知。

## 開始之前

* 您只能將一個 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶鏈結至一個 {{site.data.keyword.cloud_notm}} 使用者帳戶。
* 您使用的 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶必須符合特定需求。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 基礎架構帳戶需求](slaccountrequirement.html)。
* 如果 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶的 API 金鑰變更，則您必須在 {{site.data.keyword.vmwaresolutions_short}} 主控台的**設定**頁面上更新金鑰。

   **重要事項：**您有責任確保儲存在**設定**頁面上的 API 金鑰正確無誤且保持最新。否則，需要 API 金鑰驗證的作業可能會失敗。

## 管理使用者帳戶及設定的程序

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**設定**。
2. 在**通知**區域中，指定您的通知設定。
   * 如果您要在事件發生時透過電子郵件通知您，請按一下**啟用電子郵件通知**。
   * 如果您要在事件發生時透過主控台通知您，請按一下**啟用主控台通知**。
3. 在 **IBM Cloud 基礎架構認證**區域中，輸入您 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶的使用者名稱及 API 金鑰：
   * 如果已鏈結 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶與您的 {{site.data.keyword.cloud_notm}} 帳戶，則請按一下**擷取**以自動輸入認證。
   * 如果未鏈結 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶與您的 {{site.data.keyword.cloud_notm}} 帳戶，則您必須鏈結它們。登入 [{{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站](https://control.softlayer.com/)，然後遵循主控台上的指示以取得並輸入認證。
   * 如果您沒有 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶，則請[註冊帳戶](../vmonic/signing_softlayer_account.html)，然後遵循主控台上的指示以取得並輸入認證。
4. 按一下**儲存認證**。

## 結果

鏈結 {{site.data.keyword.cloud_notm}} 帳戶與 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶之後，主控台會自動擷取 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶認證，以與 {{site.data.keyword.cloud_notm}} 上的 VMware 環境通訊。

所儲存的 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶認證用於需要與 {{site.data.keyword.cloud_notm}} 基礎架構互動的未來作業。

如果針對某些實例事件啟用電子郵件或主控台通知，則會在發生這些事件時透過電子郵件或主控台訊息通知您。

### 相關鏈結

* [常見問題](faq.html)
* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)
* [通知](notifications.html)
* [SoftLayer API](../../../customer-portal/cpapi.html){:new_window}
