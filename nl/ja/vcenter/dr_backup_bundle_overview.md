---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

keywords: single-node trial, data protection DR, tech specs data protection DR

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial for Data Protection and Disaster Recovery の概要
{: #dr_backup_bundle_overview}

Single-node Trial for Data Protection and Disaster Recovery では、VMware ワークロードをマイグレーションしてから
{{site.data.keyword.cloud_notm}} にリカバリーする、という {{site.data.keyword.cloud}} のテスト・ドライブを行うことができます。また、Single-node Trial for Data Protection and Disaster Recovery には、Veeam on {{site.data.keyword.cloud_notm}}、VMware HCX on {{site.data.keyword.cloud_notm}}、および Zerto on {{site.data.keyword.cloud_notm}} のサービスが含まれます。

Single-node Trial は、オンプレミス環境と同じツールで管理できる単一テナントの VMware プラットフォームを提供する VMware vCenter Server on {{site.data.keyword.cloud_notm}} のトライアル・バージョンです。制御性および可視性はオンプレミスと同じレベルに保ったまま、クラウドの速度およびスケールというメリットを享受できます。

このトライアルの目的は、vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle を使用して開発用またはテスト用の単純なワークロードを最大 20 個移行することです。 数時間のうちに、自動化機能によって VMware HCX が {{site.data.keyword.cloud_notm}} にインストールされて構成され、オンプレミス HCX アクティベーション・キーが提供され、Veeam on {{site.data.keyword.cloud_notm}} および Zerto on {{site.data.keyword.cloud_notm}} がインストールされます。Veeam on {{site.data.keyword.cloud_notm}} および Zerto on {{site.data.keyword.cloud_notm}} を使用して、20 の仮想マシン (VM) をバックアップおよび複製できます。

Single-node Trial for Data Protection and Disaster Recovery は PoC (概念検証) のみを目的としています。この環境では実動ワークロードを実行しないでください。 ホストやクラスターの追加と削除、追加アドオン・サービスの注文、更新の適用などの管理機能はサポートされていません。
{:important}

Single-node Trial インスタンスのデプロイ後、[IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:new_window} の [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:new_window} を使用して、インスタンスの操作に関する支援を受けることができます。さらに、[{{site.data.keyword.cloud_notm}}Garage Services](https://www.ibm.com/cloud/garage/){:new_window} を使用すれば、クラウド・ネイティブの最新の手法でアプリケーションのモダナイゼーションを加速化できます。

このトライアル版は最大 90 日間使用できます。 月額料金は、インスタンスの注文時期ではなく、請求スケジュールに基づいて請求されます。請求サイクルの最終日以前にインスタンスをキャンセルしない場合、その次の月の分の料金が発生することになります。90 日間のトライアルでは、4 カ月分の料金が発生してしまうことがよくあります。しかし、4 カ月目が始まる前にキャンセルを完了すれば、そうはなりません。
{:note}

トライアル期間が終了したら、この環境を削除し、キャパシティーのニーズを満たす新しい環境をプロビジョンできます。

## Single-node Trial for Data Protection and Disaster Recovery インスタンスの技術仕様
{: #dr_backup_bundle_overview-tech-specs}

Single-node Trial for Data Protection and Disaster Recovery インスタンスには以下のコンポーネントが含まれています。

標準化されたハードウェア構成の使用可否と価格は、デプロイメントに選択した {{site.data.keyword.CloudDataCent_notm}}によって異なる場合があります。
{:note}

### ベア・メタル・サーバー
{: #dr_backup_bundle_overview-bare-metal}

Skylake Dual Intel Xeon Gold 5120 プロセッサー / 合計 28 コア、2.2 GHz、384 GB RAM (VM 最大約 20 台分)

#### CPU オーバーコミット
{: #dr_backup_bundle_overview-cpu}

vCenter Server 管理、HCX、およびカスタマー・ワークロード VM 20 台用に 16:1 CPU オーバーコミット

#### RAM オーバーコミット
{: #dr_backup_bundle_overview-ram}

* ワークロード VM 20 台 (8 GB/VM) のカスタマー・デプロイメントの場合は 1.22:1 RAM オーバーコミット
* ワークロード VM 9 台 (8 GB/VM) のカスタマー・デプロイメントの場合は 1:1 (オーバーコミットなし)

### NFS ストレージ
{: #dr_backup_bundle_overview-nfs-storage}

* 管理用に 2 TB
* カスタマー・ワークロード用に 1 TB (カスタマー VM 20 台の場合)

### Single-node Trial for Data Protection and Disaster Recovery インスタンスのネットワーキング仕様
{: #dr_backup_bundle_overview-networking-specs}

以下のネットワーキング・コンポーネントが注文されます。
*  10 Gbps デュアル・ネットワーク・アップリンク (パブリックとプライベート)
*  VLAN (仮想 LAN) 3 つ: パブリック VLAN 1 つとプライベート VLAN 2 つ
*  レイヤー 2 (L2) ネットワークに接続されたローカル・ワークロード間で実行される可能性のある東西通信用の DLR (分散論理ルーター) を備えた VXLAN (仮想拡張可能 LAN) 1 つ。 この VXLAN は、サンプルのルーティング・トポロジーとしてデプロイされるので、変更したり、作成の基礎として使用したり、削除したりできます。 また、DLR の新しい論理インターフェースにさらに VXLAN を接続してセキュリティー・ゾーンを追加することもできます。
*  以下の 2 つの VMware NSX Edge Services Gateway
  * アウトバウンド HTTPS 管理トラフィック用のセキュアな管理サービス VMware NSX Edge Services Gateway (ESG)。これは、管理ネットワーキング・トポロジーの一部として IBM がデプロイします。 この ESG は、IBM 管理 VM が、自動化に関連する特定の外部 IBM 管理コンポーネントと通信するために使用します。

    ユーザーは、この ESG にアクセスすることはできず、使用できません。 これを変更すると、{{site.data.keyword.vmwaresolutions_short}} コンソールから Single-node Trial for Data Protection and Disaster Recovery インスタンスを管理できなくなる可能性があります。また、ファイアウォールを使用したり、外部 IBM 管理コンポーネントへの ESG 通信を無効にしたりすると、{{site.data.keyword.vmwaresolutions_short}} が使用不可になります。
    {:important}
  * アウトバウンドとインバウンドの HTTPS ワークロード・トラフィック用のユーザー管理のセキュアな VMware NSX Edge Services Gateway。これは、VPN アクセスまたはパブリック・アクセスを提供するためにユーザーが変更可能なテンプレートとして IBM がデプロイします。

### 仮想サーバー・インスタンス
{: #dr_backup_bundle_overview-vsi}

以下の仮想サーバー・インスタンス (VSI) が注文されます。

* IBM CloudBuilder の VSI。これは、インスタンスのデプロイメントが完了した後にキャンセルされます。
* Microsoft Active Directory (AD) 用の Microsoft Windows Server VSI がデプロイされて参照可能になります。 この VSI がインスタンスの DNS として機能し、ここにホストと VM が登録されます。
* Zerto on {{site.data.keyword.cloud_notm}} 用 VSI - Zerto Virtual Manager。
* Veeam Backup and Replication 9.5 OS Add-on および Veeam Availability Suite 9.5. のある VSI。

### IBM 提供のライセンスおよび料金
{: #dr_backup_bundle_overview-license-and-fee}

Single-node Trial for Data Protection and Disaster Recovery インスタンスの注文には、以下のライセンスが含まれます。

* vCenter Server with Hybridity Bundle ライセンス:
  * VMware vSphere Enterprise Plus 6.7u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

Single-node Trial for Data Protection and Disaster Recovery インスタンスはライセンス持ち込み (BYOL) をサポートしていません。
{:note}

## VMware HCX on IBM Cloud の技術仕様
{: #dr_backup_bundle_overview-hcx-tech-specs}

Single-node Trial for Data Protection and Disaster Recovery には HCX on {{site.data.keyword.cloud_notm}} が含まれています。以下のコンポーネントが注文されて HCX on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

オンプレミスの HCX インスタンスには、ライセンス交付とアクティベーションのみが含まれます。
{:note}

### HCX 管理用の VMware NSX Edge Services Gateways のアクティブ/パッシブ・ペア
{: #dr_backup_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* ディスク: 3 GB VMDK

### HCX 管理アプライアンス - 仮想マシン
{: #dr_backup_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* ディスク: 60 GB VMDK

構成時には必要に応じて、L2 接続、WAN 最適化、およびゲートウェイ接続のために追加の HCX アプライアンスがデプロイされます。

### HCX on IBM Cloud のネットワーキング仕様
{: #dr_backup_bundle_overview-hcx-networking-specs}

* 16 個の IP アドレスを持つ 1 つのパブリック・ポータブル・サブネット
* 64 個の IP アドレスを持つ 2 つのプライベート・ポータブル・サブネット
* プライベート・ポータブル vMotion サブネットからの 8 個の IP アドレス

## Veeam on {{site.data.keyword.cloud_notm}} の技術仕様
{: #dr_backup_bundle_overview-veeam-tech-specs}

Single-node Trial for Data Protection and  Disaster Recovery には Veeam on {{site.data.keyword.cloud_notm}} が含まれています。以下のコンポーネントが注文されて Veeam on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

* Veeam Availability Suite の 25 Pack License
* 4000 GB ストレージ
* 0.25 IOPS/GB ストレージ・パフォーマンス
* Windows Server 2016 Standard Edition (64 ビット)
* 4 x 2.0 GHz コア
* 8 GB RAM
* 1 Gbps のプライベート・ネットワーク・アップリンク
* 100 GB ディスク (SAN)

## Zerto on {{site.data.keyword.cloud_notm}} の技術仕様
{: #dr_backup_bundle_overview-zerto-tech-specs}

Single-node Trial for Data Protection and Disaster Recovery には Zerto on {{site.data.keyword.cloud_notm}} が含まれています。以下のコンポーネントが注文されて Zerto on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

* Zerto Virtual Replication V6.5u3 ライセンス
* 1 つの仮想サービス・インスタンス (VSI) - Zerto Virtual Manager
* 2 x 2.0 GHz コア
* 4 GB RAM
* Windows Server 2016 Standard Edition (64 ビット)
* 100 GB (SAN) ディスク

## IBM Cloud Automation Manager の技術仕様
{: #dr_backup_bundle_overview-cam-tech-specs}

すべての Single-node Trial for Data Protection and Disaster Recovery インスタンスに、{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 が、開発/テスト用のトポロジーを使用してインストールされます。{{site.data.keyword.cloud_notm}} Automation Manager について詳しくは、[{{site.data.keyword.cloud_notm}} Automation Manager の資料](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: new_window}を参照してください。

## 関連リンク
{: #dr_backup_bundle_overview-related}

* [VMware HCX リソース](https://hcx.vmware.com/#/docs){:new_window}
* [VMware HCX ユーザー・ガイド](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:new_window}
* [Veeam on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam)
* [Zerto on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr)
