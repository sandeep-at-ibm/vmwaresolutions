---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial for VMware vCenter Server on IBM Cloud インスタンスの注文と削除
{: #vc_trial_hybrid_orderinginstance}

Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud}} は、VMware vSphere スタックをサービスとして提供する単一テナントのホステッド・プライベート・クラウドです。 クライアント管理環境は通常、最小で 3 つのノードを使用してデプロイされますが、この単一ノード・トライアルは、ハイブリッド・クラウド実装の利点を体験するために低コストのパスを提供しています。

このトライアル版は、初期デプロイメントについて IBM の高度な自動化の速度を明示したり、単純な非実稼働ワークロードをクラウドに簡単に移動できることを明示したりする PoC (概念検証) に理想的です。 VMware Hybrid Cloud Extension (HCX) を使用すれば、{{site.data.keyword.CloudDataCent_notm}}にオンプレミス・データ・センター・ネットワークを安全に拡張できるとともに、相互接続を構成するネットワークの複雑さを低減できます。 HCX は、仮想マシン (VM) に IP アドレスを割り振り直すことなくワークロードを双方向でシームレスに移動できるように、根底にあるネットワーキング・リソースを抽象化してパブリック・インターネットをトンネリングします。 HCX を使用すれば、VMware NSX をオンプレミスにインストールする必要はなくなり、VMware NSX は vSphere の古いバージョンに対して後方互換となります。  

単一ノード・トライアルは PoC (概念検証) のみを目的としています。 この環境では実動ワークロードを実行しないでください。 ホストやクラスターの追加と削除、追加アドオン・サービスの注文、更新の適用などの管理機能はサポートされていません。
{:important}

このトライアル版は最大 90 日間使用できます。 トライアル期間が終了したら、この環境を削除し、キャパシティーのニーズを満たす高可用性環境をプロビジョンできます。

アーキテクチャー設計について詳しくは、[Single-node Trial for vCenter Server on IBM Cloud の HCX on IBM Cloud アーキテクチャー設計](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html)を参照してください。

