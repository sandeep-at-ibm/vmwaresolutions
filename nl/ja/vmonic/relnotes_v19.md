---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-13"

---

# V1.9 のリリース・ノート

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## VMware vSphere on IBM Cloud

このリリースでは、VMware vSphere on {{site.data.keyword.cloud_notm}} オファリングが導入されています。このオファリングでは、選択した VMware コンポーネントに基づいて VMware 互換のコンピュート、ストレージ、ネットワークのリソースをカスタマイズして注文することで、IBM によってホストされる VMware 仮想環境を構築できます。vSphere on {{site.data.keyword.cloud_notm}} は、オプションの VMware コンポーネントのインストール、構成、オープンを自動化するものではありませんが、ビジネス・ニーズに最適な環境を設計して構築できるように柔軟性が最大化されています。{{site.data.keyword.CloudDataCent_notm}}で ESXi サーバーの vSphere クラスターを新規作成するか、既存の vSphere クラスターを拡張することから始めます。

詳しくは、以下のトピックを参照してください。
* [新規 vSphere クラスターの注文](../vsphere/vs_orderinginstances.html)
* [既存の vSphere クラスターの拡張](../vsphere/vs_scalingexistingclusters.html)

## NetApp ONTAP Select on IBM Cloud

このリリースでは、ソフトウェア定義ストレージ用の仮想アプライアンスである NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} オファリングが導入されました。これにより、IBM Cloud の専用{{site.data.keyword.baremetal_short}}上に NetApp ONTAP Select をサービスとして実装できます。 NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} は、高性能 (オール SSD) 構成と大容量 (オール SATA) 構成の両方で提供されます。
このオファリングは、専用のインフラストラクチャーでストレージをホストし、重複排除や保存データの圧縮と暗号化などの NetApp 機能を提供します。高度なデータ管理機能を使用してデータを保護しながら、俊敏性と柔軟性を備えたストレージ・リソースをプロビジョンします。例えば、高速で効率的な NetApp Snapshot® コピー、FlexClone® コピー、SnapMirror® レプリケーションなどを使用します。

詳しくは、以下のトピックを参照してください。
* [NetApp ONTAP Select の概要](../netapp/np_netappoverview.html)
* [NetApp ONTAP Select インスタンスの注文](../netapp/np_orderinginstances.html)

## F5 on IBM Cloud サービス

F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} サービスを、VMware Cloud Foundation と VMware vCenter Server の両方のインスタンスで使用できるようになりました。 このサービスは、ローカルおよびグローバル規模のインテリジェントな L4-L7 ロード・バランシングとトラフィック管理サービス、堅牢なネットワークと Web アプリケーション・ファイアウォール保護、セキュアなフェデレーテッド・アプリケーション・アクセスを提供します。
F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} サービスを組み込んだ形でインスタンスを注文するか、後から {{site.data.keyword.vmwaresolutions_short}} コンソールのインスタンス・プロパティーの詳細ページにある**「サービス」**タブで既存のインスタンスにこのサービスを追加します。要件に応じて、BIG-IP VE の 3 つのライセンス・オプションの中から 1 つを選択できます。

詳しくは、以下のトピックを参照してください。
* [F5 on {{site.data.keyword.cloud_notm}} の考慮事項](../services/f5_considerations.html)
* [F5 on {{site.data.keyword.cloud_notm}} の管理](../services/managing_f5.html)

## IBM Integrated Managed Infrastructure のマネージド・サービス

VMware Cloud Foundation インスタンスで IBM Integrated Managed Infrastructure (IMI) のマネージド・サービスを使用できるようになりました。 IMI を使用すると、モジュラー・サービスによって VMware 仮想インフラストラクチャーの管理をシンプルにすることができます。IMI は、信頼できる単一のプロバイダーとして機能するので、仮想 IT インフラストラクチャーの監視と管理の複雑さを軽減できます。 監視などの日常業務をいくらか IMI に委託することで、より価値のある業務に集中できます。

コンサルテーションと見積もりは、**「開始」**ページからいつでも要求できます。
詳しくは、[IMI のマネージド・サービスの要求](../services/managing_imi.html#requesting-managed-services-from-imi)を参照してください。

## vCenter Server および NetApp ONTAP Select インスタンスの名前に関する制限

インスタンスを注文するときに {{site.data.keyword.vmwaresolutions_short}} に入力するインスタンス名に、特殊文字 (ダッシュ文字など) を使用することはできません。 英数字のみを使用できます。 この制限は、Cloud Foundation インスタンスには適用されません。

詳しくは、以下のトピックを参照してください。
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)
* [NetApp ONTAP Select インスタンスの注文](../netapp/np_orderinginstances.html)

## VMware Cloud Foundation インスタンスの更新

### インスタンスの CPU とメモリーのカスタマイズ

