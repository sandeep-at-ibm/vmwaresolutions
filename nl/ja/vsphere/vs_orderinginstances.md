---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-26"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 新規 vSphere クラスターの注文
{: #vs_orderinginstances}

高度にカスタマイズ可能な VMware 仮想化プラットフォームをデプロイするには、VMware vSphere cluster on {{site.data.keyword.cloud}} を注文します。 次の手順を使用して、新規の vSphere クラスターを定義してください。

この手順では、新規クラスターを作成するための VMware コンポーネントの選択、{{site.data.keyword.cloud_notm}} ベア・メタル・サーバーの設定、ストレージ設定、およびネットワーキングの選択について説明します。 注文を実行すると、そのクラスター構成が取り込まれるので、必要なときに構成に戻ってクラスターをスケールアウトできます。 注文が完了したら、要件に応じて VMware クラスターを手動で構成できます。

## 要件
{: #vs_orderinginstances-req}

以下の作業を完了していることを確認してください。
*  **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定の管理](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)を参照してください。
*  [vSphere クラスターの要件と計画](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)に記載されている要件と考慮事項を確認する。

## システム設定
{: #vs_orderinginstances-sys-settings}

新しい vSphere クラスターを注文する際には、以下のシステム設定を指定する必要があります。

### クラスター名
{: #vs_orderinginstances-cluster-name}

クラスター名は、アカウント内で固有でなければなりません。

## ライセンス交付の設定
{: #vs_orderinginstances-licensing-settings}

クラスターと一緒に注文する VMware コンポーネントを選択し、それらのコンポーネントのライセンス・オプションを指定します。

### IBM ビジネス・パートナーのユーザー用のコンポーネント・バンドル
{: #vs_orderinginstances-component-bundles-for-bp-users}

IBM ビジネス・パートナーのユーザーは、新規 vSphere クラスターを注文するときにコンポーネント・ライセンス・バンドルを選択できます。 使用可能なバンドルは次のとおりです。

表 1. IBM ビジネス・パートナー向けの vSphere クラスター用のコンポーネント・バンドル

| バンドル | コンポーネント                   |
|:------------------------- |:----------------------- |
| Standard with Management | vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、vRealize Operations Enterprise |
| Advanced                 | vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、vCloud Director、NSX Base |
| Advanced with Networking | vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、NSX Advanced |
| Advanced with Networking and Management | vSphere Enterprise Plus、vCenter Server Standard、vRealize Log Insight、vRealize Operations Enterprise、vCloud Director、NSX Enterprise |

また、次の VMware コンポーネントを注文に含めることもできます。
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

IBM ビジネス・パートナーのユーザーの場合、ライセンス持ち込み (BYOL) オプションは利用できません。
{:note}

### 非ビジネス・パートナーのユーザー用の個別コンポーネント
{: #vs_orderinginstances-individual-components-for-non-bp-users}

非ビジネス・パートナーは、vSphere クラスターに以下のコンポーネントを選択できます。
* VMware vSphere Enterprise Plus 6.7 U1 または 6.5 U2
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

VMware vSphere Enterprise Plus 6.0 を注文する場合、VMware vSAN コンポーネントは使用できません。 VMware vSphere Enterprise Plus 6.0 にお客様自身のライセンスを使用する場合は、{{site.data.keyword.cloud_notm}} インフラストラクチャー・チケットが自動的にオープンされます。 このチケットは、注文した{{site.data.keyword.baremetal_short}}の vSphere ライセンスを、提供したライセンスに置き換えるように要求します。
{:note}

### ライセンス・オプション
{: #vs_orderinginstances-licensing-options}

選択した VMware コンポーネントにライセンスを適用するには、次の方法があります。
* **購入にライセンスを含める**: この場合、自動的に VMware コンポーネントの新規ライセンスを購入します。 結合された VMware ライセンスが、注文のクラスター・サイズに一致するように生成されます。
* **自分でライセンスを提供する**: この場合、VMware コンポーネントにお客様自身のライセンスを使用します。

vSphere Enterprise Plus と vCenter Server を除き、ライセンスを購入することを選択して複数の ESXi サーバーを注文した場合は、複数のライセンス・キーを結合するための {{site.data.keyword.cloud_notm}} チケットが自動的にオープンされます。 このチケットに対応し、DevOps チームで生成したライセンス・キーだけを使用するようにする作業は、お客様が行う必要があります。

個々のライセンス・キーを、結合されたライセンス・キーと一緒に使用しても、必要なライセンスの支払要件は満たされません。
{:important}

## ベア・メタル・サーバーの設定
{: #vs_orderinginstances-bare-metal-settings}

### データ・センターの場所
{: #vs_orderinginstances-dc-location}

クラスターをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。

**注:**
* vSAN コンポーネントを選択した場合は、SSD の使用可否によってロケーション・リストがフィルタリングされます。
* Broadwell ベア・メタル・サーバーは、**FRA05 - フランクフルト**のデータ・センター・ロケーションでは使用できません。
* SAP 認定ベア・メタル・サーバーと Broadwell ベア・メタル・サーバーは、**LON05 - ロンドン**のデータ・センター・ロケーションでは使用できません。

### Skylake
{: #vs_orderinginstances-skylake}

**「Skylake」**を選択した場合、必要に応じてベアメタル・サーバーの CPU と RAM の組み合わせを選択できます。 使用できるオプションは、VMware vSAN コンポーネントを選択したかどうかによって異なります。

表 2. Skylake {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 プロセッサー / 合計 16 コア、2.1 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

### SAP 認定
{: #vs_orderinginstances-sap}

VMware vSAN を以前に選択した場合、**「SAP 認定」**タブは使用できません。 **「SAP 認定」**を選択した場合、CPU や RAM の設定は変更できません。

要件に基づいて、以下のベア・メタル・サーバー構成を選択します。
  * Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 192 GB RAM
  * Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 384 GB RAM
  * Dual Intel Xeon Gold 6140 プロセッサー / 合計 36 コア、2.3 GHz / 768 GB RAM
  * Dual Intel Xeon E5-2690 v4 プロセッサー / 合計 28 コア、2.6 GHz / 512 GB RAM
  * Quad Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.2 GHz / 1024 GB RAM
  * Quad Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.2 GHz / 2048 GB RAM
  * Quad Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.2 GHz / 4096 GB RAM

### Broadwell
{: #vs_orderinginstances-broadwell}

**「Broadwell」**を選択した場合、必要に応じてベアメタル・サーバーの CPU と RAM の組み合わせを選択できます。 使用できるオプションは、VMware vSAN コンポーネントを選択したかどうかによって異なります。

表 3. Broadwell {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション        | RAM オプション       |
|:------------- |:------------- |
| クワッド Intel Xeon E7-4820 v4 / 合計 40 コア、2.0 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
| クワッド Intel Xeon E7-4850 v4 / 合計 64 コア、2.1 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |

### ベア・メタル・サーバーの数
{: #vs_orderinginstances-bare-metal-number}

vSphere クラスターに追加する ESXi サーバーの数。 すべての ESXi サーバーが同じ構成です。
* VMware NSX コンポーネントを選択した場合は、最少 3 台のサーバーが必要です。
* VMware vSAN コンポーネントを選択した場合は、最少 4 台のサーバーが必要です。

## ストレージ設定
{: #vs_orderinginstances-storage-settings}

vSAN なしの注文の場合、ESXi サーバー用に 12 ディスクのシャーシと 2 基のディスク (ESXi オペレーティング・システム (OS) 用) が注文されます。

vSAN ありの注文の場合、ESXi サーバー用に 12 ディスクのシャーシと 4 基のディスク (ESXi OS 用の 2 基とキャッシュ用に予約された 2 基) が注文されます。 これらの設定はデフォルトで構成され、変更はできません。 **「vSAN 容量ディスクのディスク・タイプとサイズ」**および**「vSAN 容量ディスクの数」**を選択して、追加の容量ディスクを注文できます。

クラスターに VMware vSAN コンポーネントを選択した場合は、以下の設定を指定します。
* **vSAN 容量ディスクのディスク・タイプとサイズ**: 必要な容量ディスクのオプションを選択します。
* **vSAN 容量ディスクの数**: 追加する容量ディスク数を指定します。
* 容量ディスクを上限の 8 個を超えて追加する場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。 このオプションでは、合計 10 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されますので、より少ない待ち時間とより高い IOPS スループットが求められるワークロードを扱うときに役立ちます。

  **「High-Performance Intel Optane」**オプションは、Skylake の CPU モデルでのみ使用できます。
  {:note}

* **「Disk Type for vSAN Cache Disks」**および**「Number of vSAN Cache Disks」**の値を確認します。 これらの値は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けたかどうかによって異なります。

## ネットワーク・インターフェースの設定
{: #vs_orderinginstances-network-interface-settings}

新しい vSphere クラスターを注文する際には、以下のネットワーク・インターフェース設定を指定する必要があります。

### ホスト名接頭部
{: #vs_orderinginstances-host-name-prefix}

ホスト名は、すべてのベア・メタル・サーバーの注文で使用されます。 vCenter Server および NSX などのすべての管理仮想マシンで、このホスト名を使用することをお勧めします。

ホスト名接頭部は、次の要件を満たす必要があります。
* この名前の先頭と末尾は英数字である必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* 最大長は 10 文字です。

### サブドメイン・ラベル
{: #vs_orderinginstances-subdomain-label}

サブドメイン・ラベルは、次の要件を満たす必要があります。
*  英数字とダッシュ (-) の文字だけを使用できます。
*  サブドメイン・ラベルの先頭と末尾は英数字である必要があります。
*  サブドメイン・ラベルの最大長は 10 文字です。
*  サブドメイン・ラベルは、アカウント内で固有でなければなりません。

### ドメイン・ネーム
{: #vs_orderinginstances-domain-name}

ドメイン・ネームは、すべての{{site.data.keyword.baremetal_short}}で使用されます。次の要件を満たす必要があります。
* ピリオド (.) で区切られた 2 つ以上の文字列で構成された名前である必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* 各文字列は英字で始まり英数字で終わる必要があり、最後の文字列には英字しか含められません。
* 最後の文字列の長さは、2 文字から 24 文字までの範囲でなければなりません。
* 他の文字列の長さは、1 文字から 63 文字までの範囲でなければなりません。
* ドメイン・ネームの最大長は 189 文字です。

### パブリックまたはプライベート・ネットワーク
{: #vs_orderinginstances-public-private-network}

ネットワーク・インターフェース・カード (NIC) の有効化設定は、**「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のどちらを選択したかに基づきます。

### VLAN
{: #vs_orderinginstances-vlans}

ネットワーク設定は、**「新規 VLAN を注文」**と**「既存の VLAN を選択」**のどちらを選択するかによって異なります。

クラスターの注文には、パブリック VLAN 1 つとプライベート VLAN 2 つが必要です。 2 つのプライベート VLAN は各ベア・メタル・サーバーにトランキングされます。

#### 新規 VLAN を注文
{: #vs_orderinginstances-new-vlans}

新規パブリック VLAN 1 つと新規プライベート VLAN 2 つを注文することを選択します。

#### 既存の VLAN を選択
{: #vs_orderinginstances-existing-vlans}

選択した {{site.data.keyword.CloudDataCent_notm}}によっては、既存のパブリック VLAN とプライベート VLAN を使用できることがあります。

  既存のパブリック VLAN とプライベート VLAN を再使用することを選択した場合は、それらの VLAN とサブネットを指定します。
  * **パブリック VLAN** は、パブリック・ネットワーク・アクセスに使用されます。
  * **プライベート VLAN** は、{{site.data.keyword.cloud_notm}} 内部のデータ・センターとサービスの間の接続に使用されます。
  * **セカンダリー・プライベート VLAN** は、vSAN などの VMware 機能に使用されます。
  * **プライマリー・サブネット**は、パブリック・ネットワーク・アクセス用に物理ホストに割り当てられます。
  * **プライマリー・プライベート・サブネット**は、管理トラフィック用に物理ホストに割り当てられます。

**重要:**
* 選択した VLAN のファイアウォール構成が管理用データ・トラフィックをブロックしていないことを確認してください。
* 選択したすべての VLAN が同じポッドに含まれていることを確認してください。 複数のポッドの VLAN に ESXi サーバーをプロビジョンすることはできません。

#### FortiGate 物理アプライアンス 300 シリーズ HA ペア
{: #vs_orderinginstances-fortigate-physical-appliance}

また、クラウド環境を保護するために FortiGate 物理アプライアンス 300 シリーズ HA ペアを含めるかどうかも選択できます。 詳しくは、[FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)を参照してください。

## 注文のサマリー
{: #vs_orderinginstances-order-summary}

構成に基づいて、見積もりコストがすぐに生成され、右側の**「注文の要約」**ペインに表示されます。 **「料金詳細」**をクリックすると、見積もりの詳細を示す PDF 文書を生成できます。

## vSphere クラスターを注文する手順
{: #vs_orderinginstances-procedure}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**をクリックしてから、**「仮想データ・センター」**セクションの**「VMware vSphere」**をクリックします。
2. **「VMware vSphere on IBM Cloud」**ページで、**「作成」**をクリックします。  
   **「新規作成」**タブが表示され、**「クラスター構成」**リストに**「新規クラスター」**が表示されていることを確認します。
3. クラスター名を入力します。
4. VMware コンポーネントを選択します。
  * IBM ビジネス・パートナーは、ライセンス・バンドルと追加の VMware コンポーネントを選択してください。
  * 非ビジネス・パートナーは、コンポーネントとエディション (ある場合) を選択して、ライセンス・オプションを指定してください。
  VMware vSphere Enterprise Plus でライセンス持ち込み (BYOL) を選択すると、注文した{{site.data.keyword.baremetal_short}}のデフォルトの vSphere ライセンスを、自分で提供したライセンスに置き換えるよう要求する {{site.data.keyword.cloud_notm}} チケットが自動的に開きます。   

    **重要:** このチケットを追跡し、新しく注文した ESXi サーバー上で vSphere ライセンスを置き換える作業は、お客様が行う必要があります。 このようにして、最初に提供された {{site.data.keyword.cloud_notm}} インフラストラクチャーの vSphere ライセンス料の取り消しが {{site.data.keyword.cloud_notm}} インフラストラクチャーによって許可されます。 ESXi vSphere ライセンスを置き換えるには、[Configure License Settings for an ESXi Host](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window} を参照してください。
5. ベア・メタル・サーバーの設定を次の手順で実行します。
   1. クラスターをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。
   2. ベア・メタル・サーバー構成を選択します。
      * **「Skylake」**または**「Broadwell」**を選択した場合は、CPU モデルと RAM サイズを指定します。
      * **「SAP 認定」**を選択した場合は、事前設定構成のいずれかを選択します。
   3. ベア・メタル・サーバーの数を指定します。
6. **VMware vSAN** コンポーネントを選択した場合は、vSAN ストレージの構成を完了します。 容量ディスクおよびキャッシュ・ディスクのディスク・タイプとディスク数を指定します。 さらにストレージが必要な場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。
7. ネットワーク・インターフェースの設定を行います。
   1. ホスト名接頭部、サブドメイン・ラベル、およびドメイン・ネームを入力します。
   2. **「パブリック・ネットワークとプライベート・ネットワーク (Public and Private Network)」**と**「プライベート・ネットワークのみ」**のいずれかのネットワーク設定を選択します。
   3. 使用するネットワーク・インターフェースを選択します。
    * 新規のパブリック VLAN とプライベート VLAN を注文する場合は、**「新規 VLAN を注文」**をクリックします。
    * 既存のパブリック VLAN とプライベート VLAN を使用できる場合に再利用するには、**「既存の VLAN を選択」**をクリックし、該当する VLAN とオプションでサブネットを指定します。
    4. クラウド環境を保護するために FortiGate 物理アプライアンス 300 シリーズ HA ペアを適用するかどうかを指定します。  
8. **「注文のサマリー」**ペインで、クラスター構成と見積もりコストを確認します。
   * 注文を実行せずに構成をテンプレートとして保存するには、**「構成の保存」**をクリックします。
   * 注文を実行するには、課金されるアカウントが正しいことを確認し、使用条件を確認して承諾してから、**「プロビジョン」**をクリックします。

   {{site.data.keyword.baremetal_short}}だけがインストールされます。 クラスターのデプロイメントの後に、VMware vCenter、VMware NSX、VMware vSAN などの各種コンポーネントをインストールして構成する作業は、お客様が行う必要があります。
   {:note}

### 結果
{: #vs_orderinginstances-results}

クラスター構成をテンプレートとして保存した場合は、その構成が正常に保存されたことを示すコンソール通知を受け取ります。そして、**「クラスター構成」**リストにそのテンプレートが表示されます。

注文を実行した場合は、クラスターのデプロイメントが自動的に開始され、注文が処理中であることを示す E メール確認を受け取ります。 クラスターが使用可能になると、E メールで通知されます。

vSphere クラスターは、vCenter Server インスタンスとは異なり、**「リソース」**ページに表示されません。
{:note}

## 関連リンク
{: #vs_orderinginstances-related}

* [既存の構成を基にした vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [既存クラスターの拡張](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [コンソール以外で作成されたクラスターの拡張](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
