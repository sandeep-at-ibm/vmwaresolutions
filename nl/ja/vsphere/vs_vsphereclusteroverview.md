---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware vSphere on IBM Cloud の概要

VMware vSphere on {{site.data.keyword.cloud}} は、合理化、最適化された VMware の注文プラットフォームです。 このプラットフォームでは、選択した VMware コンポーネントに基づいて VMware 互換ハードウェアをカスタマイズして注文することで、IBM によってホストされるお客様独自の VMware 環境を構築できます。

{{site.data.keyword.vmwaresolutions_short}} コンソールでは、お客様が選択した VMware コンポーネントに基づいて、ハードウェアが自動的にフィルタリングされます。 例えば、オール・フラッシュの VMware vSAN クラスターを新規作成する場合は、[VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php) に照らして確認されたハードウェアのみが示されます。 また、最小 4 台の ESXi サーバーが必要です。

VMware vSphere on {{site.data.keyword.cloud_notm}} では、オプションの VMware コンポーネントのインストールや構成や起動が自動化されません。 このプラットフォームでは、ホスト対象の VMware 環境を、VMware 互換ハードウェアを組み込みながら設計して構築するための柔軟性が最大化されています。

このオファリングを使用して、{{site.data.keyword.CloudDataCent_notm}}内に ESXi サーバーの新規クラスターを作成したり、ESXi サーバーの既存クラスターを拡張したりできます。 選択した VMware コンポーネントによっては、ESXi サーバー 1 つだけで始めて、後で必要に応じてクラスターを拡張することができます。

## VMware vSphere on IBM Cloud クラスターの技術仕様

ここには、VMware vSphere on {{site.data.keyword.cloud_notm}} のコンポーネントを記載します。

標準化されたハードウェア構成の使用可否と価格は、デプロイメントに選択した {{site.data.keyword.CloudDataCent_notm}}によって異なる場合があります。
{:note}

### VMware のコンポーネント

以下の VMware コンポーネントのライセンス (IBM 提供または BYOL) を選択します。
* VMware vSphere Enterprise Plus 6.0u2、6.5u1、または 6.5u2
* 以下の VMware コンポーネントはオプションです。
   * VMware vCenter Server Standard
   * VMware NSX (Base、Advanced、または Enterprise)
   * VMware vSAN (Advanced または Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### ベア・メタル・サーバー

選択した CPU モデルと RAM サイズの 1 つ以上の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} を選択します。
* 2-CPU Intel Skylake 世代 (Intel Xeon 4100/5100/6100 シリーズ)
* SAP 認定 (Intel Xeon 6140/E5-2690/E7-8890 シリーズ)
* 2-CPU Intel Broadwell 世代 (Intel Xeon E5-2600/E7-4800 シリーズ)

使用可能なオプションは、VMware vSAN コンポーネントを選択したかどうかによります。

さらに、以下のディスク仕様とネットワーキング仕様を選択します。
* 10 Gbps デュアル・ネットワーク・アップリンク (パブリックとプライベート)
* RAID ディスク・コントローラー 1 つ

### ネットワーキング

* 1 つの VLAN (仮想 LAN) パブリック VLAN と 2 つのプライベート VLAN
* (オプション) FortiGate Security Appliance デバイスの HA ペア

### ストレージ

VMware vSAN コンポーネントを選択した場合は、vSAN 構成用のユーザー・カスタマイズ型のストレージ
* 960 GB SSD SED、1.9 TB SSD SED、または 3.8 TB SSD SED のストレージ・ディスク・オプション
* 2、4、6、または 8 のディスク数量オプション

  さらに、ホストごとに 960 GB のキャッシュ・ディスクが 2 つ注文されます。

  3.8 TB SSD (ソリッド・ステート・ディスク) ドライブは、データ・センターで一般提供が開始されたらサポートされます。
  {:note}
* High-Performance Intel Optane オプション。合計 10 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されます。 このオプションは CPU モデルに応じて異なります。

## vSphere クラスター拡張ノードの技術仕様

vSphere クラスター拡張ノードごとに、{{site.data.keyword.slportal}} アカウントに以下のコンポーネントがデプロイされ、料金が発生します。

### 拡張ノード用のハードウェア

[VMware vSphere on {{site.data.keyword.cloud_notm}} クラスターの技術仕様](/docs/services/vmwaresolutions/vsphere/vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters)で示されているハードウェア構成の {{site.data.keyword.cloud_notm}} ベア・メタル・サーバー 1 つ。

### 拡張ノード用ネットワーキング

[VMware vSphere on {{site.data.keyword.cloud_notm}} クラスターの技術仕様](/docs/services/vmwaresolutions/vsphere/vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters)で示されているネットワーキング構成の {{site.data.keyword.cloud_notm}} ベア・メタル・サーバー 1 つ。

### 拡張ノード用 VMware コンポーネント

* VMware vSphere Enterprise Plus 6.0u2 または 6.5u1 が適用された {{site.data.keyword.cloud_notm}} ベア・メタル・サーバー 1 つ。  
* [VMware vSphere on {{site.data.keyword.cloud_notm}} クラスターの技術仕様](/docs/services/vmwaresolutions/vsphere/vs_vsphereclusteroverview.html#technical-specifications-for-vmware-vsphere-on-ibm-cloud-clusters)で示されているオプションの VMware コンポーネント。

注文して {{site.data.keyword.cloud_notm}} アカウントに提供された ESXi サーバー、オプションの VMware コンポーネント、追加のハードウェアの管理は、必ず {{site.data.keyword.slportal}}のみから行う必要があります。 {{site.data.keyword.vmwaresolutions_short}} コンソールで新規クラスターを作成した後、コンソールに戻り、保存されている情報を使用して、その新規クラスターを拡張できます。 詳しくは、[既存の vSphere クラスターの拡張](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html)を参照してください。
{:important}

### 関連リンク

* [VMware vSphere ソフトウェアの部品構成表](/docs/services/vmwaresolutions/vsphere/vs_bom.html)
* [vSphere クラスターの計画](/docs/services/vmwaresolutions/vsphere/vs_planning.html)
* [vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)
* [既存の vSphere クラスターの拡張](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html)
