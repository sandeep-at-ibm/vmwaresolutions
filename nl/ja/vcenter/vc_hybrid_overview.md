---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# vCenter Server with Hybridity Bundle の概要

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle は、V2.3 以降のリリースで使用可能なインスタンスです。V2.6 以降では、ビジネス・パートナーが vCenter Server with Hybridity Bundle インスタンスを使用できます。

vCenter Server with Hybridity Bundle は、VMware vSphere スタックをサービスとして提供するホステッド・プライベート・クラウドです。この VMware 環境は、4 台の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}上に構築され、専用ストレージとして VMware vSAN を使用し、VMware NSX で実装された管理しやすい論理エッジ・ファイアウォールのデプロイメントと構成が自動で実行されます。また、VMware HCX on {{site.data.keyword.cloud_notm}} サービスが含まれています。

多くの場合、環境全体を 1 日以内でプロビジョンできます。また、このベア・メタル・インフラストラクチャーのコンピュート能力は、必要に応じて迅速かつ伸縮自在に拡張や縮小ができます。

vSAN クラスターの vSAN ベース・ストレージの容量を増やすには、デプロイメント後に ESXi サーバーをさらに追加します。

VMware NSX Advanced エディションを Enterprise エディションにアップグレードできます。VMware vRealize Operations などの追加の VMware コンポーネントも購入できます。

仮想化、ゲスト OS、アプリケーション層の日常業務と保守業務から解放されたい場合は、IBM Managed Services を追加できます。クラウドの利用をすぐに開始できるように移行、実装、計画、オンボーディングのサービスを提供してお客様を支援する、{{site.data.keyword.cloud_notm}} プロフェッショナル・サービス・チームも用意されています。

## vCenter Server with Hybridity Bundle アーキテクチャー

次の図は、3 ノードの vCenter Server with Hybridity Bundle デプロイメントのアーキテクチャーとコンポーネントの全体像を示しています。

図 1. vCenter Server with Hybridity Bundle のアーキテクチャーの全体像

![vCenter Server with Hybridity Bundle のアーキテクチャー](hybrid_architecture.svg "vCenter Server with Hybridity Bundle のアーキテクチャーの全体像")

### 物理インフラストラクチャー

この層は、仮想インフラストラクチャーで使用する物理インフラストラクチャー (コンピュート、ストレージ、ネットワークのリソース) を提供します。

### 仮想化インフラストラクチャー (コンピュート、ストレージ、ネットワーク)

この層は、さまざまな VMware 製品を通して物理インフラストラクチャーを仮想化します。
* VMware vSphere は、物理コンピュート・リソースを仮想化します。
* VMware Virtual SAN (vSAN) は、物理サーバー内のストレージに基づいて、ソフトウェア定義による共有ストレージを提供します。
* VMware NSX は、論理ネットワーキング・コンポーネントと仮想ネットワークを提供するネットワーク仮想化プラットフォームです。

### 仮想化管理

この層は、vCenter Server Appliance (vCSA)、NSX Manager、2 つの NSX ESG、3 つの NSX Controller、Platform Services Controller (PSC) 仮想アプライアンス、および IBM CloudDriver 仮想サーバー・インスタンス (VSI) で構成されます。 CloudDriver VSI は、環境へのホストの追加などの特定の操作のために必要に応じてオンデマンドでデプロイします。

基本オファリングでは、最大 400 台のホストと最大 4000 個の VM が存在する環境をサポートできる規模の vCenter Server アプライアンスがデプロイされます。 vSphere API と互換性のある同じツールとスクリプトを使用して、IBM がホストする VMware 環境を管理できます。

合計で、基本オファリングには、仮想化管理層用に予約される 38 個の vCPU と 67 GB の vRAM が必要です。 VM 用の残りのホスト容量は、オーバーサブスクリプション率、VM サイジング、ワークロードのパフォーマンス要件などのいくつかの要因によって決まります。

HCX on {{site.data.keyword.cloud_notm}} サービスのデプロイ時の追加の管理リソース要件については、[VMware HCX on {{site.data.keyword.cloud_notm}} の概要](../services/hcx_considerations.html)を参照してください。

### インフラストラクチャーのハイブリッド化

この層は、オンプレミス・サイトと {{site.data.keyword.cloud_notm}} サイトの間でリソースを抽象化する役割を果たします。その結果、VM の特性 (IP アドレスなど) を変更しなくても両サイト間でワークロードを安全かつ簡単に移動できるようになります。

VMware Hybrid Cloud Extension (HCX) に基づいてオンプレミス・サイトと {{site.data.keyword.cloud_notm}} サイトの間に疎結合の相互接続を作成すれば、ダウン時間なしでの VM の一括マイグレーションや VM のライブ vMotion が可能になります。

## vCenter Server with Hybridity Bundle インスタンスの技術仕様

vCenter Server with Hybridity Bundle インスタンスには、以下のコンポーネントが含まれています。

**注:** 標準化されたハードウェア構成の使用可否と価格は、デプロイメントに選択した {{site.data.keyword.CloudDataCent_notm}}によって異なる場合があります。

### ベア・メタル・サーバー

vCenter Server with Hybridity Bundle インスタンスの注文では、カスタマイズ型の{{site.data.keyword.baremetal_short}}を 4 台注文します。 次の CPU モデルが用意されています。
  * 2-CPU Intel Broadwell 世代 (Intel Xeon E5-2600 v4 シリーズ)
  * 2-CPU Intel Skylake 世代 (Intel Xeon 4100/5100/6100 シリーズ)

### ネットワーキング

