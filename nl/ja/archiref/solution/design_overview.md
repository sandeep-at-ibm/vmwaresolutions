---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-10"

---
# 設計の概要

{{site.data.keyword.vmwaresolutions_full}} は、世界中の {{site.data.keyword.CloudDataCents_notm}}に VMware テクノロジー・コンポーネントをデプロイするための自動化機能を提供します。

## ソリューション・オファリング

ソリューション・オファリングでは、自動的にデプロイされて構成されるクラスター内に以下の VMware vSphere 製品が組み込まれます。
* VMware Cloud Foundation: vSphere ESXi、Platform Services Controller (PSC)、VMware vCenter Server Appliance、SDDC Manager、VMware NSX、VMware vSAN。
* VMware vCenter Server: vSphere ESXi、Platform Services Controller (PSC)、vCenter Server Appliance、NSX、vSAN (オプション)。

この設計では、初回注文時に単一ポッドの {{site.data.keyword.CloudDataCent_notm}}にインスタンスがデプロイされます。初期デプロイメント後、同じデータ・センター内の他のポッド、または他のデータ・センターに仮想環境を拡張できます。

またこの設計では、Cloud Foundation または vCenter Server インスタンス内の仮想キャパシティーの自動拡張と自動縮小も可能です。

## VMware on IBM Cloud のコンポーネント

図 1. VMware on {{site.data.keyword.cloud_notm}} のコンポーネント
![VMware on {{site.data.keyword.cloud_notm}} のコンポーネント](design_overview.svg "ソリューションは、物理インフラストラクチャー、仮想インフラストラクチャー、インフラストラクチャー管理、共通サービスで構成されています。")

### 関連リンク

* [物理インフラストラクチャー設計](design_physicalinfrastructure.html)
* [仮想インフラストラクチャー設計](design_virtualinfrastructure.html)
* [共通サービス設計](design_commonservice.html)
* [インフラストラクチャー管理設計](design_infrastructuremgmt.html)
