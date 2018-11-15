---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 接続ストレージのインフラストラクチャー設計

{{site.data.keyword.vmwaresolutions_full}} は、世界中の {{site.data.keyword.CloudDataCents_notm}}に自動的に展開される VMware テクノロジーを提供します。 {{site.data.keyword.cloud_notm}} ソリューション・ポートフォリオの基本の VMware vCenter Server on {{site.data.keyword.cloud_notm}} オファリングは、最大 10 個のクラスター (それぞれ vSphere ホスト最大 59 台を収容)、1 つの Platform Services Controller (PSC)、1 つの vCenter Server Appliance (最大 400 台のホストと 4,000 台の仮想マシンを管理可能) で構成されます。

ここに示すアーキテクチャーでは、環境に共有ストレージ・デバイスとして接続ストレージを追加することで、vCenter Server ソリューションが補完されます。 接続ストレージ・デバイスは、vCenter Server デプロイメントと同じ {{site.data.keyword.CloudDataCent_notm}}に置かれ、単一のネットワーク・ファイル・システム (NFS) 共有または {{site.data.keyword.cloud_notm}} の複数の NFS エクスポートで構成されます。

以下の図は、vCenter Server デプロイメントにおける接続ストレージのアーキテクチャー全体を示しています。

図 1. {{site.data.keyword.cloud_notm}} 上の接続ストレージのアーキテクチャーの全体像

![接続ストレージのアーキテクチャー](../solution/physical_nfs.svg "IBM Cloud 上の接続ストレージのアーキテクチャーの全体像")

## 物理インフラストラクチャー設計

物理インフラストラクチャーは、物理コンピュート、物理ストレージ、物理ネットワークの 3 つの主要コンポーネントで構成されます。 これには 、インフラストラクチャーで使用される {{site.data.keyword.cloud_notm}} サービス・ネットワークと物理ストレージが含まれます。

## 物理ネットワーク設計

物理ネットワークは {{site.data.keyword.cloud_notm}} によって処理されます。 このセクションでは、接続ストレージに関連する {{site.data.keyword.cloud_notm}} によって提供される物理ネットワークについて説明します。

### IBM Cloud ネットワークの概要

{{site.data.keyword.cloud_notm}} の物理ネットワークは、パブリック・ネットワーク、プライベート・ネットワーク、管理ネットワークという 3 つの異なるネットワークに分類されます。 パブリック・ネットワーク、プライベート・ネットワーク、管理ネットワークについて詳しくは、[ソリューションの概要](../solution/solution_overview.html)を参照してください。

{{site.data.keyword.cloud_notm}} ネットワークについて詳しくは、『[{{site.data.keyword.cloud_notm}} ネットワーク](https://www.ibm.com/cloud-computing/bluemix/our-network){:new_window}』を参照してください。

プライベート・ネットワークの一部であるサービス・ネットワークの説明については、次の情報を参照してください。

### プライベート・サービス・ネットワーク

{{site.data.keyword.cloud_notm}} には、ブロック・ストレージ、ファイル・ストレージ、オブジェクト・ストレージ、DNS リゾルバー、NTP サーバーなどの共通サービスを提供するプライベート・サービス・ネットワークが含まれています。 このプライベート・ネットワークはお客様のプライベート・ネットワークとは別であり、{{site.data.keyword.cloud_notm}} に配置された各種サービスにシームレスに接続するための環境を実現します。 このプライベート・ネットワークは多層化されており、その中でサーバーと他のインフラストラクチャーは集約されたバックエンド・カスタマー・スイッチ (BCS) に接続されます。 これらの集約スイッチは L3 ネットワーキング用の別々のバックエンド・カスタマー・ルーター (BCR) のペアに接続されます。 プライベート・ネットワークは、物理ホスト接続にジャンボ・フレーム、MTU 9000 を使用する機能もサポートします。

### VLAN

VLAN について詳しくは、[物理インフラストラクチャー設計](../solution/design_physicalinfrastructure.html)の『_物理ネットワーク設計_』セクションを参照してください。

## 物理ストレージ設計

このセクションでは、{{site.data.keyword.cloud_notm}} にある接続ストレージ・デバイスの構成について説明します。 接続ストレージ・デバイスは既存の vCenter Server ソリューションを補完するものです。 つまり、物理ホストに内在するローカル接続されたディスクについては説明しません。

## 接続ストレージのパフォーマンス

パフォーマンス・ストレージおよびエンデュランス・ストレージは、予測可能なパフォーマンス・レベルを必要とする高 I/O アプリケーションをサポートするように設計された、{{site.data.keyword.cloud_notm}} ストレージ・ソリューションです。 この予測可能なパフォーマンスは、個々のボリュームへのプロトコル・レベルの IOPS (input/output operations per second) の割り振りによって実現されます。

100 から 48,000 までの範囲の IOPS を、20 GB から 12 TB までの範囲のストレージ・サイズでプロビジョンできます。 パフォーマンス・ストレージおよびエンデュランス・ストレージのボリュームは、ブロック・ストレージとファイル・ストレージの両方に使用可能です。

この設計では、接続ストレージとしてエンデュランス・ストレージを vCenter Server ソリューションで利用できます。 そのため、20 GB から最大 12 TB までのサイズのエンデュランス NFS エクスポートを選択し、(自動化を介して) 接続できます。 {{site.data.keyword.cloud_notm}} では、単一のエンデュランス NFS エクスポートに最大 64 台の vSphere ESXi ホストを接続できます。

エンデュランスには、3 つの IOPS パフォーマンス・ティアが用意されているので、さまざまなアプリケーションのニーズに対応できます。

NFS 共有がプロビジョンされた後で、IOPS を増減するためにサイズを変更したり再構成したりすることができます。
{:note}

IOPS オプションについて詳しくは、[vCenter Server インスタンスの注文](../../vcenter/vc_orderinginstance.html)の_ストレージ設定_のセクションを参照してください。

ストレージ・ティアのほかにも、{{site.data.keyword.cloud_notm}} エンデュランス・ストレージは、スナップショットやレプリケーション、{{site.data.keyword.CloudDataCent_notm}}のロケーションの保存データの暗号化など、幅広いアプリケーション・ニーズをサポートしています。

### 関連リンク

* [ソリューションの概要](../solution/solution_overview.html)
