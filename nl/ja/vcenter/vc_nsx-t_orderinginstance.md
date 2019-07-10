---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: vCenter Server NSX-T order instance, order vCenter Server NSX-T, order NSX-T

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with NSX-T インスタンスの注文
{: #vc_nsx-t_orderinginstance}

ワークロードのニーズに合わせて最適化できる、柔軟でカスタマイズ可能な VMware 仮想化プラットフォームをデプロイするには、VMware vCenter Server with NSX-T インスタンスを注文します。

## vCenter Server with NSX-T の要件
{: #vc_nsx-t_orderinginstance-req}

以下の作業を完了していることを確認してください。
* **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定の管理](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)を参照してください。
* [vCenter Server インスタンスの要件と計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)の情報を確認する。
* インスタンス名とドメイン・ネームの形式を確認する。 ドメイン・ネームとサブドメイン・ラベルは、インスタンスのユーザー名とサーバー名の生成に使用されます。

表 1. インスタンス名とドメイン・ネームの値の形式

| 名前        | 値の形式      |
  |:------------|:------------ |
  | ドメイン・ネーム | `<root_domain>` |  
  | vCenter Server ログイン・ユーザー名 | `<user_id>@<root_domain>` (Microsoft Active Directory ユーザー) または `administrator@vsphere.local` |
  | vCenter Server (PSC が組み込まれたもの) の FQDN | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`。最大長は 50 文字です。 |
  | シングル・サインオン (SSO) サイト名 | `<subdomain_label>` |
  | 完全修飾 ESXi サーバー名 | `<host_prefix><n>.<subdomain_label>.<root_domain>`。ここで、`<n>` は ESXi サーバーのシーケンスです。 最大長は 50 文字です。 |

インスタンスの注文時およびデプロイ時に設定した値は変更しないでください。 変更すると、インスタンスを使用できなくなる可能性があります。 例えば、パブリック・ネットワークがシャットダウンしたり、プロビジョニング中にサーバーや仮想サーバー・インスタンス (VSI) が Vyatta の内側に移動したり、IBM CloudBuilder VSI が停止したり、削除されたりすることがあります。
{:important}

## システム設定
{: #vc_nsx-t_orderinginstance-sys-settings}

vCenter Server インスタンスを注文する際には、以下のシステム設定を指定する必要があります。

### インスタンス名
{: #vc_nsx-t_orderinginstance-inst-name}

インスタンス名は、次の要件を満たす必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* インスタンス名の先頭は英字、末尾は英数字でなければなりません。
* インスタンス名の最大の長さは 10 文字です。
* インスタンス名はアカウント内で固有である必要があります。

### VMware vSphere ライセンス
{: ##vc_nsx-t_orderinginstance-vsphere-license}

デフォルトで vSphere Enterprise Plus 6.7u1 ライセンスが選択されています。

### プライマリーまたはセカンダリー
{: #vc_nsx-t_orderinginstance-primary-secondary}

新規プライマリー・インスタンスを注文するのか、既存のプライマリー・インスタンスのセカンダリー・インスタンスを注文するのかを選択します。

## ライセンス交付の設定
{: #vc_nsx-t_orderinginstance-licensing-settings}

インスタンス内の次の VMware コンポーネントのライセンス・オプションを指定します。
* vCenter Server 6.5
* vSphere Enterprise Plus 6.7
* NSX-T 2.4 (Base、Advanced、または Enterprise エディション)

ビジネス・パートナーであるユーザーの場合、vCenter Server ライセンス (Standard エディション)、vSphere ライセンス (Enterprise Plus エディション)、NSX ライセンスが自動的に含められて購入されます。 しかし、NSX ライセンスのエディションは指定する必要があります。

ビジネス・パートナーでないユーザーの場合、**「購入に含める」**を選択してこれらのコンポーネントに IBM 提供 VMware ライセンスを使用することも、**「自分で提供する」**を選択し、所有するライセンス・キーを入力してライセンス持ち込み (BYOL) を適用することもできます。

### ライセンスに関する注意点
{: #vc_nsx-t_orderinginstance-licensing-notes}

* CPU を 2 つ搭載したサーバー 4 台を使用するため、8 個以上の CPU を使用できるライセンスが必要です。 各 VMware コンポーネントに選択したライセンスは、基本インスタンスと、そのインスタンスに後から追加する ESXi サーバーに適用されます。 ご使用のライセンスが、インフラストラクチャーの今後の容量拡張に対応できることを確認してください。
* 最小のライセンス・エディションが、ユーザー・インターフェースに表示されます。 複数のコンポーネント・エディションがサポートされている場合は、必要なエディションを選択できます。 選択した VMware コンポーネントごとに、指定したライセンス・キーが正しいことを確認してください。
* vSphere の場合は、注文時にライセンス料が発生しますが、そのライセンス料は後でアカウントに返金されます。
* インスタンスのデプロイメントが完了したら、VMware vSphere Web Client を使用して、提供したライセンスを変更できます。
* 自分でライセンスを提供した VMware コンポーネントのサポートは、IBM サポートからではなく、VMware から提供されます。

## ベア・メタル・サーバーの設定
{: #vc_nsx-t_orderinginstance-bare-metal-settings}

ベアメタルの設定は、選択したデータ・センターやベアメタル・サーバーの構成に基づきます。

### データ・センターの場所
{: #vc_nsx-t_orderinginstance-dc-location}

インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。

### Skylake
{: #vc_nsx-t_orderinginstance-skylake}

**「Skylake」**を選択した場合、必要に応じてベアメタル・サーバーの CPU と RAM の組み合わせを選択できます。

表 2. Skylake {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 プロセッサー / 合計 16 コア、2.1 GHz | 128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz | 128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 128 GB、192 GB、384 GB、768 GB、1.5 TB |

### Broadwell
{: #vc_nsx-t_orderinginstance-broadwell}

**「Broadwell」**を選択した場合、必要に応じてベアメタル・サーバーの CPU と RAM の組み合わせを選択できます。

表 3. Broadwell {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| クワッド Intel Xeon E7-4820 v4 / 合計 40 コア、2.0 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
| クワッド Intel Xeon E7-4850 v4 / 合計 64 コア、2.1 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |

### ベア・メタル・サーバーの数
{: #vc_nsx-t_orderinginstance-bare-metal-number}

* 注文するすべてのサーバーが同じ構成になります。
* vSAN ストレージを使用する予定である場合は、4 サーバーから 20 サーバーまで注文できます。
* NFS ストレージを使用する予定である場合は、2 サーバーから 20 サーバーまで注文できます。 ただし、実動ワークロード上、最低 3 サーバーをお勧めします。 詳しくは、[2 ノードの vCenter Server インスタンスの可用性は高いですか?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-) を参照してください。

## ストレージ設定
{: #vc_nsx-t_orderinginstance-storage-settings}

ストレージ設定は、選択したベア・メタル・サーバー構成とストレージ・タイプによって異なります。

デプロイ済みインスタンスの場合、NFS ストレージ共有を既存の NFS クラスターまたは vSAN クラスターに追加できます。 詳しくは、[vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances)の *vCenter Server インスタンスへの NFS ストレージの追加* のセクションを参照してください。
{:note}

### vSAN ストレージ
{: #vc_nsx-t_orderinginstance-vsan-storage}

vSAN は、**「Skylake」**と**「Broadwell」**のベアメタル構成でのみ使用できます。 以下の vSAN オプションを指定します。
* **vSAN 容量ディスクのディスク・タイプとサイズ**: 必要な容量ディスクのオプションを選択します。
* **vSAN 容量ディスクの数**: 追加する容量ディスク数を指定します。
* 容量ディスクを上限の 10 個を超えて追加する場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。 このオプションを指定すると、合計 12 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されます。したがって、このオプションは、より少ない待ち時間とより高い IOPS スループットが求められるワークロードに有用です。

  **「High-Performance Intel Optane」**オプションは、Skylake CPU モデルでのみ使用できます。
  {:note}

* **「Disk Type for vSAN Cache Disks」**および**「Number of vSAN Cache Disks」**の値を確認します。 これらの値は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けたかどうかによって異なります。
* **vSAN License**: **「Include with purchase」**を選択して vSAN コンポーネントで IBM 提供 VMware ライセンスを使用するか、**「I will provide」**を選択し、所有するライセンス・キーを入力してライセンス持ち込み (BYOL) を適用します。

### NFS ストレージ
{: #vc_nsx-t_orderinginstance-nfs-storage}

**「NFS Storage」**を選択する場合は、インスタンスにファイル・レベルの共有ストレージを追加し、すべての共有で同じ設定を使用することも、ファイル共有ごとに別々の構成設定を指定することもできます。 以下の NFS オプションを指定します。

ファイル共有の数は 1 から 32 までの範囲で指定する必要があります。
{:note}

* **Configure shares individually**: ファイル共有ごとに異なる構成設定を指定する場合に選択します。
* **Number of Shares**: どのファイル共有でも同じ構成設定を使用する場合に、追加する NFS 共有ストレージのファイル共有の数を指定します。
* **パフォーマンス (Performance)**: ワークロードの要件に基づいて、1 GB あたりの IOPS (入出力操作数/秒) を選択します。
* **サイズ (GB)**: 共有ストレージのニーズを満たす容量を選択します。
* **共有ストレージの追加 (Add Shared Storage)**: 別々の構成設定を使用するファイル共有を個々に追加するときに選択します。

表 4. NFS パフォーマンス・レベルのオプション

| オプション        | 詳細       |
  |:------------- |:------------- |
  | 0.25 IOPS/GB | このオプションは、使用頻度の低いワークロード用に設計されています。 例えば、データの貯蔵、レガシー・データを保管する大規模データベースのホスト、バックアップとして使用する仮想メモリー・システムの仮想ディスク・イメージなどの用途があります。 |
  | 2 IOPS/GB | このオプションは、最も汎用的なワークロード用に設計されています。 例えば、小規模なデータベースのホスト、Web アプリケーションのバックアップ、ハイパーバイザーの仮想マシン・ディスク・イメージなどの用途があります。 |
  | 4 IOPS/GB | このオプションは、同時に高い割合のデータがアクティブになる高負荷のワークロード用に設計されています。 例えば、トランザクション・データベースなどの用途があります。 |
  | 10 IOPS/GB | このオプションは、分析などの最も要求の厳しいワークロード・タイプ用に設計されています。 例えば、トランザクションの多いデータベースやその他のパフォーマンス重視のデータベースなどの用途があります。 このパフォーマンス・レベルは、ファイル共有あたり最大 4 TB の容量に制限されています。 |

## ネットワーク・インターフェースの設定
{: #vc_nsx-t_orderinginstance-network-interface-settings}

vCenter Server インスタンスを注文する際には、以下のネットワーク・インターフェース設定を指定する必要があります。

### ホスト名接頭部
{: #vc_nsx-t_orderinginstance-host-name-prefix}

ホスト名接頭部は、次の要件を満たす必要があります。
*  英数字とダッシュ (-) の文字だけを使用できます。
*  ホスト名接頭部の先頭と末尾は英数字である必要があります。
*  ホスト名接頭部の最大長は 10 文字です。

### サブドメイン・ラベル
{: #vc_nsx-t_orderinginstance-subdomain-label}

サブドメイン・ラベルは、次の要件を満たす必要があります。
*  英数字とダッシュ (-) の文字だけを使用できます。
*  サブドメイン・ラベルの先頭は英字、末尾は英数字でなければなりません。
*  サブドメイン・ラベルの最大長は 10 文字です。

### ドメイン・ネーム
{: #vc_nsx-t_orderinginstance-domain-name}

ルート・ドメイン・ネームは、次の要件を満たす必要があります。
* ドメイン・ネームは、ピリオド (.) で区切られた 2 つ以上のストリングで構成されていなければなりません。
* 最初の文字列は、英字で始まり英数字で終わらなければなりません。
* 最後の文字列を除き、文字列で使用できるのは、英数字とダッシュ (-) のみです。
* 最後の文字列には、英字しか使用できません。
* 最後の文字列の長さは、2 文字から 24 文字までの範囲でなければなりません。

ホストと VM の完全修飾ドメイン・ネーム (FQDN) の最大長は 50 文字です。 この最大長に対応するドメイン・ネームにする必要があります。
{:note}

### パブリックまたはプライベート・ネットワーク
{: #vc_nsx-t_orderinginstance-public-private-network}

ネットワーク・インターフェース・カード (NIC) の有効化設定は、**「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のどちらを選択したかに基づきます。

### VLAN
{: #vc_nsx-t_orderinginstance-vlans}

ネットワーク設定は、**「新規 VLAN を注文」**と**「既存の VLAN を選択」**のどちらを選択するかによって異なります。

インスタンスの注文には、パブリック VLAN 1 つとプライベート VLAN 2 つが必要です。 2 つのプライベート VLAN は各ベア・メタル・サーバーにトランキングされます。

#### 新規 VLAN を注文
{: #vc_nsx-t_orderinginstance-new-vlans}

新規パブリック VLAN 1 つと新規プライベート VLAN 2 つを注文することを選択します。

#### 既存の VLAN を選択
{: #vc_nsx-t_orderinginstance-existing-vlans}

選択した {{site.data.keyword.CloudDataCent_notm}}によっては、既存のパブリック VLAN とプライベート VLAN を使用できることがあります。

既存のパブリック VLAN とプライベート VLAN を再使用することを選択した場合は、それらの VLAN とサブネットを指定します。
* **パブリック VLAN** は、パブリック・ネットワーク・アクセスに使用されます。
* **プライベート VLAN** は、{{site.data.keyword.cloud_notm}} 内部のデータ・センターとサービスの間の接続に使用されます。
* **セカンダリー・プライベート VLAN** は、vSAN などの VMware 機能に使用されます。
* **プライマリー・サブネット**は、パブリック・ネットワーク・アクセス用に物理ホストに割り当てられます。
* **プライマリー・プライベート・サブネット**は、管理トラフィック用に物理ホストに割り当てられます。

選択した VLAN のファイアウォール構成が管理用データ・トラフィックをブロックしていないことを確認してください。 選択したすべての VLAN が同じポッドに含まれていることも確認してください。 複数のポッドの VLAN に ESXi サーバーをプロビジョンすることはできません。
{:important}

### DNS 構成
{: #vc_nsx-t_orderinginstance-dns-config}

インスタンスのドメイン・ネーム・システム (DNS) 構成を選択します。

* **Active Directory/DNS 用の単一のパブリック Windows VSI**: Microsoft Active Directory (AD) 用の単一の Microsoft Windows Server VSI。ホストと VM が登録されたインスタンスの DNS として機能します。これがデプロイされて参照可能になります。 このオプションは、V1.9 以降のインスタンスではデフォルトでデプロイされます。
* **管理クラスター上の高可用性構成の 2 つの専用 Windows Server VM**: 2 つの Microsoft Windows VM がデプロイされるので、セキュリティーと堅牢性が向上します。

2 つの Microsoft Windows VM を使用するようにインスタンスを構成する場合は、2 つの Microsoft Windows Server 2016 Standard Edition ライセンスを用意する必要があります。
{:important}

各ライセンスは単一の物理サーバーにのみ割り当てられ、最大 2 つの物理プロセッサーをカバーします。 1 つの Standard エディション・ライセンスでは、2 プロセッサーのサーバーで 2 台の仮想化 Microsoft Windows VM を実行できます。 したがって、ライセンスは 2 つ必要になります。2 つの異なるホストに 2 つの Microsoft Windows VM がデプロイされるからです。

VM は 30 日以内に有効にしてください。

Windows Server 2016 ライセンスの注文について詳しくは、[Get started with Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:new_window} を参照してください。

## 注文のサマリー
{: #vc_nsx-t_orderinginstance-order-summary}

選択した構成に基づいて、見積もりコストがすぐに生成され、右側のペインの**「注文の要約」**に表示されます。 **「料金詳細」**をクリックすると、{{site.data.keyword.vmwaresolutions_short}} リソースのコスト・サマリーが記載された PDF 文書を生成できます。

また、**「見積もりに追加」**をクリックして、プロビジョン済みリソースを {{site.data.keyword.cloud_notm}} 見積もりツールに追加することもできます。この操作は、購入を検討している他の {{site.data.keyword.cloud_notm}} リソースと一緒に、選択した {{site.data.keyword.vmwaresolutions_short}}リソースのコストを見積もる場合に役立ちます。

## vCenter Server with NSX-T インスタンスを注文する手順
{: #vc_nsx-t_orderinginstance-procedure}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**をクリックしてから、**「仮想データ・センター」**セクションの**「vCenter サーバー」**をクリックします。
2. **「VMware vCenter Server on IBM Cloud」**ページで、**「vCenter サーバー」**カードをクリックし、**「作成」**をクリックします。
3. **「vCenter サーバー」**ページで、インスタンス名を入力します。
4. インスタンス・タイプを選択します。
   * 環境の単一インスタンスをデプロイするか、マルチサイト・トポロジーの最初のインスタンスをデプロイする場合は、**「プライマリー・インスタンス」**をクリックします。
   * 可用性を向上させる場合は、**「セカンダリー・インスタンス」**をクリックし、環境内の既存の (プライマリー) インスタンスにインスタンスを接続して、以下の手順を実行します。
     1. セカンダリー・インスタンスを接続するプライマリー・インスタンスを選択します。
     2. プライマリー・インスタンスが V2.8 以降である場合は、プライマリー・インスタンスの vCenter Server 管理者パスワードを入力します。
     3. プライマリー・インスタンスが V2.5、2.6、または 2.7 である場合は、プライマリー・インスタンスの PSC 管理者パスワードを入力します。
     4. プライマリー・インスタンスが V2.4 以前である場合は、プライマリー・インスタンスの PSC 管理者パスワードの事前入力値が正しいことを確認します。
6. インスタンスのコンポーネントのライセンス設定を行います。
   *  IBM 提供のライセンスを使用するには、**「購入に含める」**を選択し、必要に応じてライセンス・エディションを選択します。
   *  所有しているライセンスを使用するには、**「自分で提供する」**を選択し、ライセンス・キーを入力します。
7. ベア・メタル・サーバーの設定を次の手順で実行します。
    1. インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。
    2. ベア・メタル・サーバー構成を選択し、CPU モデルと RAM サイズを指定します。
    3. {{site.data.keyword.baremetal_short}}の数を指定します。 vSAN をストレージ・ソリューションとして使用する場合は、4 台以上の{{site.data.keyword.baremetal_short}}が必要です。  
8. ストレージ構成を次の手順で実行します。
  * **「vSAN Storage」**を選択した場合は、容量ディスクおよびキャッシュ・ディスクのディスク・タイプ、ディスク数、vSAN ライセンス・エディションを指定します。 さらにストレージが必要な場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。
  * **「NFS ストレージ」**を選択し、すべてのファイル共有に同じ設定を構成して追加する場合は、**「共有の数」**、**「パフォーマンス」**、**「サイズ (GB)」**を指定します。
  * **「NFS Storage」**を選択してファイル共有を個別に追加して構成する場合は、**「Configure shares individually」**を選択します。 その後、ファイル共有ごとに、**「共有ストレージの追加」**ラベルの横にある**「+」**アイコンをクリックして、**「パフォーマンス」**と**「サイズ (GB)」**を選択します。 少なくとも 1 つのファイル共有を選択する必要があります。
9. ネットワーク・インターフェースの設定を行います。
   1. プロビジョンされるインスタンスのホスト名接頭部、サブドメイン・ラベル、ルート・ドメイン・ネームを入力します。 セカンダリー・インスタンスの場合、ドメイン・ネームは自動的に入力されます。
   2. **「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のいずれかのネットワーク設定を選択します。
   3. VLAN 設定を選択します。
      * 新規のパブリック VLAN とプライベート VLAN を注文する場合は、**「新規 VLAN を注文」**をクリックします。
      * 既存のパブリック VLAN とプライベート VLAN を使用できる場合に再利用するには、**「既存の VLAN を選択」**をクリックし、それらの VLAN とサブネットを指定します。
   4. DNS 構成を指定します。

11. **「発注要約」**ペインで、インスタンス構成を確認してから注文を実行します。
   1. インスタンスの設定を確認します。
   2. インスタンスの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、インスタンスを注文する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

## vCenter Server with NSX-T インスタンスを注文した結果
{: #vc_nsx-t_orderinginstance-results}

* インスタンスのデプロイメントが自動的に開始され、注文が処理中であることを示す確認を受け取ります。 「インスタンスの詳細」の**「デプロイメント履歴 (Deployment History)」**セクションを表示すると、注意すべき問題を含め、デプロイメント状況を確認できます。
* インスタンスが正常にデプロイされると、[vCenter Server with NSX-T インスタンスの技術仕様](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_overview#vc_nsx-t_overview-specs)に記述されているコンポーネントが VMware 仮想プラットフォームにインストールされます。 注文した ESXi サーバーは、デフォルトでは **cluster1** としてグループ化されます。
* インスタンスが使用可能になると、インスタンスの状況が**「使用可能」**に変わり、E メールで通知されます。
* セカンダリー・インスタンスを注文した場合は、セカンダリー・インスタンスの注文が完了した後に、(セカンダリー・インスタンスにリンクされた) プライマリー・インスタンスの VMware vSphere Web Client が再始動されることがあります。

## 次に行うこと
{: #vc_nsx-t_orderinginstance-next}

注文した vCenter Server with NSX-T インスタンスを表示および管理します。 インスタンスの表示について詳しくは、[vCenter Server インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)を参照してください。

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
{: #vc_nsx-t_orderinginstance-related}

* [{{site.data.keyword.cloud_notm}} アカウントの登録](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts)
* [vCenter Server インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [vCenter Server インスタンスのマルチサイト構成](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)
* [vCenter Server with NSX-T インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [vCenter Server with NSX-T インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)
* [vCenter Server with NSX-T インスタンスの削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
