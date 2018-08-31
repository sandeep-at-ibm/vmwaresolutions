---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-08"

---

# 將 2.5 版之前的 Cloud Foundation 實例移轉至 IBM Cloud 帳戶

{{site.data.keyword.cloud}} 帳戶中部署於 2.5 版及更新版本的 VMware Cloud Foundation 實例會自動新增至您的帳戶，並由 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 管理。

對於已部署在 2.4 版及更早版本中的實例，您可以將它們移轉至指定的 {{site.data.keyword.cloud_notm}} 帳戶，以進行啟用 IAM 功能的使用者管理。


## 程序

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在主控台的右上角，按一下您的虛擬人像，然後按一下**帳戶**欄位，選取您要將實例移轉至其中的使用者帳戶。
3. 在 **Cloud Foundation 實例**表格中，尋找 2.5 版之前的實例。
4. 在**動作**直欄中，按一下溢位功能表圖示，然後按一下**將實例移轉至帳戶**。
5. 在**將實例移轉至帳戶**視窗中，確認要將實例移轉至其中的帳戶，然後按一下**移轉**。

## 結果

1. 您會收到主控台通知，指出已接受將實例移轉至指定 {{site.data.keyword.cloud_notm}} 帳戶的要求。
2. 完成實例移轉時，實例即會顯示在**已部署的實例**頁面的移轉目的地帳戶下方。移轉的實例不再顯示於移轉來源的原始帳戶中。

### 相關鏈結

* [利用 IAM 管理使用者存取](../vmonic/iam.html)
* [邀請使用者存取服務及資源](../vmonic/iamuserinvite.html)
* [何謂 IBM Cloud IAM](https://console.stage1.bluemix.net/docs/iam/index.html#iamoverview)
