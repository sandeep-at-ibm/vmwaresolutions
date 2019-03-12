---

copyright:

  years:  2016, 2018

lastupdated: "2018-12-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V2.7 のリリース・ノート
{: #relnotes_v27}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## SAP 認定 6140 サーバーのサポート

V2.7 リリース以降、VMware vCenter Server on {{site.data.keyword.cloud_notm}} と VMware vSphere on {{site.data.keyword.cloud_notm}} のインスタンスとクラスターのデプロイメントで、以下の新しい {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU モデルを使用できるようになりました。
* Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 192 GB RAM
* Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.2 GHz / 384 GB RAM
* Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 768 GB RAM

詳しくは、以下の資料にある『*{{site.data.keyword.baremetal_short_sing}}の設定*』セクションを参照してください。
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## アドオン・サービスの更新

### IBM Cloud Private Hosted

{{site.data.keyword.cloud_notm}} Private Hosted サービスが、V2.5 以降のリリースにデプロイ (またはアップグレード) された VMware vCenter Server インスタンスに加えて、VMware vCenter Server with Hybridity Bundle インスタンスでも使用できるようになりました。 vCenter Server インスタンスや vCenter Server with Hybridity Bundle インスタンスにこのサービスを組み込んで注文できるようになりました。 初期デプロイメント後の既存の vCenter Server インスタンスや vCenter Server with Hybridity Bundle インスタンスにこのサービスを追加することもできます。

詳しくは、以下のトピックを参照してください。
* [{{site.data.keyword.cloud_notm}} Private Hosted の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [{{site.data.keyword.cloud_notm}} Private Hosted の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)

### Mission Critical VMware on IBM Cloud

Mission Critical VMware on {{site.data.keyword.cloud_notm}} サービスが、V2.7 以降のリリースにデプロイされたインスタンス、または V2.7 以降のリリースにアップグレードされたインスタンスで使用できるようになりました。

Mission Critical VMware on {{site.data.keyword.cloud_notm}} では、企業がクラウド・アプリケーションのダウン時間をなくし、クラウド領域内でのフェイルオーバーを自動化できるようにするための、マルチゾーン・クラウド・アーキテクチャーを提供しています。 ほとんどの場合、このクラウド・アーキテクチャーを使用すると、オンプレミス環境または競合他社のクラウド・プラットフォームで VMware ユーザーが作業する場合より、高い可用性とフェイルオーバー成功率を実現できます。

詳しくは、[Mission Critical VMware on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-mcv_overview)を参照してください。

### F5 on IBM Cloud

F5 on {{site.data.keyword.cloud_notm}} サービスを注文するときに、F5 のライセンス適用をパブリック・ネットワークを介して行うか、それともプロキシー・サーバーを使用するプライベート・ネットワークを介して行うかを選択できるようになりました。 詳しくは、[F5 on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)を参照してください。

### FortiGate Virtual Appliance on IBM Cloud

2018 年第 3 四半期に、Fortinet のサブスクリプション・バンドルが変更されました。 詳しくは、[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)を参照してください。

V2.7 以降の Cloud Foundation インスタンスと vCenter Server インスタンスにデプロイされた FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスでは、FortiOS 6.0.3 がプロビジョンされます。

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} を注文するときに、FortiGuard のライセンス適用とセキュリティー更新をパブリック・ネットワークを介して行うか、それともプロキシー・サーバーを使用するプライベート・ネットワークを介して行うかを選択できます。 詳しくは、[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)を参照してください。

### Zerto on IBM Cloud サービスのコンポーネントの更新

V2.7 以降の Cloud Foundation インスタンスと vCenter Server インスタンスにデプロイされた Zerto on {{site.data.keyword.cloud_notm}} サービスでは、Zerto Virtual Replication 6.0 更新 3 がプロビジョンされます。 詳しくは、[Zerto on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)を参照してください。

### KMIP for VMware on IBM Cloud と IBM Cloud Activity Tracker との統合

VMware インスタンス・イベントに加えて、KMIP for VMware on {{site.data.keyword.cloud_notm}} のイベント (鍵の作成、鍵の削除、鍵のアクセスなど) が、{{site.data.keyword.cloud_notm}} Activity Tracker インスタンスに統合されるようになりました。 KMIP for WMware on {{site.data.keyword.cloud_notm}} について詳しくは、[KMIP for VMware on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services/kmip_considerations.html)を参照してください。

### KMIP for VMware on IBM Cloud - 非推奨

(2018 年 12 月 14 日更新) KMIP for VMware on {{site.data.keyword.cloud_notm}} の現行バージョンは非推奨になります。 詳しくは、[IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)を参照してください。
{:deprecated}

## 新規資料および更新された資料

### リファレンス・アーキテクチャー資料

以下の技術資料が、ユーザー資料の『*リファレンス*』セクションに用意されています。

* [NSX Edge Services Gateway ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx_overview)
* [VMware Update Manager ガイド](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro)
* [vCenter Server ネットワーキング・ガイド](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro)
* [vCenter Server および {{site.data.keyword.cloud_notm}} Private ガイド](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [vCenter Server および IBM Kubernetes サービス・ガイド](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro)
* [VMware および Skate Advisor Concept Car ガイド](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro)
* [VMware - 株式トレーダーのためのモダナイゼーションの手順](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney)

## ユーザー・インターフェースの更新と向上

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。

* インスタンスを注文するときに{{site.data.keyword.baremetal_short_sing}}設定の CPU モデルと RAM を指定する**「カスタマイズ型 (Customized)」**タブが、サーバーの選択に役立つようにサーバー・タイプ別に**「Skylake」**タブと**「Broadwell」**タブに分けられました。
* ベア・メタル構成の**「事前構成型 (Preconfigured)」**オプションはなくなりました。
* **「デプロイ済みインスタンス」**ページの**「vCenter Server インスタンス」**表に**「タイプ」**列が含まれるようになり、vCenter Server、vCenter Server with Hybridity Bundle、vCenter Limited Test Drive の各インスタンスを識別できるようになりました。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
