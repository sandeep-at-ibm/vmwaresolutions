---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-02"

---

# vCenter Server with Hybridity Bundle インスタンスの注文

ワークロードのニーズに合わせて最適化できる、柔軟でカスタマイズ可能な VMware 仮想化プラットフォームをデプロイするには、VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle インスタンスを注文します。 vCenter Server with Hybridity Bundle インスタンスの注文には VMware Hybrid Cloud Extension (HCX) のライセンスが含まれているので、VMware HCX on {{site.data.keyword.cloud_notm}} サービスを利用することができます。 災害復旧のための [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html) などのサービスも追加できます。

## 要件

以下の作業を完了していることを確認してください。
*  **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定の管理](../vmonic/useraccount.html)を参照してください。
*  [vCenter Server with Hybridity Bundle の要件と計画](vc_hybrid_planning.html)の情報を確認する。
* インスタンス名とドメイン・ネームの形式を確認する。 ドメイン・ネームとサブドメイン・ラベルは、インスタンスのユーザー名とサーバー名の生成に使用されます。

表 1. インスタンス名とドメイン・ネームの値の形式

| 名前        | 値の形式      |
  |:------------- |:------------- |
  | ドメイン・ネーム | `<root_domain>` |  
  | vCenter Server ログイン・ユーザー名 | `<user_id>@<root_domain>` (Microsoft Active Directory ユーザー) または `administrator@vsphere.local` |
  | vCenter Server FQDN | `vcenter.<subdomain_label>.<root_domain>`. 最大長は 50 文字です。 |
  | シングル・サインオン (SSO) サイト名 | `<subdomain_label>` |
  | 完全修飾 ESXi サーバー名 | `<host_prefix><n>.<subdomain_label>.<root_domain>`。ここで `<n>` は ESXi サーバーのシーケンスです。 最大長は 50 文字です。 |  
  | PSC FQDN | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. 最大長は 50 文字です。 |

**重要**: 注文時およびインスタンスのデプロイ時に設定した値は変更しないでください。 変更すると、インスタンスが使用できなくなる可能性があります。 例えば、パブリック・ネットワークがシャットダウンしたり、プロビジョニング中にサーバーや仮想サーバー・インスタンス (VSI) が Vyatta の内側に移動したり、IBM CloudBuilder VSI が停止したり、削除されたりすることがあります。

## システム設定

vCenter Server with Hybridity Bundle インスタンスを注文する際には、以下のシステム設定を指定する必要があります。

### インスタンス名

インスタンス名は、次の要件を満たす必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* インスタンス名の先頭と末尾は英数字である必要があります。
* インスタンス名の最大の長さは 10 文字です。
* インスタンス名はアカウント内で固有である必要があります。

### プライマリーまたはセカンダリー

新規プライマリー・インスタンスを注文するのか、既存のプライマリー・インスタンスのセカンダリー・インスタンスを注文するのかを選択します。

## ライセンス交付の設定

vCenter Server with Hybridity Bundle インスタンスの注文には、以下のライセンスが含められます。 NSX ライセンス・エディションは、**「Advanced」**または**「Enterprise」**のいずれかを指定する必要があります。

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition (Advanced または Enterprise) 6.4
* VMware vSAN 6.6 ライセンス・エディション (Advanced または Enterprise)

**注意:**
* vCenter Server with Hybridity Bundle インスタンスはライセンス持ち込みをサポートしていません。
* 最小のライセンス・エディションが、ユーザー・インターフェースに表示されます。 複数のコンポーネント・エディションがサポートされている場合は、必要なエディションを選択できます。

## ベア・メタル・サーバーの設定

ベア・メタルの設定は、ユーザーが{{site.data.keyword.CloudDataCent_notm}}およびカスタマイズした構成に基づきます。

vSAN 構成の場合、初期クラスターとデプロイメント後のクラスターの両方に 4 つの ESXi サーバーが必要です。 すべての ESXi サーバーが同じ構成を共有します。 デプロイメント後には、さらに 4 つのクラスターを追加できます。

