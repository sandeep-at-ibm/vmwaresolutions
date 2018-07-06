---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# IBM Cloud for VMware Solutions について

{{site.data.keyword.vmwaresolutions_full}} を使用すると、スケーラブルで安全な高性能 {{site.data.keyword.cloud_notm}} インフラストラクチャーと業界をリードする VMware ハイブリッド仮想化テクノロジーを活用して、オンプレミスの VMware ワークロードを {{site.data.keyword.cloud_notm}} に迅速かつシームレスに統合または移行できます。

{{site.data.keyword.vmwaresolutions_short}} では、簡単に VMware 仮想環境を {{site.data.keyword.cloud_notm}} にデプロイしてインフラストラクチャー・リソースを管理することができます。 また同時に、引き続き使い慣れた VMware 製品のネイティブ・コンソールを使用して VMware ワークロードを管理できます。

## IBM Cloud for VMware Solutions の利点

{{site.data.keyword.vmwaresolutions_short}} には、以下のような大きなメリットがあります。
* **グローバル展開**: ハイブリッド・クラウドのフットプリントを、世界中に設置されているエンタープライズ・クラスの {{site.data.keyword.CloudDataCents_notm}}に最大 30 拠点まで展開できます。
* **シームレスな統合**: ハイブリッド・クラウド全体にわたる、{{site.data.keyword.cloud_notm}} インフラストラクチャーへのシームレスな統合を実現します。
* **迅速なプロビジョニング**: VMware 環境のデプロイメントと構成を自動化しているので、オンデマンドで {{site.data.keyword.cloud_notm}}{{site.data.keyword.baremetal_short}}と仮想サーバーを投入してエンタープライズ・クラスの VMware 環境を迅速にデプロイできます。
* **シンプル化**: 基礎の物理インフラストラクチャー (コンピュート、ストレージ、ネットワーク) とソフトウェア・ライセンスを定義、調達、デプロイ、管理することなく、VMware クラウド・プラットフォームを利用できます。
* **拡張と縮小の柔軟性**: ビジネス・ニーズに応じて VMware ワークロードを簡単に拡張および縮小できます。
* **単一の管理コンソール**: {{site.data.keyword.cloud_notm}} 上の VMware 環境を単一のコンソールでデプロイ、アクセス、管理できます。

## デプロイメント・オファリング

{{site.data.keyword.vmwaresolutions_short}} では、VMware 仮想環境のデプロイメントとして、標準化されたデプロイメントとカスタマイズ可能なデプロイメントを選択できます。 以下のデプロイメント・タイプが用意されています。
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}}**: この vCenter Server オファリングでは、ビジネス・ニーズに最適なカスタムのコンピュート、ストレージ、ネットワークのリソースを使用して、VMware 仮想環境をデプロイできます。
* **VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle**: この vCenter Server with Hybridity オファリングは、オンプレミスのインフラストラクチャーを素早く簡単にクラウドに拡張できるホステッド・プライベート・クラウドです。 この VMware 環境は、IBM 提供の VMware Software Defined Data Center ライセンスに基づくものであり、VMware Hybrid Cloud Extension (HCX) が含まれています。 HCX を使用すると、オンプレミスの vSphere 5.0+ 環境と IBM Cloud サイトを安全に接続して、インフラストラクチャーのシームレスなハイブリッド化と真のアプリケーション・モビリティーを実現できます。
* **VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}**: この Cloud Foundation オファリングでは、標準的な {{site.data.keyword.cloud_notm}} コンピュート、ストレージ、ネットワークのリソースを各ユーザー・デプロイメントに専用で使用して、統一された VMware 仮想環境を実現できます。
* **VMware vSphere on {{site.data.keyword.cloud_notm}}**: この vSphere on {{site.data.keyword.cloud_notm}} オファリングで提供されるカスタマイズ可能な仮想化サービスを使用すると、VMware 互換の{{site.data.keyword.baremetal_short}}、ハードウェア・コンポーネント、ライセンスを組み合わせて、IBM でホストされる独自の VMware 環境を構築できます。
* **NetApp ONTAP Select**: NetApp ONTAP Select オファリングでは、NetApp ONTAP Select をベースとする可用性の高い専用ストレージ・アプライアンスを必要とするニーズに対応するソフトウェア定義ストレージ・クラスターをデプロイできます。
* **VMware Federal on {{site.data.keyword.cloud_notm}}**: VMware Federal on {{site.data.keyword.cloud_notm}} のオファリングでは、基本 vCenter Server インスタンスを注文できるだけでなく、デプロイしたインスタンスを保護する (つまり、機密情報を削除し、インスタンスに継続的にアクセスして管理機能を操作することが可能になる開いた状態の管理接続を除去する) ためのオプションも用意されています。

