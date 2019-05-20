---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.5 のリリース・ノート
{: #relnotes_v25}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Spectre および Meltdown への対処
{: #relnotes_v25-spectre}

{{site.data.keyword.vmwaresolutions_short}} は、Spectre および Meltdown と呼ばれる脆弱性 (CVE-2017-5753、CVE-2017-5715、CVE-2017-5754) に対して VMware から提供されたパッチをリリースしました。

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## NSX コンポーネントの更新
{: #relnotes_v25-nsx}

このリリースは、VMware vCenter Server on {{site.data.keyword.cloud_notm}}、VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle、NetApp ONTAP Select の新しいデプロイメントのための VMware NSX for vSphere 6.4.1 をインストールします。

## デフォルト・バックアップ構成の削除
{: #relnotes_v25-default-backup}

{{site.data.keyword.vmwaresolutions_short}} には、バックアップ用に 2 つのアドオン・サービスが組み込まれています。それらは、IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} および Veeam on {{site.data.keyword.cloud_notm}} です。 これらのサービスにより、管理インフラストラクチャーとワークロードの両方のリカバリーを計画し、準備することができます。 さらに、IBM Resiliency Services では Veeam バックアップのためのマネージド・サービスを利用できます。

V2.5 リリース以降、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} および Veeam on {{site.data.keyword.cloud_notm}} サービスは、デプロイ時に VM のバックアップの事前構成を行いません。 この変更により、スケジュール作成、保存期間、重複排除の使用、モニタリングとアラート、暗号キーの管理など、バックアップ・ジョブのすべての側面をユーザーが適切に構成できるようになりました。 さらに、IBM CloudDriver VM は、NSX バックアップ用の永続的なファイル・サーバーとしては構成されなくなります。

お客様は、管理インフラストラクチャーとワークロードのバックアップと可用性など、すべてのソフトウェア・コンポーネントの構成、管理、およびモニタリングについての責任があります。 詳しくは、[コンポーネントのバックアップ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#backing-up-components)を参照してください。

この変更は、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} や Veeam on {{site.data.keyword.cloud_notm}} サービスがインストールされている、V2.5 より前にデプロイされたインスタンスには影響しません。
{:note}

## IBM CloudDriver の回復力
{: #relnotes_v25-cloud-driver}

V2.5 以降のリリースにデプロイまたはアップグレードされたインスタンスの場合、IBM CloudDriver コンポーネントは、vSphere クラスター内の仮想マシン (VM) として構成されることがなくなりました。 代わりに、追加のノード、クラスター、サービスをデプロイするなどの操作のために、最新の {{site.data.keyword.cloud_notm}} for VMware コードと一緒に、{{site.data.keyword.cloud_notm}} インフラストラクチャーの仮想サーバー・インスタンス (VSI) として、必要に応じてデプロイされるようになりました。 さらに、IBM CloudDriver は、{{site.data.keyword.cloud_notm}} プライベート・ネットワークを使用して {{site.data.keyword.cloud_notm}} 管理プレーンと通信するように変更されました。 この変更により、IBM CloudDriver からパブリック・ネットワークへのアウトバウンド通信を許可する 管理 NSX Edge Services Gateway (ESG) ファイアウォールおよびネットワーク・アドレス変換 (NAT) の規則が削除されました。

F5 on {{site.data.keyword.cloud_notm}}、FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}、Zerto on {{site.data.keyword.cloud_notm}} などいくつかのアドオン・サービスでは引き続きパブリック・ネットワーク・アクセスが必要なので、管理 NSX ESG は引き続きすべてのインスタンスにデプロイされます。

## IAM 対応のユーザーおよびアクセス管理
{: #relnotes_v25-iam}

V2.5 リリースから、{{site.data.keyword.vmwaresolutions_short}} は IBM Identity and Access Management (IAM) と統合され、{{site.data.keyword.cloud_notm}} アカウント内でユーザー・アカウントとユーザー・アクセスを管理するための統一されたアプローチを提供するようになりました。 これにより、以下のようになりました。
* コラボレーションのために {{site.data.keyword.cloud_notm}} アカウントに複数のユーザーを追加することができます。またそれらのユーザーに異なるプラットフォーム・アクセス役割を割り当てることにより、アカウント内でプロビジョンされるサービスおよびリソースへのユーザーのアクセスを管理することができます。  
* V2.5 以降のリリースでデプロイされるインスタンスは、インスタンスの注文時に使用されていたユーザー・アカウントに自動的にリンクされます。
* V2.4 以前のリリースでデプロイされたインスタンスは、指定の {{site.data.keyword.cloud_notm}} アカウントにマイグレーションしてから、IAM を使用して管理できます。

詳しくは、以下のトピックを参照してください。
* [サービスとリソースにアクセスするようにユーザーを招待する](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [IAM でのユーザー・アクセス権限の管理](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-iam#iam)

## VMware vCenter Server および VMware Cloud Foundation インスタンスのためのユーザー・アカウントとグループへの変更
{: #relnotes_v25-user-acct}

**ic4v-vCenter** ユーザー・グループが Microsoft Active Directory サーバーに作成されて、vCenter Server のグローバル許可および NSX Manager のユーザー・グループに追加されました。 そのグループには、vCenter Server インスタンス用の **automation** ユーザー・アカウント、および vCenter Server と Cloud Foundation インスタンス用のサービス固有のユーザー・アカウントが含まれます。

VMware vSphere Web Client の**「ユーザーおよびグループ」**ページで**「ic4v-vCenter」**グループのグローバル許可を編集しないでください。 編集すると、管理操作が影響を受ける可能性があります。

Cloud Foundation インスタンスの場合、**customerroot** ホスト・ユーザー ID を **root** ホスト・ユーザー ID の代わりに使用します。

vCenter Server インスタンスの場合、**root** ホスト・ユーザー ID を引き続き使用します。 **ic4vroot** ホスト・ユーザー ID は、IBM 専用に作成されたものです。

ユーザー・アカウントについて詳しくは、[vCenter Server 成果物の変更に関する考慮事項](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact)を参照してください。

## アドオン・サービスの更新
{: #relnotes_v25-services}

### IBM Cloud Private Hosted (2018 年 8 月 30 日更新)
{: #relnotes_v25-scp-hosted}

{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} サービスが、V2.5 以降のリリースでデプロイ (または V2.5 以降のリリースにアップグレード) された vCenter Server インスタンスで使用できるようになりました。

{{site.data.keyword.cloud_notm}} Private Hosted は、マイクロサービスとコンテナーの機能を {{site.data.keyword.cloud_notm}} 上の VMware 環境で利用できるようにします。 このサービスを利用することで、使い慣れたオンプレミスの VMware と {{site.data.keyword.cloud_notm}} Private の操作モデルとツールを、{{site.data.keyword.cloud_notm}} に拡張できます。

このサービスは、vCenter Server インスタンスの注文後に要求できます。

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v25-spp}

V2.5 リリースから、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスは、ベスト・プラクティスに基づいて 2 つの独立した VM としてデプロイされます。1 つの VM は IBM Spectrum Protect Plus サーバーを実行し、もう 1 つの VM は vSnap サーバーと VADP プロキシーを実行します。

最大 10 個のバックアップ・データ・ストアを注文できるので、最大 120 TB のバックアップ・ストレージが可能になります。 vSnap および VADP VM は、選択したバックアップ・ストレージ・サイズと [IBM Spectrum Protect Plus Blueprints](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints) の情報に基づいてサイズ変更されます。

### KMIP for VMware on IBM Cloud
{: #relnotes_v25-kmip}

ドイツでは、KMIP for VMware on {{site.data.keyword.cloud_notm}} サービス用に新しいエンドポイントが使用可能になりました。

## 新規資料および更新された資料
{: #relnotes_v25-new-docs}

### 接続されたストレージの資料
{: #relnotes_v25-docs-storage}

vCenter Server on IBM Cloud の接続されたストレージに関する技術資料が、ユーザー資料の『*リファレンス*』セクションに用意されています。 詳しくは、[vCenter Server on IBM Cloud の接続されたストレージ](/docs/services/vmwaresolutions/archiref/attached-storage?topic=vmware-solutions-storage-benefits)を参照してください。

### 技術仕様
{: #relnotes_v25-docs-tech-specs}

すべてのインスタンス・タイプとサービス・タイプの技術仕様がユーザー資料で確認できるようになっており、ユーザー・インターフェースからもリンクできるようになっています。 詳しくは、使用するインスタンスとサービスに対応した概要トピックを参照してください。

### サービスの資料
{: #relnotes_v25-docs-services}

サービス情報が改善されて、使用可能になったときのリリース番号に基づき、サービス・サポートを簡単に識別できるようになりました。

詳しくは、以下のトピックを参照してください。

* [vCenter Server インスタンスで使用可能なサービス](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices#available-services-for-vcenter-server-instances)
* [vCenter Server with Hybridity Bundle インスタンスで使用可能なサービス](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances)

## ユーザー・インターフェースの更新と向上
{: #relnotes_v25-ui}

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。

* {{site.data.keyword.cloud_notm}} アカウントにリンクされた {{site.data.keyword.cloud_notm}}  インフラストラクチャー (SoftLayer) アカウントがある場合、**「設定」**ページで新しく追加された**「取得 (Retrieve)」**ボタンをクリックして、{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントのユーザー名の API 鍵を自動的に取得できるようになりました。
* インスタンスのデプロイメント履歴を調べるための新しい**「デプロイメント履歴」**タブが、インスタンス詳細ページの左側ナビゲーション・ペインに追加されました。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
