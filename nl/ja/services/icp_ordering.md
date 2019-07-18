---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-20"

keywords: IBM Cloud Private Hosted, ICP configuration, order Cloud Private

subcollection: vmware-solutions


---

# IBM Cloud Private Hosted の注文
{: #icp_ordering}

{{site.data.keyword.cloud}} Private Hosted サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの IBM Cloud Private Hosted の注文
{: #icp_ordering-new}

以下のいずれかの方法を使用して、{{site.data.keyword.cloud_notm}} Private Hosted サービスを組み込む形で新しいインスタンスを注文できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから新しいインスタンスを注文する時に、**「オプション・サービス」**セクションの**「IBM Cloud Private Hosted」**を選択します。
* {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware サービス」**セクションの**「IBM Cloud Private Hosted」**カードをクリックします。サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの IBM Cloud Private Hosted の注文
{: #icp_ordering-existing}

以下のいずれかの方法を使用して、既存のインスタンスに {{site.data.keyword.cloud_notm}} Private Hosted サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware サービス」**セクションの**「IBM Cloud Private Hosted」**カードをクリックします。サービス設定を指定し、**「Add to Existing Instance」**を選択します。

## IBM Cloud Private Hosted サービスの構成
{: #icp_ordering-config}

このサービスを注文する際には、以下の設定を行います。
* 必要に応じて、**「実動対応 (Production-Ready)」**または**「開発/テスト (Development/Test)」**を選択します。
* {{site.data.keyword.cloud_notm}} Private Hosted サービスをデプロイするために必要なライセンスを既に取得していることを証明する、必要なチェック・ボックスを選択します。

## 追加ノードのデプロイ
{: #icp_ordering-deploy-nodes}

追加ノードをデプロイする場合は、以下の情報を参照してください。
* {{site.data.keyword.cloud_notm}} Private Hosted の初回インストールでデプロイされる {{site.data.keyword.cloud_notm}} Private Ubuntu テンプレート (Ubuntu1604) を使用します。
* Ubuntu テンプレートを検索するには、VMware vSphere Web Client で、`cam` フォルダーの**「VMs and Templates」**タブに進みます。
* Ubuntu テンプレートのデフォルト・パスワードは `icponcloud` です。 テンプレートを使用する前にこのパスワードを変更することをお勧めします。
* {{site.data.keyword.vmwaresolutions_short}} では、Ubuntu テンプレートのアップデートとパッチの適用はサポートされていません。 これらのアップデートは、自分でモニターし適用する必要があります。

## 関連リンク
{: #icp_ordering-related}

* [IBM Cloud Private Hosted の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
