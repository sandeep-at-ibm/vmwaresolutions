---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-03"

---

# 管理使用者帳戶及設定

{{site.data.keyword.vmwaresolutions_full}} 透過 {{site.data.keyword.slapi_short}} 呼叫，與 {{site.data.keyword.cloud_notm}} 基礎架構進行通訊。若要安全地存取 {{site.data.keyword.slapi_short}}，您必須使 {{site.data.keyword.cloud_notm}} 帳戶的認證與 {{site.data.keyword.vmwaresolutions_short}} 使用者帳戶產生關聯。

**附註**：{{site.data.keyword.cloud_notm}} 帳戶先前稱為 IBM SoftLayer 帳戶。

在 {{site.data.keyword.vmwaresolutions_short}}主控台上，您還可以指定是否要接收各種事件的電子郵件通知。

## 開始之前

* 您只能使一個 {{site.data.keyword.cloud_notm}} 帳戶與 {{site.data.keyword.vmwaresolutions_short}} 使用者帳戶產生關聯。
* 您使用的 {{site.data.keyword.cloud_notm}} 帳戶必須符合特定需求。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 帳戶需求](slaccountrequirement.html)。
* 如果 {{site.data.keyword.cloud_notm}} 帳戶中的 API 金鑰變更，則您必須更新 {{site.data.keyword.vmwaresolutions_short}} 使用者帳戶中的金鑰。

   **重要事項**：您有責任確保儲存在**設定**頁面上的 API 金鑰正確無誤且保持最新。否則，需要 API 金鑰驗證的作業可能會失敗。

如果要使 {{site.data.keyword.vmwaresolutions_short}} 帳戶與 {{site.data.keyword.cloud_notm}} 帳戶產生關聯，請在 {{site.data.keyword.vmwaresolutions_short}} 主控台的**設定**頁面上輸入 {{site.data.keyword.cloud_notm}} 帳戶認證。

與 {{site.data.keyword.cloud_notm}} 帳戶產生關聯之後，主控台會自動擷取 {{site.data.keyword.cloud_notm}} 帳戶認證，以便與 {{site.data.keyword.cloud_notm}} 上的 VMware 環境進行通訊。

## 程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**設定**。
2. 如果您要在新事件發生時透過電子郵件通知您，請選取**啟用電子郵件通知**勾選框。
3. 如果您要在新事件發生時透過主控台通知您，請選取**啟用主控台通知**勾選框。
4. 在 **IBM Cloud 基礎架構認證**區域中，輸入 {{site.data.keyword.cloud_notm}} 帳戶的使用者名稱，然後遵循主控台上的指示來輸入 {{site.data.keyword.slapi_short}} 金鑰。
5. 按一下**儲存認證**。

## 結果

所儲存的 {{site.data.keyword.cloud_notm}} 帳戶認證將使用於會需要與 {{site.data.keyword.cloud_notm}} 基礎架構互動的未來作業。如果針對某些實例事件啟用電子郵件或主控台通知，則會在發生這些事件時透過電子郵件或主控台訊息通知您。

## 相關鏈結

* [常見問題](faq.html)
* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)
* [通知](notifications.html)
* [SoftLayer API](../../../customer-portal/cpapi.html){:new_window}
