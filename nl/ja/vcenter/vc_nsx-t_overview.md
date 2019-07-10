---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: vCenter Server NSX-T, NSX-T, tech specs vCenter Server NSX-T

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with NSX-T の概要
{: #vc_nsx-t_overview}

VMware vCenter Server with NSX-T on {{site.data.keyword.cloud}} は、VMware vSphere スタックをサービスとして提供するホステッド・プライベート・クラウドです。 VMware 環境は 3つ以上の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}上に構築され、ネットワークに接続された共有ストレージと専用のソフトウェア定義ストレージのどちらかを選択して使用できます。また、VMware NSX-T で実装される、管理しやすい論理エッジ・ファイアウォールのデプロイメントと構成の自動化機能も含まれています。

多くの場合、環境全体を 1 日以内でプロビジョンできます。また、このベア・メタル・インフラストラクチャーのコンピュート能力は、必要に応じて迅速かつ伸縮自在に拡張や縮小ができます。

デプロイメント後に、{{site.data.keyword.slportal}}からネットワーク・ファイル・システム (NFS) ファイル共有をさらに注文してからクラスター内のすべての ESXi サーバーにそれらを手動で接続することによって、共有ストレージを増やすことができます。

VMware vSAN は専用ストレージのオプションとしても利用できます。 vSAN クラスターの vSAN ベース・ストレージの容量を増やすには、デプロイメント後に ESXi サーバーをさらに追加します。

vCenter Server with NSX-T インスタンスは、PoC (概念検証) とサンドボックス・テストのみを目的としています。 この環境では実動ワークロードを実行しないでください。 アドオン・サービスの注文、更新の適用などの管理機能はサポートされません。
{:important}

