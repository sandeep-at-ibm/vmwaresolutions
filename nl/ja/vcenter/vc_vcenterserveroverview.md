---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-01"

---

# vCenter Server の概要

VMware vCenter Server on {{site.data.keyword.cloud}} は、VMware vSphere スタックをサービスとして提供するホステッド・プライベート・クラウドです。 VMware 環境は 2 つ以上 (推奨 3 つ) の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}上に構築され、ネットワークに接続された共有ストレージと専用のソフトウェア定義ストレージのどちらかを選択して使用できます。また、VMware NSX で実装される、管理しやすい論理エッジ・ファイアウォールのデプロイメントと構成の自動化機能も含まれています。

多くの場合、環境全体を 1 日以内でプロビジョンできます。また、このベア・メタル・インフラストラクチャーのコンピュート能力は、必要に応じて迅速かつ伸縮自在に拡張や縮小ができます。

デプロイメント後に、{{site.data.keyword.slportal}}から追加の NFS (ネットワーク・ファイル・システム) ファイル共有を注文して共有ストレージを増やし、クラスター内のすべての ESXi サーバーにそれらを手動で接続できます。 専用ストレージが必要な場合は、[NetApp ONTAP Select on IBM Cloud](../netapp/np_netappoverview.html) を、高性能 (オール SSD) 構成と大容量 (オール SATA) 構成の両方で利用できます。

VMware vSAN は専用ストレージのオプションとしても利用できます。 vSAN クラスターの vSAN ベース・ストレージの容量を増やすには、デプロイメント後に ESXi サーバーをさらに追加します。

IBM 提供の VMware ライセンスを購入した場合は、VMware NSX Base Edition を Advanced Edition または Enterprise Edition にアップグレードできます。VMware vRealize Operations などの追加の VMware コンポーネントも購入できます。

仮想化、ゲスト OS、アプリケーション層の日常業務と保守業務から解放されたい場合は、IBM Managed Services を追加できます。 クラウドの利用をすぐに開始できるように移行、実装、計画、オンボーディングのサービスを提供してお客様を支援する、IBM クラウド・プロフェッショナル・サービス・チームも用意されています。

## vCenter Server アーキテクチャー

次の図は、3 ノードの vCenter Server デプロイメントのアーキテクチャーとコンポーネントの全体像を示しています。

図 1. 3 ノードのクラスターの vCenter Server アーキテクチャーの全体像

![vCenter Server アーキテクチャー](vc_architecture.svg "3 ノードのクラスターの vCenter Server アーキテクチャーの全体像")

### 物理インフラストラクチャー

この層は、仮想インフラストラクチャーで使用する物理インフラストラクチャー (コンピュート、ストレージ、ネットワークのリソース) を提供します。

### 仮想化インフラストラクチャー (コンピュートとネットワーク)

この層は、さまざまな VMware 製品を通して物理インフラストラクチャーを仮想化します。
* VMware vSphere は、物理コンピュート・リソースを仮想化します。
* VMware NSX は、論理ネットワーキング・コンポーネントと仮想ネットワークを提供するネットワーク仮想化プラットフォームです。

### 仮想化管理

この層は、vCenter Server Appliance (vCSA)、NSX Manager、2 つの NSX ESG、3 つの NSX Controller、Platform Services Controller (PSC) 仮想アプライアンス、および IBM CloudDriver 仮想マシンで構成されます。

基本オファリングでは、最大 400 台のホストと最大 4000 個の VM が存在する環境をサポートできる規模の vCenter Server アプライアンスがデプロイされます。 vSphere API と互換性のある同じツールとスクリプトを使用して、IBM がホストする VMware 環境を管理できます。

合計で、基本オファリングには、仮想化管理層用に予約される 38 個の vCPU と 67 GB の vRAM が必要です。 VM 用の残りのホスト容量は、オーバーサブスクリプション率、VM サイジング、ワークロードのパフォーマンス要件などのいくつかの要因によって決まります。

<!-- For details about the architecture, read the _Reference documentation_ on the [Virtualization reference architecture](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/reference-architecture) page. -->

## vCenter Server の技術仕様

vCenter Server インスタンスには、以下のコンポーネントが含まれています。

