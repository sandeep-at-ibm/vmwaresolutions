---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: vCenter Server order instance, order vCenter Server, order vCenter Server instance

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server インスタンスの注文
{: #vc_orderinginstance}

ワークロードのニーズに合わせて最適化できる、柔軟でカスタマイズ可能な VMware 仮想化プラットフォームをデプロイするには、VMware vCenter Server インスタンスを注文します。 初回注文時に、災害復旧のための [Zerto on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) などのサービスも追加できます。

## 要件
{: #vc_orderinginstance-req}

以下の作業を完了していることを確認してください。
* **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定の管理](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)を参照してください。
* [vCenter Server インスタンスの要件と計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)の情報を確認する。
* インスタンス名とドメイン・ネームの形式を確認する。 ドメイン・ネームとサブドメイン・ラベルは、インスタンスのユーザー名とサーバー名の生成に使用されます。

| 名前        | 値の形式      |
|:------------|:------------ |
| ドメイン・ネーム | `<root_domain>` |  
| vCenter Server ログイン・ユーザー名 | `<user_id>@<root_domain>` (Microsoft Active Directory ユーザー) または `administrator@vsphere.local` |
| vCenter Server (PSC が組み込まれたもの) の FQDN | `<instance_name>-vc.<root_domain>`。最大長は 50 文字です。 |
| シングル・サインオン (SSO) サイト名 | `<subdomain_label>` |
| 完全修飾 ESXi サーバー名 | `<data_center>-<host_prefix><n>.<subdomain_label>.<root_domain>`。ここで、`n` は ESXi サーバーのシーケンスです。 最大長は 50 文字です。 |
{: caption="表 1. インスタンス名とドメイン・ネームの値の形式" caption-side="top"}

インスタンスの注文時およびデプロイ時に設定した値は変更しないでください。 変更すると、インスタンスを使用できなくなる可能性があります。 例えば、パブリック・ネットワークがシャットダウンしたり、プロビジョニング中にサーバーや仮想サーバー・インスタンス (VSI) が Vyatta の内側に移動したり、IBM CloudBuilder VSI が停止したり、削除されたりすることがあります。
{:important}

## システム設定
{: #vc_orderinginstance-sys-settings}

vCenter Server インスタンスを注文する際には、以下のシステム設定を指定する必要があります。

### インスタンス名
{: #vc_orderinginstance-inst-name}

インスタンス名は、次の要件を満たす必要があります。
* 英字の小文字、数字、およびダッシュ (-) の文字だけを使用できます。
* インスタンス名は小文字の英字で始まらなければなりません。
* インスタンス名は小文字の英字または数字で終わらなければなりません。
* インスタンス名の最大の長さは 10 文字です。
* インスタンス名はアカウント内で固有である必要があります。

### 初期クラスター名
{: #vc_orderinginstance-cluster-name}

初期のクラスター名は、以下の要件を満たしている必要があります。
* 英字の小文字、数字、およびダッシュ (-) の文字だけを使用できます。
* クラスター名は小文字の英字で始まらなければなりません。
* クラスター名は小文字の英字または数字で終わらなければなりません。
* クラスター名の最大の長さは 30 文字です。
* クラスター名は、vCenter Server インスタンス内で固有のものでなければなりません。

### VMware vSphere のバージョン
{: #vc_orderinginstance-vsphere-license}

vSphere Enterprise Plus 6.7u2 と vSphere Enterprise Plus 6.5u2 のどちらを注文するかを選択します。

vSphere Enterprise Plus 6.7u2 は、Skylake、Cascade、および Broadwell {{site.data.keyword.cloud_notm}} の{{site.data.keyword.baremetal_short}}でのみ使用できます。
{:note}

### プライマリーまたはセカンダリー
{: #vc_orderinginstance-primary-secondary}

新規プライマリー・インスタンスを注文するのか、既存のプライマリー・インスタンスのセカンダリー・インスタンスを注文するのかを選択します。

## ライセンス交付の設定
{: #vc_orderinginstance-licensing-settings}

インスタンス内の次の VMware コンポーネントのライセンス・オプションを指定します。
* vCenter Server 6.5
* vSphere Enterprise Plus 6.5 または 6.7
* NSX Service Providers 6.4 (Base、Advanced、または Enterprise エディション)

VMware HCX on {{site.data.keyword.cloud_notm}} サービスには、NSX Advanced エディションまたは NSX Enterprise エディションのライセンスが必要です。
{:note}

ビジネス・パートナーであるユーザーの場合、vCenter Server ライセンス (Standard エディション)、vSphere ライセンス (Enterprise Plus エディション)、NSX ライセンスが自動的に含められて購入されます。 しかし、NSX ライセンスのエディションは指定する必要があります。

ビジネス・パートナーでないユーザーの場合は、**「購入に含める (Include with purchase)」**を選択することにより、IBM 提供の VMware ライセンスをこれらのコンポーネントに対して使用するか、**「自分で提供する (I will provide)」**を選択して所有するライセンス・キーを入力することにより、ライセンス持ち込み (BYOL) を適用することができます。

### ライセンスに関する注意点
{: #vc_orderinginstance-licensing-notes}

* CPU を 2 つ搭載したサーバー 4 台を使用するため、8 個以上の CPU を使用できるライセンスが必要です。 各 VMware コンポーネントに選択したライセンスは、基本インスタンスと、そのインスタンスに後から追加する ESXi サーバーに適用されます。 ご使用のライセンスが、インフラストラクチャーの今後の容量拡張に対応できることを確認してください。
* 最小のライセンス・エディションが、ユーザー・インターフェースに表示されます。 複数のコンポーネント・エディションがサポートされている場合は、必要なエディションを選択できます。 選択した VMware コンポーネントごとに、指定したライセンス・キーが正しいことを確認してください。
* vSphere の場合は、注文時にライセンス料が発生しますが、そのライセンス料は後でアカウントに返金されます。
* インスタンスのデプロイメントが完了したら、VMware vSphere Web Client を使用して、提供したライセンスを変更できます。
* 自分でライセンスを提供した VMware コンポーネントのサポートは、IBM サポートからではなく、VMware から提供されます。

## ベア・メタル・サーバーの設定
{: #vc_orderinginstance-bare-metal-settings}

ベアメタルの設定は、選択したデータ・センターやベアメタル・サーバーの構成に基づきます。

### データ・センターの場所
{: #vc_orderinginstance-dc-location}

インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。

### Skylake
{: #vc_orderinginstance-skylake}

**「Skylake」**を選択した場合、必要に応じてベアメタル・サーバーの CPU と RAM の組み合わせを選択できます。

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 プロセッサー / 合計 16 コア、2.1 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
{: caption="表 2. Skylake {{site.data.keyword.baremetal_short}}のオプション" caption-side="top"}

### Cascade
{: #vc_orderinginstance-cascade}

**「Cascade」**設定の場合、**「CPU モデル」**と**「RAM」**には複数のオプションがあります。

Cascade {{site.data.keyword.baremetal_short}} は、VMware vSphere Enterprise Plus 6.7 U2 インスタンスでのみ使用できます。
{:note}

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| Dual Intel Xeon Gold 4210 Processor / 合計 20 コア、2.3 GHz | 64 GB、96 GB、128 GB、192 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5218 Processor / 合計 32 コア、2.3 GHz | 64 GB、96 GB、128 GB、192 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6248 Processor / 合計 40 コア、2.5 GHz | 64 GB、96 GB、128 GB、192 GB、768 GB、1.5 TB |
{: caption="表 3. Cascade {{site.data.keyword.baremetal_short}}のオプション" caption-side="top"}


### SAP 認定
{: #vc_orderinginstance-sap}

**「SAP 認定」**を選択した場合、CPU や RAM の設定は変更できません。

要件に基づいて、以下のベア・メタル・サーバー構成を選択します。
  * Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 192 GB RAM
  * Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 384 GB RAM
  * Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 768 GB RAM
  * Dual Intel Xeon E5-2690 v4 プロセッサー / 合計 28 コア、2.6 GHz / 512 GB RAM
  * Quad Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.2 GHz / 1024 GB RAM
  * Quad Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.2 GHz / 2048 GB RAM
  * Quad Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.2 GHz / 4096 GB RAM

### Broadwell
{: #vc_orderinginstance-broadwell}

**「Broadwell」**を選択した場合、必要に応じてベアメタル・サーバーの CPU と RAM の組み合わせを選択できます。

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| クワッド Intel Xeon E7-4820 v4 / 合計 40 コア、2.0 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
| クワッド Intel Xeon E7-4850 v4 / 合計 64 コア、2.1 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
{: caption="表 4. Broadwell {{site.data.keyword.baremetal_short}}のオプション" caption-side="top"}

### ベア・メタル・サーバーの数
{: #vc_orderinginstance-bare-metal-number}

* 注文するすべてのサーバーが同じ構成になります。
* vSAN ストレージを使用する予定である場合は、4 サーバーから 20 サーバーまで注文できます。
* NFS ストレージを使用する予定である場合は、2 サーバーから 20 サーバーまで注文できます。 ただし、実動ワークロード上、最低 3 サーバーをお勧めします。 詳しくは、[2 ノードの vCenter Server インスタンスの可用性は高いですか?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-) を参照してください。

## ストレージ設定
{: #vc_orderinginstance-storage-settings}

ストレージ設定は、選択したベア・メタル・サーバー構成とストレージ・タイプによって異なります。

インスタンス V2.8 以降の場合、NFS ストレージ共有を既存の NFS または vSAN クラスターに追加できます。 詳しくは、[vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances)の *vCenter Server インスタンスへの NFS ストレージの追加* のセクションを参照してください。
{:note}

### vSAN ストレージ
{: #vc_orderinginstance-vsan-storage}

vSAN は、**「Skylake」**、**「Cascade」**、および**「Broadwell」**のベアメタル構成でのみ使用できます。 以下の vSAN オプションを指定します。
* **vSAN 容量ディスクのディスク・タイプとサイズ**: 必要な容量ディスクのオプションを選択します。
* **vSAN 容量ディスクの数**: 追加する容量ディスク数を指定します。
* 容量を上限の 10 ディスクを超えて追加する場合は、**「High-Performance with Intel Optane」**ボックスにチェック・マークを付けます。 このオプションを指定すると、合計 12 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されます。したがって、このオプションは、より少ない待ち時間とより高い IOPS スループットが求められるワークロードに有用です。

  **「High-Performance with Intel Optane」**オプションは、Skylake および Cascade の CPU モデルでのみ使用できます。
  {:note}

* **「Disk Type for vSAN Cache Disks」**および**「Number of vSAN Cache Disks」**の値を確認します。 これらの値は、**「High-Performance with Intel Optane」**ボックスにチェック・マークを付けたかどうかによって異なります。
* **vSAN License**: **「Include with purchase」**を選択して vSAN コンポーネントで IBM 提供 VMware ライセンスを使用するか、**「I will provide」**を選択し、所有するライセンス・キーを入力してライセンス持ち込み (BYOL) を適用します。

### NFS ストレージ
{: #vc_orderinginstance-nfs-storage}

**「NFS Storage」**を選択する場合は、インスタンスにファイル・レベルの共有ストレージを追加し、すべての共有で同じ設定を使用することも、ファイル共有ごとに別々の構成設定を指定することもできます。 以下の NFS オプションを指定します。

ファイル共有の数は 1 から 32 までの範囲で指定する必要があります。
{:note}

* **Configure shares individually**: ファイル共有ごとに異なる構成設定を指定する場合に選択します。
* **Number of Shares**: どのファイル共有でも同じ構成設定を使用する場合に、追加する NFS 共有ストレージのファイル共有の数を指定します。
* **パフォーマンス (Performance)**: ワークロードの要件に基づいて、1 GB あたりの IOPS (入出力操作数/秒) を選択します。
* **サイズ (GB)**: 共有ストレージのニーズを満たす容量を選択します。
* **共有ストレージの追加 (Add Shared Storage)**: 別々の構成設定を使用するファイル共有を個々に追加するときに選択します。

必要に応じて、パフォーマンス・レベルのオプションを選択します。

| オプション        | 詳細       |
|:------------- |:------------- |
| 0.25 IOPS/GB | このオプションは、使用頻度の低いワークロード用に設計されています。 例えば、データの貯蔵、レガシー・データを保管する大規模データベースのホスト、バックアップとして使用する仮想メモリー・システムの仮想ディスク・イメージなどの用途があります。 |
| 2 IOPS/GB | このオプションは、最も汎用的なワークロード用に設計されています。 例えば、小規模なデータベースのホスト、Web アプリケーションのバックアップ、ハイパーバイザーの仮想マシン・ディスク・イメージなどの用途があります。 |
| 4 IOPS/GB | このオプションは、同時に高い割合のデータがアクティブになる高負荷のワークロード用に設計されています。 例えば、トランザクション・データベースなどの用途があります。 |
| 10 IOPS/GB | このオプションは、分析などの最も要求の厳しいワークロード・タイプ用に設計されています。 例えば、トランザクションの多いデータベースやその他のパフォーマンス重視のデータベースなどの用途があります。 このパフォーマンス・レベルは、ファイル共有あたり最大 4 TB の容量に制限されています。 |
{: caption="表 5. NFS パフォーマンス・レベルのオプション" caption-side="top"}

### ローカル・ディスク
{: #vc_orderinginstance-local-disks}

ローカル・ディスク・オプションは、**SAP 認定**のクワッド Intel Xeon E7-8890 v4 プロセッサーのベアメタル構成でのみ使用できます。 以下のオプションを指定します。
* **ディスク数 (Disk Count)**: 追加するディスクの数を選択します。
* **ディスク・タイプ**: 必要なディスク・タイプのオプションを選択します。

## ネットワーク・インターフェースの設定
{: #vc_orderinginstance-network-interface-settings}

vCenter Server インスタンスを注文する際には、以下のネットワーク・インターフェース設定を指定する必要があります。

### ホスト名接頭部
{: #vc_orderinginstance-host-name-prefix}

ホスト名接頭部は、次の要件を満たす必要があります。
* 英字の小文字、数字、およびダッシュ (-) の文字だけを使用できます。
* ホスト名接頭部は小文字の英字で始まらなければなりません。
* ホスト名接頭部は小文字の英字または数字で終わらなければなりません。
* ホスト名接頭部の最大長は 10 文字です。

### サブドメイン・ラベル
{: #vc_orderinginstance-subdomain-label}

サブドメイン・ラベルは、次の要件を満たす必要があります。
* 英字の小文字、数字、およびダッシュ (-) の文字だけを使用できます。
* サブドメイン・ラベルは小文字の英字で始まらなければなりません。
* サブドメイン・ラベルは小文字の英字または数字で終わらなければなりません。
* サブドメイン・ラベルの最大長は 10 文字です。
* サブドメイン・ラベルは、マルチサイト構成のすべてのインスタンス内で固有でなければなりません。

### ドメイン・ネーム
{: #vc_orderinginstance-domain-name}

ルート・ドメイン・ネームは、次の要件を満たす必要があります。
* ドメイン・ネームは、ピリオド (.) で区切られた 2 つ以上のストリングで構成されていなければなりません。
* 最初の文字列は小文字の英字で始まらなければなりません。
* 最初の文字列は小文字の英字または数字で終わらなければなりません。
* 最後の文字列を除き、文字列で使用できるのは、英小文字、数字、およびダッシュ (-) のみです。
* 最後の文字列には、英字の小文字しか使用できません。
* 最後の文字列の長さは、2 文字から 24 文字までの範囲でなければなりません。

ホストと VM の完全修飾ドメイン・ネーム (FQDN) の最大長は 50 文字です。 この最大長に対応するドメイン・ネームにする必要があります。
{:note}

### パブリックまたはプライベート・ネットワーク
{: #vc_orderinginstance-public-private-network}

ネットワーク・インターフェース・カード (NIC) の有効化設定は、**「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のどちらを選択したかに基づきます。

**「プライベート・ネットワークのみ」**オプションを選択した場合は、以下のようになります。
* VMware NSX Edge Services Gateway (ESG) は (管理サービスの ESG もユーザー管理の ESG も) プロビジョンされません。
* パブリック NIC を必要とする以下のアドオン・サービスは使用不可になります。
  * F5 on {{site.data.keyword.cloud_notm}}
  * Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
  * Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### VLAN
{: #vc_orderinginstance-vlans}

ネットワーク設定は、**「新規 VLAN を注文」**と**「既存の VLAN を選択」**のどちらを選択するかによって異なります。

インスタンスの注文には、パブリック VLAN 1 つとプライベート VLAN 2 つが必要です。 2 つのプライベート VLAN は各ベア・メタル・サーバーにトランキングされます。

#### 新規 VLAN を注文
{: #vc_orderinginstance-new-vlans}

新規パブリック VLAN 1 つと新規プライベート VLAN 2 つを注文することを選択します。

#### 既存の VLAN を選択
{: #vc_orderinginstance-existing-vlans}

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
{: #vc_orderinginstance-dns-config}

インスタンスのドメイン・ネーム・システム (DNS) 構成を選択します。

* **Active Directory/DNS 用の単一のパブリック Windows VSI**: Microsoft Active Directory (AD) 用の単一の Microsoft Windows Server VSI。ホストと VM が登録されたインスタンスの DNS として機能します。これがデプロイされて参照可能になります。 このオプションは、V1.9 以降のインスタンスではデフォルトでデプロイされます。
* **管理クラスター上の高可用性構成の 2 つの専用 Windows Server VM**: 2 つの Microsoft Windows VM がデプロイされるので、セキュリティーと堅牢性が向上します。

2 つの Microsoft Windows VM を使用するようにインスタンスを構成する場合は、2 つの Microsoft Windows Server 2016 Standard Edition ライセンスを用意する必要があります。
{:important}

各ライセンスは単一の物理サーバーにのみ割り当てられ、最大 2 つの物理プロセッサーをカバーします。 1 つの Standard エディション・ライセンスでは、2 プロセッサーのサーバーで 2 台の仮想化 Microsoft Windows VM を実行できます。 したがって、ライセンスは 2 つ必要になります。2 つの異なるホストに 2 つの Microsoft Windows VM がデプロイされるからです。

VM は 30 日以内に有効にしてください。

Windows Server 2016 ライセンスの注文について詳しくは、[Get started with Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:external} を参照してください。

## サービスの設定
{: #vc_orderinginstance-addon-services}

vCenter Server インスタンスを注文するときには、アドオン・サービスを注文することもできます。 サービスについて詳しくは、[vCenter Server インスタンスで使用可能なサービス](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices#available-services-for-vcenter-server-instances)を参照してください。

VMware HCX on {{site.data.keyword.cloud_notm}} サービスを注文する際は、12 カ月間のコミットメントが必要です。{:note}

## 注文のサマリー
{: #vc_orderinginstance-order-summary}

選択したインスタンス構成とアドオン・サービス構成に基づいて、見積もりコストがすぐに生成され、右側の**「発注要約」**ペインに表示されます。 **「料金詳細」**をクリックすると、{{site.data.keyword.vmwaresolutions_short}} リソースのコスト・サマリーが記載された PDF 文書を生成できます。

また、**「見積もりに追加」**をクリックして、プロビジョン済みリソースを {{site.data.keyword.cloud_notm}} 見積もりツールに追加することもできます。 この操作は、購入を検討している他の {{site.data.keyword.cloud_notm}} リソースと一緒に、選択した {{site.data.keyword.vmwaresolutions_short}}リソースのコストを見積もる場合に役立ちます。

## vCenter Server インスタンスを注文する手順
{: #vc_orderinginstance-procedure}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware 仮想データ・センター」**セクションの**「VMware vCenter Server on IBM Cloud」**カードをクリックします。
2. **「VMware vCenter Server on IBM Cloud」**ページで、**「vCenter サーバー」**カードをクリックし、**「作成」**をクリックします。
3. **「vCenter サーバー」**ページで、インスタンス名を入力します。
4. vSphere バージョンを選択します。
5. インスタンス・タイプを選択します。
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
    2. ベア・メタル・サーバー構成を選択します。
       * **「Skylake」**、**「Cascade」**、または**「Broadwell」**を選択した場合は、CPU モデルと RAM サイズを指定します。
       * **「SAP 認定」**を選択した場合は、事前設定構成のいずれかを選択します。
    3. {{site.data.keyword.baremetal_short}}の数を指定します。 vSAN ストレージを使用する予定である場合は、最低 4 つの{{site.data.keyword.baremetal_short}}が必要です。  
8. ストレージ構成を次の手順で実行します。
  * **「vSAN Storage」**を選択した場合は、容量ディスクおよびキャッシュ・ディスクのディスク・タイプ、ディスク数、vSAN ライセンス・エディションを指定します。 さらにストレージが必要な場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。
  * **「NFS ストレージ」**を選択し、すべてのファイル共有に同じ設定を構成して追加する場合は、**「共有の数」**、**「パフォーマンス」**、**「サイズ (GB)」**を指定します。
  * **「NFS Storage」**を選択してファイル共有を個別に追加して構成する場合は、**「Configure shares individually」**を選択します。 その後、ファイル共有ごとに、**「共有ストレージの追加」**ラベルの横にある**「+」**アイコンをクリックして、**「パフォーマンス」**と**「サイズ (GB)」**を選択します。 少なくとも 1 つのファイル共有を選択する必要があります。
  * **「ローカル・ディスク」**を選択した場合は、ディスク数とディスク・タイプを指定します。
9. ネットワーク・インターフェースの設定を行います。
   1. プロビジョンされるインスタンスのホスト名接頭部、サブドメイン・ラベル、ルート・ドメイン・ネームを入力します。 セカンダリー・インスタンスの場合、ドメイン・ネームは自動的に入力されます。
   2. **「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のいずれかのネットワーク設定を選択します。
   3. VLAN 設定を選択します。
      * 新規のパブリック VLAN とプライベート VLAN を注文する場合は、**「新規 VLAN を注文」**をクリックします。
      * 既存のパブリック VLAN とプライベート VLAN を使用できる場合に再利用するには、**「既存の VLAN を選択」**をクリックし、それらの VLAN とサブネットを指定します。
   4. DNS 構成を指定します。

10. インスタンスにデプロイするアドオン・サービスを、対応するサービス・カードをクリックして選択します。 サービスに構成が必要な場合は、サービス固有の設定を入力し、カードの**「サービスの追加」**をクリックします。
サービスの設定方法について詳しくは、対応するサービス注文トピックを参照してください。

11. **「発注要約」**ペインで、インスタンス構成を確認してから注文を実行します。
   1. インスタンスの設定を確認します。
   2. インスタンスの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、インスタンスを注文する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

## vCenter Server インスタンスを注文した結果
{: #vc_orderinginstance-results}

* インスタンスのデプロイメントが自動的に開始され、注文が処理中であることを示す確認を受け取ります。 「インスタンスの詳細」の**「デプロイメント履歴 (Deployment History)」**セクションを表示すると、注意すべき問題を含め、デプロイメント状況を確認できます。
* インスタンスが正常にデプロイされると、[vCenter Server インスタンスの技術仕様](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs)に記述されているコンポーネントが VMware 仮想プラットフォームにインストールされます。 アドオン・サービスを注文した場合は、注文の完了後にサービスのデプロイメントが開始されます。
* インスタンスが使用可能になると、インスタンスの状況が**「使用可能」**に変わり、E メールで通知されます。
* セカンダリー・インスタンスを注文した場合は、セカンダリー・インスタンスの注文が完了した後に、(セカンダリー・インスタンスにリンクされた) プライマリー・インスタンスの VMware vSphere Web Client が再始動されることがあります。

## 次に行うこと
{: #vc_orderinginstance-next}

注文した vCenter Server インスタンスを表示および管理します。

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
{: #vc_orderinginstance-related}

* [{{site.data.keyword.cloud_notm}} アカウントの登録](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts)
* [vCenter Server インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [vCenter Server インスタンスのマルチサイト構成](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)
* [vCenter Server インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)
* [vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [vCenter Server インスタンスの削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance)