以下のネットワーキング・コンポーネントが注文されます。
*  10 Gbps デュアル・ネットワーク・アップリンク (パブリックとプライベート)
*  VLAN (仮想 LAN) 3 つ: パブリック VLAN 1 つとプライベート VLAN 2 つ
*  レイヤー 2 (L2) ネットワークに接続されたローカル・ワークロード間で実行される可能性のある東西通信用の DLR (分散論理ルーター) を備えた VXLAN (仮想拡張可能 LAN) 1 つ。 この VXLAN は、サンプルのルーティング・トポロジーとしてデプロイされるので、変更したり、作成の基礎として使用したり、削除したりできます。 また、DLR の新しい論理インターフェースに追加の VXLAN を接続してセキュリティー・ゾーンを追加することもできます。
*  以下の 2 つの VMware NSX Edge Services Gateway
  * アウトバウンド HTTPS 管理トラフィック用のセキュアな管理サービス VMware NSX Edge Services Gateway (ESG)。これは、管理ネットワーキング・トポロジーの一部として IBM がデプロイします。 この ESG は、IBM 管理 VM が、自動化に関連する特定の外部 IBM 管理コンポーネントと通信するために使用します。 詳しくは、[ユーザー管理の ESG を使用するためのネットワークの構成](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)を参照してください。

    **重要**: ユーザーは、この ESG にアクセスすることはできず、使用できません。 これを変更すると、{{site.data.keyword.vmwaresolutions_short}} コンソールから vCenter Server with Hybridity Bundle インスタンスを管理できなくなる可能性があります。 また、ファイアウォールを使用したり、外部 IBM 管理コンポーネントへの ESG 通信を無効にしたりすると、{{site.data.keyword.vmwaresolutions_short}} が使用不可になります。
  * アウトバウンドとインバウンドの HTTPS ワークロード・トラフィック用のユーザー管理のセキュアな VMware NSX Edge Services Gateway。これは、VPN アクセスまたはパブリック・アクセスを提供するためにユーザーが変更可能なテンプレートとして IBM がデプロイします。 詳しくは、[ユーザー管理の NSX Edge にはセキュリティーのリスクがありますか?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-) を参照してください。

HCX on {{site.data.keyword.cloud_notm}} サービスのデプロイ時に注文するネットワーキング・コンポーネントについて詳しくは、[HCX on {{site.data.keyword.cloud_notm}} の概要](../services/hcx_considerations.html)を参照してください。

### 仮想サーバー・インスタンス

以下の仮想サーバー・インスタンス (VSI) が注文されます。
* IBM CloudBuilder の VSI。これは、インスタンスのデプロイメントが完了した後にシャットダウンされます。
* Microsoft Active Directory (AD) 用に 1 つの Microsoft Windows Server VSI をデプロイするか、管理クラスターに 2 つの高可用性 Microsoft Windows VM をデプロイしてセキュリティーと堅牢性を強化するかを選択できます。

### vSAN ストレージ

vSAN ストレージでは構成をカスタマイズできます。ディスクのタイプと数にも多様なオプションがあります。
* ディスクの数: 2、4、6、8。
* ストレージ・ディスク: 960 GB SSD SED、1.9 TB SSD SED、3.8 TB SSD SED。

  さらに、ホストごとに 960 GB のキャッシュ・ディスクが 2 つ注文されます。
* High-Performance Intel Optane オプション。合計 10 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されます。このオプションは CPU モデルに応じて異なります。

### IBM 提供のライセンスおよび料金

vCenter Server with Hybridity Bundle インスタンスの注文には、以下のライセンスが含められます。

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Advanced または Enterprise) 6.4
* VMware vSAN (Advanced または Enterprise) 6.6

追加のサポートとサービスの料金が適用される可能性があります。

## vCenter Server with Hybridity Bundle 拡張ノードの技術仕様

vCenter Server with Hybridity Bundle 拡張ノードごとに、{{site.data.keyword.cloud_notm}} アカウントに以下のコンポーネントがデプロイされ、料金が発生します。

### 拡張ノード用のハードウェア

1 つのベアメタル・サーバー (カスタマイズ構成)。

### 拡張ノード用のライセンスと料金

* VMware vSphere Enterprise Plus 6.5u1 1 つ
* VMware NSX Service Providers Edition (Advanced または Enterprise) 6.4 1 つ
* 1 つのサポートとサービスの料金
* VMware vSAN (Advanced または Enterprise) 6.6

**重要**: {{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。 {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されません。

**注意**: インスタンスを注文したときに {{site.data.keyword.cloud_notm}} アカウントにインストールされた {{site.data.keyword.vmwaresolutions_short}} コンポーネントを、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で管理すると、環境が不安定になる可能性があります。 これには以下の管理アクティビティーが該当します。
*  コンポーネントの追加、変更、返却、または削除
*  ESXi サーバーの追加または削除によるインスタンス容量の拡張または縮小
*  コンポーネントのパワーオフ
*  サービスの再始動

   {{site.data.keyword.slportal}}での共有ストレージのファイル共有の管理は、上記アクティビティーに該当しません。 これには、共有ストレージのファイル共有の注文、削除 (マウントされている場合はデータ・ストアに影響する可能性があります)、承認、マウントなどのアクティビティーが含まれます。

### 関連リンク

* [vCenter Server ソフトウェアの部品構成表](vc_bom.html)
* [vCenter Server with Hybridity Bundle インスタンスの要件と計画](vc_hybrid_planning.html)
* [vCenter Server with Hybridity Bundle インスタンスの注文](vc_hybrid_orderinginstance.html)
* [HCX on {{site.data.keyword.cloud_notm}} の概要](../services/hcx_considerations.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
