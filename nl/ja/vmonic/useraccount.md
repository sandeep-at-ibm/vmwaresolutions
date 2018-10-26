---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# ユーザー・アカウントと設定の管理

{{site.data.keyword.vmwaresolutions_full}} は、{{site.data.keyword.slapi_short}} 呼び出しを介して {{site.data.keyword.cloud_notm}} インフラストラクチャーと対話します。 {{site.data.keyword.slapi_short}} に安全にアクセスするには、{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントの資格情報を {{site.data.keyword.cloud_notm}} アカウントにリンクさせる必要があります。

**注:** {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントは、以前は IBM SoftLayer アカウントと呼ばれていました。

各種イベントの E メールとコンソールの通知を受け取るかどうかを指定することもできます。

## 始める前に

* 1 つの {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントだけを 1 つの {{site.data.keyword.cloud_notm}} ユーザー・アカウントにリンクできます。
* 使用する {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントは特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの要件](slaccountrequirement.html)を参照してください。
* {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントの API 鍵が変更された場合は、{{site.data.keyword.vmwaresolutions_short}} コンソールの**「設定」**ページで鍵を更新する必要があります。

   **重要:** **「設定」**ページに保存されている API 鍵が最新かつ正確であることを確認してください。 正確でない場合、API 鍵の検証を必要とする操作が失敗する可能性があります。

## ユーザー・アカウントと設定を管理する手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「設定」**をクリックします。
2. **「通知」**領域で、通知の設定を指定します。
   * イベントが発生したときに E メールで通知を受け取るには、**「E メール通知を有効にする」**をクリックします。
   * イベントが発生したときにコンソールで通知を受け取るには、**「コンソール通知を有効にする」**をクリックします。
3. **「IBM Cloud インフラストラクチャーの資格情報」**領域に、{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントのユーザー名と API 鍵を入力します。
   * {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントと {{site.data.keyword.cloud_notm}} アカウントがリンクしている場合、**「取得 (Retrieve)」**をクリックして、資格情報を自動入力します。
   * {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントと {{site.data.keyword.cloud_notm}} アカウントがリンクしていない場合は、それらをリンクする必要があります。 [{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータル](https://control.softlayer.com/)にログインしてから、コンソールの指示に従って資格情報を取得して入力します。
   * {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントがない場合、[アカウントを登録](../vmonic/signing_softlayer_account.html)してから、コンソールの指示に従って資格情報を取得して入力します。
4. **「資格情報の保存」**をクリックします。

## 結果

{{site.data.keyword.cloud_notm}} アカウントと {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントがリンクされると、コンソールは自動的に {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントの資格情報を取得し、{{site.data.keyword.cloud_notm}} 上の VMware 環境と対話します。

これ以降、{{site.data.keyword.cloud_notm}} インフラストラクチャーとの対話を必要とするアクションには、ここで保管した {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウント資格情報が使用されます。

E メール通知またはコンソール通知を有効にしたインスタンス・イベントがある場合、それらのイベントが発生すると、E メールまたはコンソールのメッセージで通知されます。

### 関連リンク

* [よくある質問](faq.html)
* [Cloud Foundation インスタンスの注文](../sddc/sd_orderinginstance.html)
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)
* [通知](notifications.html)
* [SoftLayer API](../../../customer-portal/cpapi.html){:new_window}
