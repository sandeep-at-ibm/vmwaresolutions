---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# Zerto on IBM Cloud の概要

Zerto on {{site.data.keyword.cloud}} サービスは、複製と災害復旧の機能を提供します。これらの機能をデプロイメント・オファリングに組み込むことで、{{site.data.keyword.cloud_notm}} 上の VMware 仮想環境内のデータの保護と復旧を行えます。

## Zerto on IBM Cloud の技術的な考慮事項

以下のコンポーネントが注文されて Zerto on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

**注**: Zerto Virtual Manager (ZVM) コンポーネントはデフォルト・クラスターにのみデプロイされます。

### VSI

* 1 つの仮想サービス・インスタンス (VSI) - Zerto Virtual Manager
* 2 x 2.0 GHz コア
* 4 GB RAM
* Windows Server 2012 R2 Standard Edition (64 ビット)

### ストレージ

ディスク: 100 GB (SAN)

### ネットワーキング

* 1 つのプライマリー・プライベート IP アドレス
* 1 Gbps のプライベート・ネットワーク・アップリンク

### ライセンスと料金

Zerto レプリケーション V5.5 ライセンス

### 関連リンク

* [{{site.data.keyword.vmwaresolutions_short}} について](../vmonic/prod_overview.html)
* [Zerto on {{site.data.keyword.cloud_notm}} の注文](zerto_ordering.html)
* [Zerto on {{site.data.keyword.cloud_notm}} の管理](managingzertodr.html)
* [Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービスの要求](managing_zerto_services.html)
* [zerto.com Web サイト](https://www.zerto.com){:new_window}
* [Zerto 技術資料](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
