---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# V2.7 のリリース・ノート

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## SAP 認定 6140 サーバーのサポート

V2.7 リリース以降、VMware vCenter Server on {{site.data.keyword.cloud_notm}} と VMware vSphere on {{site.data.keyword.cloud_notm}} のインスタンスとクラスターのデプロイメントで、以下の新しい {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU モデルを使用できるようになりました。
* Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 192 GB RAM
* Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.2 GHz / 384 GB RAM
* Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 768 GB RAM

詳しくは、以下の資料にある『*{{site.data.keyword.baremetal_short_sing}}の設定*』セクションを参照してください。
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [新規 vSphere クラスターの注文](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## アドオン・サービスの更新

### IBM Cloud Private Hosted

{{site.data.keyword.cloud_notm}} Private Hosted サービスが、V2.5 以降のリリースにデプロイ (またはアップグレード) された VMware vCenter Server インスタンスに加えて、VMware vCenter Server with Hybridity Bundle インスタンスでも使用できるようになりました。vCenter Server インスタンスや vCenter Server with Hybridity Bundle インスタンスにこのサービスを組み込んで注文したり、初期デプロイメント後の既存の vCenter Server インスタンスや vCenter Server with Hybridity Bundle インスタンスにこのサービスを追加したりすることができるようになりました。

詳しくは、以下を参照してください。
* [{{site.data.keyword.cloud_notm}} Private Hosted の概要](../services/icp_overview.html)
* [{{site.data.keyword.cloud_notm}} Private Hosted の注文](../services/icp_ordering.html)

### Mission Critical VMware on IBM Cloud

Mission Critical VMware on {{site.data.keyword.cloud_notm}} サービスが、V2.7 以降のリリースにデプロイされたインスタンス、または V2.7 以降のリリースにアップグレードされたインスタンスで使用できるようになりました。

Mission Critical VMware on {{site.data.keyword.cloud_notm}} では、企業がクラウド・アプリケーションのダウン時間をなくし、クラウド領域内でのフェイルオーバーを自動化できるようにするための、マルチゾーン・クラウド・アーキテクチャーを提供しています。ほとんどの場合、このクラウド・アーキテクチャーを使用すると、オンプレミス環境または競合他社のクラウド・プラットフォームで VMware ユーザーが作業する場合より、高い可用性とフェイルオーバー成功率を実現できます。

詳しくは、[Mission Critical VMware on {{site.data.keyword.cloud_notm}} の概要](../services/mcv_overview.html)を参照してください。

### F5 on IBM Cloud

F5 on {{site.data.keyword.cloud_notm}} サービスを注文するときに、F5 のライセンス適用をパブリック・ネットワークを介して行うか、それともプロキシー・サーバーを使用するプライベート・ネットワークを介して行うかを選択できるようになりました。詳しくは、[F5 on {{site.data.keyword.cloud_notm}} の注文](../services/f5_ordering.html)を参照してください。

### FortiGate Virtual Appliance on IBM Cloud

2018 年第 3 四半期に、Fortinet のサブスクリプション・バンドルが変更されました。詳しくは、[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の注文](../services/fortinetvm_ordering.html)を参照してください。

V2.7 以降の Cloud Foundation インスタンスと vCenter Server インスタンスにデプロイされた FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスでは、FortiOS 6.0.3 がプロビジョンされます。

さらに、FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスを注文するときに、FortiGuard のライセンス適用とセキュリティー更新をパブリック・ネットワークを介して行うか、それともプロキシー・サーバーを使用するプライベート・ネットワークを介して行うかを選択できます。詳しくは、[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の注文](../services/fortinetvm_ordering.html)を参照してください。

### Zerto on IBM Cloud サービスのコンポーネントの更新

V2.7 以降の Cloud Foundation インスタンスと vCenter Server インスタンスにデプロイされた Zerto on {{site.data.keyword.cloud_notm}} サービスでは、Zerto Virtual Replication 6.0 更新 3 がプロビジョンされます。詳しくは、[Zerto on {{site.data.keyword.cloud_notm}} の概要](../services/addingzertodr.html)を参照してください。

### KMIP for VMware on IBM Cloud と IBM Cloud Activity Tracker との統合

VMware インスタンス・イベントに加えて、KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスのイベント (鍵の作成、鍵の削除、鍵のアクセスなど) が、{{site.data.keyword.cloud_notm}} Activity Tracker インスタンスに統合されるようになりました。KMIP for WMware on {{site.data.keyword.cloud_notm}} について詳しくは、[KMIP for VMware on {{site.data.keyword.cloud_notm}} の概要](../services/kmip_considerations.html)を参照してください。

## 新規資料および更新された資料

### リファレンス・アーキテクチャー資料

以下の技術資料が、ユーザー資料の『*リファレンス*』セクションに用意されています。

* [NSX Edge Services Gateway ソリューションのアーキテクチャー](../archiref/nsx/nsx_overview.html)
* [VMware Update Manager ガイド](../archiref/vum/vum-intro.html)
* [vCenter Server ネットワーキング・ガイド](../archiref/vcsnsxt/vcsnsxt-intro.html)
* [vCenter Server および {{site.data.keyword.cloud_notm}} Private ガイド](../archiref/vcsicp/vcsicp-intro.html)
* [vCenter Server および IBM Kubernetes サービス・ガイド](../archiref/vcsiks/vcsiks-intro.html)
* [VMware および Skate Advisor Concept Car ガイド](../archiref/vcscar/vcscar-intro.html)
* [VMware: 株式トレーダーのためのモダナイゼーションの手順](../archiref/vcscontent/vcscontent-modjourney.html)

これらのリファレンス・アーキテクチャー資料の一部は英語版しかありません。

## ユーザー・インターフェースの更新と向上

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。

* インスタンスの注文時に{{site.data.keyword.baremetal_short_sing}}設定の CPU モデルと RAM を指定する、元の**「カスタマイズ済み」**タブが、サーバー・タイプに基づいて**「Skylake」**タブと**「Broadwell」**タブに分割されたので、サーバーの選択が容易になりました。
* **「デプロイ済みインスタンス」**ページの**「vCenter Server インスタンス」**表に**「タイプ」**列が含まれるようになり、vCenter Server、vCenter Server with Hybridity Bundle、vCenter Limited Test Drive の各インスタンスを識別できるようになりました。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
