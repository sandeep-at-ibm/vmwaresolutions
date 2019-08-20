---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# HCX Client のデプロイメント
{: #hcxclient-vcs-client-deployment}

HCX インストールの最小構成は、1 つのクラウド・サイドと 1 つのクライアント・サイドのデプロイメントです。

HCX のクライアント・サイドは、HCX でサポートされているどのバージョンの vSphere にもインストールできます。
ただし、クライアント・サイドとクラウド・サイドの間にネットワーク接続があることが条件になります。

## 要件
{: #hcxclient-vcs-client-deployment-req}

| コンポーネント | CPU 数 | メモリー (GB) | ディスク (GB) |
|--------|--------|---------|-------|
| HCX Manager | 4 | 12G |  60G |
| HCX 相互接続 (HCX-IX) | 4 | 3G |  2G |
| HCX ネットワーク拡張 (HCX-NE) | 4 | 3G |  2G |
| HCX WAN 最適化プログラム (HCX-WAN) | 8 | 14G |  100G |

## クライアント・ライセンス交付
{: #hcxclient-vcs-client-deployment-licensing}

HCX はサービスです。 HCX のライセンスは、サイトごと、仮想マシン (VM) ごとに交付され、VMware 管理下のライセンス・サーバーで管理されます。 HCX のクラウド・サイドとクライアント・サイドのインスタンスでは、
ライフサイクル全体で VMware 登録サイトとの通信が必要になります。
- 80 と 443 で `https://connect.hybridity.vmware.com` へのトラフィックを許可する必要があります。
- クライアント・サイドのインストールで使用する一回限りの登録キーが {{site.data.keyword.vmwaresolutions_full}} コンソールで提供されます。クライアント・サイドの HCX インストールごとにキーが必要です。

### オンプレミス HCX ライセンスを注文する手順
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「オンプレミス HCX ライセンス」**テーブルにスクロールして、**「新規プロビジョン」**をクリックします。
3. ライセンス名を指定します。
4. 注文に適用される条件のリンクをクリックして、ライセンスを注文する前にこれらの条件に同意しておく必要があります。
5. **「プロビジョン」**をクリックします。

## IP アドレス要件
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

HCX をデプロイするためには、オンプレミスとターゲット IBM Cloud の両方に適切な数の IP アドレスを用意する必要があります。

* vMotion アドレス
  オンプレミスのデータ・センターでは、vMotion 用に専用のネットワークを用意することが一般的です。 その vMotion ネットワークにクラウド・ゲートウェイからアクセスできなければなりません。 アクセスできない場合、vMotion ネットワークと通信するための追加の IP アドレスが必要になります。

* オンプレミス
  * HCX Manager アプライアンス用に IP アドレス 1 つ。
  * 各相互接続アプライアンス用に 1 つずつ。vMotion 専用のネットワークがある場合はさらに 1 つ追加します。
  * 各標準ネットワーク拡張用に 1 つずつ

* IBM Cloud
  * IBM Cloud に接続する HCX Manager アプライアンス 1 つにつき 2 つの IP アドレス。 これらのアドレスを使用して、インターネットまたは 1 つ以上の専用接続回線に接続できます。
  * vMotion 専用のネットワーク接続がある場合はさらに 1 つ追加します。

## クライアント・サイド OVA のダウンロード
{: #hcxclient-vcs-client-deployment-client-ova}

クライアント・サイドの HCX は、ユーザーがデプロイします。それにはソース vCenter に対する管理者レベルの許可が必要です。 この資料の執筆時点で、HCX のクライアント・サイド・マネージャーの OVA は約 1.7 GB です。 {{site.data.keyword.vmwaresolutions_short}} コンソールを使用して HCX を注文する場合は、
クラウド・サイドにデプロイされている HCX のバージョンに合ったバージョンの HCX を
クライアント・サイドにダウンロードするためのリンクという形で URL が提供されます。 そのリンクは、クラウド・サイドの HCX Manager ユーザー・インターフェース (UI) に表示されます。

一回限りの登録キーも提供されます。 以下の手順でユーザー登録を構成できます。

1. クラウド・サイドの HCX UI に表示されるリンクから HCX クライアント (エンタープライズ) OVA をダウンロードします。
    1. IBM 提供の HCX 登録 UI を使用してクラウド・サイドの HCX UI にログインします。
    2. クラウド vCenter の ID とパスワードを使用して UI にログインします。
    3. **「Administration」**タブで**「request download link」**を選択して、クライアント・サイドの OVA をダウンロードします。 OVA のデプロイ先のソース vCenter にあるローカルのジャンプ・ボックスを使用して、この手順を実行します。

## ソースでの HCX の構成およびインストール
{: #hcxclient-vcs-client-deployment-install-cfg-src}

オンプレミスへのインストールでは、HCX 管理アプライアンスをデプロイし、それを vCenter 環境に登録する必要があります。

### HCX Manager アプライアンスのインストール
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

HCX Manager アプライアンスをオンプレミス vCenter にインストールします。
1. **「My VMware」**にログインし、製品のダウンロード・ページから Hybrid クラウド・サービスの OVA ファイルをダウンロードします。
2. ブラウザーを開き、vSphere Web Client にログインします。 **「ホーム」**タブを表示します。
3. **「インベントリ ツリー」**リストで、**「ホストおよびクラスタ」**をクリックします。
4. 階層を展開して、データ・センターを表示します。
5. ターゲット・データ・センターを右クリックし、メニューから**「OVF テンプレートのデプロイ」**を選択します。 **「OVF テンプレートのデプロイ」**メニュー項目が表示されるまで数秒かかることがあります。
6. **「OVF テンプレートのデプロイ」**を選択します。
  1. **「ローカル ファイル」**を選択し、**「参照」**をクリックし、コンピューターにダウンロードした OVA ファイルを見つけます。 **「次へ」**をクリックします。
  2. **「詳細の確認」**ページで、**「追加の構成オプションの承諾」**ボックスにチェック・マークを付け、**「次へ」**をクリックします。
  3. **「EULA の承諾」**ページをスクロールダウンして VMware ユーザー・ライセンス契約条件を確認します。 **「承諾」**をクリックし、**「次へ」**をクリックします。
  4. **「名前およびフォルダの選択」**ページで、必要に応じて名前を編集し、ハイブリッド・クラウド・サービスの場所を選択します。 **「次へ」**をクリックします。
  5. **「リソースの選択」**ページで、インストール場所を選択します。
  6. **「ストレージの選択」**ページで、ハイブリッド・クラウド・サービスのストレージを選択し、**「次へ」**をクリックします。 **「仮想ディスク フォーマットの選択」**リストから、**「シン プロビジョニング」**または**「シック プロビジョニング」**を選択できます。
  7. **「ネットワークのセットアップ」**ページで、ハイブリッド・クラウド・サービスのアダプターを、**「宛先」**リストから選択したホスト・ネットワークにマップします。
7. **「テンプレートのカスタマイズ」**ページで、環境に固有の以下の値を入力します。
  * パスワードについては、コマンド・ライン・インターフェース (CLI) と Web ユーザー・インターフェースの両方とも、デフォルト・ユーザー名は **admin** です。 Web ユーザー・インターフェースにログインするための **admin** ユーザーとパスワードだけでなく、パスワードを設定できる **root** ユーザー・アカウントも必要です。
  * CLI の **admin** ユーザーのパスワードを入力し、再入力します。
  * **root** ユーザーのパスワードを入力し、再入力します。 将来、VMware Global Support Services (GSS) の支援が必要になったときには、このパスワードを伝えてシステムをトラブルシューティングしてもらう必要があります。
  * ネットワーク・プロパティーについては、HCX Manager VM のホスト名を入力します。 ネットワークの IPv4 アドレス、IPv4 プレフィックス (CIDR)、およびデフォルト・ゲートウェイを入力します。 次の表に、各値の例を示します。

表 1. ネットワーク・プロパティーの値の例

| フィールド                    | 値           |
|--------------------------|-----------------|
| ホスト名                 | HCM_1           |
| ネットワーク 1 の IPv4 アドレス   | 192.168.200.101 |
| ネットワーク 1 の IPv4 プレフィックス    | 24              |
| デフォルト IPv4 ゲートウェイ     | 192.168.200.1   |
| ネットワーク 1 の IPv6 アドレス   |                 |
| ネットワーク 1 の IPv6 プレフィックス    |                 |

8. 「vService バインド」ページを確認します。 **「次へ」**をクリックして先に進みます。
9. **「終了準備の完了」**ページで、以下の手順を実行します。
  * **「デプロイメント後にパワーオン」**ボックスにチェック・マークを付けます。
  * ハイブリッド・クラウド・サービスの設定を確認し、**「終了」**をクリックします。 ハイブリッド・クラウド・サービスのアプライアンスが電源オンになるまで数分かかることがあります。
  * 状況を確認するには、vSphere Web Client のホーム・ページに移動し、**「ホーム」**タブの**「インベントリ」**に移動し、**「ホストおよびクラスタ」**をクリックします。 データ・センターの階層を展開し、ハイブリッド・クラウド・サービスの仮想マシンをクリックして、中央のペインにサマリーを表示します。
  * **「サマリ」**タブを表示すると、コンソールに**「パワーオン」**と表示され、**「再生」**アイコンが緑色になっています。
10. HCX Manager が電源オンになり、オンプレミス vCenter に登録する準備ができました。

## HCX Manager アプライアンスの初期構成
{: #hcxclient-vcs-client-deployment-inital-config}

1. ハイブリッド・クラウド・サービスの仮想アプライアンスが `https://connect.hcx.vmware.com` にアウトバウンド・アクセスできることを確認します。
2. ハイブリッド・クラウド・サービスの仮想アプライアンスの管理インターフェース `https://<IP>: 9443` に **admin** でログインします。
3. クライアント・サイドの前提条件で収集されたライセンス・キーを指定します。
4. HCX クラウドのデータ・センターの場所
    - HCX クラウド・インスタンスが存在するデータ・センターに最も近い都市を入力します。 そのような都市が存在しない場合は、最も近い主要都市を選択します。
5. システム名を指定します

## vSphere サーバー証明書のインポート
{: #hcxclient-vcs-client-deployment-import-cert}

1. HCX Manager の管理インターフェース `https://<IP>:9443` にログインします
2. **「証明書」**->**「トラステッド CA 証明書」**の下にある**「管理」**タブを選択します。
3. vSphere サーバー Web サイトのインポート
   1. URL から証明書をインポートするオプションを選択し、HCX クラウド・サイド登録 URL を入力します。
     * サンパウロ: `https://ssao01dirhcx01.vmware-solutions.cloud.ibm.com`

## HCX Manager を vCenter/SSO/NSX に登録する手順
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. ハイブリッド・クラウド・サービスのサービス仮想アプライアンスにログインします。
2. **「ダッシュボード」**ペインで、以下の手順を実行します。
  1. 左のペインの**「システムの構成 (Configure Systems)」**で、vCenter を選択します。
  2. 右上の**「vCenter の追加 (Add vCenter)」**をクリックします。
  3. vCenter Server の IP アドレスを `https://vCenter-host-name` または `https://vCenter-IP-address` という形式で入力します。 例えば、`https://My-vCenter` や `https://10.108.26.211` などです。
  4. vCenter Server のユーザー名とパスワードを入力します。 使用するアカウントには、vCenter 管理者の役割が必要です。
  5. **「OK」**をクリックします。 _「アプリを再始動する必要があります (You need to restart the app)」_ というメッセージが表示された場合は、再始動しないでください。
3. SSO/ルックアップ・サービスを構成します。
  6. **「管理」**タブをクリックします。
  7. **「ルックアップ・サービス URL (Lookup Service URL)」**テキスト・ボックスの横にある**「編集」**をクリックします。
  8. ルックアップ・ネットワーク・サービス・エンドポイントを次の形式で入力します。
    * vCenter Server 6.5 の場合は `https://psc/`
  9.  必要に応じて NSX の詳細を指定します。
  10. **「OK」**をクリックします。 Web エンジンを再始動するメッセージが表示された場合は、再始動しないでください。
4. **「サマリー」**タブをクリックし、**「ハイブリッド管理コンポーネント (Hybridity Management Components)」**セクションを見つけます。 アプリケーション・エンジンと Web エンジンの両方を停止してから始動してください。
5. 登録を確定するには、vSphere Web Client をログアウトします。 vSphere Web Client に再度ログインして、HCX タブが存在することを確認します。

## 結果
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

左側に既存の**「ハイブリッド・クラウド (Hybrid Cloud)」**アイコンと**「ハイブリッド・クラウド・サービス (Hybrid Cloud Services)」**メニュー項目があることに注目してください。 ハイブリッド・クラウド・サービスを登録すると、これらのラベルが更新されます。 インベントリーで、アイコンのラベルが**「ハイブリッド・クラウド・サービス (Hybrid Cloud Services)」**になります。

## 関連リンク
{: #hcxclient-vcs-client-deployment-related}

* [HCX のコンポーネントと用語集](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [インストール環境の準備](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX オンプレミスのサービス・メッシュ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud のマイグレーション](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [パラメーターとコンポーネントのモニター](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX のトラブルシューティング](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
