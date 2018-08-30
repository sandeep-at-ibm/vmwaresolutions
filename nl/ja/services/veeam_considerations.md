---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Veeam on IBM Cloud の概要

Veeam on {{site.data.keyword.cloud}} サービスは VMware ハイパーバイザーに直接、シームレスに統合され、企業での高可用性の実現を支援します。 このサービスを使用すると、アプリケーションとデータのリカバリー・ポイントと目標復旧時間を利用できます。 リカバリー・ポイントと目標復旧時間は、構成が完了してから 15 分以内に利用可能になります。 このサービスを使用することにより、ご使用のインフラストラクチャーに配置されたすべての仮想マシン (VM) のバックアップとリストアの両方を Veeam コンソールから直接制御できます。

**利用可否**: このサービスは、V1.8 以降のリリースでデプロイされたインスタンスでのみ利用可能です。

## Veeam on IBM Cloud の技術仕様

以下のコンポーネントが注文され、Veeam on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### VSI

* Veeam Backup および Replication 9.5 OS Add-on のある単一の VSI
* Windows Server 2016 Standard Edition (64 ビット)
* 4 x 2.0 GHz コア
* 8 GB RAM
* 1 Gbps のプライベート・ネットワーク・アップリンク
* 100 GB ディスク (SAN)

### バックアップ用ストレージ

* エンデュランス iSCSI ストレージ (2000、4000、8000、または 12000 GB)
* ストレージ・パフォーマンス (0.25、2、または 4 IOPS/GB)

### ネットワーキング

1 つのプライマリー・プライベート IP アドレス。

### ライセンスと料金

Veeam Backup および Replication 9.5 Enterprise Plus (10、25、50、100、または 200 VM ライセンス)。

### 管理

最大 5 個の VM と 2000 GB のストレージを使用してデフォルトで構成される管理バックアップ。

## Veeam on IBM Cloud をインストールする際の考慮事項

ストレージ・リポジトリーと Veeam サーバーは、元のポッドおよびデータ・センターにあります。そのため、リモート・クラスターのバックアップ操作のパフォーマンスが低下する可能性があります。

## Veeam on IBM Cloud を削除する際の考慮事項

Veeam on {{site.data.keyword.cloud_notm}} サービスを削除する前に、このサービスを削除するとすべてのバックアップ (管理 VM のバックアップを含む) が停止し、作成済みのバックアップがすべて削除されることに留意してください (削除操作は取り消しできません)。 その後に管理 VM が破損しても、リストアできません。

### 関連リンク

* [Veeam on {{site.data.keyword.cloud_notm}} の注文](veeam_ordering.html)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理](managingveeam.html)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理対象サービスの要求](managing_veeam_services.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam の Web サイト](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