## その他のサービス

{{site.data.keyword.vmwaresolutions_short}} では、インスタンスの注文時に、また、インスタンスをデプロイした後でも、さまざまなサービスを追加できます。 以下のサービスが提供されています。

### FortiGate Security Appliance on IBM Cloud

このサービスは、FortiGate Security Appliance (FSA) 300 シリーズ・デバイスの HA ペアをデプロイします。これにより、ファイアウォール、ルーティング、NAT、および VPN サービスを利用して、自環境へのパブリック・ネットワーク接続を保護できます。

このサービスは、V1.8 以降のリリースでデプロイされたインスタンスでのみ使用できます。

詳しくは、[FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} の管理](../services/managingfsa.html)を参照してください。

### FortiGate Virtual Appliance on IBM Cloud

このサービスは、FortiGate Virtual Appliance の HA ペアをデプロイします。これにより、仮想インフラストラクチャー内にクリティカルなセキュリティー制御を実装してリスクを削減できます。

このサービスは、V2.0 以降のリリースでデプロイされたインスタンスでのみ使用できます。

詳しくは、[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の管理](../services/managingfortinetvm.html)を参照してください。

### F5 on IBM Cloud

このサービスは、F5 BIG-IP Virtual Edition (VE) を使用してアプリケーションのパフォーマンスを最適化し、可用性とセキュリティーを確保します。

このサービスは、V1.9 以降のリリースでデプロイされたインスタンスでのみ使用できます。

詳しくは、[F5 on {{site.data.keyword.cloud_notm}} の管理](../services/managing_f5.html)を参照してください。

### IBM Spectrum Protect Plus on IBM Cloud

このサービスは、仮想環境のデータ保護、データ再使用、データ・リカバリーのための効率的でスケーラブルなソリューションを提供します。 スタンドアロン・ソリューションとして実装することも、お客様の IBM Spectrum Protect&trade; Plus 環境と統合して長期保管とデータ・ガバナンスのためにコピーをオフロードすることもできます。

**注**:
* このサービスは、V2.2 以降のリリースでデプロイまたは V2.2 以降のリリースにアップグレードされたインスタンスでのみ使用できます。
* V2.3 以降のリリースでデプロイされたインスタンスの場合、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} は管理 VM のバックアップを自動的に行います。
* V2.2 でデプロイされたインスタンスの場合、このサービスはワークロード VM のデータのみを保護します。

詳しくは、[IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} の管理](../services/managingspp.html)を参照してください。

### IBM Cloud での Veeam

このサービスは、管理コンポーネントのバックアップとリストアを含め、環境内のすべての仮想マシン (VM) のバックアップとリストアを管理できるように、VMware 環境とシームレスに統合されます。 データの構成時に 15 分未満の RPO (目標復旧時点) を設定できます。

このサービスは、インスタンスのデプロイ直後に管理 VM をバックアップするように構成されています。

このサービスは、V1.8 以降のリリースでデプロイされたインスタンスでのみ使用できます。

詳しくは、[Veeam on {{site.data.keyword.cloud_notm}} の管理](../services/managingveeam.html)を参照してください。

### IBM Cloud での Zerto

このサービスは、ワークロードを保護するためにレプリケーション機能と災害復旧機能を提供します。 詳しくは、[Zerto on {{site.data.keyword.cloud_notm}} の管理](../services/managingzertodr.html)を参照してください。

### IMI のマネージド・サービス

これらのサービスは、IBM Integrated Managed Infrastructure (IMI) が幅広いクラウド・インフラストラクチャーに動的リモート管理サービスを提供できるようにします。

これらのサービスは、Cloud Foundation インスタンスでのみ使用できます。

詳しくは、[IMI のマネージド・サービスの要求](../services/managing_imi.html)を参照してください。

## 関連リンク

* [概説](../index.html)
* [Cloud Foundation の概要](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server の概要](../vcenter/vc_vcenterserveroverview.html)
* [vSphere on {{site.data.keyword.cloud_notm}}](../vsphere/vs_planning.html)
* [NetApp ONTAP Select](../netapp/np_netappoverview.html)
