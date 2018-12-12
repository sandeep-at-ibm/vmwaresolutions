---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# アーキテクチャーの概要

このセクションでは、このリファレンス・アーキテクチャーで使用しているネットワーク・アーキテクチャーについて詳しく説明します。以下のセクションで構成されています。
* **VCS の概要** – このセクションでは、VCS プラットフォームの特長を説明します。
* **ネットワークの概要** – これらのセクションでは、このリファレンス・アーキテクチャーで使用しているネットワーク・コンポーネントについて説明します。
  - **IBM Cloud ネットワーキング** – {{site.data.keyword.cloud}} で提供される物理ネットワークは、{{site.data.keyword.cloud_notm}} によって完全に管理されます。このネットワークの重要な特性を理解しておかないと、オンプレミスとオフプレミスの間のネットワーク・フローや、複数の異なるサービスでホストされるワークロード間のネットワーク・フローを理解することはできません。
  - **NSX-V** - VCS ネットワーキングは、VMware NSX-V によって提供されるオーバーレイを使用して {{site.data.keyword.cloud_notm}} ネットワーク上に構築されます。 このオーバーレイは、{{site.data.keyword.cloud_notm}} アンダーレイ・ネットワークからのトラフィックをセグメント化することにより、BYOIPを含むより高度な制御と構成を可能にします。
  - **IBM Kubernetes Service** - IKS は、コンテナー・ネットワーク・インターフェース・プラグインとして Calico を使用します。
  - **IBM Cloud Private** - ICP は、コンテナー・ネットワーク・インターフェース・プラグインとして Calico を使用します。

* **統合** – このセクションでは、必要なネットワーク・トラフィック・フローおよびアドレッシングを可能にするための以下のネットワーキング・コンポーネントのアーキテクチャーについて説明します。
  - IP アドレスの割り振り
  - ネットワーク・トラフィック・フロー

## VCS の概要

VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle (VCS) は、セキュアでシームレスなインフラストラクチャー・ハイブリッド性と真のアプリケーション・モビリティーを実現するために、素早く簡単にオンプレミス・インフラストラクチャーをクラウドに拡張するために役立つ、ホステッド・プライベート・クラウドです。

VCS Hybridity Bundle は、最低 4 つの {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}上にデプロイされ、仮想ストレージ・エリア・ネットワーク (VSAN) を介して専用ストレージを提供します。さらに、管理しやすいソフトウェア定義ネットワーキング・インフラストラクチャー (NSX-V) を自動でデプロイメントして構成できます。 VCS Hybridity Bundle は、自動化によってデプロイされるリファレンス・アーキテクチャーであり、一貫性、パフォーマンス、コンプライアンスを確保します。 多くの場合、環境全体を 1 日以内にプロビジョンできます。また、このベアメタル・インフラストラクチャーのコンピュート能力とストレージ容量は、必要に応じて迅速かつ伸縮自在に拡張や縮小ができます。

VCS Hybridity Bundle を拡張するために、多くのオプションが用意されています。 {{site.data.keyword.cloud_notm}} サービス・オファリングは、アドオン・ストレージ・オプションやさまざまなパブリック/プライベート WAN 接続オプションを用意しているだけではなく、バックアップと災害復旧を目的としたプラットフォーム・セキュリティー、ネットワーク・セキュリティー、トラフィック・ロード・バランシングの領域も網羅しています。

プラットフォーム・セキュリティー・サービスには HyTrust CloudControl on {{site.data.keyword.cloud_notm}} が含まれますが、これは、自動化されたセキュリティーおよびコンプライアンスのサポートを提供し、クラウド環境と管理者に対してより優れた可視性と制御を可能にしています。 HyTrust DataControl on {{site.data.keyword.cloud_notm}} は、強力な暗号化とスケーラブルな鍵管理によるデータ保護機能を備え、ワークロードを全ライフサイクルにわたって保護します。 {{site.data.keyword.cloud_notm}} Secure Virtualization は、コンプライアンスを簡素化し、暗号化やジオフェンシング・ポリシー、そして役割ベースのアクセス制御によってデータを保護しますが、KMIP for VMware on {{site.data.keyword.cloud_notm}} の暗号鍵ライフサイクル管理オファリングは、{{site.data.keyword.cloud_notm}} サービスやお客様の組み込みアプリケーションで使用される暗号鍵を管理します。

ネットワーク・セキュリティーのオプションには、FortiGate Security Appliance デバイスの高可用性ペアをプロビジョンする FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} があります。これにより、ネットワーク・トラフィックを分析し、仮想インフラストラクチャーを保護できます。別のオプションとして、{{site.data.keyword.cloud_notm}} 上に FortiGate VM の高可用性ペアをデプロイする FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}があります。これにより、仮想インフラストラクチャー内に重要なセキュリティー制御を実装してリスクを軽減できます。 追加のネットワーク・セキュリティー・オファリングを開発中です。

F5 on {{site.data.keyword.cloud_notm}} ネットワーク・ロード・バランサー・サービス・オファリングは、パフォーマンスを最適化し、F5 BIG-IP スイートを使用して、最も重要なアプリケーションの可用性とセキュリティーを確保します。

IBM、Veeam、および Zerto のバックアップおよび災害復旧オファリングは、災害が発生した場合にも安心して運用を継続することができます。 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} は、仮想環境のためのデータ保護と可用性のソリューションです。 Veeam on {{site.data.keyword.cloud_notm}} は、{{site.data.keyword.cloud_notm}} 上で統合されたバックアップ、リカバリー、および複製を行う Always-On Enterprise™ を使用可能にします。 Zerto on {{site.data.keyword.cloud_notm}} は、オンプレミスと {{site.data.keyword.cloud_notm}} のお客様に、フレキシブルかつスケーラブルでセキュアな災害復旧ソリューションを提供します。

{{site.data.keyword.cloud_notm}} VCS Hybridity Bundle は、マネージド・サービスではありませんが、IBM-Managed Services を追加して、仮想化層、ゲスト OS 層、またはアプリケーション層の日常の運用と保守をオフロードできます。 クラウドの利用をすぐに開始できるように移行、実装、計画、オンボーディングのサービスを提供してお客様を支援する、{{site.data.keyword.cloud_notm}} プロフェッショナル・サービス・チームも用意されています。

VCS Hybridity Bundle のプラットフォーム統合オプションは、vRealize Suite や vSphere with Operations Management などの VMware 提供のオプションに限定されず、[vCenter Server と IBM Kubernetes](../vcsiks/vcsiks-intro.html) や [vCenter Server と {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) など、オープン・ソースの Terraform を使用してインフラストラクチャーをコードとして管理、提供する複数の {{site.data.keyword.cloud_notm}} サービス・オファリングにわたります。

VCS Hybridity Bundle で使用可能な広範なサービス・ポートフォリオとマルチオファリング統合オプションは、真のハイブリッド・プラットフォームを提供し、「サービスとしてのハイブリッド性」を可能にします。

### 関連リンク

* [VCS Hybridity Bundle の概要](../vcs/vcs-hybridity-intro.html)