## Single-node Trial for vCenter Server インスタンスの技術仕様
{: #vc_trial_hybrid_orderinginstance-tech-specs}

Single-node Trial for vCenter Server インスタンスには以下のコンポーネントが含まれています。

標準化されたハードウェア構成の使用可否と価格は、デプロイメントに選択した {{site.data.keyword.CloudDataCent_notm}}によって異なる場合があります。
{:note}

### ベア・メタル・サーバー
{: #vc_trial_hybrid_orderinginstance-bare-metal}

Dual Intel Xeon Gold 5120 (28 コア、2.20 GHz) プロセッサー、384 GB の RAM を搭載。

### Single-node Trial for vCenter Server インスタンスのネットワーキング仕様
{: #vc_trial_hybrid_orderinginstance-networking-specs}

以下のネットワーキング・コンポーネントが注文されます。
*  10 Gbps デュアル・ネットワーク・アップリンク (パブリックとプライベート)
*  VLAN (仮想 LAN) 3 つ: パブリック VLAN 1 つとプライベート VLAN 2 つ
*  レイヤー 2 (L2) ネットワークに接続されたローカル・ワークロード間で実行される可能性のある東西通信用の DLR (分散論理ルーター) を備えた VXLAN (仮想拡張可能 LAN) 1 つ。 この VXLAN は、サンプルのルーティング・トポロジーとしてデプロイされるので、変更したり、作成の基礎として使用したり、削除したりできます。 また、DLR の新しい論理インターフェースに追加の VXLAN を接続してセキュリティー・ゾーンを追加することもできます。
*  以下の 2 つの VMware NSX Edge Services Gateway
  * アウトバウンド HTTPS 管理トラフィック用のセキュアな管理サービス VMware NSX Edge Services Gateway (ESG)。これは、管理ネットワーキング・トポロジーの一部として IBM がデプロイします。 この ESG は、IBM 管理 VM が、自動化に関連する特定の外部 IBM 管理コンポーネントと通信するために使用します。

    ユーザーは、この ESG にアクセスすることはできず、使用できません。 これを変更すると、{{site.data.keyword.vmwaresolutions_short}} コンソールから Single-node Trial for vCenter Server インスタンスを管理できなくなる可能性があります。 また、ファイアウォールを使用したり、外部 IBM 管理コンポーネントへの ESG 通信を無効にしたりすると、{{site.data.keyword.vmwaresolutions_short}} が使用不可になります。
    {:important}
  * アウトバウンドとインバウンドの HTTPS ワークロード・トラフィック用のユーザー管理のセキュアな VMware NSX Edge Services Gateway。これは、VPN アクセスまたはパブリック・アクセスを提供するためにユーザーが変更可能なテンプレートとして IBM がデプロイします。

### 仮想サーバー・インスタンス
{: #vc_trial_hybrid_orderinginstance-vsi}

以下の仮想サーバー・インスタンス (VSI) が注文されます。
* IBM CloudBuilder の VSI。これは、インスタンスのデプロイメントが完了した後にキャンセルされます。
* Microsoft Active Directory (AD) 用の Microsoft Windows Server VSI がデプロイされて参照可能になります。 この VSI がインスタンスの DNS として機能し、ここにホストと VM が登録されます。

### IBM 提供のライセンスおよび料金
{: #vc_trial_hybrid_orderinginstance-license-and-fee}

Single-node Trial for vCenter Server インスタンスの注文には、以下のライセンスが含まれています。
* VMware vSphere Enterprise Plus 6.5
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

Single-node Trial for vCenter Server インスタンスは、ライセンス持ち込みをサポートしていません。
{:note}

## VMware HCX on IBM Cloud の技術仕様
{: #vc_trial_hybrid_orderinginstance-hcx-tech-specs}

Single-node Trial for vCenter Server には、HCX on {{site.data.keyword.cloud_notm}} が含まれています。 以下のコンポーネントが注文されて HCX on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

オンプレミスの HCX インスタンスには、ライセンス交付とアクティベーションのみが含まれます。
{:note}

### HCX 管理用の VMware NSX Edge Services Gateways のアクティブ/パッシブ・ペア
{: #vc_trial_hybrid_orderinginstance-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* ディスク: 3 GB VMDK

### HCX 管理アプライアンス - 仮想マシン
{: #vc_trial_hybrid_orderinginstance-hcs-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* ディスク: 60 GB VMDK

構成時には必要に応じて、L2 接続、WAN 最適化、およびゲートウェイ接続のために追加の HCX アプライアンスがデプロイされます。

### HCX on IBM Cloud サービスのネットワーキング仕様
{: #vc_trial_hybrid_orderinginstance-hcx-networking-specs}

* 16 個の IP アドレスを持つ 1 つのパブリック・ポータブル・サブネット
* 64 個の IP アドレスを持つ 2 つのプライベート・ポータブル・サブネット
* プライベート・ポータブル vMotion サブネットからの 8 個の IP アドレス

## Single-node Trial for vCenter Server インスタンスの注文の要件と計画
{: #vc_trial_hybrid_orderinginstance-req}

以下の要件を満たし、以下の作業を完了していることを確認してください。
* オンプレミス HCX インスタンスの前提条件:
 * VMware vSphere および vCenter 5.5 以降が必要です。
 * vSphere 環境には、{{site.data.keyword.cloud_notm}} にマイグレーションされる VMx 用の分散スイッチが必要です。
 * HCX Manager 仮想アプライアンスが、オンプレミス環境のプライベート・ネットワークにデプロイできる状態であり、パブリック・インターネットにもアクセスできる状態でなければなりません。
 * {{site.data.keyword.vmwaresolutions_short}} を使用してインスタンスを注文するには、{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントが必要です。 インスタンス内で注文したコンポーネントの費用は、その {{site.data.keyword.cloud_notm}} アカウントに請求されます。
 *  **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャー資格情報を構成します。 {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「設定」**をクリックします。
 * インスタンス名の要件を確認します。
    * 英数字とダッシュ (-) の文字だけを使用できます。
    * インスタンス名の先頭と末尾は英数字である必要があります。
    * インスタンス名の最大の長さは 10 文字です。
    * インスタンス名はアカウント内で固有である必要があります。

## Single-node Trial for vCenter Server インスタンスを注文する手順
{: #vc_trial_hybrid_orderinginstance-procedure}

1. **「Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}}」**ページで、**「続行」**をクリックします。
2. **「Single-node Trial for VMware vCenter Server (Single-node Trial for VMware vCenter Server)」**ページで、{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントを要求するステップを実行するか、既存の**「ユーザー名」**と**「API キー」**を指定して**「取得」**をクリックします。

 API 鍵が既に存在する場合、このセクションは非表示になります。
 {:note}
3. インスタンス名を入力します。
4. インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。  

 デフォルトでは、DAL09 {{site.data.keyword.CloudDataCent_notm}}が事前選択されています。 必要に応じて別の {{site.data.keyword.CloudDataCent_notm}}の場所を選択します。
 {:note}
5. **「発注要約」**ペインで、インスタンス構成を確認してから注文を実行します。
   1. インスタンスの設定を確認します。
   2. インスタンスの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、インスタンスを注文する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

### 結果
{: #vc_trial_hybrid_orderinginstance-results}

インスタンスのデプロイメントが自動的に開始され、オンプレミスの HCX on {{site.data.keyword.cloud_notm}} サービス・アクティベーション・キーが注文されます。

#### HCX on IBM Cloud のデプロイメント・プロセス
{: #vc_trial_hybrid_orderinginstance-hcs-deploy-process}

HCX on {{site.data.keyword.cloud_notm}} のデプロイメントは自動的に行われます。 以下の手順が {{site.data.keyword.vmwaresolutions_short}} 自動化プロセスによって実行されます。
1. {{site.data.keyword.cloud_notm}} インフラストラクチャー上の HCX 用に、次の 3 つのサブネットが注文されます。
   * HCX 管理用のプライベート・ポータブル・サブネット 2 つ。
   * VMware でのアクティベーションやメンテナンスで使用されるパブリック・ポータブル・サブネットを 1 つ。 このサブネットは、HCX 相互接続にも使用されます。

   HCX 用に注文されたサブネット内の IP アドレスは、VMware on {{site.data.keyword.cloud_notm}} の自動化機能によって管理されるようになっています。 ユーザーが作成した VMware リソース (VM や NSX Edge など) にこれらの IP アドレスを割り当てることはできません。 VMware 成果物用に追加の IP アドレスが必要な場合は、{{site.data.keyword.cloud_notm}} 上の独自のサブネットを注文する必要があります。
   {:important}
3. HCX 用のリソース・プールと VM フォルダーが 3 つずつ作成されます。これらは、HCX 相互接続、ローカル HCX コンポーネント、リモート HCX コンポーネントに必要です。
4. HCX 管理トラフィック用の VMware NSX Edge Services Gateway (ESG) のペアがデプロイされ、構成されます。
   * 注文したサブネットに基づいて、パブリック・アップリンク・インターフェースとプライベート・アップリンク・インターフェースが構成されます。
   * ESG がエクストラ・ラージ・エッジ・アプライアンスのペアとして構成され、高可用性 (HA) が有効になります。
   * HCX Manager との間のインバウンドとアウトバウンドの HTTPS トラフィックが可能になるように、ファイアウォール・ルールとネットワーク・アドレス変換 (NAT) ルールが構成されます。
   * ロード・バランサー・ルールとリソース・プールが構成されます。 これらのルールとリソース・プールを使用して、HCX 関連のインバウンド・トラフィックが、HCX Manager および vCenter Server (Platform Services Controller が組み込まれたもの) の適切な仮想アプライアンスに転送されます。
   * ESG を通ってくる HCX 関連のインバウンド HTTPS トラフィックを暗号化するための SSL 証明書が適用されます。

   HCX 管理エッジは、オンプレミスの HCX コンポーネントとクラウド・サイドの HCX コンポーネントの間の HCX 管理トラフィック専用です。 HCX 管理エッジは、変更したり、HCX ネットワーク拡張に使用したりしないでください。 ネットワーク拡張用には別のエッジを作成してください。 また、ファイアウォールを使用したり、プライベート IBM 管理コンポーネントやパブリック・インターネットへの HCX 管理エッジ通信を無効にしたりすると、HCX の機能に悪影響を与える恐れがあります。
   {:important}

5. {{site.data.keyword.cloud_notm}} 上の HCX Manager がデプロイされ、アクティブにされ、構成されます。
   * HCX Manager が vCenter Server に登録されます。
   * HCX Manager、vCenter Server (Platform Services Controller が組み込まれたもの)、および NSX Manager が構成されます。
   * HCX フリートが構成されます。
   * ローカルとリモートの HCX デプロイメント・コンテナーが構成されます。
6. HCX Manager のホスト名と IP アドレスが VMware vCenter Server on {{site.data.keyword.cloud_notm}} の DNS サーバーに登録されます。

#### インスタンスの詳細の表示
{: #vc_trial_hybrid_orderinginstance-view-inst-details}

インスタンスの詳細を表示して、デプロイメントの状況を確認できます。 左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックし、**「vCenter Server インスタンス」**または**「オンプレミス HCX インスタンス」**表を見つけて、注文したインスタンスに関する情報を確認します。

インスタンスが正常にデプロイされると、このトピックの*技術仕様*セクションで説明しているコンポーネントが VMware 仮想プラットフォームにインストールされ、オンプレミスの HCX on {{site.data.keyword.cloud_notm}} サービス・アクティベーション・キーが**「オンプレミス HCX インスタンス」**表にリストされます。

インスタンスの状況が**「使用可能」**に変わり、E メールで通知が届きます。

### 次に行うこと
{: #vc_trial_hybrid_orderinginstance-next}

オンプレミス HCX Enterprise Manager をインストールし、HCX on {{site.data.keyword.cloud_notm}} インスタンスへの接続を構成します。

1. **「デプロイ済みインスタンス」**ページでオンプレミスのアクティベーション・キーを見つけます。
  1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
  2. **「vCenter Server インスタンス」**テーブルで、**「タイプ」**列を確認して vCenter Server 単一ノード・トライアル・インスタンスを見つけ、インスタンス名をメモします。
  3. **「オンプレミス HCX インスタンス」**表までスクロールし、**「名前」**列を確認して、注文した単一ノード・インスタンスと同じ名前に *-OnPrem* サフィックスが付いたインスタンスを見つけます。
  4. **「アクティベーション・キー」**フィールドの鍵をメモします。
2. オンプレミス HCX Enterprise Manager の Open Virtual Appliance (OVA) を、HCX on {{site.data.keyword.cloud_notm}} HCX Manager コンソールから取得します。
  1. HCX クラウド・コンソールに接続します。
    1. **「vCenter Server インスタンス」**表で、単一ノードの試用インスタンスをクリックしてインスタンスの詳細を表示します。
    2. **「アクセス情報」**で、vCenter 資格情報を見つけてメモします。
    3. 左側のナビゲーション・ペインの**「サービス」**をクリックします。
    4. **「サービス」**ページで、**「HCX on IBM Cloud」**をクリックします。
    5. **「HCX on IBM Cloud」**の詳細ページで、**HCX クラウド IP** を見つけてメモします。
    6. {{site.data.keyword.cloud_notm}} プライベート・ネットワークにアクセスするために VPN に接続していることを確認します。
    7. **「HCX クラウド・コンソールの表示 (View HCX Cloud Console)」**をクリックします。
  2. **「HCX クラウド・コンソール」**で、以下のステップを実行します。
      1. **「管理」**タブをクリックします。
      2. **「システム更新」**タブで、**「ダウンロード・リンクの要求」**をクリックします。
      3. **「リンクのコピー」**をクリックし、このリンクを使用して、オンプレミス vSphere 環境へのアクセス権限によって HCX Enterprise Client をオンプレミス環境にダウンロードします。
3. VMware vSphere Web Client で、HCX Enterprise Client を HCX Manager 仮想アプライアンス (HCX Manager) としてオンプレミス環境にデプロイします。 詳しくは、[Installing the HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html) を参照してください。

    オンプレミス HCX Manager をプライベート・ネットワークにデプロイし、パブリック・ネットワークへのアクセスを許可する必要があります。 NSX Edge、Vyatta、または類似のゲートウェイを使用して、オンプレミス HCX Manager へのインターネット・アクセスを許可することができます。 使用するゲートウェイがプライベート・ネットワーク・アクセスとパブリック・ネットワーク・アクセスとで異なる場合は、デフォルト・ゲートウェイを使用してパブリック・ネットワーク・アクセスを許可し、オンプレミスの**「HCX Manager 管理コンソール」**を使用して、プライベート・ネットワーク・アクセス用の静的ルートを作成することをお勧めします。  
    {:note}
4. ステップ 1 でメモしたオンプレミスのアクティベーション・キーを使用して、オンプレミスの HCX Enterprise Manager VM をアクティブ化します。
  1. OVA のデプロイ時に指定した資格情報を使用して、オンプレミスの HCX Enterprise Manager VM にログインします。
  2. プロンプトが出されたら、アクティベーション・キーを入力します。

  詳しくは、[HCX Activation and Initial Configuration](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html) を参照してください。
  {:note}
5. 自己署名 SSL 証明書が HCX on {{site.data.keyword.cloud_notm}} サービスによって生成されました。 以下のステップを実行して、その証明書をオンプレミス HCX Manager にインポートする必要があります。
    1. オンプレミスの**「HCX Manager 管理コンソール」**で、**「管理」**タブをクリックします。
    2. 左側のナビゲーション・ペインで、**「トラステッド CA 証明書」**をクリックし、右側の**「インポート」**をクリックします。
    3. **「URL」**をクリックし、適用する証明書の URL、つまり **HCX クラウド IP** (``https://<cloud-side public IP>``) を入力します。これは、{{site.data.keyword.vmwaresolutions_short}} コンソールの HCX on {{site.data.keyword.cloud_notm}} サービス詳細ページで確認できます。
    4. **「適用」**をクリックします。
6. 初期構成を続行し、相互接続を作成します。 詳しくは、[Installing and Configuring VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html) を参照してください。
7. VMware HCX のネットワークをオンプレミスから {{site.data.keyword.cloud_notm}} に拡張します。 詳しくは、[Extending Networks with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g) を参照してください。
8. オンプレミスと {{site.data.keyword.cloud_notm}} の間で VM をマイグレーションします。 詳しくは、[Migrating Virtual Machines with VMware HCX](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA) を参照してください。

{{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} インフラストラクチャー・コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。
これらのコンポーネントを {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されず、環境が不安定になります。
{:important}

## Single-node Trial for vCenter Server インスタンスを削除する手順
{: #vc_trial_hybrid_orderinginstance-deleting-procedure}

Single-node Trial for vCenter Server インスタンスを削除すると、以下のコンポーネントが順次解放されます。

1. デプロイされたすべてのサービス
3. VMware 製品ライセンス
4. ESXi サーバー
5. サブネット
6. VLAN

リソースに依存関係があるため、インスタンスのコンポーネントは、インスタンスを削除してもすぐには解放されません。 例えば、{{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルの終わりに、ESXi サーバーが {{site.data.keyword.cloud_notm}} によって完全に回収されるまで、サブネットと VLAN は削除できません。 {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常は 30 日) の最後に、サブネットと VLAN が削除され、インスタンスの削除が完了します。

削除したインスタンスについての {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
{:note}

Single-node Trial for vCenter Server インスタンスを削除するには、以下の手順を実行します。

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、削除するインスタンスを見つけます。
3. **「アクション」**列で削除アイコンをクリックします。
   インスタンスの状況が**「削除中」**に変わります。 インスタンスが正常に削除されると、インスタンスのコンポーネントが解放され、インスタンスの状況が**「削除済み」**に変わります。
4. {{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンス・レコードを削除する場合は、以下の手順を実行します。
   1. **「アクション」**列で削除アイコンをもう一度クリックします。
   2. **「インスタンスの削除」**ウィンドウで**「OK」**をクリックします。

## 関連リンク
{: #vc_trial_hybrid_orderinginstance-related}

* [Single-node Trial for vCenter Server on IBM Cloud の HCX on IBM Cloud アーキテクチャー設計](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html)
* [VMware Hybrid Cloud Extension の資料](https://hcx.vmware.com/#/vm-documentation)
* [Obtaining the HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)
