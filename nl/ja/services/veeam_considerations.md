---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud の概要
{: #veeam_considerations}

Veeam on {{site.data.keyword.cloud}} サービスは VMware ハイパーバイザーに直接、シームレスに統合され、企業での高可用性の実現を支援します。 このサービスを使用すると、アプリケーションとデータのリカバリー・ポイントと目標復旧時間を設定できます。 リカバリー・ポイントと目標復旧時間は、構成が完了してから 15 分以内に利用可能になります。 このサービスを使用することにより、ご使用のインフラストラクチャーに配置されたすべての仮想マシン (VM) のバックアップとリストアの両方を Veeam コンソールから直接制御します。

このサービスは、V1.8 以降でデプロイされたインスタンスでのみ利用可能です。 現在インストールされている Veeam のバージョンは 9.5u4 です。
{:note}

## Veeam on IBM Cloud の技術仕様
{: #veeam_considerations-specs}

以下のコンポーネントが注文され、Veeam on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### VSI
{: #veeam_considerations-specs-vsi}

* Veeam Backup and Replication 9.5 OS Add-on のある単一の VSI
* Windows Server 2016 Standard Edition (64 ビット)
* 4 x 2.0 GHz コア
* 8 GB RAM
* 1 Gbps のプライベート・ネットワーク・アップリンク
* 100 GB ディスク (SAN)

### バックアップ用ストレージ
{: #veeam_considerations-specs-storage}

* エンデュランス iSCSI ストレージ (2000、4000、8000、または 12000 GB)
* ストレージ・パフォーマンス (0.25、2、または 4 IOPS/GB)

### ネットワーキング
{: #veeam_considerations-specs-networking}

1 つのプライマリー・プライベート IP アドレス。

### ライセンスと料金
{: #veeam_considerations-specs-licenses}

Veeam Backup and Replication 9.5 Enterprise Plus (10、25、50、100、または 200 VM ライセンス)。

### 管理
{: #veeam_considerations-specs-mgmt}

最大 5 個の VM と 2000 GB のストレージを使用してデフォルトで構成される管理バックアップ。

## Veeam on IBM Cloud をインストールする際の考慮事項
{: #veeam_considerations-install}

ストレージ・リポジトリーと Veeam サーバーは、元のポッドおよびデータ・センターにあります。 そのため、リモート・クラスターのバックアップ操作のパフォーマンスが低下する可能性があります。

## Veeam on IBM Cloud を削除する際の考慮事項
{: #veeam_considerations-remove}

Veeam on {{site.data.keyword.cloud_notm}} サービスを削除すると、すべてのバックアップは停止され、以前のバックアップはすべて削除されます。 管理 VM のバックアップは停止し、以前のバックアップの削除は取り消しできません。 管理 VM が破損しても、リストアできません。

## 関連リンク
{: #veeam_considerations-related}

* [Veeam on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Veeam on {{site.data.keyword.cloud_notm}} 用マネージド・サービスの要求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam の Web サイト](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
