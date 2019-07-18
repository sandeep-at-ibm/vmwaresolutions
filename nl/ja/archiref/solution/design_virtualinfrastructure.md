---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 仮想インフラストラクチャー設計
{: #design_virtualinfrastructure}

仮想インフラストラクチャー層には、物理インフラストラクチャー層で提供されるコンピュート、ストレージ、ネットワーク・リソースを仮想化する VMware ソフトウェア・コンポーネント (VMware vSphere ESXi、VMware NSX-V または NSX-T、VMware vSAN (オプション)) が含まれます。

![仮想インフラストラクチャー](../../images/vcsv4radiagrams-ra-virtinfra.svg "仮想インフラストラクチャー")

## VMware vSphere 設計
{: #design_virtualinfrastructure-vsphere-design}

vSphere ESXi 構成は、以下の側面から成ります。
* ブート構成
* 時刻同期
* ホスト・アクセス
* ユーザー・アクセス
* DNS 構成

次の表は、各側面の仕様の概要を示しています。 ESXi の構成とインストール後、ホストが VMware vCenter Server に追加され、そこから管理されます。

この設計では、Direct Console User Interface (DCUI) および vSphere Web Client を介して仮想ホストにアクセスできます。 セキュア・シェル (SSH) と ESXi シェルは、プロビジョニング後に無効になるのがベスト・プラクティスです。

デフォルトでは、直接ログインできるユーザーは、ホストの物理マシンの _root_ ユーザーおよび _ibmvmadmin_ ユーザーのみです。 管理者は、Microsoft Active Directory (MSAD) ドメインからユーザーを追加して、ホストへのユーザー・アクセスを可能にすることができます。 vCenter Server ソリューション設計に含まれるホストはすべて、中央 NTP サーバーと同期するように構成されます。

表 1. vSphere ESXi 構成

| 属性              | 構成パラメーター |
|:---------------------- |:----------------------- |
| ESXi ブート・ロケーション     | RAID-1 に構成されたローカル・ディスクを使用 |
| 時刻同期   | {{site.data.keyword.cloud}} NTP サーバーを使用 |
| ホスト・アクセス            | DCUI をサポート。 SSH と ESXi シェルはサポートされますが、デフォルトで無効です |
| ユーザー・アクセス            | ローカル認証と MSAD |
| ドメイン・ネームの解決 | DNS を使用 ([共通サービス設計](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice)を参照) |
| EVC モード | Skylake (新規の vSphere 6.7 デプロイメントの場合のみ) |

vSphere クラスターには、vCenter Server インスタンスとユーザー・ワークロード用コンピュート・リソースを管理する仮想マシン (VM) が収容されます。

* vCenter Server インスタンスが vSAN を使用する場合、初期デプロイメント時の ESXi ホストの最小数は 4 です。
* vCenter Server インスタンスが共有ファイル・レベルまたはブロック・レベルのストレージを使用する場合、初期デプロイメント時の ESXi ホストの最小数は 3 です。

初期デプロイメント時または初期デプロイメント後に、最大 59 ESXi ホストまで拡大できます。

より大きなユーザー・ワークロードをサポートするには、以下の方法で環境を拡大できます。  
* 既存クラスターで追加のコンピュート・ホストをデプロイする
* 同じ vCenter Server Appliance によって管理される追加のクラスターをデプロイする
* 新しい vCenter Server インスタンスをそれ専用の vCenter Server Appliance とともにデプロイする

クラスターの詳細については、[{{site.data.keyword.cloud_notm}} running VMware clusters solution architecture](https://www.ibm.com/cloud/garage/files/IBM-Cloud-for-VMware-Solutions-Multicluster-Architecture.pdf) を参照してください。

## VMware vSAN 設計
{: #design_virtualinfrastructure-vsan-design}

この設計では、vSphere ホストの共有ストレージを提供するために、VMware vSAN ストレージが vCenter Server インスタンスで使用されます。

次の図に示すように、vSAN は、vSphere クラスター内の複数の ESXi ホストそれぞれのローカル・ストレージを集約し、集約ストレージを単一の VM データ・ストアとして管理します。 この設計では、ESXi オペレーティング・システム (OS) と vSAN データ・ストアのためのローカル・ディスク・ドライブがコンピュート・ノードに含まれます。 ノードがどのクラスターに属するかに関係なく、ESXi インストールを収容するために 2 つの OS ドライブが各ノードに組み込まれます。

![vSAN 概念](../../images/vcsv4radiagrams-ra-vsan.svg "vSAN は、vSphere クラスター内の複数の ESXi ホストそれぞれのローカル・ストレージを集約し、集約ストレージを単一の VM データ・ストアとして管理します")

vSAN では、以下のコンポーネントが使用されます。
* 2 ディスク・グループ vSAN 設計。各ディスク・グループは 2 つ以上のディスクで構成されます。 グループ内の最小サイズの SSD 1 つがキャッシュ層として使用され、残りの SSD または NVMe ドライブが容量層として使用されます。
* 2 つの OS ドライブを除いて、ドライブごとにオンボード RAID コントローラーが RAID-0 アレイで構成されます。
* すべてのストレージから単一の vSAN データ・ストアが作成されます。

使用可能な vSAN の機能は、インスタンスの注文時に選択するライセンス・エディションによります。 詳しくは、[VMware vSAN エディションの比較](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix#vmware-vsan-edition-comparison)を参照してください。

### vSAN 用仮想ネットワークのセットアップ
{: #design_virtualinfrastructure-net-setup}

この設計では、vSAN トラフィックは専用プライベート VLAN 上の ESXi ホスト間を横断します。 プライベート・ネットワーク・スイッチに接続された 2 つのネットワーク・アダプターは、vSphere 内で vSphere 分散スイッチ (vDS) として構成され、どちらのネットワーク・アダプターもアップリンクとして指定されます。 vSAN VLAN 用に構成された専用 vSAN カーネル・ポート・グループは、vDS 内に常駐します。 プライベート vDS でジャンボ・フレーム (MTU 9000) が使用可能になります。

vSAN はアップリンク上のトラフィックのロード・バランスを行いません。 結果として、一方のアダプターがアクティブの間、もう一方は高可用性 (HA) をサポートするためにスタンバイ状態になります。 vSAN のネットワーク・フェイルオーバー・ポリシーは、物理ネットワーク・ポート間の**明示的フェイルオーバー**として構成されます。

物理 NIC 接続の詳細については、[物理ホストの NIC 接続](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_physicalinfrastructure#design_physicalinfrastructure-host-connect)を参照してください。

### vSAN ポリシー設計
{: #design_virtualinfrastructure-storage-policy}

vSAN が使用可能になって構成されると、VM ストレージ特性を定義するためにストレージ・ポリシーが構成されます。 ストレージ特性では、VM ごとに異なるサービス・レベルが指定されます。

この設計のデフォルトのストレージ・ポリシーは、単一障害を許容します。 デフォルト・ポリシーにはイレージャー・コーディングが構成され、**「障害許容方式 (Failure tolerance method)」**が**「RAID-5/6 (イレージャー・コーディング) - 容量 (RAID-5/6 (Erasure Coding) - Capacity)」**に設定され、**「障害のプライマリー・レベル (Primary level of failures)」**が 1 に設定されます。RAID 5 構成では最低 4 つのホストが必要です。

あるいは RAID 6 構成を選択して、**「障害許容方式 (Failure tolerance method)」**を**「RAID-5/6 (イレージャー・コーディング) - 容量 (RAID-5/6 (Erasure Coding) - Capacity)」**に設定し、**「障害のプライマリー・レベル (Primary level of failures)」**を 2 に設定することもできます。RAID 6 構成では最低 6 つのホストが必要です。 デフォルトのストレージ・ポリシーで**「複製 (Duplication)」**と**「圧縮 (compression)」**も有効になります。

vSphere コンソールから特に指定されない限り、インスタンスはデフォルト・ポリシーを使用します。 カスタム・ポリシーが構成された場合、vSAN は可能であればそのカスタム・ポリシーを保証します。 しかし、ポリシーを保証できなければ、そのポリシーを使用する VM をプロビジョンすることはできません。ただし、VM が強制的にプロビジョンできるようになっている場合を除きます。

新しい ESXi ホストの追加後、または ESXi ホストのパッチ後は、ストレージ・ポリシーを再適用する必要があります。

### vSAN の設定
{: #design_virtualinfrastructure-vsan-sett}

vSAN の設定は、{{site.data.keyword.cloud_notm}} 内に VMware ソリューションをデプロイするためのベスト・プラクティスに基づいて構成されます。 vSAN の設定には、SIOC 設定、明示的フェイルオーバー設定のポート・グループ、ディスク・キャッシュ設定が含まれます。
* SSD キャッシュ・ポリシーの設定: **「先読み (Read Ahead)」**、**「ライトスルー (Write Through)」**、**「直接 (Direct)」** (NRWTD) なし
* ネットワーク I/O 制御の設定
   * 管理 - 20 共有
   * 仮想マシン - 30 共有
   * vMotion - 50 共有
   * vSAN - 100 共有
* vSAN カーネル・ポート: **「明示的フェイルオーバー (Explicit Failover)」**

## NFS 接続ストレージ
{: #design_virtualinfrastructure-nfs-storage}

NFS ネットワーク接続ストレージを使用する場合、このアーキテクチャーによって、NFS v4.1 ではなく NFS v3 の使用が指示されます。NFS v4.1 を使用すると、NFS サーバー LIF マイグレーションによって過度の待ち時間が生じる可能性があるためです。 各 vSphere ホストはそのホスト名を使用して NFS ストレージに接続されます。

1 つの 2-TB NFS データ・ストアが、4 IOPS/GB パフォーマンス・ティアの管理コンポーネントが使用するために 1 つのクラスターに接続されます。 他のデータ・ストアを、各種のサイズとパフォーマンス・ティアでワークロードに使用するためにクラスターに接続することもできます。

また、このアーキテクチャーでは、NFS ストレージがあるサブネット用に作成されたサブネット経路がすべてのホストに含まれていることも必要です。 このサブネット経路は、この設計で NFS トラフィックに指定されたポート・グループ、サブネット、VLAN をすべての NFS トラフィックで使用するよう指示するためのものです。 複数の NFS データ・ストアが接続されている場合、複数の経路を構成する必要が生じることもあります。これらのデータ・ストアが異なるリモート・サブネットにある可能性があるためです。

管理仮想マシンは、NFS データ・ストアに配置されている場合があります。 これにより、一部の管理マシンが、NFS ホスト名を解決するために使用される DNS サービスの責任を担うことがあるため、ブートストラッピングの問題が生じます。 そのため、このアーキテクチャーでは、管理データ・ストア用に少なくとも 1 つの IP アドレスを各ホストの `/etc/hosts` でハードコーディングするよう指定しています。

## VMware NSX-V 設計
{: #design_virtualinfrastructure-nsx-design}

ネットワーク仮想化により、仮想レイヤー内にネットワーク・オーバーレイが存在するようになります。 ネットワーク仮想化により、オンデマンド仮想ネットワークの迅速なプロビジョニング、デプロイメント、再構成、消滅などの機能を備えたアーキテクチャーになります。 この設計では、vDS と VMware NSX for vSphere を使用して仮想ネットワーキングを実装します。

この設計では、NSX Manager は初期クラスター内にデプロイされます。 NSX Manager には、管理コンポーネント用に指定されたプライベート・ポータブル・アドレス・ブロックから VLAN-backed IP アドレスが割り当てられ、[共通サービス設計](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice)で説明されている DNS サーバーと NTP サーバーが構成されます。

次の図は、NSX Manager の配置をアーキテクチャー内の他のコンポーネントとの関係で示しています。

![NSX Manager ネットワークの概要](../../images/vcsv4radiagrams-ra-vcs-nsx-overview.svg "このアーキテクチャーの他のコンポーネントとの NSX Manager の位置関係")

初期デプロイメント後、{{site.data.keyword.cloud_notm}} の自動化機能によって、初期クラスター内に 3 つの NSX コントローラーがデプロイされます。 コントローラーのそれぞれに、管理コンポーネント用に指定された**プライベート A** ポータブル・サブネットから VLAN-backed IP アドレスが割り当てられます。 さらに、この設計では、クラスター内のホストの中のコントローラーを分離するための VM-VM アンチアフィニティー・ルールが作成されます。 コントローラーの高可用性を確保するためには、初期クラスターに最低 3 つのノードが含まれなければなりません。

コントローラーに加えて、VXLAN トンネル・エンドポイント (VTEP) を介して仮想化ネットワークを使用できるように、NSX VIBS を備えたデプロイ済み vSphere ホストが {{site.data.keyword.cloud_notm}} 自動化機能によって準備されます。 VTEP 用に指定された**プライベート A** ポータブル IP アドレス範囲 ([VLAN](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_physicalinfrastructure#design_physicalinfrastructure-vlans)にリストが記されている) から VLAN-backed IP アドレスが VTEP に割り当てられます。 VXLAN トラフィックはタグの外された VLAN 上に存在し、プライベート vDS に割り当てられます。

続いて、セグメント ID プールが割り当てられ、クラスター内のホストがトランスポート・ゾーンに追加されます。 {{site.data.keyword.cloud_notm}} 内で Internet Group Management Protocol (IGMP) スヌープが構成されないため、トランスポート・ゾーンで使用されるのはユニキャストのみです。 VMW のベスト・プラクティスに従えば、同じ VTEP 専用サブネットのホストごとに 2 つの VTEP カーネル・ポートを構成します。

その後、インスタンスにパブリック・ネットワーク・インターフェースがある場合、2 つの NSX Edge Services Gateway ペアがデプロイされます。 プライベート・ネットワークに常駐する自動化コンポーネントからのアウトバウンド・トラフィックにゲートウェイ・ペアが 1 つ使用されます。 2 つ目のゲートウェイ (カスタマー管理エッジと呼ばれる) がデプロイされ、パブリック・ネットワークへのアップリンクとプライベート・ネットワークに割り当てられるインターフェースが構成されます。 ソリューションの一部としてデプロイされる NSX Edge Services Gateway について詳しくは、[NSX Edge Services Gateway ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-nsx_overview#nsx_overview)を参照してください。

クラウド管理者は、分散論理ルーター (DLR)、論理スイッチ、ファイアウォールなどの必要な NSX コンポーネントを構成できます。 使用可能な NSX の機能は、インスタンスの注文時に選択する NSX ライセンス・エディションによります。 詳しくは、[VMware NSX エディションの比較](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix#vmware-nsx-edition-comparison)を参照してください。

NSX Manager は、次の表に示す仕様でインストールされます。

表 3. NSX Manager の要件

| 属性       | 仕様 |
|:--------------- |:------------- |
| NSX Manager     | 仮想アプライアンス |
| vCPU の数 | 4 |
| メモリー          | 16 GB |
| ディスク            | 管理 NFS 共有上に 60 GB |
| ディスク・タイプ       | シン・プロビジョン |
| ネットワーク         | 管理コンポーネント用に指定された**プライベート A** ポータブル |

### 分散スイッチ設計
{: #design_virtualinfrastructure-distr-switch}

この設計では、最低限の数の vDS スイッチが使用されます。 クラスター内のホストはパブリック・ネットワークとプライベート・ネットワークに接続されます。 ホストには 2 つの分散仮想スイッチが構成されます。 2 つのスイッチの使用は、パブリック・ネットワークとプライベート・ネットワークを分離する {{site.data.keyword.cloud_notm}} ネットワークの手法に従います。 次の図は、vDS 設計を示しています。

![分散スイッチ設計](../../images/vcsv4radiagrams-distributed-switch-design.svg "分散スイッチ設計")

前の図に示すように、一方の vDS はパブリック・ネットワーク接続 (SDDC - 分散スイッチ - パブリック) 用に構成され、もう一方の vDS はプライベート・ネットワーク接続 (SDDC - 分散スイッチ - プライベート) 用に構成されます。 コンテンションと待ち時間を軽減し、セキュリティーを高めるためには、さまざまなタイプのトラフィックを分離することが必要です。

物理ネットワークの機能をセグメント化するために VLAN が使用されます。 この設計では、3 つの VLAN が使用されます。2 つはプライベート・ネットワーク・トラフィック用、1 つはパブリック・ネットワーク・トラフィック用です。 次の表は、トラフィック分離を示しています。

表 4. VLAN とトラフィック・タイプのマッピング

| VLAN  | 指定 | トラフィック・タイプ |
|:----- |:----------- |:------------ |
| VLAN 1 | プライベート A   | ESXi 管理、管理、VXLAN (VTEP) |
| VLAN 2 | プライベート B   | vSAN、NFS、および vMotion|
| VLAN 3 | パブリック      | インターネット・アクセスに使用できます |

ワークロードからのトラフィックは VXLAN­backed 論理スイッチ上を移動します。

vSphere クラスターは、以下の表のように構成された 2 つの vSphere 分散スイッチを使用します。

表 5. コンバージド・クラスター分散スイッチ

| vSphere 分散<br>スイッチ名 | 機能 | ネットワーク<br>I/O 制御 | ロード・バランシング<br>モード | 物理 NIC<br>ポート | MTU |
|:------------- |:------------- |:------------- |:------------- |:------------- |:------------- |
| SDDC - 分散スイッチ - プライベート | ESXi 管理、vSAN、vSphere vMotion、VXLAN トンネル・エンドポイント、NFS (VTEP) | 有効 | 明示的フェイルオーバー (vSAN、vMotion) 起点仮想ポート (その他すべて) に基づくルート | 2 | 9,000<br>(ジャンボ・フレーム) |
| SDDC - 分散スイッチ - パブリック | 外部管理トラフィック (南北) | 有効 | 起点仮想ポートに基づくルート | 2 | 1,500<br>(デフォルト) |

ホスト NIC の名前、数、順序付けは、{{site.data.keyword.CloudDataCent_notm}} とホスト・ハードウェアの選択によって変ることがあります。
{:note}

表 6. コンバージド・クラスター分散スイッチのポート・グループの構成設定

| パラメーター          | 設定       |
|:------------------ |:------------- |
| ロード・バランシング     | 起点仮想ポートに基づくルート \* |
| フェイルオーバー検出 | リンク状況のみ |
| スイッチに通知    | 有効 |
| フェイルバック           | いいえ |
| フェイルオーバー順序     | アクティブ・アップリンク: Uplink1、Uplink2 \* |

\* vSAN ポート・グループは、vSAN ストレージ・トラフィックのロード・バランシングをサポートしていないため、アクティブまたはスタンバイによる明示的フェイルオーバーを使用します。
{:note}

表 7. コンバージド・クラスター仮想スイッチのポート・グループ、VLAN、分散スイッチ **SDDC-Dswitch-Private**

ポート・グループ|チーミング|アップリンク|VLAN ID
---|---|---|--
SDDC - 分散ポート・グループ - 管理|起点仮想ポート|アクティブ: 0、1|VLAN 1
SDDC - 分散ポート・グループ - vMotion|起点仮想ポート|アクティブ: 0、1|VLAN 2
SDDC - 分散ポート・グループ - VSAN|明示的フェイルオーバー|アクティブ: 0、スタンバイ: 1|VLAN 2
SDDC - 分散ポート・グループ - NFS|起点仮想ポート|アクティブ: 0、1|VLAN 2
NSX 生成|起点仮想ポート|アクティブ: 0、1|VLAN 1
SDDC - 分散ポート・グループ - 外部|起点仮想ポート|アクティブ: 0、1|VLAN 3

表 8. コンバージド・クラスター VMkernel アダプター、分散スイッチ **SDDC-Dswitch-Private**

目的|接続されるポート・グループ|使用可能サービス|MTU
--|---|---|---|--
管理|SDDC - 分散ポート・グループ - 管理|管理トラフィック|1500 (デフォルト)
vMotion|SDDC - 分散ポート・グループ - vMotion|vMotion トラフィック|9000
VTEP|NSX 生成|-|9000
vSAN|SDDC - 分散ポート・グループ - VSAN|vSAN|9000
NAS|SDDC - 分散ポート・グループ - NFS|NAS|9000

### NSX 構成
{: #design_virtualinfrastructure-nsx-config}

この設計では、NSX コンポーネントの構成を指定しますが、ネットワーク・オーバーレイ・コンポーネント構成は適用しません。 必要に応じてネットワーク・オーバーレイを設計できます。

以下の側面が事前構成されます。
* 管理サーバーとコントローラーがインストールされ、vCenter Web UI に組み込まれます。
* ESXi ホストごとに ESXi エージェントがインストールされ、VTEP IP アドレスが構成されます。
* VTEP 構成、コントローラー構成、VXLAN 構成 (トランスポート・ゾーン)。
* 管理コンポーネント用 NSX Edge Services Gateway アプライアンス。
* お客様用 NSX Edge Services Gateway アプライアンス。
* NSX VXLAN 処理のお客様のワークロードが分散ローカル・ルーター (DLR) に接続され、DLR とお客様用 ESG の間に伝送 VXLAN が設定されます。
* VXLAN 用の RFC 1918 アドレス・スペースと、お客様用 ESG の egress ネットワークとして使用する IBM Cloud のプライベート/パブリック・ポータブル IP スペース。

以下の側面は構成されません。
* マイクロ・セグメンテーション
* 他の VMware インスタンスに対するリンク NSX 管理

![デプロイされたカスタマー NSX トポロジー例](../../images/vcsv4radiagrams-ra-vcs-nsx-topology-customer-example.svg "デプロイされたカスタマー NSX トポロジー例")

## パブリック・ネットワーク接続

さまざまな理由によって、ご使用のインスタンスでパブリック・ネットワーク接続が必要となることがあります。 例えば、地理位置情報データベースや気象データなどのワークロードのためにパブリック更新サービスや他のパブリック・サービスにアクセスする場合などです。 仮想化管理サービスとアドオン・サービスでも、パブリック接続が必要となったり、パブリック接続を活用すると便利であったりすることがあります。 一例として、vCenter は HCL データベースを更新し、[VMware Update Manager (VUM)](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro) の更新をパブリック・ネットワーク経由で取得できます。 Zerto、Veeam、VMware HCX、F5 BIG-IP、FortiGate-VM では、いずれも製品ライセンス、アクティベーション、使用レポートの一部でパブリック・ネットワーク接続が使用されています。 さらに、レプリケーションのためにオンプレミスのデータ・センターに接続するときにパブリック・ネットワーク経由でトンネルを使用することもあります。

通常、このような通信は管理用またはお客様用のエッジ・サービス・ゲートウェイ (ESG) を介して選択的にパブリック・ネットワークに転送され、NAT 処理されます。 ただし、追加のセキュリティー要件があったり、プロキシーを使用して通信パスを簡略化する方が適していたりする場合もあります。 また、パブリック・インターフェースを無効にした状態でインスタンスをデプロイした場合、ESG を使用してパブリック・ネットワークに経路指定することはできなくなります。

このアーキテクチャーを使用すると、以下のオプションによって、トラフィックをパブリック・ネットワークに経路指定したりプロキシーしたりできます。

方法|説明|制限
--|--|--
仮想化ゲートウェイ|プライベート・ネットワークとパブリック・ネットワークを接続する仮想化ゲートウェイ (例えば、NSX ESG、F5 BIG-IP、FortiGate-VM、お客様が選択した仮想アプライアンスなど) をデプロイします。 パブリック・ネットワーク・トラフィックのみがゲートウェイに送られるようにソース・システム (例えば、vCenter、Zerto、ご使用のワークロードなど) での経路指定を構成し、必要に応じてゲートウェイも構成します。|パブリック・インターフェースを使用できるインスタンスにのみ適用できます。 この構成は、アウトバウンドとインバウンドの両方のトラフィック・パターンに使用できます。
プロキシーを使用した仮想化ゲートウェイ|前述のように仮想化ゲートウェイをデプロイします。 このゲートウェイの背後に[プロキシー・サーバーをデプロイ](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-init-config#vum-init-config)し、このプロキシー経由でパブリック・ネットワークに接続するようにサービスとアプリケーションを構成します。|パブリック・インターフェースを使用できるインスタンスにのみ適用できます。 アウトバウンド・トラフィック・パターンではプロキシーを使用できますが、インバウンド・トラフィック・パターンに関してはゲートウェイで管理する必要があります。
ハードウェア・ゲートウェイ|管理 VLAN に対して[ハードウェア・ゲートウェイ・アプライアンス](https://cloud.ibm.com/catalog/infrastructure/gateway-appliance)をデプロイします。 必要に応じてパブリック・ネットワークにアウトバウンドをネットワーク・アドレス変換するようにゲートウェイを構成します。|パブリック・インターフェースを使用できるかどうかに関係なく、すべてのインスタンスに適用できます。 この構成は、アウトバウンドとインバウンドの両方のトラフィック・パターンに使用できます。
プロキシーを使用したハードウェア・ゲートウェイ|前述のようにゲートウェイ・アプライアンスをデプロイします。 このゲートウェイの背後に[プロキシー・サーバーをデプロイ](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-init-config#vum-init-config)し、このプロキシー経由でパブリック・ネットワークに接続するようにサービスとアプリケーションを構成します。|パブリック・インターフェースを使用できるかどうかに関係なく、すべてのインスタンスに適用できます。 アウトバウンド・トラフィック・パターンではプロキシーを使用できますが、インバウンド・トラフィック・パターンに関してはゲートウェイで管理する必要があります。
ロード・バランサー|IBM Cloud には、アプリケーションに対してインバウンド・ネットワーク・アクセスを提供するために使用できるいくつかの[ロード・バランサー・サービス](https://cloud.ibm.com/catalog/infrastructure/load-balancer-group)が備わっています。|すべてのインスタンスに適用できますが、インバウンド・トラフィック・パターンに限定されます。

## 関連リンク
{: #design_virtualinfrastructure-related}

* [VMware クラスターを実行する {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](https://www.ibm.com/cloud/garage/files/IBM-Cloud-for-VMware-Solutions-Multicluster-Architecture.pdf)
* [NSX Edge Services Gateway ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-nsx_overview#nsx_overview)
