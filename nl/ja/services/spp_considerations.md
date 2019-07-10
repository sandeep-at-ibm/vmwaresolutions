---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: IBM Spectrum Protect Plus, SPP, tech specs SPP

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Spectrum Protect Plus on IBM Cloud の概要
{: #spp_considerations}

{{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスは、仮想環境のデータ保護、データ再使用、データ・リカバリーのための効率的でスケーラブルなソリューションを提供します。 サービスをスタンドアロン・ソリューションとして実装することも、お客様の IBM Spectrum Protect 環境と統合して長期保管とデータ・ガバナンスのためにコピーをオフロードすることもできます。

このサービスは、vSphere 6.5 を実行する、V2.2 以降でデプロイまたは V2.2 以降にアップグレードされたインスタンスでのみ利用できます。 現在インストールされている {{site.data.keyword.IBM}} Spectrum Protect Plus のバージョンは V10.1.3 です。
{:note}

## IBM Spectrum Protect Plus on IBM Cloud の技術仕様
{: #spp_considerations-specs}

以下のコンポーネントが注文され、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### vCenter リソース
{: #spp_considerations-vcenter}

* IBM Spectrum Protect Plus サーバーを実行しているサーバー VM
   * Linux 3.10.0-693.11.1.el7.x86_64 オペレーティング・システム
   * 4 x 2.0 GHz コア
   * 32 GB RAM
   * 370 GB のディスク
* IBM Spectrum Protect Plus vSnap サーバーと VADP プロキシーを実行しているセカンダリー VM
   * Linux 3.10.0-693.11.1.el7.x86_64 オペレーティング・システム
   * 選択したストレージ・サイズと [IBM Spectrum Protect Plus Blueprint](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) サイジング・ガイダンスに基づいて構成された CPU および RAM
   * 150 GB のディスク

### バックアップ用ストレージ
{: #spp_considerations-backup-storage}

バックアップ用のカスタマイズ可能ストレージには以下のオプションがあります。
* ファイル・ストレージの数: 1 から 10
* 各エンデュランス・ファイル・ストレージ: 500、1000、2000、4000、8000、または 12000 GB
* ストレージ・パフォーマンス: 0.25、2、または 4 IOPS/GB

計画とサイズ変更について詳しくは、[IBM Spectrum Protect Plus blueprint and sizing tool](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) を参照してください。

### 管理用のストレージ
{: #spp_considerations-mgmt-storage}

1 つのエンデュランス・ファイル・ストレージ (1000 GB、2 IOPS/GB)。これは、IBM Spectrum Protect Plus 仮想マシンをホストし、バックアップ・ストレージと同じサブネット上で稼働します。

### ネットワーキング
{: #spp_considerations-network}

2 個のポータブル・プライベート IP アドレス。

### ライセンスと料金
{: #spp_considerations-license}

* IBM Spectrum Protect Plus (10 個単位で増分可能な、10 個から 1000 個までの VM ライセンス)
* {{site.data.keyword.vmwaresolutions_short}} コンソールから (VM の数は 10 個単位)、または BYOL として提供される IBM Spectrum Protect Plus ライセンス

## IBM Spectrum Protect Plus on IBM Cloud をインストールする際の考慮事項
{: #spp_considerations-install}

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスをインストールする前に、以下の考慮事項を検討してください。

* インスタンスのデフォルト・クラスター内の CPU とメモリーが、IBM Spectrum Protect Plus 仮想マシンを使用するのに十分であることを確認します。
* ESXi サーバーで使用できる NFS マウントが、ESXi サーバーのバージョンに基づいて十分であることを確認します。

  V2.2 以降のリリースでデプロイ (または V2.2 以降のリリースにアップグレード) されたインスタンスでは、VMware に `NFS.MaxVolumes` パラメーターの設定があります。 このパラメーターは、ESXi サーバー上の NFS マウントの最大数を定義するもので、最大 256 に設定できます (ESXi サーバーのバージョンに固有)。 詳しくは、[Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239) を参照してください。

  IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスは、インスタンスのデフォルト・クラスターにおける ESXi サーバーごとに、最大 11 個の NFS ボリュームを使用します。 さらに、このサービスは、バックアップとリストア用の一時的な NFS マウントを作成します。 そのため、確実にサービスを正常にインストールして機能させるためには、NFS マウント数を 64 個以上に設定する必要があります。

## IBM Spectrum Protect Plus on IBM Cloud を削除する際の考慮事項
{: #spp_considerations-remove}

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスを削除する前に、以下の考慮事項を検討してください。
* すべてのバックアップ・ジョブ構成が、アクティブなバックアップ操作またはリストア操作とともに削除されていることを確認します。
* サービスを削除すると、バックアップ・リポジトリーのストレージが IBM Spectrum Protect Plus VM から削除され、ストレージ注文がキャンセルされて、バックアップ・リポジトリー・データが完全に削除されます。
* サービスを削除すると、サービスのために注文したバックアップ・ストレージも削除されます。 サービスの削除中は、すべてのバックアップがアクセス不能になります。

## 関連リンク
{: #spp_considerations-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Preventive Service Planning](https://www-01.ibm.com/support/docview.wss?uid=swg22012650){:new_window}
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp) の管理
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering) の注文
* [IBM Spectrum Protect Plus の資料](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
