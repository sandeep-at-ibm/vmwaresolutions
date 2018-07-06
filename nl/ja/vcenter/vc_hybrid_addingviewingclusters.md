---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# vCenter Server with Hybridity Bundle インスタンスのクラスターの追加、表示、削除

インスタンスの注文時に構成した ESXi サーバーは、デフォルトでは **cluster1** としてグループ化されます。

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle インスタンスにクラスターを追加して、コンピュート能力やストレージ容量を拡張できます。 クラスター内で ESXi サーバーを管理すると、リソース割り振りを改善したり高可用性を実現したりできます。 不要になった場合には、追加したクラスターをインスタンスから削除できます。

## vCenter Server with Hybridity Bundle インスタンスへのクラスターの追加

vCenter Server with Hybridity Bundle インスタンスには最大 10 個のクラスターを追加できます。

### システム設定

vCenter Server with Hybridity Bundle インスタンスにクラスターを追加するときには、以下の設定を指定する必要があります。

#### クラスター名

クラスター名は、以下の要件を満たしている必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* クラスター名の先頭と末尾は、英数字でなければなりません。
* クラスター名の最大の長さは 30 文字です。
* クラスター名は、vCenter Server with Hybridity Bundle インスタンス内で固有でなければなりません。

#### データ・センターの場所

クラスターの {{site.data.keyword.CloudDataCent}}の場所はデフォルトで、vCenter Server インスタンスの {{site.data.keyword.CloudDataCent_notm}}に設定されます。 デプロイ済みのインスタンスとは異なる {{site.data.keyword.CloudDataCent_notm}}にクラスターをデプロイできますが、それら 2 カ所の {{site.data.keyword.CloudDataCents_notm}}間のネットワーク待ち時間が、150 ms 未満になるようにしてください。 ネットワーク待ち時間を確認するには、[SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} などのツールを使用できます。

別の {{site.data.keyword.CloudDataCent_notm}}または {{site.data.keyword.cloud_notm}} インフラストラクチャー・ポッドにクラスターをデプロイする場合は、注文した{{site.data.keyword.baremetal_short}}で使用するために 3 つの追加 VLAN が注文されます。

### ベア・メタル・サーバーの設定

#### カスタマイズ型

ベア・メタル・サーバーの CPU モデルと RAM を指定します。 利用できるオプションは、インスタンスを最初にデプロイしたバージョンによって異なる場合があります。

表 2. カスタマイズ型のベア・メタル・サーバーのオプション

| CPU オプション        | RAM オプション       |
|:------------- |:------------- |
| デュアル Intel Xeon E5-2620 v4 / 合計 16 コア、2.1 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2650 v4 / 合計 24 コア、2.2 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2690 v4 / 合計 28 コア、2.6 GHz | 64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 96 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Silver 4110 Processor / 合計 16 コア、2.1 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

#### ベア・メタル・サーバーの数

クラスター 1 つにつき、2 つ以上の{{site.data.keyword.baremetal_short}}が必要です。

1 つのクラスターに最大 59 台の{{site.data.keyword.baremetal_short}}を追加できます。1 台から 59 台の ESXi サーバーを一度に追加できます。

デプロイメント後に、最大 4 つのクラスターを追加で作成できます。 VMware vSAN ストレージの場合、初期クラスターとデプロイメント後のクラスターの両方に 4 つのサーバーが必要です。

### vSAN ストレージ設定

vCenter Server with Hybridity Bundle インスタンスの注文には、VMware vSAN 6.6 が含められます。 ライセンス・エディションは、**「Advanced」**または**「Enterprise」**のいずれかを指定する必要があります。

* **vSAN 容量ディスクのディスク・タイプとサイズ**: 共有ストレージのニーズを満たす容量を選択します。
* **vSAN 容量ディスクの数**: 追加する vSAN 共有ストレージのディスク数を選択します。 ディスク数は、2、4、6、または 8 でなければなりません。
* VMware vSAN 6.6 ライセンス・エディション (Advanced または Enterprise) を選択します。

