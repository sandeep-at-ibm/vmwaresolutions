---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud の概要

Zerto on {{site.data.keyword.cloud}} サービスは、レプリケーション機能と災害復旧機能をデプロイメント・オファリングに統合して、{{site.data.keyword.cloud_notm}} 上の VMware 仮想環境内のデータを保護および復旧します。

このサービスは、V1.2 以降でデプロイされたインスタンスでのみ利用可能です。 現在インストールされている Zerto バージョンは 6.0 更新 3 です。
{:note}

## Zerto on IBM Cloud の技術仕様

以下のコンポーネントが注文されて Zerto on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

**注:** Zerto Virtual Manager コンポーネントはデフォルト・クラスターにのみデプロイされます。

### VSI

* 1 つの仮想サービス・インスタンス (VSI) - Zerto Virtual Manager
* 2 x 2.0 GHz コア
* 4 GB RAM
* Windows Server 2016 Standard Edition (64 ビット)

### ストレージ

100 GB (SAN) ディスク

### ネットワーキング

* 1 つのプライマリー・プライベート IP アドレス
* 1 Gbps のプライベート・ネットワーク・アップリンク

### ライセンスと料金

Zerto Replication V6.0 更新 3 ライセンス

### 関連リンク

* [{{site.data.keyword.vmwaresolutions_short}} について](../vmonic/prod_overview.html)
* [Zerto on {{site.data.keyword.cloud_notm}} の注文](zerto_ordering.html)
* [Zerto on {{site.data.keyword.cloud_notm}} の管理](managingzertodr.html)
* [Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービスの要求](managing_zerto_services.html)
* [zerto.com Web サイト](https://www.zerto.com){:new_window}
* [Zerto 技術資料](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
