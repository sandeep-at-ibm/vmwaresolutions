---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial for Migration and App Modernization の概要
{: #cloud_modern_bundle_overview}

Single-node Trial for Migration and App Modernization では、VMware ワークロードを {{site.data.keyword.cloud_notm}} にマイグレーションしてから、コンテナーを使用して単純なワークロードをモダナイズする、という {{site.data.keyword.cloud_notm}} のテスト・ドライブを行うことができます。

この Single-node Trial は、VMware vCenter Server on {{site.data.keyword.cloud_notm}} に置かれた {{site.data.keyword.cloud_notm}} Private Hosted のトライアル・バージョンです。オンプレミス環境と同じツールで管理できる Kubernetes コンテナー管理プラットフォームと単一テナント VMware プラットフォームが提供されます。 制御性および可視性はオンプレミスと同じレベルに保ったまま、クラウドの速度およびスケールというメリットを享受できます。

このトライアルの目的は、vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle を使用して開発用またはテスト用の単純なワークロードを最大 20 個移行し、Kubernetes ベースの {{site.data.keyword.cloud_notm}} Private Hosted アプリケーション開発プラットフォームを使用してそれらのワークロードをコンテナー化することです。 自動機能によって、VMware HCX が {{site.data.keyword.cloud_notm}} にインストールされて構成され、オンプレミス HCX アクティベーション・キーが提供され、小規模な開発/テスト用のトポロジーの {{site.data.keyword.cloud_notm}} Private Hosted が数時間のうちにインストールされて構成されます。

Single-node Trial for Migration and App Modernization は PoC (概念検証) のみを目的としています。 この環境では実動ワークロードを実行しないでください。 ホストやクラスターの追加と削除、アドオン・サービスの注文、更新の適用などの管理機能はサポートされません。
{:important}

Single-node Trial インスタンスを最大限に利用するには、[IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:new_window} の [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:new_window} を使用してください。これは、{{site.data.keyword.cloud_notm}} への VMware ワークロードのマイグレーションを支援するものです。 さらに、[{{site.data.keyword.cloud_notm}}Garage Services](https://www.ibm.com/cloud/garage/){:new_window} を使用すれば、クラウド・ネイティブの最新の手法でアプリケーションのモダナイゼーションを加速化できます。

このトライアル版は最大 90 日間使用できます。 トライアル期間が終了したら、この環境を削除し、キャパシティーのニーズを満たす新しい環境をプロビジョンできます。
{:note}

## Single-node Trial for Migration and App Modernization インスタンスの技術仕様
{: #cloud_modern_bundle_overview-tech-specs}

Single-node Trial for Migration and App Modernization インスタンスには以下のコンポーネントが含まれています。

標準化されたハードウェア構成の使用可否と価格は、デプロイメントに選択した {{site.data.keyword.CloudDataCent_notm}}によって異なる場合があります。
{:note}

### ベア・メタル・サーバー
{: #cloud_modern_bundle_overview-bare-metal}

Dual Intel Xeon Gold 5120 プロセッサー / 合計 28 コア、2.2 GHz、384 GB RAM (VM は最大約 20 台)

#### CPU オーバーコミット
{: #cloud_modern_bundle_overview-cpu}

* vCenter Server 管理、HCX、およびカスタマー・ワークロード VM 20 台用に 16:1 CPU オーバーコミット
* {{site.data.keyword.cloud_notm}} Private 用に 11:1 CPU オーバーコミット

#### RAM オーバーコミット
{: #cloud_modern_bundle_overview-ram}

* ワークロード VM 20 台 (8 GB/VM) のカスタマー・デプロイメントの場合は 1.22:1 RAM オーバーコミット
* ワークロード VM 9 台 (8 GB/VM) のカスタマー・デプロイメントの場合は 1:1 (オーバーコミットなし)

### NFS ストレージ
{: #cloud_modern_bundle_overview-nfs-storage}

* 管理用に 2 TB
* カスタマー・ワークロード用に 1 TB (カスタマー VM 20 台の場合)
* {{site.data.keyword.cloud_notm}} Private Hosted 用に 4 TB

### Single-node Trial for Migration and App Modernization インスタンスのネットワーキング仕様
{: #cloud_modern_bundle_overview-networking-specs}

以下のネットワーキング・コンポーネントが注文されます。
*  10 Gbps デュアル・ネットワーク・アップリンク (パブリックとプライベート)
*  VLAN (仮想 LAN) 3 つ: パブリック VLAN 1 つとプライベート VLAN 2 つ
*  レイヤー 2 (L2) ネットワークに接続されたローカル・ワークロード間で実行される可能性のある東西通信用の DLR (分散論理ルーター) を備えた VXLAN (仮想拡張可能 LAN) 1 つ。 この VXLAN は、サンプルのルーティング・トポロジーとしてデプロイされるので、変更したり、作成の基礎として使用したり、削除したりできます。 また、DLR の新しい論理インターフェースにさらに VXLAN を接続してセキュリティー・ゾーンを追加することもできます。
*  以下の 2 つの VMware NSX Edge Services Gateway
  * アウトバウンド HTTPS 管理トラフィック用のセキュアな管理サービス VMware NSX Edge Services Gateway (ESG)。これは、管理ネットワーキング・トポロジーの一部として IBM がデプロイします。 この ESG は、IBM 管理 VM が、自動化に関連する特定の外部 IBM 管理コンポーネントと通信するために使用します。

    ユーザーは、この ESG にアクセスすることはできず、使用できません。 これを変更すると、{{site.data.keyword.vmwaresolutions_short}} コンソールから Single-node Trial for Migration and App Modernization インスタンスを管理できなくなる可能性があります。 また、ファイアウォールを使用したり、外部 IBM 管理コンポーネントへの ESG 通信を無効にしたりすると、{{site.data.keyword.vmwaresolutions_short}} が使用不可になります。
    {:important}
  * アウトバウンドとインバウンドの HTTPS ワークロード・トラフィック用のユーザー管理のセキュアな VMware NSX Edge Services Gateway。これは、VPN アクセスまたはパブリック・アクセスを提供するためにユーザーが変更可能なテンプレートとして IBM がデプロイします。

### 仮想サーバー・インスタンス
{: #cloud_modern_bundle_overview-vsi}

以下の仮想サーバー・インスタンス (VSI) が注文されます。

* IBM CloudBuilder の VSI。これは、インスタンスのデプロイメントが完了した後にキャンセルされます。
* Microsoft Active Directory (AD) 用の Microsoft Windows Server VSI がデプロイされて参照可能になります。 この VSI がインスタンスの DNS として機能し、ここにホストと VM が登録されます。

### IBM 提供のライセンスおよび料金
{: #cloud_modern_bundle_overview-license-and-fee}

Single-node Trial for Migration and App Modernization インスタンスの注文には、以下のライセンスが含まれています。

* VMware vSphere Enterprise Plus 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

Single-node Trial for Migration and App Modernization インスタンスは、ライセンス持ち込みをサポートしていません。
{:note}

## VMware HCX on IBM Cloud の技術仕様
{: #cloud_modern_bundle_overview-hcx-tech-specs}

Single-node Trial for Migration and App Modernization には、HCX on {{site.data.keyword.cloud_notm}} が含まれています。 以下のコンポーネントが注文されて HCX on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

オンプレミスの HCX インスタンスには、ライセンス交付とアクティベーションのみが含まれます。
{:note}

### HCX 管理用の VMware NSX Edge Services Gateways のアクティブ/パッシブ・ペア
{: #cloud_modern_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* ディスク: 3 GB VMDK

### HCX 管理アプライアンス - 仮想マシン
{: #cloud_modern_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* ディスク: 60 GB VMDK

構成時には必要に応じて、L2 接続、WAN 最適化、およびゲートウェイ接続のために追加の HCX アプライアンスがデプロイされます。

### HCX on IBM Cloud のネットワーキング仕様
{: #cloud_modern_bundle_overview-hcx-networking-specs}

* 16 個の IP アドレスを持つ 1 つのパブリック・ポータブル・サブネット
* 64 個の IP アドレスを持つ 2 つのプライベート・ポータブル・サブネット
* プライベート・ポータブル vMotion サブネットからの 8 個の IP アドレス

## IBM Cloud Private Hosted の技術仕様
{: #cloud_modern_bundle_overview-icp-tech-specs}

すべての Single-node Trial for Migration and App Modernization インスタンスに、{{site.data.keyword.cloud_notm}} Private Hosted V3.1.2 が開発/テスト用のトポロジーでインストールされます。 {{site.data.keyword.cloud_notm}} Private Hosted について詳しくは、[{{site.data.keyword.cloud_notm}}Private Hosted の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)を参照してください。

## IBM Cloud Automation Manager の技術仕様
{: #cloud_modern_bundle_overview-cam-tech-specs}

すべての Single-node Trial for Migration and App Modernization インスタンスに、{{site.data.keyword.cloud_notm}} Automation Manager V3.1.2 が開発/テスト用のトポロジーでインストールされます。 {{site.data.keyword.cloud_notm}} Automation Manager について詳しくは、[{{site.data.keyword.cloud_notm}} Automation Manager の資料](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: new_window}を参照してください。

## 関連リンク
{: #cloud_modern_bundle_overview-related}

* [vCenter Server および {{site.data.keyword.cloud_notm}} Private ガイド](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [{{site.data.keyword.cloud_notm}} Private のチケットをオープン](https://www.ibm.com/mysupport/s/?language=en_US){:new_window}
* [VMware HCX リソース](https://hcx.vmware.com/#/docs){:new_window}
* [VMware HCX ユーザー・ガイド](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:new_window}