### ライセンス交付の設定

以下のための IBM 提供の VMware ライセンス:
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition (Advanced または Enterprise) 6.3

### 注文のサマリー

選択したクラスター構成に基づいて、見積もりコストがすぐに生成され、右側のペインの**「注文の要約」**に表示されます。

## vCenter Server with Hybridity Bundle インスタンスにクラスターを追加する手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、クラスターを表示するインスタンスをクリックします。

   **注**: インスタンスの状況が**「使用可能」**であることを確認してください。 そうでない場合、インスタンスにクラスターを追加できません。

3. 左側のナビゲーション・ペインにある**「インフラストラクチャー」**をクリックし、**「クラスター」**テーブルの右上隅にある**「追加」**をクリックします。
4. **「Add Cluster」**ページで、クラスター名を入力します。
5. インスタンスのホスト以外の {{site.data.keyword.CloudDataCent_notm}} でクラスターをホストする場合は、**「Bare Metal Server」**で**「Select a different location」**チェック・ボックスにチェック・マークを付けて、インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}} を選択します。
6. ベアメタル構成として、**CPU モデル**、**RAM** の量、**ベア・メタル・サーバーの数**を選択します。
7.  ストレージ構成として、**vSAN ストレージ** を選択し、**「vSAN 容量ディスクの数」**と**「vSAN 容量ディスクのディスク・タイプとサイズ」**を選択します。
8. ライセンス構成として、VMware vSAN のライセンス・エディションを選択します。
9. **「発注要約」**ペインで、クラスター構成を確認してからクラスターを追加します。
   1. クラスターの設定を確認します。
   2. クラスターの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、クラスターを追加する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

### vCenter Server with Hybridity Bundle インスタンスにクラスターを追加した結果

1. クラスターのデプロイメントが自動的に開始され、クラスターの状況が**「初期化中」**に変更されます。 インスタンスの**「サマリー」**ページでデプロイメント履歴を表示して、デプロイメントの状況を確認できます。
2. クラスターを使用する準備ができると、状況が**「使用可能」**に変更されます。 新しく追加されたクラスターで、vSphere High Availability (HA) と vSphere Distributed Resource Scheduler (DRS) が有効になります。

**重要**: クラスター名は変更できません。 クラスター名を変更すると、クラスター内の ESXi サーバーの追加または削除の操作が失敗することがあります。

## vCenter Server with Hybridity Bundle インスタンス内のクラスターの表示

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

不要になったクラスターをインスタンスから削除したい場合があります。

### 削除する前に

* クラスターは一度に 1 つしか削除できません。 複数のクラスターを削除する場合は、順番に削除する必要があります。つまり、前のクラスターが削除されるまで待ってから、次のクラスターを削除してください。
* クラスターを削除する前に、クラスター内のすべてのノードが電源オンの状態で作動可能であることを確認します。
* クラスターを削除すると、クラスターのすべての VM (仮想マシン) も削除され、復旧できなくなります。 VM を保持したい場合は、他のクラスターに移行してください。
* デフォルトのクラスターは削除できません。

## vCenter Server with Hybridity Bundle インスタンスからクラスターを削除する手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、クラスターを削除するインスタンスをクリックします。

   **注**: インスタンスの状況が**「使用可能」**であることを確認してください。 そうでない場合、インスタンスからクラスターを削除できません。

3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。 **「クラスター」**テーブルで、削除するクラスターを見つけて、**「アクション」**列にある**「削除」**アイコンをクリックします。

## 関連リンク

* [vCenter Server with Hybridity Bundle インスタンスの表示](vc_hybrid_viewinginstances.html)
* [vCenter Server with Hybridity Bundle インスタンスの容量の拡張と縮小](vc_hybrid_addingremovingservers.html)
