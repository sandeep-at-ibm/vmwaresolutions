---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud の注文
{: #zerto_ordering}

Zerto on {{site.data.keyword.cloud}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## Zerto レプリケーションの請求
{: #zerto_ordering-billing}

Zerto を使用して複製される VM は、Zerto および {{site.data.keyword.cloud_notm}} によって計測されます。 この使用量に対する請求は、{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントではなく {{site.data.keyword.cloud_notm}} 有料アカウントを通じて課金されます。

Zerto on {{site.data.keyword.cloud_notm}} を注文する前に、{{site.data.keyword.cloud_notm}} アカウントが有料アカウントであり、インスタンスのデプロイ先と同じ {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントにリンクされていることを確認してください。

V3.0 以前の Zerto on {{site.data.keyword.cloud_notm}} インストール済み環境がある場合、VM レプリケーション費用はまだ {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求を使用して請求されています。 アカウントと請求設定が前述の要件を満たしている場合は、Zerto 請求方法を請求可能に変換できます。

{{site.data.keyword.vmwaresolutions_short}} コンソールで、{{site.data.keyword.cloud_notm}} インフラストラクチャー・プランから有料プランへ変換し、必要に応じて {{site.data.keyword.cloud_notm}} アカウントから有料アカウントへアップグレードするよう求めるプロンプトが出されます。

* 無料アカウントおよび有料アカウントについては、[アカウント・タイプ](/docs/account?topic=account-accounts)を参照してください。
* 有料アカウントへのアップグレードについては、[アカウントのアップグレード](/docs/account?topic=account-upgrading-account)を参照してください。
* {{site.data.keyword.cloud_notm}} と {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントのリンクについては、[IBMid への切り替えとアカウントのリンク](/docs/account?topic=account-unifyingaccounts)を参照してください。

## 新しいインスタンスでの Zerto on IBM Cloud の注文
{: #zerto_ordering-new}

以下のいずれかの方法を使用して、新しいインスタンスで Zerto on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「Zerto on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware サービス」**セクションの**「Zerto on IBM Cloud」**カードをクリックします。サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの Zerto on IBM Cloud の注文
{: #zerto_ordering-existing}

以下のいずれかの方法を使用して、既存のインスタンスに Zerto on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware サービス」**セクションの**「Zerto on IBM Cloud」**カードをクリックします。サービス設定を指定し、**「Add to Existing Instance」**を選択します。

保守モードの ESXi サーバーを持つ vCenter Server インスタンスに Zerto on {{site.data.keyword.cloud_notm}} を追加する場合は、Zerto Virtual Manager (ZVM) コンソールと事前定義済みの Zerto Virtual Replication Appliance (VRA) IP アドレスを使用して、VRA 仮想マシン (VM) を手動でデプロイする必要があります。
{:note}

## プライベート専用インスタンスでの Zerto on IBM Cloud の注文
{: #zerto_ordering-private-only}

Zerto on {{site.data.keyword.cloud_notm}} をプライベート専用インスタンスに追加する場合、以下の要件が満たされていることを確認してください。
* インターネットに接続するために独自のプロキシー・サーバーをセットアップする作業は、お客様が行う必要があります。 詳しくは、[パブリック・ネットワーク接続](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity)を参照してください。
* Zerto の Call Home 機能も設定する必要があります。 Zerto Call Home について詳しくは、[エンタープライズ環境向けの Zerto Reporting (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:external} を参照してください。

## 関連リンク
{: #zerto_ordering-related}

* [Zerto on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービス](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com Web サイト](https://www.zerto.com){:external}
* [Zerto 技術資料](https://www.zerto.com/myzerto/technical-documentation/){:external}