### データ・センターの場所

インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。

### カスタマイズ型

カスタマイズ型ベア・メタル・サーバーの CPU モデルと RAM の量を指定します。

表 2. カスタマイズ型{{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| デュアル Intel Xeon E5-2620 v4 / 合計 16 コア、2.1 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2650 v4 / 合計 24 コア、2.2 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2690 v4 / 合計 28 コア、2.6 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| Dual Intel Xeon Silver 4110 Processor / 合計 16 コア、2.1 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
### ベア・メタル・サーバーの数

デフォルトで 4 つの ESXi サーバーが選択されます。変更はできません。

## ストレージ設定

vCenter Server with Hybridity Bundle インスタンスの注文には、VMware vSAN 6.6 が含められます。 このインスタンスを注文する際には、以下のストレージ設定を指定する必要があります。

* **vSAN 容量ディスクのディスク・タイプとサイズ**: 共有ストレージのニーズを満たす容量を選択します。
* **vSAN 容量ディスクの数**: 追加する vSAN 共有ストレージのディスク数を選択します。 ディスク数は、2、4、6、または 8 でなければなりません。

## ネットワーク・インターフェースの設定

vCenter Server with Hybridity Bundle インスタンスを注文する際には、以下のネットワーク・インターフェース設定を指定する必要があります。

### ホスト名接頭部

  ホスト名接頭部は、次の要件を満たす必要があります。
  *  英数字とダッシュ (-) の文字だけを使用できます。
  *  ホスト名接頭部の先頭と末尾は英数字である必要があります。
  *  ホスト名接頭部の最大長は 10 文字です。

### サブドメイン・ラベル

サブドメイン・ラベルは、次の要件を満たす必要があります。
*  英数字とダッシュ (-) の文字だけを使用できます。
*  サブドメイン・ラベルの先頭と末尾は英数字である必要があります。
*  サブドメイン・ラベルの最大長は 10 文字です。
*  サブドメイン・ラベルは、アカウント内で固有でなければなりません。

### ドメイン・ネーム

ルート・ドメイン・ネームは、次の要件を満たす必要があります。
* ドメイン・ネームは、ピリオド (.) で区切られた 2 つ以上のストリングで構成されていなければなりません。
* 最初の文字列は、英字で始まり英数字で終わらなければなりません。
* 最後の文字列を除き、文字列で使用できるのは、英数字とダッシュ (-) だけです。
* 最後の文字列には、英字しか使用できません。
* 最後の文字列の長さは、2 文字から 24 文字までの範囲でなければなりません。

**注:** ホストと VM (仮想マシン) の FQDN (完全修飾ドメイン・ネーム) の最大長は 50 文字です。 この最大長に対応するドメイン・ネームにする必要があります。

### 新規 VLAN を注文

**「新規 VLAN を注文」**を選択して、新しいパブリック VLAN 1 つと新しいプライベート VLAN 2 つを注文します。

インスタンスの注文には、パブリック VLAN 1 つとプライベート VLAN 2 つが必要です。 2 つのプライベート VLAN は各ベア・メタル・サーバーにトランキングされます。

### 既存の VLAN を選択

選択した {{site.data.keyword.CloudDataCent_notm}}によっては、既存のパブリック VLAN とプライベート VLAN を使用できることがあります。

インスタンスの注文には、パブリック VLAN 1 つとプライベート VLAN 2 つが必要です。 2 つのプライベート VLAN は各ベア・メタル・サーバーにトランキングされます。

**「既存の VLAN を選択」**を選択して、既存のパブリック VLAN とプライベート VLAN を再使用し、使用可能な VLAN とサブネットの中から選択します。

**重要:**
* 選択した VLAN のファイアウォール構成が管理用データ・トラフィックをブロックしていないことを確認してください。
* 選択したすべての VLAN が同じポッドに含まれていることを確認してください。複数のポッドの VLAN に ESXi サーバーをプロビジョンすることはできません。

### DNS 構成

インスタンスのドメイン・ネーム・システム (DNS) 構成を選択します。

* **Active Directory/DNS 用の単一のパブリック Windows VSI**: Microsoft Active Directory (AD) 用の単一の Microsoft Windows Server VSI。ホストと VM が登録されたインスタンスの DNS として機能します。これがデプロイされて参照可能になります。
* **管理クラスター上の高可用性構成の 2 つの専用 Windows Server VM**: 2 つの Microsoft Windows VM がデプロイされるので、セキュリティーと堅牢性が向上します。

**重要:** 2 つの Microsoft Windows VM を使用するようにインスタンスを構成する場合は、2 つの Microsoft Windows Server 2012 R2 ライセンスを提供する必要があります。 Microsoft Windows Server 2012 R2 Standard エディションのライセンスと Microsoft Windows Server 2012 R2 Datacenter エディションのライセンスのいずれかまたは両方を使用してください。

各ライセンスは単一の物理サーバーにのみ割り当てられ、最大 2 つの物理プロセッサーをカバーします。 1 つの Standard エディション・ライセンスでは、2 プロセッサーのサーバーで 2 つの Microsoft Windows VM を実行できます。 したがって、ライセンスは 2 つ必要になります。2 つの異なるホストに 2 つの Microsoft Windows VM がデプロイされるからです。

VM は 30 日以内に有効にしてください。

Windows ライセンスの注文方法について詳しくは、[Windows Server 2012 R2 の資料](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2)を参照してください。

## サービスの設定

vCenter Server with Hybridity Bundle インスタンスを注文するときに、追加のサービスも注文することができます。 サービスについて詳しくは、[vCenter Server with Hybridity Bundle インスタンスで使用可能なサービス](vc_hybrid_addingremovingservices.html#available-services-for-vcenter-server-with-hybridity-bundle-instances)を参照してください。

## 注文のサマリー

選択したインスタンス構成とアドオン・サービス構成に基づいて、見積もりコストがすぐに生成され、右側のペインの**「注文の要約」**セクションに表示されます。 右側のペインの下部の**「料金詳細」**をクリックすると、見積もりの詳細を示す PDF 文書を生成できます。

## 手順

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**をクリックしてから、**「仮想データ・センター」**セクションの**「vCenter サーバー」**をクリックします。
2. **「VMware vCenter Server on IBM Cloud」**ページで、**「vCenter Server with Hybridity Bundle」**カードをクリックし、**「作成」**をクリックします。
3. **「vCenter サーバー」**ページで、インスタンス名を入力します。
4. インスタンス・タイプを選択します。
   * 環境の単一インスタンスをデプロイするか、マルチサイト・トポロジーの最初のインスタンスをデプロイする場合は、**「プライマリー・インスタンス」**をクリックします。
   * 可用性を向上させる場合は、**「セカンダリー・インスタンス」**をクリックし、環境内の既存の (プライマリー) インスタンスにインスタンスを接続して、以下の手順を実行します。
     1. セカンダリー・インスタンスを接続するプライマリー・インスタンスを選択します。
     2. プライマリー・インスタンスの PSC 管理者パスワードを入力します。
5. NSX ライセンス・エディションと vSAN ライセンス・エディションを選択します。
6. ベア・メタル・サーバーの設定を次の手順で実行します。
  1. インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。
  2. **「カスタマイズ型」**の CPU モデルと **RAM** の容量を選択します。

  **注:** **「ベア・メタル・サーバーの数」**はデフォルトで 4 に設定されます。変更はできません。

7. ストレージ構成を次の手順で実行します。
  1. **「vSAN 容量ディスクのディスク・タイプとサイズ」**を選択します。
  2. **「vSAN 容量ディスクの数」**を選択します。
8. ネットワーク・インターフェース構成を行います。
  1. ホスト名接頭部、サブドメイン・ラベル、ルート・ドメイン・ネームを入力します。
  2. VLAN 構成を選択します。
     *  新規のパブリック VLAN とプライベート VLAN を注文する場合は、**「新規 VLAN を注文」**をクリックします。
     *  既存のパブリック VLAN とプライベート VLAN を使用できる場合に再利用するには、**「既存の VLAN を選択」**をクリックし、パブリック VLAN、プライマリー・サブネット、プライベート VLAN、プライベート・プライマリー・サブネット、セカンダリー・プライベート VLAN を選択します。
  3. DNS 構成を選択します。
9. インスタンスにデプロイするアドオン・サービスを、対応するサービス・カードをクリックして選択します。 サービスに構成が必要な場合は、サービス固有の設定を入力し、カードの**「サービスの追加」**をクリックします。  
サービスの設定方法については、対応するサービス注文トピックを参照してください。

8. **「発注要約」**ペインで、インスタンス構成を確認してから注文を実行します。
   1. インスタンスの設定を確認します。
   2. インスタンスの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、インスタンスを注文する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

## 結果

インスタンスのデプロイメントが自動的に開始されます。 注文が処理されていることを示す確認メッセージが表示されます。デプロイメントの状況を確認するには、インスタンスの詳細を表示します。

インスタンスが正常にデプロイされると、[vCenter Server with Hybridity Bundle インスタンスの技術仕様](vc_hybrid_overview.html#technical-specifications-for-vcenter-server-with-hybridity-bundle-instances)に記述されているコンポーネントが VMware 仮想プラットフォームにインストールされます。 注文した ESXi サーバーは、デフォルトでは **cluster1** としてグループ化されます。 追加のサービスを注文した場合は、注文の完了後にサービスのデプロイメントが開始されます。

インスタンスが使用可能になると、インスタンスの状況が**「使用可能」**に変わり、E メールで通知されます。

セカンダリー・インスタンスを注文した場合は、セカンダリー・インスタンスの注文が完了した後に、(セカンダリー・インスタンスにリンクされた) プライマリー・インスタンスの VMware vSphere Web Client が再始動されることがあります。

## 次に行うこと

注文した vCenter Server with Hybridity Bundle インスタンスを表示して管理します。

**重要**: {{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。
{{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されません。

**注意**: インスタンスを注文したときに {{site.data.keyword.cloud_notm}} アカウントにインストールされた {{site.data.keyword.vmwaresolutions_short}} コンポーネントを、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で管理すると、環境が不安定になる可能性があります。 これには以下の管理アクティビティーが該当します。
*  コンポーネントの追加、変更、返却、または削除
*  ESXi サーバーの追加または削除によるインスタンス容量の拡張または縮小
*  コンポーネントのパワーオフ
*  サービスの再始動

   {{site.data.keyword.slportal}}での共有ストレージのファイル共有の管理は、上記アクティビティーに該当しません。 これには、共有ストレージのファイル共有の注文、削除 (マウントされている場合はデータ・ストアに影響する可能性があります)、承認、マウントなどのアクティビティーが含まれます。

### 関連リンク

* [{{site.data.keyword.cloud_notm}} アカウントへの登録](../vmonic/signing_softlayer_account.html)
* [vCenter Server with Hybridity Bundle インスタンスの表示](vc_hybrid_viewinginstances.html)
* [vCenter Server with Hybridity Bundle インスタンスのマルチサイト構成](vc_hybrid_multisite.html)
* [vCenter Server with Hybridity Bundle インスタンスのクラスターの追加と表示](vc_hybrid_addingviewingclusters.html)
* [vCenter Server with Hybridity Bundle インスタンスの容量の拡張と縮小](vc_hybrid_addingremovingservers.html)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](vc_hybrid_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle インスタンスの削除](vc_hybrid_deletinginstance.html)
