---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-02"

keywords: Zerto, Zerto components, tech specs Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud の概要
{: #addingzertodr}

Zerto on {{site.data.keyword.cloud}} サービスは、レプリケーション機能と災害復旧機能をデプロイメント・オファリングに統合して、{{site.data.keyword.cloud_notm}} 上の VMware 仮想環境内のデータを保護および復旧します。

現在インストールされている Zerto on {{site.data.keyword.cloud_notm}} のバージョンは 6.5 更新 4 です。
{:note}

## 始める前に
{: #addingzertodr-req}

* {{site.data.keyword.cloud_notm}} アカウントが有料アカウントであり、インスタンスがデプロイされている {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントにリンクされていることを確認します。 詳しくは、[Zerto レプリケーションの請求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing)を参照してください。
* このサービスは、V1.2 以降でデプロイされたインスタンスでのみ利用可能です。 現在インストールされている Zerto バージョンは 6.5 更新 3 です。

## Zerto on IBM Cloud の技術仕様
{: #addingzertodr-specs}

以下のコンポーネントが注文されて Zerto on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

Zerto Virtual Replication Appliance (VRA) のコンポーネントは、デフォルト・クラスターにのみデプロイされます。
{:note}

### 仮想サービス・インスタンス
{: #addingzertodr-specs-vsi}

* 1 つの仮想サービス・インスタンス (VSI) - Zerto Virtual Manager
* 2 x 2.0 GHz コア
* 4 GB RAM
* Windows Server 2016 Standard Edition (64 ビット)

### ストレージ
{: #addingzertodr-specs-storage}

100 GB (SAN) ディスク

### ネットワーキング
{: #addingzertodr-specs-network}

* VSI
  * 1 つのプライマリー・プライベート IP アドレス
  * 1 Gbps のプライベート・ネットワーク・アップリンク
* Virtual Replication Appliance (VRA)
  * VRA デプロイメント用のプライベート・ポータブル・サブネットを 1 つ。

### ライセンスと料金
{: #addingzertodr-specs-licenses}

Zerto Replication V6.5 更新 3 ライセンス

## 関連リンク
{: #addingzertodr-related}

* [Zerto on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Zerto on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービス](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com Web サイト](https://www.zerto.com){: external}
* [Zerto 技術資料](https://www.zerto.com/myzerto/technical-documentation/){: external}
