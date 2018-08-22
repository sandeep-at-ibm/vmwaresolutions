---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-13"

---

# インフラストラクチャーの管理の設計

インフラストラクチャーの管理とは、VMware インフラストラクチャーを管理するコンポーネントのことを指します。この設計では 1 つの外部 Platform Services Controller (PSC) インスタンスと 1 つの vCenter Server インスタンスを使用します。
* vCenter Server は vSphere 環境を管理するための中央プラットフォームで、このソリューションの基本的なコンポーネントの 1 つです。
* このソリューションでは PSC を利用して、VMware vCenter のシングル・サインオン、ライセンス・サービス、ルックアップ・サービス、VMware 証明局など、一連のインフラストラクチャー・サービスを提供します。

PSC インスタンスと vCenter Server インスタンスは別々の仮想マシン (VM) です。

## PSC の設計

この設計では、管理 VM と関連付けられたプライベート VLAN のポータブル・サブネット上に、1 つの外部 PSC が仮想アプライアンスとしてデプロイされます。このデフォルト・ゲートウェイは、バックエンド・カスタマー・ルーター (BCR) に設定されます。仮想アプライアンスは、次の表の仕様を使って構成されます。

**注**: これらの値はデプロイメント時に設定され、変更できません。

表 1. Platform Services Controller の仕様

|属性                    |仕様|
|------------------------------|--------------------------------|
| Platform Services Controller |仮想アプライアンス|
|vCPU の数              | 2                              |
| メモリー                       | 4 GB                           |
|ディスク                        | 114 GB (ローカル VMFS データストア)|
| ディスク・タイプ| シン (プロビジョン済み)|

プライマリー・インスタンスにある PSC には、デフォルトの SSO ドメインである `vsphere.local` が割り当てられます。

## vCenter Server の設計

vCenter Server も仮想アプライアンスとしてデプロイされます。さらに、vCenter Server は管理 VM と関連付けられたプライベート VLAN のポータブル・サブネット上にインストールされます。そのデフォルト・ゲートウェイは、その特定のサブネットの BCR に割り当てられた IP アドレスに設定されます。仮想アプライアンスは、次の表の仕様を使って構成されます。

表 2. vCenter Server アプライアンスの仕様

|属性                    |仕様|
|------------------------------|-------------------------------------|
| vCenter Server               |仮想アプライアンス|
|アプライアンスのインストール・サイズ|メディア (最大でホスト 400 個、VM 4,000 個) |
| Platform Services Controller |外部|
|vCPU の数              | 8                                   |
| メモリー                       | 24 GB                               |
|ディスク                        | ローカル・データストアに 400 GB|
| ディスク・タイプ| シン (プロビジョン済み)|

### vCenter Server データベース

vCenter Server の構成では、アプライアンスに含まれているローカルの組み込み PostgreSQL データベースを使用します。この組み込みのデータベースは、外部データベースおよびライセンス交付の依存関係を削除するために使用されます。

### vCenter Server クラスターの仕様

この設計では、ソリューションでプロビジョニングされた vSphere ESXi ホストをクラスター化することができます。ただし、クラスターを作成する前に、vSphere ESXi ホストとデータ・センター内のポッドの場所を指示するデータ・センター・オブジェクトを作成します。クラスターは、データ・センター・オブジェクトが作成された後に作成されます。クラスターは、VMware vSphere High Availability (HA) と VMware vSphere Distributed Resource Scheduler (DRS) を有効にした状態でデプロイされます。

### vSphere Distributed Resource Scheduler

この設計では、初期クラスターで vSphere Distributed Resource Scheduling (DRS) を使用して VM を配置し、追加のクラスターで DRS を使用して VM を動的にマイグレーションして、バランスのとれたクラスターを実現します。自動化レベルを「完全自動化」に設定して、最初の配置とマイグレーションの推奨が vSphere によって自動的に実行されるようにします。さらに、マイグレーションのしきい値を「中度」に設定することにより、vCenter が優先度 1、2、3 の推奨を適用して、クラスターのロード・バランシングにしかるべき程度以上の改善が見られるようにする必要があります。

**注:** この設計では**分散電源管理**機能での電源管理は使用しません。

### vSphere High Availability

この設計では、初期クラスターおよび追加クラスターで vSphere High Availability (HA) によりコンピューティングの障害が検出され、クラスター内で実行されている VM が修復されます。この設計の vSphere HA 機能は、クラスター内で「**ホストのモニタリング (Host Monitoring)**」と「**アドミッション制御 (Admission Control)**」の両方のオプションを有効にして構成されます。さらに、初期クラスターには、アドミッション制御ポリシーのための予備容量として 1 ノード分のリソースが予約されています。

**注**: クラスターが後に拡張または縮小されるときは、お客様にアドミッション制御ポリシーを調整する責任があります。

