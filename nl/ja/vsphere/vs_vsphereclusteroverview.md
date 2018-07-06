---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# VMware vSphere on IBM Cloud の概要

VMware vSphere on {{site.data.keyword.cloud}} は、合理化、最適化された VMware の注文プラットフォームです。このプラットフォームでは、選択した VMware コンポーネントに基づいて VMware 互換ハードウェアをカスタマイズして注文することで、IBM によってホストされるお客様独自の VMware 環境を構築できます。

{{site.data.keyword.vmwaresolutions_short}} コンソールでは、お客様が選択した VMware コンポーネントに基づいて、ハードウェアが自動的にフィルタリングされます。 例えば、オール・フラッシュの VMware vSAN クラスターを新規作成する場合は、[VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php) に照らして確認されたハードウェアのみが示され、最低限 4 つの ESXi サーバーが必要になります。

VMware vSphere on {{site.data.keyword.cloud_notm}} は、オプションの VMware コンポーネントのインストール、構成、起動を自動実行しませんが、ホストされる VMware 環境を、VMware 互換ハードウェアを組み込みながら設計して構築できるように柔軟性が最大化されています。

このオファリングを使用して、{{site.data.keyword.CloudDataCent_notm}}内に ESXi サーバーの新規クラスターを作成したり、ESXi サーバーの既存クラスターを拡張したりできます。 選択した VMware コンポーネントによっては、ESXi サーバー 1 つだけで始めて、後で必要に応じてクラスターを拡張することができます。

## VMware vSphere on IBM Cloud のコンポーネント

ここには、VMware vSphere on {{site.data.keyword.cloud_notm}} のコンポーネントを記載します。

**注**: 標準化されたハードウェア構成の使用可否と価格は、デプロイメントに選択した {{site.data.keyword.CloudDataCent_notm}}によって異なる場合があります。

### VMware のコンポーネント

以下の VMware コンポーネントのライセンス (IBM 提供ライセンスまたは BYOL ライセンス):
* VMware vSphere Enterprise Plus 6.0u2 または 6.5u1
* オプションの VMware コンポーネント:
   * VMware vCenter Server Standard
   * VMware NSX (Base、Advanced、または Enterprise)
   * VMware vSAN (Advanced または Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### ベア・メタル・サーバー

選択した CPU モデルと RAM サイズの 1 つ以上の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}:
* 2-CPU Intel Broadwell 世代 (Intel Xeon E5-2600 v4 シリーズ)
* 2-CPU Intel Skylake 世代 (Intel Xeon 4100/5100/6100 シリーズ)

使用可能なオプションは、VMware vSAN コンポーネントを選択したかどうかによります。

さらに、以下のディスク仕様とネットワーキング仕様:
* 10 Gbps デュアル・ネットワーク・アップリンク (パブリックとプライベート)
* RAID ディスク・コントローラー 1 つ

### ネットワーキング

* VLAN (仮想 LAN) 3 つ: パブリック VLAN 1 つとプライベート VLAN 2 つ
* (オプション) FortiGate Security Appliance デバイスの HA ペア

### ストレージ

VMware vSAN コンポーネントを選択した場合は、vSAN 構成用のユーザー・カスタマイズ型のストレージ
* ストレージ・ディスク・オプション: 960 GB SSD SED、1.9 TB SSD SED、または 3.8 TB SSD SED
* ディスク数量オプション: 2、4、6、または 8

**注:** 3.8 TB SSD (ソリッド・ステート・ディスク) ドライブは、データ・センターで一般提供が開始されたらサポートされる予定です。

## vSphere クラスター拡張ノードのコンポーネント

各 vSphere クラスター拡張ノードは、{{site.data.keyword.slportal}}のアカウントに以下のコンポーネントをデプロイするので、料金が発生します。

### 拡張ノード用のハードウェア

[VMware vSphere on IBM Cloud のコンポーネント](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)で示されているハードウェア構成の IBM Cloud ベア・メタル・サーバー 1 つ。

### 拡張ノード用ネットワーキング

[VMware vSphere on IBM Cloud のコンポーネント](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)で示されているネットワーキング構成の IBM Cloud ベア・メタル・サーバー 1 つ。

### 拡張ノード用 VMware コンポーネント

* VMware vSphere Enterprise Plus 6.0u2 または 6.5u1 が適用された IBM Cloud ベア・メタル・サーバー 1 つ。  
* [VMware vSphere on IBM Cloud のコンポーネント](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud)で示されているオプションの VMware コンポーネント。

**重要**: 注文して {{site.data.keyword.cloud_notm}} アカウントに提供された ESXi サーバー、オプションの VMware コンポーネント、追加のハードウェアの管理は、必ず {{site.data.keyword.slportal}}のみから行う必要があります。 {{site.data.keyword.vmwaresolutions_short}} コンソールで新規クラスターを作成した後、コンソールに戻り、保存されている構成を使用して、その新規クラスターを拡張できます。 詳しくは、[既存の vSphere クラスターの拡張](vs_scalingexistingclusters.html)を参照してください。

## 関連リンク

* [VMware vSphere ソフトウェアの部品構成表](vs_bom.html)
* [vSphere クラスターの計画](vs_planning.html)
* [vSphere クラスターの注文](vs_orderinginstances.html)
* [既存の vSphere クラスターの拡張](vs_scalingexistingclusters.html)
