---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-24"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial for Migration and App Modernization インスタンスの注文、表示、および削除
{: #cloud_modern_bundle_orderinginstance}

Single-node Trial for Migration and App Modernization インスタンスを注文する前に、計画要件を確認してください。

## Single-node Trial for Migration and App Modernization インスタンスの注文の要件と計画
{: #cloud_modern_bundle_orderinginstance-req}

以下の要件を満たし、以下の作業を完了していることを確認してください。

### オンプレミス HCX インスタンスの前提条件
{: #cloud_modern_bundle_orderinginstance-hcx-req}

* VMware vSphere および vCenter 5.5 以降が必要です。
* vSphere 環境には、{{site.data.keyword.cloud_notm}} にマイグレーションされる VM 用の分散スイッチが必要です。
* HCX Manager 仮想アプライアンスが、オンプレミス環境のプライベート・ネットワークにデプロイできる状態であり、パブリック・インターネットにもアクセスできる状態でなければなりません。

### IBM Cloud インフラストラクチャー・アカウント
{: #cloud_modern_bundle_orderinginstance-account-req}

* {{site.data.keyword.vmwaresolutions_short}} を使用してインスタンスを注文するには、{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントが必要です。 インスタンス内で注文したコンポーネントの費用は、その {{site.data.keyword.cloud_notm}} アカウントに請求されます。
*  **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャー資格情報を構成します。 {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「設定」**をクリックします。

### インスタンス名の要件
{: #cloud_modern_bundle_orderinginstance-inst-name-req}

インスタンス名の要件を確認します。
* 英数字とダッシュ (-) の文字だけを使用できます。
* インスタンス名の先頭は英字、末尾は英数字でなければなりません。
* インスタンス名の最大の長さは 10 文字です。
* インスタンス名はアカウント内で固有である必要があります。

## Single-node Trial for Migration and App Modernization インスタンスを注文する手順
{: #cloud_modern_bundle_orderinginstance-procedure}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**をクリックしてから、**「仮想データ・センター」**セクションの**「Single-node Trial for Migration and App Modernization」**をクリックします。
2. **「Single-node Trial for Migration and App Modernization」**ページで、**「続行」**をクリックします。
3. {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントを要求するステップを実行するか、既存の**「ユーザー名」**と**「API キー」**を指定して**「取得」**をクリックします。

 API 鍵が存在する場合、このセクションは非表示になります。
 {:note}
4. インスタンス名を入力します。
5. インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。  

 デフォルトでは、DAL09 {{site.data.keyword.CloudDataCent_notm}} が事前選択されています。 必要に応じて別の {{site.data.keyword.CloudDataCent_notm}}の場所を選択します。
 {:note}
6. **「発注要約」**ペインで、インスタンス構成を確認してから注文を実行します。
   1. インスタンスの設定を確認します。
   2. インスタンスの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、インスタンスを注文する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

### 結果
{: #cloud_modern_bundle_orderinginstance-results}

インスタンスのデプロイメントが自動的に開始され、オンプレミスの HCX on {{site.data.keyword.cloud_notm}} サービス・アクティベーション・キーが注文されます。

#### HCX on IBM Cloud のデプロイメント・プロセス
{: #cloud_modern_bundle_orderinginstance-hcx-deploy-process}

HCX on {{site.data.keyword.cloud_notm}} のデプロイメントは自動的に行われます。 以下の手順が {{site.data.keyword.vmwaresolutions_short}} 自動化プロセスによって実行されます。
1. {{site.data.keyword.cloud_notm}} インフラストラクチャー上の HCX 用に、次の 3 つのサブネットが注文されます。
   * HCX 管理用のプライベート・ポータブル・サブネット 2 つ。
   * VMware でのアクティベーションやメンテナンスで使用されるパブリック・ポータブル・サブネットを 1 つ。 このサブネットは、HCX 相互接続にも使用されます。

   HCX 用に注文されたサブネット内の IP アドレスは、VMware on {{site.data.keyword.cloud_notm}} の自動化機能によって管理されるようになっています。 ユーザーが作成した VMware リソース (VM や NSX Edge など) にこれらの IP アドレスを割り当てることはできません。 ユーザーの VMware 成果物用に追加の IP アドレスが必要な場合は、独自のサブネットを {{site.data.keyword.cloud_notm}} に注文する必要があります。
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
{: #cloud_modern_bundle_orderinginstance-view-inst-details}

インスタンスの詳細を表示して、デプロイメントの状況を確認できます。 左側のナビゲーション・ペインの**「リソース」**をクリックし、**「vCenter Server インスタンス」**または**「オンプレミス HCX インスタンス」**表を見つけて、注文したインスタンスに関する情報を確認します。

インスタンスが正常にデプロイされると、このトピックの*技術仕様*セクションで説明しているコンポーネントが VMware 仮想プラットフォームにインストールされ、オンプレミスの HCX on {{site.data.keyword.cloud_notm}} サービス・アクティベーション・キーが**「オンプレミス HCX インスタンス」**表にリストされます。

インスタンスの状況が**「使用可能」**に変わり、E メールで通知が届きます。

### 次に行うこと
{: #cloud_modern_bundle_orderinginstance-next}

オンプレミス HCX Enterprise Manager をインストールし、HCX on {{site.data.keyword.cloud_notm}} インスタンスへの接続を構成します。

1. **「リソース」**ページでオンプレミスのアクティベーション・キーを見つけます。
  1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
  2. **「vCenter Server インスタンス」**表で、**「タイプ」**列を確認して Single-node Trial for Migration and App Modernization インスタンスを見つけ、インスタンス名をメモします。
  3. **「オンプレミス HCX インスタンス」**表までスクロールし、**「名前」**列を確認して、注文した単一ノード・インスタンスと同じ名前に *-OnPrem* サフィックスが付いたインスタンスを見つけます。
  4. **「アクティベーション・キー」**フィールドの鍵をメモします。
2. オンプレミス HCX Enterprise Manager の Open Virtual Appliance (OVA) を、HCX on {{site.data.keyword.cloud_notm}} HCX Manager コンソールから取得します。
  1. HCX クラウド・コンソールに接続します。
    1. **「vCenter Server インスタンス」**表で、Single-node Trial for Migration and App Modernization インスタンスをクリックしてインスタンスの詳細を表示します。
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
3. VMware vSphere Web Client で、HCX Enterprise Client を HCX Manager 仮想アプライアンス (HCX Manager) としてオンプレミス環境にデプロイします。 詳しくは、[Installing the VMware HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-HCX/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html) を参照してください。

    オンプレミス HCX Manager をプライベート・ネットワークにデプロイし、パブリック・ネットワークへのアクセスを許可する必要があります。 NSX Edge、Vyatta、または類似のゲートウェイを使用して、オンプレミス HCX Manager へのインターネット・アクセスを許可することができます。 使用するゲートウェイがプライベート・ネットワーク・アクセスとパブリック・ネットワーク・アクセスとで異なる場合は、デフォルト・ゲートウェイを使用してパブリック・ネットワーク・アクセスを許可し、オンプレミスの**「HCX Manager 管理コンソール」**を使用して、プライベート・ネットワーク・アクセス用の静的ルートを作成することをお勧めします。  
    {:note}
4. ステップ 1 でメモしたオンプレミスのアクティベーション・キーを使用して、オンプレミスの HCX Enterprise Manager VM をアクティブ化します。
  1. OVA のデプロイ時に指定した資格情報を使用して、オンプレミスの HCX Enterprise Manager VM にログインします。
  2. プロンプトが出されたら、アクティベーション・キーを入力します。

  詳しくは、[VMware HCX Activation and Initial Configuration](https://docs.vmware.com/en/VMware-HCX/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html) を参照してください。
  {:note}
5. 自己署名 SSL 証明書が HCX on {{site.data.keyword.cloud_notm}} サービスによって生成されました。 以下のステップを実行して、その証明書をオンプレミス HCX Manager にインポートする必要があります。
    1. オンプレミスの**「HCX Manager 管理コンソール」**で、**「管理」**タブをクリックします。
    2. 左側のナビゲーション・ペインで、**「トラステッド CA 証明書」**をクリックし、右側の**「インポート」**をクリックします。
    3. **「URL」**をクリックしてから、適用する証明書の URL を入力します。 これが、{{site.data.keyword.vmwaresolutions_short}} コンソールの HCX on {{site.data.keyword.cloud_notm}} サービス詳細ページに表示される **HCX クラウド IP** (``https://<cloud-side public IP>``) になります。
    4. **「適用」**をクリックします。
6. 初期構成を続行し、相互接続を作成します。 詳しくは、[Installing and Configuring VMware HCX Enterprise](https://docs.vmware.com/en/VMware-HCX/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html) を参照してください。
7. VMware HCX のネットワークをオンプレミスから {{site.data.keyword.cloud_notm}} に拡張します。 詳しくは、[Extending Networks with VMware HCX](https://docs.vmware.com/en/VMware-HCX/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html) を参照してください。
8. オンプレミスと {{site.data.keyword.cloud_notm}} の間で VM をマイグレーションします。 詳しくは、[Migrating Virtual Machines with VMware HCX](https://docs.vmware.com/en/VMware-HCX/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html) を参照してください。

{{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} インフラストラクチャー・コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。
これらのコンポーネントを {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されず、環境が不安定になります。
{:important}

## Single-node Trial for Migration and App Modernization インスタンスを削除する手順
{: #cloud_modern_bundle_orderinginstance-deleting-procedure}

Single-node Trial for Migration and App Modernization インスタンスを削除すると、以下のコンポーネントが順次解放されます。

1. デプロイされたすべてのサービス
3. VMware 製品ライセンス
4. ESXi サーバー
5. サブネット
6. VLAN

リソースに依存関係があるため、インスタンスのコンポーネントは、インスタンスを削除してもすぐには解放されません。 例えば、{{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルの終わりに、ESXi サーバーが {{site.data.keyword.cloud_notm}} によって完全に回収されるまで、サブネットと VLAN は削除できません。 {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常は 30 日) の最後に、サブネットと VLAN が削除され、インスタンスの削除が完了します。

削除したインスタンスについての {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
{:note}

Single-node Trial for Migration and App Modernization インスタンスを削除するには、以下の手順を実行します。

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、削除するインスタンスを見つけます。
3. **「アクション」**列で削除アイコンをクリックします。
   インスタンスの状況が**「削除中」**に変わります。 インスタンスが正常に削除されると、インスタンスのコンポーネントが解放され、インスタンスの状況が**「削除済み」**に変わります。
4. {{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンス・レコードを削除する場合は、以下の手順を実行します。
   1. **「アクション」**列で削除アイコンをもう一度クリックします。
   2. **「インスタンスの削除」**ウィンドウで**「OK」**をクリックします。

## 関連リンク
{: #cloud_modern_bundle_orderinginstance-related}

* [vCenter Server および IBM Cloud Private ガイド](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [IBM Cloud Private のチケットをオープン](https://www.ibm.com/mysupport/s/?language=en_US)
* [VMware HCX 資料](https://hcx.vmware.com/#/docs)
* [Obtaining the VMware HCX OVA](https://docs.vmware.com/en/VMware-HCX/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html?hWord=N4IghgNiBcIPICMAuYCWA7DBzABEgFgKY4ASAwgBo5wBqAgiAL5A)
