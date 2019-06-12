---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle インスタンスの注文
{: #vc_hybrid_orderinginstance}

ワークロードのニーズに合わせて最適化できる、柔軟でカスタマイズ可能な VMware 仮想化プラットフォームをデプロイするには、VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle インスタンスを注文します。 vCenter Server with Hybridity Bundle インスタンスの注文には VMware Hybrid Cloud Extension (HCX) のライセンスが含まれているので、VMware HCX on {{site.data.keyword.cloud_notm}} サービスを利用することができます。 災害復旧のための [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) などのサービスも追加できます。

## vCenter Server with Hybridity Bundle インスタンスを注文するための要件
{: #vc_hybrid_orderinginstance-req}

以下の作業を完了していることを確認してください。
*  **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定の管理](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)を参照してください。
*  [vCenter Server with Hybridity Bundle の要件と計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)の情報を確認する。
* インスタンス名とドメイン・ネームの形式を確認する。 ドメイン・ネームとサブドメイン・ラベルは、インスタンスのユーザー名とサーバー名の生成に使用されます。

表 1. インスタンス名とドメイン・ネームの値の形式

| 名前        | 値の形式      |
  |:------------- |:------------- |
  | ドメイン・ネーム | `<root_domain>` |  
  | vCenter Server ログイン・ユーザー名 | `<user_id>@<root_domain>` (Microsoft Active Directory ユーザー) または `administrator@vsphere.local` |
  | vCenter Server (PSC が組み込まれたもの) の FQDN | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`。最大長は 50 文字です。 |
  | シングル・サインオン (SSO) サイト名 | `<subdomain_label>` |
  | 完全修飾 ESXi サーバー名 | `<host_prefix><n>.<subdomain_label>.<root_domain>`。`<n>` は ESXi サーバーのシーケンスです。 最大長は 50 文字です。 |

インスタンスの注文時およびデプロイ時に設定した値は変更しないでください。 変更すると、インスタンスを使用できなくなる可能性があります。 例えば、パブリック・ネットワークがシャットダウンしたり、プロビジョニング中にサーバーや仮想サーバー・インスタンス (VSI) が Vyatta の内側に移動したり、IBM CloudBuilder VSI が停止したり、削除されたりすることがあります。
{:important}

## システム設定
{: #vc_hybrid_orderinginstance-sys-settings}

vCenter Server with Hybridity Bundle インスタンスを注文する際には、以下のシステム設定を指定する必要があります。

### インスタンス名
{: #vc_hybrid_orderinginstance-inst-name}

インスタンス名は、次の要件を満たす必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* インスタンス名の先頭は英字、末尾は英数字でなければなりません。
* インスタンス名の最大の長さは 10 文字です。
* インスタンス名はアカウント内で固有である必要があります。

### VMware vSphere ライセンス
{: #vc_hybrid_orderinginstance-vsphere-license}

vSphere Enterprise Plus 6.7u1 と vSphere Enterprise Plus 6.5u2 のどちらを注文するかを選択します。

vSphere Enterprise Plus 6.7u1 は Broadwell および Skylake の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} でのみ使用可能です。
{:note}

### プライマリーまたはセカンダリー
{: #vc_hybrid_orderinginstance-primary-secondary}

新規プライマリー・インスタンスを注文するのか、既存のプライマリー・インスタンスのセカンダリー・インスタンスを注文するのかを選択します。

## ライセンス交付の設定
{: #vc_hybrid_orderinginstance-licensing-settings}

vCenter Server with Hybridity Bundle インスタンスの注文には、以下の VMware ライセンスが含められます。 NSX および vSAN のライセンスのエディションを指定する必要があります。

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5 または 6.7
* NSX Service Providers 6.4 (Advanced または Enterprise エディション)
* vSAN 6.6 (Advanced または Enterprise エディション)

### 注意
{: #vc_hybrid_orderinginstance-attention}

* vCenter Server with Hybridity Bundle インスタンスはライセンス持ち込みをサポートしていません。
* 最小のライセンス・エディションが、ユーザー・インターフェースに表示されます。 複数のコンポーネント・エディションがサポートされている場合は、必要なエディションを選択できます。

## ベア・メタル・サーバーの設定
{: #vc_hybrid_orderinginstance-bare-metal-settings}

ベアメタルの設定は、選択した{{site.data.keyword.CloudDataCent_notm}}やベアメタル・サーバーの構成に基づきます。

vSAN 構成の場合、初期クラスターとデプロイメント後のクラスターの両方に 4 つの ESXi サーバーが必要です。 すべての ESXi サーバーが同じ構成を共有します。 デプロイメント後には、さらに 4 つのクラスターを追加できます。

### データ・センターの場所
{: #vc_hybrid_orderinginstance-dc-location}

インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。

### Skylake
{: #vc_hybrid_orderinginstance-skylake}

**「Skylake」**を選択した場合、必要に応じてベアメタル・サーバーの CPU と RAM の組み合わせを選択できます。

表 2. Skylake {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 プロセッサー / 合計 16 コア、2.1 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

### Broadwell
{: #vc_hybrid_orderinginstance-broadwell}

**「Broadwell」**を選択した場合、必要に応じてベアメタル・サーバーの CPU と RAM の組み合わせを選択できます。

表 3. Broadwell {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| クワッド Intel Xeon E7-4820 v4 / 合計 40 コア、2.0 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
| クワッド Intel Xeon E7-4850 v4 / 合計 64 コア、2.1 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |

### ベア・メタル・サーバーの数
{: #vc_hybrid_orderinginstance-bare-metal-number}

* 注文したすべてのサーバーが同じ構成です。
* 4 から 20 までのサーバーを注文できます。

## ストレージ設定
{: #vc_hybrid_orderinginstance-storage-settings}

vCenter Server with Hybridity Bundle インスタンスの注文には、VMware vSAN 6.6 が含められます。 以下の vSAN オプションを指定します。
* **vSAN 容量ディスクのディスク・タイプとサイズ**: 必要な容量ディスクのオプションを選択します。
* **vSAN 容量ディスクの数**: 追加する容量ディスク数を指定します。
* 容量ディスクを上限の 10 個を超えて追加する場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。 このオプションでは、合計 12 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されますので、より少ない待ち時間とより高い IOPS スループットが求められるワークロードを扱うときに役立ちます。

  **「High-Performance Intel Optane」**オプションは、Skylake CPU モデルでのみ使用できます。
  {:note}

* **「Disk Type for vSAN Cache Disks」**および**「Number of vSAN Cache Disks」**の値を確認します。 これらの値は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けたかどうかによって異なります。

## ネットワーク・インターフェースの設定
{: #vc_hybrid_orderinginstance-network-interface-settings}

vCenter Server with Hybridity Bundle インスタンスを注文する際には、以下のネットワーク・インターフェース設定を指定する必要があります。

### ホスト名接頭部
{: #vc_hybrid_orderinginstance-host-name-prefix}

  ホスト名接頭部は、次の要件を満たす必要があります。
  *  英数字とダッシュ (-) の文字だけを使用できます。
  *  ホスト名接頭部の先頭と末尾は英数字である必要があります。
  *  ホスト名接頭部の最大長は 10 文字です。

### サブドメイン・ラベル
{: #vc_hybrid_orderinginstance-subdomain-label}

サブドメイン・ラベルは、次の要件を満たす必要があります。
*  英数字とダッシュ (-) の文字だけを使用できます。
*  サブドメイン・ラベルの先頭は英字、末尾は英数字でなければなりません。
*  サブドメイン・ラベルの最大長は 10 文字です。
*  サブドメイン・ラベルは、アカウント内で固有でなければなりません。

### ドメイン・ネーム
{: #vc_hybrid_orderinginstance-domain-name}

ルート・ドメイン・ネームは、次の要件を満たす必要があります。
* ドメイン・ネームは、ピリオド (.) で区切られた 2 つ以上のストリングで構成されていなければなりません。
* 最初の文字列は、英字で始まり英数字で終わらなければなりません。
* 最後の文字列を除き、文字列で使用できるのは、英数字とダッシュ (-) のみです。
* 最後の文字列には、英字しか使用できません。
* 最後の文字列の長さは、2 文字から 24 文字までの範囲でなければなりません。

ホストと VM (仮想マシン) の FQDN (完全修飾ドメイン・ネーム) の最大長は 50 文字です。 この最大長に対応するドメイン・ネームにする必要があります。
{:note}

### パブリックまたはプライベート・ネットワーク
{: #vc_hybrid_orderinginstance-public-private-network}

ネットワーク・インターフェース・カード (NIC) の有効化設定は、**「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のどちらを選択したかに基づきます。

**「プライベート・ネットワークのみ」**オプションを選択した場合:
* VMware NSX Edge Services Gateways (ESG) はプロビジョンされません (管理サービス ESG もユーザー管理の ESG もプロビジョンされません)。
* パブリック NIC を必要とする次のアドオン・サービスは利用できません。
  * F5 on {{site.data.keyword.cloud_notm}}
  * Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
  * Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### 新規 VLAN を注文
{: #vc_hybrid_orderinginstance-new-vlans}

**「新規 VLAN を注文」**を選択して、新しいパブリック VLAN 1 つと新しいプライベート VLAN 2 つを注文します。

インスタンスの注文には、パブリック VLAN 1 つとプライベート VLAN 2 つが必要です。 2 つのプライベート VLAN は各ベア・メタル・サーバーにトランキングされます。

### 既存の VLAN を選択
{: #vc_hybrid_orderinginstance-existing-vlans}

選択した {{site.data.keyword.CloudDataCent_notm}}によっては、既存のパブリック VLAN とプライベート VLAN を使用できることがあります。

インスタンスの注文には、パブリック VLAN 1 つとプライベート VLAN 2 つが必要です。 2 つのプライベート VLAN は各ベア・メタル・サーバーにトランキングされます。

**「既存の VLAN を選択」**を選択して、既存のパブリック VLAN とプライベート VLAN を再使用し、使用可能な VLAN とサブネットの中から選択します。

* 選択した VLAN のファイアウォール構成が管理用データ・トラフィックをブロックしていないことを確認してください。
* 選択したすべての VLAN が同じポッドに含まれていることを確認してください。複数のポッドの VLAN に ESXi サーバーをプロビジョンすることはできません。
{:important}

### DNS 構成
{: #vc_hybrid_orderinginstance-dns-config}

インスタンスのドメイン・ネーム・システム (DNS) 構成を選択します。

* **Active Directory/DNS 用の単一のパブリック Windows VSI**: Microsoft Active Directory (AD) 用の単一の Microsoft Windows Server VSI。ホストと VM が登録されたインスタンスの DNS として機能します。これがデプロイされて参照可能になります。
* **管理クラスター上の高可用性構成の 2 つの専用 Windows Server VM**: 2 つの Microsoft Windows VM がデプロイされるので、セキュリティーと堅牢性が向上します。

2 つの Microsoft Windows VM を使用するようにインスタンスを構成する場合は、2 つの Microsoft Windows Server 2016 ライセンスを提供する必要があります。 Microsoft Windows Server 2016 Standard エディションのライセンスと Microsoft Windows Server 2016 Datacenter エディションのライセンスのいずれかまたは両方を使用してください。
{:important}

各ライセンスは単一の物理サーバーにのみ割り当てられ、最大 2 つの物理プロセッサーをカバーします。 1 つの Standard エディション・ライセンスでは、2 プロセッサーのサーバーで 2 つの Microsoft Windows VM を実行できます。 したがって、ライセンスは 2 つ必要になります。2 つの異なるホストに 2 つの Microsoft Windows VM がデプロイされるからです。

VM は 30 日以内に有効にしてください。

Windows Server 2016 ライセンスの注文について詳しくは、[Windows Server 2016 の使用を開始する](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:new_window}を参照してください。

## サービスの設定
{: #vc_hybrid_orderinginstance-addon-services}

vCenter Server with Hybridity Bundle インスタンスを注文するときに、追加のサービスも注文することができます。 サービスについて詳しくは、[vCenter Server with Hybridity Bundle インスタンスで使用可能なサービス](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances)を参照してください。

## 注文のサマリー
{: #vc_hybrid_orderinginstance-order-summary}

選択したインスタンス構成とアドオン・サービス構成に基づいて、見積もりコストがすぐに生成され、右側のペインの**「注文の要約」**セクションに表示されます。 右側のペインの下部の**「料金詳細」**をクリックすると、見積もりの詳細を示す PDF 文書を生成できます。

## vCenter Server with Hybridity Bundle インスタンスを注文する手順
{: #vc_hybrid_orderinginstance-procedure}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**をクリックしてから、**「仮想データ・センター」**セクションの**「vCenter サーバー」**をクリックします。
2. **「VMware vCenter Server on IBM Cloud」**ページで、**「vCenter Server with Hybridity Bundle」**カードをクリックし、**「作成」**をクリックします。
3. **「vCenter サーバー」**ページで、インスタンス名を入力します。
5. vSphere バージョンを選択します。
4. インスタンス・タイプを選択します。
   * 環境の単一インスタンスをデプロイするか、マルチサイト・トポロジーの最初のインスタンスをデプロイする場合は、**「プライマリー・インスタンス」**をクリックします。
   * 可用性を向上させる場合は、**「セカンダリー・インスタンス」**をクリックし、環境内の既存の (プライマリー) インスタンスにインスタンスを接続して、以下の手順を実行します。
     1. セカンダリー・インスタンスを接続するプライマリー・インスタンスを選択します。
     2. プライマリー・インスタンスが V2.8 以降である場合は、プライマリー・インスタンスの vCenter Server 管理者パスワードを入力します。
     3. プライマリー・インスタンスが V2.7 以前である場合は、プライマリー・インスタンスの PSC 管理者パスワードを入力します。
6. NSX ライセンス・エディションと vSAN ライセンス・エディションを選択します。
7. ベア・メタル・サーバーの設定を次の手順で実行します。
  1. インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。
  2. **「Skylake」**または**「Broadwell」**の CPU モデルと **RAM** の容量を選択します。
8. ストレージ構成を次の手順で実行します。 容量ディスクおよびキャッシュ・ディスクのディスク・タイプとディスク数を指定します。 さらにストレージが必要な場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。
9. ネットワーク・インターフェース構成を行います。
  1. プロビジョンされているインスタンスのホスト名接頭部、サブドメイン・ラベル、ルート・ドメイン・ネームを入力します。
  2. **「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のいずれかのネットワーク設定を選択します。
  3. VLAN 構成を選択します。
     *  新規のパブリック VLAN とプライベート VLAN を注文する場合は、**「新規 VLAN を注文」**をクリックします。
     *  既存のパブリック VLAN とプライベート VLAN を使用できる場合に再利用するには、**「既存の VLAN を選択」**をクリックし、パブリック VLAN、プライマリー・サブネット、プライベート VLAN、プライベート・プライマリー・サブネット、セカンダリー・プライベート VLAN を選択します。
  4. DNS 構成を選択します。
10. 組み込まれている HCX on {{site.data.keyword.cloud_notm}} サービスの構成を完了します。 サービスの設定方法について詳しくは、[VMware HCX on IBM Cloud の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering#vmware-hcx-on-ibm-cloud-configuration)の『_VMware HCX on IBM Cloud の構成_』セクションを参照してください。
11. インスタンスにデプロイするアドオン・サービスを、対応するサービス・カードをクリックして選択します。 サービスに構成が必要な場合は、サービス固有の設定を入力し、カードの**「サービスの追加」**をクリックします。  
サービスの設定方法について詳しくは、対応するサービス注文トピックを参照してください。

12. **「発注要約」**ペインで、インスタンス構成を確認してから注文を実行します。
   1. インスタンスの設定を確認します。
   2. インスタンスの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、インスタンスを注文する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

## 結果
{: #vc_hybrid_orderinginstance-results}

インスタンスのデプロイメントが自動的に開始されます。 注文が処理されていることを示す確認メッセージが表示されます。デプロイメントの状況を確認するには、インスタンスの詳細を表示します。

インスタンスが正常にデプロイされると、[vCenter Server with Hybridity Bundle インスタンスの技術仕様](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#specs)に記述されているコンポーネントが VMware 仮想プラットフォームにインストールされます。 注文した ESXi サーバーは、デフォルトでは **cluster1** としてグループ化されます。 アドオン・サービスを注文した場合は、注文の完了後にサービスのデプロイメントが開始されます。

インスタンスが使用可能になると、インスタンスの状況が**「使用可能」**に変わり、E メールで通知されます。

セカンダリー・インスタンスを注文した場合は、セカンダリー・インスタンスの注文が完了した後に、(セカンダリー・インスタンスにリンクされた) プライマリー・インスタンスの VMware vSphere Web Client が再始動されることがあります。

## 次に行うこと
{: #vc_hybrid_orderinginstance-next}

注文した vCenter Server with Hybridity Bundle インスタンスを表示して管理します。

{{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。
{{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されません。
{:important}

**注意:** インスタンスを注文したときに {{site.data.keyword.cloud_notm}} アカウントにインストールされた {{site.data.keyword.vmwaresolutions_short}} コンポーネントを、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で管理すると、環境が不安定になる可能性があります。 これには以下の管理アクティビティーが該当します。
*  コンポーネントの追加、変更、返却、または削除
*  ESXi サーバーの追加または削除によるインスタンス容量の拡張または縮小
*  コンポーネントのパワーオフ
*  サービスの再始動

   {{site.data.keyword.slportal}}での共有ストレージのファイル共有の管理は、上記アクティビティーに該当しません。 これには、共有ストレージのファイル共有の注文、削除 (マウントされている場合はデータ・ストアに影響する可能性があります)、承認、マウントなどのアクティビティーが含まれます。

## 関連リンク
{: #vc_hybrid_orderinginstance-related}

* [{{site.data.keyword.cloud_notm}} アカウントの登録](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)
* [vCenter Server with Hybridity Bundle インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [vCenter Server with Hybridity Bundle インスタンスのマルチサイト構成](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_multisite)
* [vCenter Server with Hybridity Bundle インスタンスのクラスターの追加と表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [vCenter Server with Hybridity Bundle インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [vCenter Server with Hybridity Bundle インスタンスの削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance)
