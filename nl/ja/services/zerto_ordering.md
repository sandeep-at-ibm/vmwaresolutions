---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud の注文
{: #zerto_ordering}

Zerto on {{site.data.keyword.cloud}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの Zerto on IBM Cloud の注文
{: #zerto_ordering-new}

以下のいずれかの方法を使用して、新しいインスタンスで Zerto on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「Zerto on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} カタログから**「Zerto on IBM Cloud」**を選択し、サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの Zerto on IBM Cloud の注文
{: #zerto_ordering-existing}

以下のいずれかの方法を使用して、既存のインスタンスに Zerto on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} カタログから**「Zerto on IBM Cloud」**を選択し、サービス設定を指定し、**「Add to Existing Instance」**を選択します。

保守モードの ESXi サーバーを持つ vCenter Server インスタンスに Zerto for {{site.data.keyword.cloud_notm}} を追加する場合は、Zerto Virtual Manager (ZVM) コンソールと事前定義済みの Zerto Virtual Replication Appliance (VRA) IP アドレスを使用して、VRA 仮想マシン (VM) を手動でデプロイする必要があります。
{:note}

## プライベート専用インスタンスでの Zerto on IBM Cloud の注文
{: #zerto_ordering-private-only}

Zerto on {{site.data.keyword.cloud_notm}} をプライベート専用インスタンスに追加する場合は、以下の要件を満たしてください。
* インターネットに接続するにはお客様が独自のプロキシー・サーバーをセットアップする必要があります。詳しくは、[パブリック・ネットワーク接続](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity)を参照してください。
* Zerto のコール・ホーム機能を構成する必要もあります。Zerto のコール・ホームについて詳しくは、[Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:new_window} を参照してください。

## 関連リンク
{: #zerto_ordering-related}

* [Zerto on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービスの要求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com Web サイト](https://www.zerto.com){:new_window}
* [Zerto 技術資料](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
