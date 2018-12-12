---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# ユース・ケース

## IBM Cloud へのワークロードのマイグレーション
Acme Skateboards 社は、オンプレミスの VMware SDDC を VMware vCenter Server on {{site.data.keyword.cloud}} インスタンスにシームレスに拡張したいと考えています。 その際には、ビジネスを継続して、ダウン時間を最小限に抑える必要があります。 使用しているアプリケーションをクラウドで実行するように再構成することは、最適なソリューションではありません。

VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle を使用することにより、{{site.data.keyword.cloud_notm}} とオンプレミスの VMware 仮想化データ・センターの間にシームレスな接続を作成することができます。

{{site.data.keyword.cloud_notm}} の vCenter Server with Hybridity Bundle オファリングにより、ピアのオンプレミス・ソース・サイトと {{site.data.keyword.cloud_notm}} ターゲット・サイトの間のセキュア接続が可能になります。

図 1. VMware Hybridity サービス

![VMware Hybrid Cloud Extension サービス](vcsicp-hcx.svg)

VMware Hybrid Cloud Extension サービスでは、オンプレミスと {{site.data.keyword.cloud_notm}} 間の疎結合された相互接続が作成され、以下のような機能を使用できるようになります。
- **単純な相互接続** - 論理ネットワーク接続が、公衆インターネット、プライベート VPN、{{site.data.keyword.cloud_notm}} Direct Link などの物理接続を介して簡単に確立されます。
- **レイヤー 2 拡張** - オンプレミス・ネットワーク (オンプレミス・サブネットと IP アドレッシングを含む) がクラウドに拡張されます。
- **暗号化** - ピア・サイト間でネットワーク・トラフィックが安全に暗号化されます。
- **ネットワーク最適化** - 最適な接続を選択し、ネットワーク・トラフィックをできるだけ速く移動するように効率的に接続をフラッディングします。
- **データ重複排除** – 50% ものネットワーク・トラフィックの削減を達成できます。
- **インテリジェント・ルーティング** – ワークロードが移動されるときに、ネットワーク・トラフィックが発信元のサイトに「ヘアピン通信」で戻ることがないようにターゲット・サイトのゲートウェイを使用するようにするため、隣接性ルーティングによってネットワーク・パス (つまり、ゲートウェイ) を変更できます。
- **ゼロ・ダウン時間のマイグレーション** – vMotion を使用して、実行中の仮想マシン (VM) をクラウドとの間で移動できます。
- **スケジュールされたマイグレーション** – 任意の数の VM を宛先サイトに複製し、指定された時刻にそのサイトでアクティブ化して、元のサイトで実行されているシステムを置き換えることができます。
- **セキュリティー・ポリシーのマイグレーション** - NSX をオンプレミスで使用する場合、セキュリティー・ポリシーやファイアウォールなどはすべてワークロードとともに移動されます。

Acme Skateboards 社はこのソリューションを使用して、オンプレミスの VMware ワークロードを {{site.data.keyword.cloud_notm}} に正常にマイグレーションし、ダウン時間がほとんどなく、アプリケーションの再構成も必要ないという要件を満たすことができました。

## ハイブリッド・アーキテクチャーのデプロイメント

Acme Skateboards 社は、アプリケーション・モダナイゼーションに至る過程で、vCenter Server と ICP で構成されるハイブリッド・アーキテクチャーを {{site.data.keyword.cloud_notm}} にデプロイしたいと考えています。 この際の要件は、仮想マシン上でデータベースを実行し、コンテナー内でアプリケーションと Web サービスを実行するとともに、ネットワークとセキュリティーの管理に共通のツール・セットを使用することです。

図 2. Acme Skateboards 社のハイブリッド・アプリケーション

![Acme Skateboards 社のハイブリッド・アプリケーション](vcsicp-acme-skateboards-app.svg)

{{site.data.keyword.vmwaresolutions_short}} は、世界中の {{site.data.keyword.CloudDataCents_notm}}に VMware テクノロジー・コンポーネントをデプロイするための自動化機能を提供します。 このアーキテクチャーは単一のクラウド領域で構成されます。また、別の地域にある追加のクラウド領域、または同じデータ・センター内の別の {{site.data.keyword.cloud_notm}} ポッド (あるいはその両方) に拡張する機能をサポートします。

{{site.data.keyword.cloud_notm}} Private (ICP) 製品および Cloud Automation Manager (CAM) 製品は、オンプレミスの仮想化プラットフォームに手動でデプロイされるので、オンプレミス・ロケーションからクラウド管理を行うことができます。 あるいは、ICP および CAM は、既存または新規の vCenter Server デプロイメントのサービス拡張として自動化機能によって提供され、{{site.data.keyword.cloud_notm}} からのクラウド管理を可能にします。

次の図は、vCenter Server インスタンスで実行される ICP を表しています。ICP オーバーレイ・ネットワークにアクセスするために専用スイッチ/VXLAN、DLR、ESG を使用して NSX-V が構成されており、アンダーレイ・ネットワークにアクセスするために ESG を介してルーティングがセットアップされています。

Acme Skateboards 社は、{{site.data.keyword.cloud_notm}} 自動化を使用して、データベース VM を実行するための VMware on {{site.data.keyword.cloud_notm}} と、アプリとフロントエンド Web サービスをコンテナー内で実行するための VMware on {{site.data.keyword.cloud_notm}} 上の ICP で構成されるハイブリッド・ソリューションをプロビジョンできます。 NSX は、オーバーレイ・ネットワーク内のネットワークとセキュリティー用の共通の管理ツール・セットを提供します。

図 3. ICP を使用する vCenter Server

![ICP を使用する vCenter Server](vcsicp-virtual-icp-deployment-vcs.svg)

### 関連リンク

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](../vcs/vcs-hybridity-intro.html)
