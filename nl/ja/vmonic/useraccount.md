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

# ユーザー・アカウントと設定の管理
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}} は、{{site.data.keyword.slapi_short}} 呼び出しを介して {{site.data.keyword.cloud_notm}} インフラストラクチャーと対話します。 {{site.data.keyword.slapi_short}} に安全にアクセスするには、{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの資格情報を {{site.data.keyword.cloud_notm}} アカウントにリンクさせる必要があります。

各種イベントの E メールとコンソールの通知を受け取るかどうかを指定することもできます。

## 始める前に
{: #useraccount-reqs}

* 1 つの {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントだけを 1 つの {{site.data.keyword.cloud_notm}} ユーザー・アカウントにリンクできます。
* 使用する {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントは特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの要件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)を参照してください。
* {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの API 鍵が変更された場合は、{{site.data.keyword.vmwaresolutions_short}} コンソールの**「設定」**ページで鍵を更新する必要があります。

   **「設定」**ページに保存されている API 鍵が最新かつ正確であることを確認してください。 正確でない場合、API 鍵の検証を必要とする操作が失敗する可能性があります。
   {:important}

## 通知を設定する手順
{: #useraccount-set-notif}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「設定」**をクリックします。
2. イベントが発生したときに E メールで通知を受け取るには、**「E メール通知を有効にする」**をクリックします。
3. イベントが発生したときにコンソールで通知を受け取るには、**「コンソール通知を有効にする」**をクリックします。

## ユーザー・アカウント資格情報を設定する手順
{: #useraccount-set-cred}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「設定」**をクリックします。
2. **「IBM Cloud インフラストラクチャー資格情報 (IBM Cloud Infrastructure Credentials)」**領域で、実行する必要がある手順を確認します。
3. {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントと {{site.data.keyword.cloud_notm}} アカウントの両方があり、それらがリンクされている場合は、**「取得 (Retrieve)」**をクリックすると、資格情報が自動的に入力されます。
4. {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントと{{site.data.keyword.cloud_notm}} アカウントの両方があり、それらがリンクされていない場合は、それらのアカウントをリンクさせる必要があります。[IBMid アカウントのリンク](/docs/account?topic=account-unifyingaccounts#link_accounts)の手順を実行してから、**「取得 (Retrieve)」**をクリックして、資格情報を自動的に取り込みます。
5. {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントがなく、{{site.data.keyword.cloud_notm}} 請求可能アカウントもない場合には、まず[アカウントをアップグレード](/docs/account?topic=account-upgrading-account)してから、[クラシック・インフラストラクチャー API キーを作成](/docs/iam?topic=iam-classic_keys)します。
6. {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントがなく、{{site.data.keyword.cloud_notm}} 請求可能アカウントがある場合には、[クラシック・インフラストラクチャー API キーを作成](/docs/iam?topic=iam-classic_keys)する必要があります。
7. **「資格情報の保存」**をクリックします。

## 結果
{: #useraccount-results}

{{site.data.keyword.cloud_notm}} アカウントと {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントがリンクされると、コンソールは自動的に {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの資格情報を取得し、{{site.data.keyword.cloud_notm}} 上の VMware 環境と対話します。

これ以降、{{site.data.keyword.cloud_notm}} インフラストラクチャーとの対話を必要とするアクションには、ここで保管した {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウント資格情報が使用されます。

E メール通知またはコンソール通知を有効にしたインスタンス・イベントがある場合、それらのイベントが発生すると、E メールまたはコンソールのメッセージで通知されます。

## 関連リンク
{: #useraccount-related}

* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [通知](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [SoftLayer API](/docs/customer-portal?topic=customer-portal-customerportal_api)
