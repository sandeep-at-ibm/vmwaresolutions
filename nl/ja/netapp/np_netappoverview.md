---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: NetApp ONTAP, NetApp, tech specs NetApp ONTAP

subcollection: vmware-solutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}


# NetApp ONTAP Select の概要
{: #np_netappoverview}

{{site.data.keyword.cloud}} デプロイメント上の NetApp ONTAP Select のアーキテクチャーとコンポーネントについて説明します。

## NetApp ONTAP Select のアーキテクチャー
{: #np_netappoverview-archi}

{{site.data.keyword.cloud_notm}} オファリング上の NetApp ONTAP Select は、vCenter Server デプロイメントを補完するためのストレージ仮想化サービスを提供します。

以下の図は、vCenter Server デプロイメントにおける NetApp ONTAP Select のアーキテクチャー全体を示しています。

![NetApp ONTAP Select のアーキテクチャー](../images/np_architecture.svg "NetApp ONTAP Select のアーキテクチャー")

### 物理インフラストラクチャー
{: #np_netappoverview-physical-infras}

この層は、仮想インフラストラクチャーで使用される物理インフラストラクチャー (コンピュート、ネットワーク、ストレージの各リソース) を提供します。

### 仮想化インフラストラクチャー (コンピュート、ネットワーク、NetApp ONTAP Select)
{: #np_netappoverview-virtual-infras}

この層は、以下の VMware 製品と NetApp ONTAP Select 製品により、物理インフラストラクチャーを仮想化します。
* VMware vSphere は、物理コンピュート・リソースを仮想化します。
* VMware NSX は、論理ネットワーキング・コンポーネントと仮想ネットワークを提供するネットワーク仮想化プラットフォームです。
* {{site.data.keyword.cloud_notm}} 上の NetApp ONTAP Select は、4 つのホスト用の 4 つの VM からなる ONTAP Select クラスターをデプロイします。

以下の図は、NetApp ONTAP Select デプロイメントのコンポーネントを示しています。

![NetApp ONTAP Select コンポーネント](../images/np_netappcomponents.svg "NetApp ONTAP Select のコンポーネント")

### 仮想化管理
{: #np_netappoverview-virtualization-mgmt}

仮想化管理レイヤーは、以下のコンポーネントで構成されています。

* 組み込みプラットフォーム・サービス・コントローラー (PSC) を備えた vCenter Server Appliance (vCSA)
* NSX Manager
* 2 つの NSX Edge Services Gateway (ESG)
* 3 つの NSX Controller
* IBM CloudDriver 仮想サーバー・インスタンス (VSI)

NetApp ONTAP Select は、VMware クラスター内で実行され、ホスト上のローカル・ストレージを仮想化します。 NetApp ONTAP Select は専用モデルでデプロイされます。つまり、他のワークロードとクラスターを共有するという想定にはなっていません。 そのため、{{site.data.keyword.cloud_notm}} オファリング上の NetApp ONTAP Select のハードウェア構成のサイズは、NetApp ONTAP Select の要件のみに基づいて決まります。

## NetApp ONTAP Select インスタンスの技術仕様
{: #np_netappoverview-specs}

NetApp ONTAP Select インスタンスには以下のコンポーネントが含まれます。

標準化された構成の選択肢と料金は、デプロイメントの対象として選択された {{site.data.keyword.CloudDataCent_notm}}に基づいて異なる場合があります。
{:note}

### ストレージ
{: #np_netappoverview-storage}

* **ハイパフォーマンス (ミディアム)**、**ハイパフォーマンス (ラージ)**、**大容量**のいずれかを選択します。
* RAID 5 とホット・スペア
* 2 台の 1 TB SATA ドライブ ESXi OS – RAID 1
* 管理データ・ストア – 管理 VM 用に 500 GB

### 事前設定構成
{: #np_netappoverview-preset-config}

以下の構成オプションがある 4 つの {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}が提供されています。
* **ハイパフォーマンス (ミディアム)** – プレミアム・ライセンス / Dual Intel Xeon E5-2650 v4 (合計 24 コア、2.2 GHz) / 128 GB RAM / ノードあたり 22 個の 1.9 TB SSD ドライブ容量 / 4 ノード・クラスターの実効容量 – 59 TB
* **ハイパフォーマンス (ラージ)** – プレミアム・ライセンス / Dual Intel Xeon E5-2650 v4 (合計 24 コア、2.2 GHz) / 128 GB RAM / ノードあたり 22 個の 3.8 TB SSD ドライブ容量 / 4 ノード・クラスターの実効容量 – 118 TB
* **大容量** – 標準ライセンス / Dual Intel Xeon E5-2650 v4 (合計 24 コア、2.2 GHz) / 64 GB RAM / ノード当たり 34 個の 4 TB SATA ドライブ容量 / 4 ノード・クラスターの有効容量 – 190 TB

3.8 TB SSD (ソリッド・ステート・ディスク) ドライブは、データ・センターで一般提供が開始されたらサポートされます。
{:note}

### ハードウェア
{: #np_netappoverview-hardware}

* 3 つの RAM とディスクのオプション: **ハイパフォーマンス (ミディアム)**、**ハイパフォーマンス (ラージ)**、**大容量**
* 2 台の 1 TB SATA ドライブ ESXi OS
* RAID ディスク・コントローラー 1 つ
* VMware Server Virtualization 6.5

### ネットワーキング
{: #np_netappoverview-network}

* 10 Gbps デュアル・ネットワーク・アップリンク (パブリックとプライベート)
* VLAN (仮想 LAN) 3 つ: パブリック VLAN 1 つとプライベート VLAN 2 つ
* セキュア VMware NSX Edge Services Gateway 1 つ

### 仮想サーバー・インスタンス
{: #np_netappoverview-vsi}

2 つの VSI (仮想サーバー・インスタンス):
* Microsoft Active Directory (AD) とドメイン・ネーム・システム (DNS) サービス用に 1 つの VSI。
* IBM CloudBuilder の VSI。これは、インスタンスのデプロイメントが完了した後にシャットダウンされます。

### ライセンスと料金
{: #np_netappoverview-license-and-fee}

*  NetApp ONTAP Select の 4 つの Premium または Standard エディションのライセンス (ユーザー提供)
*  VMware vSphere 6.5 Enterprise Plus エディション
*  VMware vCenter Server 6.5
*  VMware NSX Service Providers Edition (Base、Advanced、または Enterprise) 6.4
*  サポートとサービスの料金 (ノード当たり 1 つのライセンス)

{{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。 {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されません。
{:important}

**注意:** インスタンスを注文したときに {{site.data.keyword.cloud_notm}} アカウントにインストールされた {{site.data.keyword.vmwaresolutions_short}} コンポーネントを、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で管理すると、環境が不安定になる可能性があります。 これには以下の管理アクティビティーが該当します。
*  コンポーネントの追加、変更、返却、削除、電源オフ
*  ESXi サーバーの追加または削除によるインスタンス容量の拡張または縮小
*  サービスの再始動

   {{site.data.keyword.slportal}}での共有ストレージのファイル共有の管理は、上記アクティビティーに該当しません。 これには、共有ストレージのファイル共有の注文、削除 (マウントされている場合はデータ・ストアに影響する可能性があります)、承認、マウントなどのアクティビティーが含まれます。

## ファイアウォールに関する考慮事項
{: #np_netappoverview-firewall-considerations}

ファイアウォールを使用している場合は、{{site.data.keyword.IBM}} CloudDriver 仮想サーバー・インスタンス (VSI) と SDDC Manager 仮想マシン (VM) からのすべての通信に関してルールを構成する必要があります。 これらのルールでは、すべてのプロトコルが IP アドレス `10.0.0.0/8` と `161.26.0.0/16` 上で通信できるよう許可する必要があります。 このようなファイアウォールの例としては、NSX Distributed Firewalls (DFW)、Vyatta ファイアウォールなどがあります。

## 関連リンク
{: #np_netappoverview-related}

* [NetApp ONTAP Select インスタンスの計画](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning#requirements-and-planning-for-netapp-ontap-select-instances)
* [NetApp ONTAP Select インスタンスの注文](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)
* [vCenter Server の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [NetApp ONTAP ドキュメント・センター](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html){: external}