**注**: 標準化されたハードウェア構成の使用可否と価格は、デプロイメントに選択した {{site.data.keyword.CloudDataCent_notm}}によって異なる場合があります。

### ベア・メタル・サーバー

以下のいずれかの構成で{{site.data.keyword.baremetal_short}}を 3 つ以上注文できます。
*  **カスタマイズ型**: 選択した CPU モデルと RAM サイズの{{site.data.keyword.baremetal_short}}。   
   * 2-CPU Intel Broadwell 世代 (Intel Xeon E5-2600 v4 シリーズ)
   * 2-CPU Intel Skylake 世代 (Intel Xeon 4100/5100/6100 シリーズ)

     **注:** vSAN ストレージを使用する計画がある場合は、構成に 4 つの{{site.data.keyword.baremetal_short}}が必要です。
*  **事前構成型**: 2-CPU Intel Broadwell 世代 (Intel Xeon E5-2600 v4 シリーズ)
   * **スモール** (Dual Intel Xeon E5-2620 v4 / 合計 16 コア、2.1 GHz / 128 GB RAM / 2 ディスク)
   * **ミディアム** (デュアル Intel Xeon E5-2650 v4 / 合計 24 コア、2.2 GHz / 256 GB RAM / 2 ディスク)
   * **ラージ** (Dual Intel Xeon E5-2690 v4 / 合計 28 コア、2.6 GHz / 512 GB RAM / 2 ディスク)

### ネットワーキング

以下のネットワーキング・コンポーネントが注文されます。
*  10 Gbps デュアル・ネットワーク・アップリンク (パブリックとプライベート)
*  VLAN (仮想 LAN) 3 つ: パブリック VLAN 1 つとプライベート VLAN 2 つ
*  レイヤー 2 (L2) ネットワークに接続されたローカル・ワークロード間で実行される可能性のある東西通信用の DLR (分散論理ルーター) を備えた VXLAN (仮想拡張可能 LAN) 1 つ。 この VXLAN は、サンプルのルーティング・トポロジーとしてデプロイされるので、変更したり、作成の基礎として使用したり、削除したりできます。 また、DLR の新しい論理インターフェースに追加の VXLAN を接続してセキュリティー・ゾーンを追加することもできます。
*  以下の 2 つの VMware NSX Edge Services Gateway
  * アウトバウンド HTTPS 管理トラフィック用のセキュアな管理サービス VMware NSX Edge Services Gateway (ESG)。これは、管理ネットワーキング・トポロジーの一部として IBM がデプロイします。 この ESG は、IBM 管理仮想マシンが、自動化に関連する特定の外部 IBM 管理コンポーネントと通信するために使用します。 詳しくは、[ユーザー管理の ESG を使用するためのネットワークの構成](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)を参照してください。

    **重要**: ユーザーは、この ESG にアクセスすることはできず、使用できません。 これを変更すると、{{site.data.keyword.vmwaresolutions_short}} コンソールから vCenter Server インスタンスを管理できなくなる可能性があります。 また、ファイアウォールを使用したり、外部 IBM 管理コンポーネントへの ESG 通信を無効にしたりすると、{{site.data.keyword.vmwaresolutions_short}} が使用不可になります。
  * アウトバウンドとインバウンドの HTTPS ワークロード・トラフィック用のユーザー管理のセキュアな VMware NSX Edge Services Gateway。これは、VPN アクセスまたはパブリック・アクセスを提供するためにユーザーが変更可能なテンプレートとして IBM がデプロイします。 詳しくは、[ユーザー管理の NSX Edge にはセキュリティーのリスクがありますか?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-) を参照してください。

### 仮想サーバー・インスタンス

以下の仮想サーバー・インスタンス (VSI) が注文されます。
* IBM CloudBuilder の VSI。これは、インスタンスのデプロイメントが完了した後にシャットダウンされます。
* (V2.2 以降のインスタンス) Microsoft Active Directory (AD) 用に 1 つの Microsoft Windows Server VSI をデプロイするか、管理クラスターに 2 つの高可用性 Microsoft Windows VM をデプロイしてセキュリティーと堅牢性を強化するかを選択できます。
* (インスタンス V1.9 から V2.1 の場合) Microsoft Active Directory (AD) 用の Microsoft Windows Server VSI。ホストと仮想マシンが登録されたインスタンスの DNS として機能します。これがデプロイされて参照可能になります。
* (インスタンス V1.8 以前の場合) 管理コンポーネントのスナップショット・ベース・バックアップ用の VSI。これは、インスタンスのデプロイメントが完了した後も継続して実行されます。