## vCenter Server with NSX-T アーキテクチャー
{: #vc_nsx-t_overview-archi}

次の図は、3 ノードの vCenter Server with NSX-T デプロイメントのアーキテクチャーとコンポーネントの全体像を示しています。

![vCenter Server with NSX-T のアーキテクチャー](../images/vc_nsx-t_architecture.svg "vCenter Server with NSX-T のアーキテクチャー")

### 物理インフラストラクチャー
{: #vc_nsx-t_overview-physical-infras}

この層は、仮想インフラストラクチャーで使用する物理インフラストラクチャー (コンピュート、ストレージ、ネットワークのリソース) を提供します。

### 仮想化インフラストラクチャー (コンピュートとネットワーク)
{: #vc_nsx-t_overview-virtualization-infras}

この層は、さまざまな VMware 製品を通して物理インフラストラクチャーを仮想化します。
* VMware vSphere は、物理コンピュート・リソースを仮想化します。
* VMware NSX-T は、論理ネットワーキング・コンポーネントと仮想ネットワークを提供するネットワーク仮想化プラットフォームです。

### 仮想化管理
{: #vc_nsx-t_overview-virtualization-mgmt}

この層は、Platform Services Controller (PSC) が組み込まれた vCenter Server Appliance (vCSA)、3 つの NSX ノード、3 つの NSX Edge Services Gateways (ESG)、および IBM CloudDriver 仮想サーバー・インスタンス (VSI) で構成されます。 CloudDriver VSI は、環境へのホストの追加などの特定の操作のために必要に応じてオンデマンドでデプロイします。

基本オファリングでは、最大 400 台のホストと最大 4000 個の VM が存在する環境をサポートできる規模の vCenter Server アプライアンスがデプロイされます。 vSphere API と互換性のある同じツールとスクリプトを使用して、IBM がホストする VMware 環境を管理できます。

合計で、基本オファリングには、仮想化管理層用に予約される 38 個の vCPU と 128 GB の vRAM が必要です。 VM 用の残りのホスト容量は、オーバーサブスクリプション率、仮想マシン (VM) サイジング、ワークロードのパフォーマンス要件などのいくつかの要因によって決まります。

アーキテクチャーについて詳しくは、[{{site.data.keyword.vmwaresolutions_short}} アーキテクチャーの参照情報](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)を参照してください。

## vCenter Server with NSX-T インスタンスの技術仕様
{: #vc_nsx-t_overview-specs}

vCenter Server with NSX-T インスタンスには、以下のコンポーネントが含まれています。

標準化されたハードウェア構成の使用可否と価格は、デプロイメントに選択した {{site.data.keyword.CloudDataCent_notm}}によって異なる場合があります。
{:note}

### ベア・メタル・サーバー
{: #vc_nsx-t_overview-bare-metal}

以下のいずれかの構成で{{site.data.keyword.baremetal_short}}を 3 つ以上注文できます。
* **Skylake**: 選択した CPU モデルおよび RAM サイズの 2 CPU Intel Skylake 世代サーバー (Intel Xeon 4100/5100/6100 シリーズ)。  
* **Broadwell**: 選択した CPU モデルおよび RAM サイズの 4 CPU Intel Broadwell 世代サーバー (Intel Xeon E7-4800 シリーズ)。

vSAN ストレージを使用する予定である場合は、構成に最低 4 つの{{site.data.keyword.baremetal_short}}が必要です。
{:note}

### ネットワーキング
{: #vc_nsx-t_overview-networking}

以下のネットワーキング・コンポーネントが注文されます。
*  10 Gbps デュアル・ネットワーク・アップリンク (パブリックとプライベート)
*  VLAN (仮想 LAN) 3 つ: パブリック VLAN 1 つとプライベート VLAN 2 つ
* T1 ルーターと T0 ルーターを備えたオーバーレイ・ネットワーク 1 つ (レイヤー 2 (L2) ネットワークに接続されたローカル・ワークロード間で実行される可能性のある東西通信用)。 これはサンプルのルーティング・トポロジーとしてデプロイされるので、変更したり、作成の基礎として使用したり、削除したりできます。
*  以下の 3 つの VMware NSX-T Edge Services Gateway
  * アウトバウンド HTTPS 管理トラフィック用のセキュアな管理サービス VMware NSX ESG 1 つ。これは、管理ネットワーキング類型の一部として IBM がデプロイします。 この ESG は、IBM 管理 VM が、自動化に関連する特定の外部 IBM 管理コンポーネントと通信するために使用します。 詳しくは、[ユーザー管理の NSX ESG を VM で使用するためのネットワークの構成](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config)を参照してください。
  * アウトバウンドとインバウンドの HTTPS ワークロード・トラフィック用のユーザー管理のセキュアな VMware NSX ESG 2 つ。 このゲートウェイは、VPN アクセスまたはパブリック・アクセスを提供するためにユーザーが変更可能なテンプレートとして IBM がデプロイします。 詳しくは、[ユーザー管理の NSX Edge にはセキュリティーのリスクがありますか?](/docs/services/vmwaresolutions?topic=vmware-solutions-faq#faq-customer-nsx) を参照してください。

  この ESG は **mgmt-nsx-edge0** という名前です。 お客様がこの ESG にアクセスしたり使用したりすることはできません。 これを変更すると、{{site.data.keyword.vmwaresolutions_short}} コンソールから vCenter Server インスタンスを管理できなくなる可能性があります。 また、ファイアウォールを使用したり、外部 IBM 管理コンポーネントへの ESG 通信を無効にしたりすると、{{site.data.keyword.vmwaresolutions_short}} が使用できなくなる可能性があります。
  {:important}

### 仮想サーバー・インスタンス
{: #vc_nsx-t_overview-vsi}

以下の仮想サーバー・インスタンス (VSI) が注文されます。
* IBM CloudBuilder の VSI。これは、インスタンスのデプロイメントが完了した後にシャットダウンされます。
* Microsoft Active Directory (AD) 用に 1 つの Microsoft Windows Server VSI をデプロイするか、管理クラスターに 2 つの高可用性 Microsoft Windows VM をデプロイしてセキュリティーと堅牢性を強化するかを選択できます。

### ストレージ
{: #vc_nsx-t_overview-storage}

最初のデプロイメントのときに、vSAN と NFS のどちらかのストレージ・オプションを選択できます。

デプロイの後、NFS ストレージ共有を既存の NFS クラスターまたは vSAN クラスターに追加できます。 詳しくは、[vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)の *vCenter Server インスタンスへの NFS ストレージの追加* のセクションを参照してください。
{:note}

#### vSAN ストレージ
{: #vc_nsx-t_overview-vsan-storage}

vSAN オプションでは、構成をカスタマイズできます。ディスクのタイプ、サイズ、数にも次のように多様なオプションがあります。
* ディスクの数: 2、4、6、8
* ストレージ・ディスク: 960 GB SSD SED、1.9 TB SSD SED、3.8 TB SSD SED。

  さらに、ホストごとに 960 GB のキャッシュ・ディスクが 2 つ注文されます。

  3.8 TB SSD (ソリッド・ステート・ディスク) ドライブは、データ・センターで一般提供が開始されたらサポートされる予定です。
  {:note}
* High-Performance Intel Optane オプション。合計 12 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されます。 このオプションは CPU モデルに応じて異なります。

#### NFS ストレージ
{: #vc_nsx-t_overview-nfs-storage}

NFS オプションでは、ワークロード用のファイル・レベルの共有ストレージをカスタマイズできます。サイズとパフォーマンスをさまざまなオプションから選択できます。
* サイズ: 20 GB から 24 TB
* パフォーマンス: 0.25、2、4、または 10 IOPS/GB
* ファイル共有の個々の構成

  10 IOPS/GB パフォーマンス・レベルは、ファイル共有あたり最大 4 TB の容量に制限されています。
  {:note}

NFS オプションを選択すると、管理コンポーネント用の 2 TB および 4 IOPS/GB ファイル共有が 1 つ注文されます。

### ライセンス (IBM 提供または BYOL) および料金
{: #vc_nsx-t_overview-license-and-fee}

* VMware vSphere Enterprise Plus 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base、Advanced、または Enterprise) 6.4 (IBM 提供のみ)
* (vSAN クラスターの場合) VMware vSAN Advanced または Enterprise 6.6
* サポートとサービスの料金 (ノード当たり 1 つのライセンス)

## vCenter Server with NSX-T 拡張ノードの技術仕様
{: #vc_nsx-t_overview-expansion-node-specs}

vCenter Server with NSX-T 拡張ノードごとに、{{site.data.keyword.cloud_notm}} アカウントに以下のコンポーネントがデプロイされ、料金が発生します。

### 拡張ノード用のハードウェア
{: #vc_nsx-t_overview-expansion-node-hardware}

[vCenter Server with NSX-T インスタンスの技術仕様](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_overview#vc_nsx-t_overview-specs)に示されている構成になっている、1 台のベアメタル・サーバー。

### 拡張ノード用のライセンスと料金
{: #vc_nsx-t_overview-expansion-node-license-and-fee}

* VMware vSphere Enterprise Plus 6.7u1 1 つ
* VMware NSX Service Providers Edition (Base、Advanced、Enterprise) 6.4 1 つ
* 1 つのサポートとサービスの料金
* (vSAN クラスターの場合) VMware vSAN Advanced または Enterprise 6.6

{{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。 {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されません。
インスタンスを注文したときに {{site.data.keyword.cloud_notm}} アカウントにインストールされた {{site.data.keyword.vmwaresolutions_short}} コンポーネントを、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で管理すると、環境が不安定になる可能性があります。 これには以下の管理アクティビティーが該当します。
*  コンポーネントの追加、変更、返却、または削除
*  ESXi サーバーの追加または削除によるインスタンス容量の拡張または縮小
*  コンポーネントのパワーオフ
*  サービスの再始動
   {{site.data.keyword.slportal}}での共有ストレージのファイル共有の管理は、上記アクティビティーに該当しません。 これには、共有ストレージのファイル共有の注文、削除 (マウントされている場合はデータ・ストアに影響する可能性があります)、承認、マウントなどのアクティビティーが含まれます。
   {:important}

## 関連リンク
{: #vc_nsx-t_overview-related}

* [vCenter Server ソフトウェアの部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [vCenter Server インスタンスの計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [vCenter Server with NSX-T インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [vCenter Server の接続ストレージ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-storage-benefits#storage-benefits)
* [ファイル共有容量の拡張](/docs/infrastructure/FileStorage?topic=FileStorage-expandCapacity#expandCapacity)
