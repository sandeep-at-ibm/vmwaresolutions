---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-18"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server インスタンスのクラスターの追加、表示、削除
{: #adding-and-viewing-clusters-for-vcenter-server-instances}

インスタンスの注文時に構成した ESXi サーバーは、デフォルトでは **cluster1** としてグループ化されます。

VMware vCenter Server インスタンスに独自のクラスターを追加して、コンピュート能力やストレージ容量を拡張できます。 クラスター内で ESXi サーバーを管理すると、リソース割り振りを改善したり高可用性を実現したりできます。 不要になった場合は、追加したクラスターをインスタンスから削除します。

クラスターの削除機能は、V2.3 以降でデプロイ (または V2.3 以降にアップグレード) されたインスタンスでのみ利用できます。
{:note}

## vCenter Server インスタンスへのクラスターの追加
{: #vc_addingviewingclusters-adding}

インスタンスに追加できるクラスターの数は、インスタンスのバージョンに応じて以下のように異なります。
* V2.5 以降でデプロイ (または V2.5 以降にアップグレード) されたインスタンスの場合は、追加できるクラスター数の上限は、クラスター、ホスト、および VM の数によって決まります。 VMware のサイズ設定についてのガイドラインおよびデプロイに応じた上限を守る必要があります。
* V2.2 以降でデプロイ (または V2.2 以降にアップグレード) されたインスタンスの場合、最大 10 個のクラスターを追加できます。
* V2.1 以前でデプロイされたインスタンスの場合、最大 5 個のクラスターを追加できます。

上限について詳しくは、[VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window} を参照してください。

### システム設定
{: #vc_addingviewingclusters-adding-sys-settings}

vCenter Server インスタンスにクラスターを追加するときには、以下の設定を指定する必要があります。

#### クラスター名
{: #vc_addingviewingclusters-adding-cluster-name}

クラスター名は、以下の要件を満たしている必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* クラスター名の先頭と末尾は、英数字でなければなりません。
* 最大文字数は 30 です。
* クラスター名は、vCenter Server インスタンス内で固有のものでなければなりません。

#### データ・センターの場所
{: #vc_addingviewingclusters-adding-dc-location}

クラスターの {{site.data.keyword.CloudDataCent}}の場所はデフォルトで、vCenter Server インスタンスの {{site.data.keyword.CloudDataCent_notm}}に設定されます。 デプロイ済みのインスタンスとは異なる {{site.data.keyword.CloudDataCent_notm}}にクラスターをデプロイできますが、それら 2 カ所の {{site.data.keyword.CloudDataCents_notm}}間のネットワーク待ち時間が、150 ms 未満になるようにしてください。 ネットワーク待ち時間を確認するには、[SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/) などのツールを使用できます。

別の {{site.data.keyword.CloudDataCent_notm}}または {{site.data.keyword.cloud_notm}} インフラストラクチャー・ポッドにクラスターをデプロイする場合は、注文した{{site.data.keyword.baremetal_short}}で使用するために 3 つの追加の VLAN を注文します。

### ベア・メタル・サーバーの設定
{: #vc_addingviewingclusters-bare-metal-settings}

**「Skylake」**、**「SAP 認定」**、または**「Broadwell」**のいずれかを選択できます。

#### Skylake
{: #vc_addingviewingclusters-adding-skylake}

**「Skylake」**設定の場合、**「CPU モデル」**と**「RAM」**には複数のオプションがあります。 利用できるオプションは、インスタンスを最初にデプロイしたバージョンによって異なる場合があります。

表 1. Skylake {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 プロセッサー / 合計 16 コア、2.1 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

#### SAP 認定
{: #vc_addingviewingclusters-adding-sap}

**「SAP 認定」**を選択した場合、CPU や RAM の設定は変更できません。

要件に基づいて、以下のベア・メタル・サーバー構成を選択します。
* Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 192 GB RAM
* Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 384 GB RAM
* Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 768 GB RAM
* Dual Intel Xeon E5-2690 v4 プロセッサー / 合計 28 コア、2.6 GHz / 512 GB RAM
* Quad Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.2 GHz / 1024 GB RAM
* Quad Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.2 GHz / 2048 GB RAM
* Quad Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.2 GHz / 4096 GB RAM

#### Broadwell
{: #vc_addingviewingclusters-adding-broadwell}

**「Broadwell」**設定の場合、**「CPU モデル」**と**「RAM」**には複数のオプションがあります。 利用できるオプションは、インスタンスを最初にデプロイしたバージョンによって異なる場合があります。

表 2. Broadwell {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| デュアル Intel Xeon E5-2620 v4 / 合計 16 コア、2.1 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2650 v4 / 合計 24 コア、2.2 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2690 v4 / 合計 28 コア、2.6 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| クワッド Intel Xeon E7-4820 v4 / 合計 40 コア、1.9 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
| クワッド Intel Xeon E7-4850 v4 / 合計 64 コア、2.2 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |

#### ベア・メタル・サーバーの数
{: #vc_addingviewingclusters-adding-bare-metal-number}

クラスターには 2 台以上の{{site.data.keyword.baremetal_short}}が必要です。

V2.1 以降にデプロイされた vCenter Server インスタンスの場合、1 つのクラスターに最大 59 台の{{site.data.keyword.baremetal_short}}を追加できます。 一度に 1 台から 59 台の ESXi サーバーを追加できます。

V2.0 以前にデプロイされた vCenter Server インスタンスの場合、1 つのクラスターに最大 32 台の{{site.data.keyword.baremetal_short}}を追加できます。 **Skylake**、**SAP 認定**、および **Broadwell** のベア・メタル・サーバー構成に対して、一度に 1 台から 20 台の ESXi サーバーを追加できます。

デプロイメント後に、最大 4 つのクラスターを追加で作成できます。 **「Skylake」**または**「Broadwell」**のベアメタル・サーバー構成と VMware vSAN ストレージを選択した場合は、初期クラスターとデプロイメント後のクラスターの両方に 4 つのサーバーが必要です。

### ストレージ設定
{: #vc_addingviewingclusters-adding-storage-settings}

ストレージ設定は、選択したベア・メタル・サーバー構成とストレージ・タイプによって異なります。

#### vSAN ストレージ
{: #vc_addingviewingclusters-adding-vsan-storage}

以下の vSAN オプションを指定します。
* **vSAN 容量ディスクのディスク・タイプとサイズ**: 必要な容量ディスクのオプションを選択します。
* **vSAN 容量ディスクの数**: 追加する容量ディスク数を指定します。
* 容量ディスクを上限の 8 個を超えて追加する場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。 このオプションでは、合計 10 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されますので、より少ない待ち時間とより高い IOPS スループットが求められるワークロードを扱うときに役立ちます。

  **High-Performance Intel Optane** オプションは、Skylake の CPU モデルの Dual Intel Xeon Gold 5120 および Dual Intel Xeon Gold 6140 でのみ使用できます。
  {:note}

* **「Disk Type for vSAN Cache Disks」**および**「Number of vSAN Cache Disks」**の値を確認します。 これらの値は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けたかどうかによって異なります。
* **vSAN License**: **「Include with purchase」**を選択して vSAN コンポーネントで IBM 提供 VMware ライセンスを使用するか、**「I will provide」**を選択し、所有するライセンス・キーを入力してライセンス持ち込み (BYOL) を適用します。

初期クラスターが vSAN クラスターであった場合、追加の vSAN クラスターは同じ vSAN ライセンスを使用し、初期クラスターと同じ構成になります。 インスタンス内のいずれかのクラスター (初期または追加) に対し、vSAN を選択してデプロイした場合も同様になります。 初回は、vSAN ライセンス (BYOL または購入) とエディションを入力するように求められます。 次回に新規クラスター用に vSAN を選択するときには、初回に選択したライセンスが再使用されます。

#### NFS ストレージ
{: #vc_addingviewingclusters-adding-nfs-storage}

**「NFS Storage」**を選択する場合は、インスタンスにファイル・レベルの共有ストレージを追加し、すべての共有で同じ設定を使用することも、ファイル共有ごとに別々の構成設定を指定することもできます。 以下の NFS オプションを指定します。

ファイル共有の数は 1 から 32 までの範囲で指定する必要があります。
{:note}

* **Configure shares individually**: ファイル共有ごとに異なる構成設定を指定する場合に選択します。
* **Number of Shares**: どのファイル共有でも同じ構成設定を使用する場合に、追加する NFS 共有ストレージのファイル共有の数を指定します。
* **サイズ**: 共有ストレージのニーズを満たす容量を選択します。
* **パフォーマンス (Performance)**: ワークロードの要件に基づいて、1 GB あたりの IOPS (入出力操作数/秒) を選択します。
* **ADD NFS**: 別々の構成設定を使用する個々のファイル共有を追加する場合に選択します。

表 3. NFS パフォーマンス・レベルのオプション

| オプション        | 詳細       |
  |:------------- |:------------- |
  | 0.25 IOPS/GB | このオプションは、使用頻度の低いワークロード用に設計されています。 例えば、データの貯蔵、レガシー・データを保管する大規模データベースのホスト、バックアップとして使用する仮想メモリー・システムの仮想ディスク・イメージなどの用途があります。 |
  | 2 IOPS/GB | このオプションは、最も汎用的なワークロード用に設計されています。 例えば、小規模なデータベースのホスト、Web アプリケーションのバックアップ、ハイパーバイザーの仮想マシン (VM) ディスク・イメージなどの用途があります。 |
  | 4 IOPS/GB | このオプションは、同時に高い割合のデータがアクティブになる高負荷のワークロード用に設計されています。 例えば、トランザクション・データベースなどの用途があります。 |
  | 10 IOPS/GB | このオプションは、分析などの最も要求の厳しいワークロード・タイプ用に設計されています。 例えば、トランザクションの多いデータベースやその他のパフォーマンス重視のデータベースなどの用途があります。 このパフォーマンス・レベルは、ファイル共有あたり最大 4 TB の容量に制限されています。 |

### ローカル・ディスク
{: #vc_addingviewingclusters-adding-local-disks}

ローカル・ディスク・オプションは、**SAP 認定**のクワッド Intel Xeon E7-8890 v4 プロセッサーのベアメタル構成でのみ使用できます。 以下のオプションを指定します。
* **ディスク数 (Disk Count)**: 追加するディスクの数を選択します。
* **ディスク・タイプ**: 必要なディスク・タイプのオプションを選択します。

### ライセンス交付の設定
{: #vc_addingviewingclusters-adding-licensing-settings}

クラスター内の VMware vSphere コンポーネントには以下のライセンス・オプションを指定します。
* ビジネス・パートナーであるユーザーの場合、vSphere ライセンス (Enterprise Plus エディション) が自動的に含められて購入されます。
* ビジネス・パートナーでないユーザーの場合、**「購入に含める」**を選択してこのコンポーネントに IBM 提供 VMware ライセンスを使用することも、**「自分で提供する」**を選択し、所有するライセンス・キーを入力してライセンス持ち込み (BYOL) を適用することもできます。

### ネットワーク・インターフェースの設定
{: #vc_addingviewingclusters-adding-network-interface-settings}

ネットワーク・インターフェース・カード (NIC) の有効化設定は、**「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のどちらを選択したかに基づきます。 以下のアドオン・サービスはパブリック NIC を必要とするため、プライベート・オプションを選択した場合は利用できません。

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### 注文のサマリー
{: #vc_addingviewingclusters-adding-order-summary}

選択したクラスター構成に基づいて、見積もりコストがすぐに生成され、右側のペインの**「注文の要約」**に表示されます。

## vCenter Server インスタンスにクラスターを追加する手順
{: #vc_addingviewingclusters-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、クラスターを追加するインスタンスをクリックします。

   インスタンスの状況が**「使用可能」**であることを確認してください。 そうでない場合、インスタンスにクラスターを追加できません。
   {:note}
3. 左側のナビゲーション・ペインにある**「インフラストラクチャー」**をクリックし、**「クラスター」**テーブルの右上隅にある**「追加」**をクリックします。
4. **「Add Cluster」**ページで、クラスター名を入力します。
5. インスタンスのホスト以外の {{site.data.keyword.CloudDataCent_notm}} でクラスターをホストする場合は、**「Bare Metal Server」**で**「Select a different location」**チェック・ボックスにチェック・マークを付けて、インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}} を選択します。
6. ベア・メタル構成を次の手順で実行します。
   * **「Skylake」**または**「Broadwell」**を選択した場合は、**CPU モデル**、**RAM** 量、**{{site.data.keyword.baremetal_short}}の数**を指定します。
   * **「SAP 認定」**を選択した場合は、CPU モデルを指定します。
7. ストレージ構成を次の手順で実行します。
  * **「vSAN Storage」**を選択した場合は、容量ディスクおよびキャッシュ・ディスクのディスク・タイプ、ディスク数、vSAN ライセンス・エディションを指定します。 さらにストレージが必要な場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。
  * **「NFS ストレージ」**を選択し、すべてのファイル共有に同じ設定を構成して追加する場合は、**「共有の数」**、**「パフォーマンス」**、**「サイズ (GB)」**を指定します。
  * **「NFS Storage」**を選択してファイル共有を個別に追加して構成する場合は、**「Configure shares individually」**を選択します。 その後、ファイル共有ごとに、**「共有ストレージの追加」**ラベルの横にある**「+」**アイコンをクリックして、**「パフォーマンス」**と**「サイズ (GB)」**を選択します。 少なくとも 1 つのファイル共有を選択する必要があります。
  * **「ローカル・ディスク」**を選択した場合は、ディスク数とディスク・タイプを指定します。
8. ネットワーク・インターフェースの設定を行います。
8. vSphere ライセンス・キーの提供方法を指定します。
  * ビジネス・パートナーであるユーザーの場合、vSphere ライセンス (Enterprise Plus エディション) が自動的に含められて購入されます。
  * ビジネス・パートナーでないユーザーの場合は、以下のオプションのいずれかを選択できます。
      * 新規ライセンスを自動購入する場合は、コンポーネントの**「購入に含める」**を選択します。
      * 所有している VMware ライセンスをコンポーネントに使用する場合は、**「自分で提供する」**を選択し、そのライセンス・キーを入力します。
9. **「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のいずれかのネットワーク設定を選択します。
10. **「発注要約」**ペインで、クラスター構成を確認してからクラスターを追加します。
   1. クラスターの設定を確認します。
   2. クラスターの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、クラスターを追加する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

### vCenter Server インスタンスにクラスターを追加した結果
{: #vc_addingviewingclusters-adding-results}

1. クラスターのデプロイメントが自動的に開始され、クラスターの状況が**「初期化中」**に変更されます。 インスタンスの**「サマリー」**ページでデプロイメント履歴を表示して、デプロイメントの状況を確認できます。
2. クラスターを使用する準備ができると、状況が**「使用可能」**に変更されます。 新しく追加されたクラスターで、vSphere High Availability (HA) と vSphere Distributed Resource Scheduler (DRS) が有効になります。

クラスター名は変更できません。 クラスター名を変更すると、クラスター内の ESXi サーバーの追加または削除の操作が失敗することがあります。
{:important}

## vCenter Server インスタンスでクラスターを表示する手順
{: #vc_addingviewingclusters-viewing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、クラスターを表示するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。 **「クラスター」**表で、クラスターに関する要約を表示します。
  * **名前**: クラスターの名前。
  * **ESXi サーバー**: クラスター内の ESXi サーバー数。
  * **CPU**: クラスター内の ESXi サーバーの CPU 仕様。
  * **カスタマイズ vSAN ディスク**: クラスター内の vSAN ディスクの数 (ディスク・タイプおよび容量も含む)。
  * **メモリー**: クラスター内の ESXi サーバーの合計メモリー・サイズ。
  * **データ・センターの場所**: クラスターがホストされている {{site.data.keyword.CloudDataCent_notm}}。
  * **ポッド (Pod)**: クラスターがデプロイされているポッド。
  * **状況**: クラスターの状況。 状況は、以下のいずれかの値になります。
    <dl class="dl">
        <dt class="dt dlterm">初期化中</dt>
        <dd class="dd">クラスターは作成され、構成されています。</dd>
        <dt class="dt dlterm">変更中</dt>
        <dd class="dd">クラスターは変更されています。</dd>
        <dt class="dt dlterm">使用可能</dt>
        <dd class="dd">クラスターは使用可能です。</dd>
        <dt class="dt dlterm">削除中</dt>
        <dd class="dd">クラスターは削除中です。</dd>
        <dt class="dt dlterm">削除済み</dt>
        <dd class="dd">クラスターが削除された場合。</dd>
    </dl>
  * **アクション**: **「削除」**アイコンをクリックしてクラスターを削除できます。
4. クラスター名をクリックして、ESXi サーバーとストレージを表示します。

表 4. ESXi サーバーの詳細

| 項目        | 説明       |  
|:------------- |:------------- |
| 名前 | ESXi サーバーの名前は以下の形式です。<br> `<host_prefix><n>.<subdomain_label>.<root_domain>` <br> 各部の意味は、次のとおりです。<br> `host_prefix` はホスト名の接頭部です<br> `n` はサーバーの順序です<br> `subdomain_label` はサブドメイン・ラベルです<br> `root_domain` はルート・ドメイン名です|
| バージョン | ESXi サーバーのバージョン。 |
| 資格情報 | ESXi サーバーにアクセスするために使用するユーザー名とパスワード。 |
| プライベート IP | ESXi サーバーのプライベート IP アドレス。 |
| 状況 | ESXi サーバーの状況。次の値のいずれかになります。<br> **追加済み**: ESXi サーバーが追加され、使用可能な状態です。<br> **追加中**: ESXi サーバーが追加されています。<br> **削除中**: ESXi サーバーが削除されています。 |

表 5. ストレージの詳細

| 項目        | 説明       |  
|:------------- |:------------- |
| 名前 | データ・ストア名。 |
| サイズ | ストレージの容量。 |
| IOPS/GB | ストレージのパフォーマンス・レベル。 |
| NFS プロトコル | ストレージの NFS バージョン。 |

## vCenter Server インスタンスからのクラスターの削除
{: #vc_addingviewingclusters-deleting}

不要になったクラスターをインスタンスから削除したい場合があります。

### 削除する前に
{: #vc_addingviewingclusters-deleting-prereq}

* この手順を使用して、V2.3 以降でデプロイされたインスタンスからクラスターを削除できます。
* V2.2 以前のインスタンスでデプロイしたクラスターの場合、インスタンスに追加したクラスターを削除するには、インスタンスを V2.3 にアップグレードする必要があります。
* クラスターは一度に 1 つしか削除できません。 複数のクラスターを削除する場合は、順番に行う必要があります。 前のクラスターが削除されるまで待ってから、次のクラスターを削除してください。
* クラスターを削除する前に、クラスター内のすべてのノードが電源オンの状態で作動可能であることを確認します。
* クラスターを削除すると、クラスターのすべての VM も削除され、復旧できなくなります。 VM を保持したい場合は、他のクラスターに移行してください。
* デフォルトのクラスターは削除できません。

### vCenter Server インスタンスからクラスターを削除する手順
{: #vc_addingviewingclusters-deleting-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、クラスターを削除するインスタンスをクリックします。

   インスタンスの状況が**「使用可能」**であることを確認してください。 そうでない場合、インスタンスからクラスターを削除できません。
   {:note}

3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。 **「クラスター」**テーブルで、削除するクラスターを見つけて、**「アクション」**列にある**「削除」**アイコンをクリックします。
4. 他のクラスターに VM を移行する必要がある場合は、その移行が完了したことを確認し、クラスターを削除することを確認します。

## 関連リンク
{: #vc_addingviewingclusters-related}

* [vCenter Server インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