デフォルトで、「**VM 再起動優先順位 (VM restart priority)**」オプションは「中 (medium)」に、「**ホスト分離応答 (Host isolation response)**」オプションは無効に設定されています。さらに、「**VM のモニタリング (VM monitoring)**」は無効に設定され、「**データストア・ハートビート (Datastore Heartbeating)**」フィーチャーはすべてのクラスター・データ・ストアを含めるように構成されます。この方法では、NAS データ・ストアがあるときにはそれらを使用します。

## 自動化

これらのソリューションの要となるのは自動化です。自動化では次のようなメリットがあります。
* デプロイメントの複雑性を軽減します。
* デプロイメントの時間を劇的に短縮します。
* VMware インスタンスが一貫した方法でデプロイされることが保証されます。

{{site.data.keyword.IBM}} CloudBuilder、IBM CloudDriver、および SDDC Manager の VM は連携して新たな VMware インスタンスを提供し、ライフサイクル管理機能を実行します。

### IBM CloudBuilder と IBM CloudDriver

IBM CloudBuilder と IBM CloudDriver の仮想サーバー・インスタンス (VSI) は、ユーザーがアクセスできない IBM 開発コンポーネントです。
* IBM CloudBuilder は、プロビジョニングされたベア・メタル ESXi ホスト内でソリューション・コンポーネントのデプロイメント、構成、妥当性検査をブートストラップする、一時的な {{site.data.keyword.cloud_notm}} 仮想サーバー・インスタンス (VSI) です。
* IBM CloudDriver VSI はインスタンス作成のためにデプロイされ、その後は、追加のノード、クラスター、またはサービスのデプロイなどの操作のために {{site.data.keyword.cloud_notm}} for VMware の最新コードで必要に応じて定期的にデプロイされます。IBM CloudDriver は、インスタンスを管理する目的のためにだけデプロイされた VMware NSX Edge Services Gateway を介して {{site.data.keyword.vmwaresolutions_short}} コンソールと通信し、インスタンスを保守するためのエージェントとして機能します。IBM CloudDriver は、クラスターへの新しいベア・メタル・ホストの追加や、インスタンスへのアドオン・サービスのデプロイなど、進行中のアクションに対して責任を負います。Cloud Foundation インスタンスの場合は、IBM CloudDriver は VMware SDDC Manager VM と通信して、ホストの追加やパッチ適用などの機能を実行します。

以降のセクションで説明する VM は、ユーザーによって削除されたり損傷されたりする可能性があります。VM が削除されたり、シャットダウンされたり、稼働不能になったりすると、{{site.data.keyword.vmwaresolutions_short}} コンソール上の Cloud Foundation または vCenter Server の次の操作は中断されます。
* インスタンスやホストの状態の表示
* クラスターの追加や削除
* ESXi ホストの追加や削除
* サービスの追加や削除
* パッチ適用

### SDDC Manager

Cloud Foundation インスタンスの場合、SDDC Manager VM は、VMware によって開発され、保守されるコンポーネントです。そのライフサイクル全体にわたって、インスタンスの一部となります。これは、インスタンスの次のライフサイクル機能に対して責任を負います。
* VMware コンポーネント (vCenter Server、Platform Services Controller (PSC)、vSAN、および NSX) の管理。これには、IP アドレスの割り振りとホスト名の解決などが含まれます。
* NSX VTEP、vSAN、リソース・プールなどの影響を受けるサービスが含まれるクラスター内の ESXi ホストの拡張または縮小。

vCenter Server インスタンスでは SDDC Manager がないため、これらのアクティビティーは IBM CloudDriver によって実行されます。

### 自動化フロー

次の手順は、VMware インスタンスが {{site.data.keyword.vmwaresolutions_short}} コンソールを介して注文される場合のイベントの注文について説明しています。
1.  {{site.data.keyword.cloud_notm}} からネットワーキングのための VLAN とサブネットの注文。
2.  vSphere Hypervisor をインストールした {{site.data.keyword.baremetal_short}} の注文。
3.  該当する場合、Active Directory ドメイン・コントローラーとして機能する Microsoft Windows 仮想サーバー・インスタンス (VSI) の注文。
4.  ネットワーキングとデプロイ済みハードウェアの妥当性検査。
5.  該当する場合、単一ノード vSAN の初期構成。
6.  該当する場合、Active Directory ドメイン・コントローラーとして機能する 2 台の Microsoft Windows 仮想マシンのデプロイメントと構成。
7.  vCenter、PSC、および NSX のデプロイメントと構成。
8.  残りの ESXi ノードのクラスター化、vSAN の拡張 (該当する場合)、および NSX コンポーネント (VTEP) の構成。
9.  VMware Cloud Foundation SDDC Manager VM (該当する場合) および IBM CloudDriver VSI のデプロイメント。
10.  環境のインストールおよび構成の妥当性検査。
11. CloudBuilder VSI の削除。
12. バックアップ・サーバーやストレージなど、オプション・サービスのデプロイメント。

### 関連リンク

* [物理インフラストラクチャー設計](design_physicalinfrastructure.html)
* [仮想インフラストラクチャー設計](design_virtualinfrastructure.html)
* [共通サービス設計](design_commonservice.html)