### ストレージ

最初のデプロイメントのときに、vSAN と NFS のどちらかのストレージ・オプションを選択できます。

vSAN オプションでは、構成をカスタマイズできます。ディスクのタイプと数にも次のように多様なオプションがあります。
* ディスクの数: 2、4、6、8
* ストレージ・ディスク: 960 GB SSD SED、1.9 TB SSD SED、3.8 TB SSD SED。

  さらに、ホストごとに 960 GB のキャッシュ・ディスクが 2 つ注文されます。

  **注:** 3.8 TB SSD (ソリッド・ステート・ディスク) ドライブは、データ・センターで一般提供が開始されたらサポートされる予定です。

NFS オプションでは、ワークロード用のファイル・レベルの共有ストレージをカスタマイズできます。サイズとパフォーマンスをさまざまなオプションから選択できます。
* サイズ: 1、2、4、8、12 TB
* パフォーマンス: 2、4、10 IOPS/GB。
* ファイル共有の個々の構成。

NFS オプションを選択すると、以下のファイル共有が注文されます。
* 管理コンポーネント用の 2 TB の 4 IOPS/GB ファイル共有 1 つ。
* バックアップ用の 2 TB (最大 12 TB まで拡張可能) のブロック・レベルの共有ストレージ 1 つ。 バックアップ・サービスを選択することで、バックアップ用ストレージが要るかどうかを選択できます。

### ライセンス (IBM 提供または BYOL) および料金

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base、Advanced、または Enterprise) 6.3
* (vSAN クラスターの場合) VMware vSAN Advanced または Enterprise 6.6
* サポートとサービスの料金 (ノード当たり 1 つのライセンス)

## vCenter Server 拡張ノードのコンポーネント

vCenter Server 拡張ノードごとに、{{site.data.keyword.cloud_notm}} アカウントに以下のコンポーネントがデプロイされ、料金が発生します。

### 拡張ノード用のハードウェア

[vCenter Server の概要](vc_vcenterserveroverview.html)の『_vCenter Server の技術仕様_』セクションに記載している構成のベア・メタル・サーバー 1 つ。

### 拡張ノード用のライセンスと料金

* VMware vSphere Enterprise Plus 6.5u1 1 つ
* VMware NSX Service Providers Edition (Base、Advanced、Enterprise) 6.3 1 つ
* 1 つのサポートとサービスの料金
* (vSAN クラスターの場合) VMware vSAN Advanced または Enterprise 6.6

**重要**: {{site.data.keyword.cloud_notm}} アカウントに作成された {{site.data.keyword.vmwaresolutions_short}} コンポーネントの管理は、{{site.data.keyword.vmwaresolutions_short}} コンソールでのみ行ってください。{{site.data.keyword.slportal_full}}などのコンソール以外の手段は使用しないでください。 {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されません。

**注意**: インスタンスを注文したときに {{site.data.keyword.cloud_notm}} アカウントにインストールされた {{site.data.keyword.vmwaresolutions_short}} コンポーネントを、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で管理すると、環境が不安定になる可能性があります。 これには以下の管理アクティビティーが該当します。
*  コンポーネントの追加、変更、返却、または削除
*  ESXi サーバーの追加または削除によるインスタンス容量の拡張または縮小
*  コンポーネントのパワーオフ
*  サービスの再始動

   {{site.data.keyword.slportal}}での共有ストレージのファイル共有の管理は、上記アクティビティーに該当しません。 これには、共有ストレージのファイル共有の注文、削除 (マウントされている場合はデータ・ストアに影響する可能性があります)、承認、マウントなどのアクティビティーが含まれます。

## 関連リンク

* [vCenter Server ソフトウェアの部品構成表](vc_bom.html)
* [vCenter Server インスタンスの計画](vc_planning.html)
* [vCenter Server インスタンスの注文](vc_orderinginstance.html)
* [{{site.data.keyword.cloud_notm}} のファイル・ストレージとブロック・ストレージ](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}
