---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

---

# KMIP for VMware on IBM Cloud インスタンスの注文
{: #kmip_standalone_ordering}

KMIP for VMware on {{site.data.keyword.cloud}} インスタンスは VMware インスタンスと関連付けずに注文できるので、サービスとインスタンスを柔軟に管理できます。

## 始める前に
{: #kmip_standalone_ordering-req}

以下の作業を完了していることを確認してください。
* **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)を参照してください。
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスをインストールする際の考慮事項](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations-install)に記載されている、すべての考慮事項を確認する。

## KMIP for VMware on IBM Cloud インスタンスを注文する手順
{: #kmip_standalone_ordering-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「開始 (Getting started)」**をクリックします。
2. **「追加サービスの注文 (Order additional services)」**領域で、**「KMIP for VMware on IBM Cloud」**をクリックします。
3. **「KMIP for VMware on IBM Cloud」**ページで、必要に応じてサービス設定を構成します。
4. **「プロビジョン」**をクリックします。

## KMIP for VMware on IBM Cloud サービスの構成
{: #kmip_standalone_ordering-config}

このサービスを注文する際には、以下の設定を行います。

### インスタンス名
{: #kmip_standalone_ordering-config-instance-name}

KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスの名前を指定します。

### サービス地域
{: #kmip_standalone_ordering-config-service-region}

KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスをホストする {{site.data.keyword.cloud_notm}} の地域を選択します。

{{site.data.keyword.cloud_notm}} は、可用性の高い KMIP for VMware on {{site.data.keyword.cloud_notm}} ネットワーク・サービス・エンドポイントを、サービスが使用可能な各地域で維持管理しています。

表 1. KMIP for VMware on {{site.data.keyword.cloud_notm}} ネットワーク・サービス・エンドポイントの地域

| 地域         | エンドポイント               |
|:---------------|:-----------------------|
| ドイツ        |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| シドニー        |  <ul><li><code>kmip-1.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| 東京          | <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| 米国南部       |  <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### サービス ID の API キー
{: #kmip_standalone_ordering-config-api-key}

IBM Key Protect Service インスタンスへのアクセスに使用する {{site.data.keyword.cloud_notm}} サービス ID の API 鍵を入力します。

### Key Protect インスタンス
{: #kmip_standalone_ordering-config-key-protect}

**「Retrieve」**をクリックして、利用可能な IBM Key Protect Service インスタンスのリストを取得し、鍵管理に使用するインスタンスを選択します。

### カスタマー・ルート・キー
{: #kmip_standalone_ordering-config-root-key}

**「Retrieve」**をクリックして、選択した鍵マネージャー・インスタンスに保管されているカスタマー・ルート・キーを取得します。

## 結果
{: #kmip_standalone_ordering-results}

KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスの注文が自動的に開始します。お客様は、注文を処理していることを示す確認メッセージを受信します。インスタンスの詳細を参照して、注文状況を確認できます。

インスタンスを使用する準備ができると、インスタンスの状況が**「インストール済み」**に変更され、お客様は E メールで通知を受け取ります。

## 次に行うこと
{: #kmip_standalone_ordering-next}

注文した KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスにクライアント証明書を追加します。 詳しくは、[KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスの証明書の追加、表示、削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)を参照してください。

## 関連リンク
{: #kmip_standalone_ordering-related}

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスの参照](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスの削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker イベント](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
