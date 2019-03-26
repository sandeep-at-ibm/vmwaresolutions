---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-11"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle インスタンスのクラスターの追加、表示、削除
{: #vc_hybrid_addingviewingclusters}

インスタンスの注文時に構成した ESXi サーバーは、デフォルトでは **cluster1** としてグループ化されます。

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle インスタンスにクラスターを追加して、コンピュート能力やストレージ容量を拡張できます。 クラスター内で ESXi サーバーを管理して、リソース割り振りを改善し、高可用性を実現します。 不要になった場合は、追加したクラスターをインスタンスから削除します。

## vCenter Server with Hybridity Bundle インスタンスへのクラスターの追加
{: #vc_hybrid_addingviewingclusters-adding}

インスタンスに追加できるクラスターの数は、インスタンスのバージョンに応じて以下のように異なります。
* V2.5 以降でデプロイ (または V2.5 以降にアップグレード) されたインスタンスの場合は、追加できるクラスター数の上限は、クラスター、ホスト、および VM の数によって決まります。 VMware のサイズ設定についてのガイドラインおよびデプロイに応じた上限を守る必要があります。
* V2.3 以降でデプロイ (または V2.3 以降にアップグレード) されたインスタンスの場合は、最大 10 個のクラスターを追加できます。

上限について詳しくは、[VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window} を参照してください。

### システム設定
{: #vc_hybrid_addingviewingclusters-adding-sys-settings}

vCenter Server with Hybridity Bundle インスタンスにクラスターを追加するときには、以下の設定を指定する必要があります。

#### クラスター名
{: #vc_hybrid_addingviewingclusters-adding-cluster-name}

クラスター名は、以下の要件を満たしている必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* クラスター名の先頭と末尾は、英数字でなければなりません。
* クラスター名の最大の長さは 30 文字です。
* クラスター名は、vCenter Server with Hybridity Bundle インスタンス内で固有でなければなりません。

#### データ・センターの場所
{: #vc_hybrid_addingviewingclusters-adding-dc-location}

クラスターの {{site.data.keyword.CloudDataCent_notm}}の場所はデフォルトで、vCenter Server インスタンスの {{site.data.keyword.CloudDataCent_notm}}に設定されます。 デプロイ済みのインスタンスとは異なる {{site.data.keyword.CloudDataCent_notm}}にクラスターをデプロイできますが、それら 2 カ所の {{site.data.keyword.CloudDataCents_notm}}間のネットワーク待ち時間が、150 ms 未満になるようにしてください。 ネットワーク待ち時間を確認するには、[SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} などのツールを使用します。

別の {{site.data.keyword.CloudDataCent_notm}}または {{site.data.keyword.cloud_notm}} インフラストラクチャー・ポッドにクラスターをデプロイする場合は、注文した{{site.data.keyword.baremetal_short}}で使用するためにさらに 3 つの VLAN を注文します。

### ベア・メタル・サーバーの設定
{: #vc_hybrid_addingviewingclusters-adding-bare-metal}

**「Skylake」**または**「Broadwell」**のいずれかを選択できます。 オプションは、インスタンスを最初にデプロイしたバージョンによって異なる場合があります。

#### Skylake
{: #vc_hybrid_addingviewingclusters-adding-skylake}

**「Skylake」**を選択した場合、必要に応じて CPU と RAM の組み合わせを選択できます。

表 1. Skylake ベアメタル・サーバーのオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 プロセッサー / 合計 16 コア、2.1 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

#### Broadwell
{: #vc_hybrid_addingviewingclusters-adding-broadwell}

**「Broadwell」**を選択した場合、必要に応じて CPU と RAM の組み合わせを選択できます。

表 2. Broadwell ベアメタル・サーバーのオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| デュアル Intel Xeon E5-2620 v4 / 合計 16 コア、2.1 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2650 v4 / 合計 24 コア、2.2 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2690 v4 / 合計 28 コア、2.6 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| クワッド Intel Xeon E7-4820 v4 / 合計 40 コア、1.9 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
| クワッド Intel Xeon E7-4850 v4 / 合計 64 コア、2.2 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |

#### ベア・メタル・サーバーの数
{: #vc_hybrid_addingviewingclusters-adding-bare-metal-number}

クラスター 1 つにつき、2 つ以上の{{site.data.keyword.baremetal_short}}が必要です。

1 つのクラスターに最大 59 台の{{site.data.keyword.baremetal_short}}を追加できます。1 台から 59 台の ESXi サーバーを一度に追加できます。

デプロイメント後に、最大 4 つのクラスターを追加で作成できます。 VMware vSAN ストレージの場合、初期クラスターとデプロイメント後のクラスターの両方に 4 つのサーバーが必要です。

### vSAN ストレージ設定
{: #vc_hybrid_addingviewingclusters-adding-vsan-storage-settings}

vCenter Server with Hybridity Bundle インスタンスの注文には、VMware vSAN 6.6 が含められます。 以下の vSAN オプションを指定します。
* **vSAN 容量ディスクのディスク・タイプとサイズ**: 必要な容量ディスクのオプションを選択します。
* **vSAN 容量ディスクの数**: 追加する容量ディスク数を指定します。
* 容量ディスクを上限の 8 個を超えて追加する場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。 このオプションでは、合計 10 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されますので、より少ない待ち時間とより高い IOPS スループットが求められるワークロードを扱うときに役立ちます。

  **High-Performance Intel Optane** オプションは、Skylake の CPU モデルの Dual Intel Xeon Gold 5120 および Dual Intel Xeon Gold 6140 でのみ使用できます。
  {:note}

* **「Disk Type for vSAN Cache Disks」**および**「Number of vSAN Cache Disks」**の値を確認します。 これらの値は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けたかどうかによって異なります。
* **vSAN ライセンス**: VMware vSAN 6.6 ライセンス・エディション (Advanced または Enterprise) を選択します。

### ライセンス交付の設定
{: #vc_hybrid_addingviewingclusters-adding-licensing-settings}

IBM では、以下の VMware コンポーネントのライセンスを提供しています。
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (Advanced または Enterprise エディション)

### ネットワーク・インターフェースの設定
{: #vc_hybrid_addingviewingclusters-adding-network-interface-settings}

ネットワーク・インターフェース・カード (NIC) の設定は、**「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のどちらを選択したかに基づきます。 以下のアドオン・サービスはパブリック NIC を必要とするため、プライベート・オプションを選択した場合は利用できません。

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### 注文のサマリー
{: #vc_hybrid_addingviewingclusters-adding-order-summary}

選択したクラスター構成に基づいて、見積もりコストがすぐに生成され、右側のペインの**「注文の要約」**に表示されます。

## vCenter Server with Hybridity Bundle インスタンスにクラスターを追加する手順
{: #vc_hybrid_addingviewingclusters-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、クラスターを表示するインスタンスをクリックします。

   インスタンスの状況が**「使用可能」**であることを確認してください。 そうでない場合、インスタンスにクラスターを追加できません。
   {:note}

3. 左側のナビゲーション・ペインにある**「インフラストラクチャー」**をクリックし、**「クラスター」**テーブルの右上隅にある**「追加」**をクリックします。
4. **「Add Cluster」**ページで、クラスター名を入力します。
5. インスタンスのホスト以外の {{site.data.keyword.CloudDataCent_notm}} でクラスターをホストできます。 これを行うには、**「Bare Metal Server」**で**「Select a different location」**チェック・ボックスにチェック・マークを付けて、インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。
6. ベアメタル構成として、**CPU モデル**、**RAM** の量、**ベア・メタル・サーバーの数**を選択します。
7.  **「vSAN Storage」**を選択し、容量ディスクおよびキャッシュ・ディスクのディスク・タイプとディスク数を指定します。 さらにストレージが必要な場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。
8. ライセンス構成として、VMware vSAN のライセンス・エディションを選択します。
9. **「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のいずれかのネットワーク設定を選択します。
10. **「発注要約」**ペインで、クラスター構成を確認してからクラスターを追加します。
   1. クラスターの設定を確認します。
   2. クラスターの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、クラスターを追加する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

### vCenter Server with Hybridity Bundle インスタンスにクラスターを追加した結果
{: #vc_hybrid_addingviewingclusters-adding-results}

1. クラスターのデプロイメントが自動的に開始され、クラスターの状況が**「初期化中」**に変更されます。 インスタンスの**「サマリー」**ページでデプロイメント履歴を表示して、デプロイメントの状況を確認できます。
2. クラスターを使用する準備ができると、状況が**「使用可能」**に変更されます。 新しく追加されたクラスターで、vSphere High Availability (HA) と vSphere Distributed Resource Scheduler (DRS) が有効になります。

クラスター名は変更できません。 クラスター名を変更すると、クラスター内の ESXi サーバーの追加または削除の操作が失敗することがあります。
{:important}

## vCenter Server with Hybridity Bundle インスタンスでクラスターを表示する手順
{: #vc_hybrid_addingviewingclusters-viewing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
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
4. クラスター名をクリックして、ESXi サーバーとストレージの詳細を表示します。

  * ESXi サーバーの詳細:
     * **名前**: ESXi サーバーの名前は、`<host_prefix><n>.<subdomain_label>.<root_domain>` という形式です。各部の意味は次のとおりです。

       `host_prefix` はホスト名の接頭部です。

       `n` はサーバーの順序です。

       `subdomain_label` はサブドメイン・ラベルです。

       `root_domain` はルート・ドメイン名です。

     * **バージョン**: ESXi サーバーのバージョン。
     * **資格情報**: ESXi サーバーにアクセスするためのユーザー名とパスワード。
     * **プライベート IP**: ESXi サーバーのプライベート IP アドレス。
     * **状況**: ESXi サーバーの状況。以下の値のいずれかになります。
        <dl class="dl">
        <dt class="dt dlterm">追加済み</dt>
        <dd class="dd">ESXi サーバーが追加され、使用可能な状態です。 </dd>
        <dt class="dt dlterm">追加中</dt>
        <dd class="dd">ESXi サーバーが追加されています。 </dd>
        <dt class="dt dlterm">削除中</dt>
        <dd class="dd">ESXi サーバーが削除されています。</dd>
        </dl>
  * ストレージの詳細:
    * **名前**: データ・ストア名。
    * **サイズ**: ストレージの容量。
    * **IOPS/GB**: ストレージのパフォーマンス・レベル。
    * **NFS プロトコル**: ストレージの NFS バージョン。

## vCenter Server with Hybridity Bundle インスタンスからのクラスターの削除
{: #vc_hybrid_addingviewingclusters-deleting}

不要になったクラスターをインスタンスから削除したい場合があります。

### 削除する前に
{: #vc_hybrid_addingviewingclusters-deleting-prereq}

* クラスターは一度に 1 つしか削除できません。 複数のクラスターを削除する場合は、順番に削除する必要があります。つまり、前のクラスターが削除されるまで待ってから、次のクラスターを削除してください。
* クラスターを削除する前に、クラスター内のすべてのノードが電源オンの状態で作動可能であることを確認します。
* クラスターを削除すると、クラスターのすべての VM (仮想マシン) も削除され、復旧できなくなります。 VM を保持したい場合は、他のクラスターに移行してください。
* デフォルトのクラスターは削除できません。

## vCenter Server with Hybridity Bundle インスタンスからクラスターを削除する手順
{: #vc_hybrid_addingviewingclusters-deleting-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、クラスターを削除するインスタンスをクリックします。

   インスタンスの状況が**「使用可能」**であることを確認してください。 そうでない場合、インスタンスからクラスターを削除できません。
   {:note}

3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。 **「クラスター」**テーブルで、削除するクラスターを見つけて、**「アクション」**列にある**「削除」**アイコンをクリックします。

## 関連リンク
{: #vc_hybrid_addingviewingclusters-related}

* [vCenter Server with Hybridity Bundle インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [vCenter Server with Hybridity Bundle インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
