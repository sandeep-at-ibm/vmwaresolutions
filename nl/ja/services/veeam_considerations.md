---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-02"

keywords: Veeam, Veeam install, tech specs Veeam

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud の概要
{: #veeam_considerations}

Veeam on {{site.data.keyword.cloud}} サービスは VMware ハイパーバイザーに直接、シームレスに統合され、企業での高可用性の実現を支援します。 このサービスを使用すると、アプリケーションとデータのリカバリー・ポイントと目標復旧時間を設定できます。 リカバリー・ポイントと目標復旧時間は、構成が完了してから 15 分以内に利用可能になります。 このサービスを使用することにより、ご使用のインフラストラクチャーに配置されたすべての仮想マシン (VM) のバックアップとリストアの両方を Veeam コンソールから直接制御します。

このサービスは、V1.8 以降でデプロイされたインスタンスでのみ利用可能です。 現在インストールされている Veeam のバージョンは 9.5u4b です。
{:note}

## Veeam on IBM Cloud の技術仕様
{: #veeam_considerations-specs}

以下のコンポーネントが注文され、Veeam on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### VSI
{: #veeam_considerations-specs-vsi}

* Veeam Backup and Replication 9.5 OS Add-on と Veeam Availability Suite 9.5 のある単一の VSI
* Windows Server 2016 Standard Edition (64 ビット)
* 4 x 2.0 GHz コア
* 8 vCPU、32 GB RAM
* 1 Gbps のプライベート・ネットワーク・アップリンク
* 100 GB ディスク (SAN)

### バックアップ用ストレージ
{: #veeam_considerations-specs-storage}

* エンデュランス iSCSI ストレージ (2,000、4,000、8,000、または 12,000 GB)
* ストレージ・パフォーマンス (0.25、2、または 4 IOPS/GB)

Veeam サービスのインストールおよび構成の一部として、以下のリポジトリーが作成されます。
* Veeam 構成バックアップ・ファイルの場合: `IC4V Default Config Backup Repository` という名前のリポジトリー。 Veeam バックアップが保管されているフォルダーのパスは、`<Drive>:\ConfigBackup\` です。
* スケールアウトの場合: `IC4V Scale-Out Repository` という名前のリポジトリー。 詳しくは、[スケールアウト・リポジトリーの追加](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icos_ordering#icos_ordering-scale-repo)を参照してください。
* 仮想マシン (VM) バックアップの場合: ``IC4V Default VM Backup Repository`` という名前のリポジトリー。 VM バックアップが保管されているフォルダーのパスは、``<Drive>:\VMBackup\` です。 このリポジトリーは、エクステントとして IC4V Scale-Out Repository`` に追加されます。

### ネットワーキング
{: #veeam_considerations-specs-networking}

1 つのプライマリー・プライベート IP アドレス。

### ライセンスと料金
{: #veeam_considerations-specs-licenses}

* Veeam Availability Suite 9.5 (10、25、50、100、または 200 VM ライセンス)

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
* [Veeam on {{site.data.keyword.cloud_notm}} 用マネージド・サービス](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam の Web サイト](https://www.veeam.com/){:external}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:external}