事前に構築され、テストされた「スモール」、「標準」オプションのほか、ユーザー・カスタマイズ型サーバーのオプションも用意されています。 ワークロードの CPU と RAM の比率に合った VMware 互換ハードウェアにするために、デュアル CPU サーバー上のコアの合計数と RAM の量をユーザーが選択できるようになりました。 ローカル・ストレージはカスタマイズできません。

詳しくは、[Cloud Foundation インスタンスの注文](../sddc/sd_orderinginstance.html)を参照してください。

## VMware vCenter Server インスタンスの更新

### データ・センターをまたぐクラスターのサポート

ホストされる VMware 環境の拡張を強化するために、インスタンスで最初のクラスターをデプロイしたものとは別の {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) ポッドまたは {{site.data.keyword.CloudDataCent_notm}}に新規クラスターを作成できるようになりました。

詳しくは、[vCenter Server インスタンスのクラスターの追加と表示](../vcenter/vc_addingviewingclusters.html)を参照してください。

### コンポーネントの変更

このリリースでは、シングル・サインオン管理者が VMware のネイティブ・ツールで vCenter Server リソースを変更しても、{{site.data.keyword.vmwaresolutions_short}} コンソールでの操作に影響しなくなりました。 例えば、VMware vSphere Web Client から VMware 仮想データ・センター、クラスター、スイッチ、ポート・グループ、データ・ストア名を変更して、企業や個人の命名規則に従ってデプロイメントをカスタマイズしても、{{site.data.keyword.vmwaresolutions_short}} コンソールでの操作に下流影響が生じることはありません。

詳しくは、[vCenter Server インスタンスのコンポーネントの変更による影響](../vcenter/vcenter_chg_impact.html)を参照してください。

### 追加の RAM サイズ

ワークロードの CPU と RAM の比率に合ったハードウェアを使用できるように、vCenter Server インスタンスを注文する際や、vCenter Server インスタンスのクラスターを追加する際に選択できる RAM サイズが増えました。{{site.data.keyword.vmwaresolutions_short}} コンソールからサーバーを注文する際に、**「ユーザー・カスタマイズ型」**構成オプションで 64 GB、128 GB、256 GB、384 GB、512 GB、768 GB、1.5 TB の中から選択できます。

詳しくは、[vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)を参照してください。

### ネットワーク・ファイル・システムのバージョン更新

ネットワーク・ファイル・システム (NFS) バージョン 4.1 は、ユーザー・インターフェースにストレージ設定として表示されなくなりました。 すべての vCenter Server インスタンスは、NFS V3 でデプロイされます。 NFS V3 は前のプロトコル・バージョンですが、VMware Storage Distributed Resource Scheduler (SDRS) と Storage I/O Control (SIOC) をサポートするので、VMware 環境の拡張機能が有効になります。

詳しくは、[vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)を参照してください。

### 単一サイトのドメイン・ネーム・サーバーのドメイン・ネーム

注文中に vCenter Server インスタンスのドメイン・ネーム・サーバー (DNS) のドメイン・ネームを指定できるようになりました。 ホストと仮想マシンが登録されたインスタンスの DNS として機能する Microsoft Windows Server 仮想サーバー・インスタンス (VSI) が、デプロイされて参照可能になります。 この Microsoft Windows VSI には Microsoft Active Directory (AD) もセットアップされていて、DNS ドメイン・ネームは AD ドメインのフォレスト・ルートになります。 この Microsoft Windows VSI は、V1.9 以降でのみ使用できます。

詳しくは、以下のトピックを参照してください。
* [vCenter Server の概要](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server インスタンスの表示](../vcenter/vc_viewinginstances.html)

## Windows Server の更新の自動インストール要件

Microsoft Active Directory (AD) / ドメイン・ネーム・サーバー (DNS) には、更新プログラムのダウンロードだけが自動的にセットアップされます。 それらの更新プログラムのインストールと再始動は、自動的には行われません。 更新プログラムを手動でインストールし、実行中の Active Directory サーバーの構成ジョブやその他のバックアップ・ジョブが中断されないように計画した時刻に再始動する必要があります。Windows 更新プログラムを適用するには、手動で更新プログラムをインストールしてください。

## 新規資料および更新された資料

* プライベートなマルチサイト Cloud Foundation インスタンスを保護し、パブリックな {{site.data.keyword.cloud_notm}} サービスを使用するように VMware アプリケーションを拡張する方法を説明します。 詳しくは、[Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window} を参照してください。
* IBM CloudDriver 仮想マシンと SDDC Manager 仮想マシンからのすべてのプロトコル通信を許可するファイアウォールを構成できるように、さらに資料が提供されています。詳しくは、[Fortinet on {{site.data.keyword.cloud_notm}} のコンポーネントと考慮事項](../services/fsa_considerations.html)を参照してください。
