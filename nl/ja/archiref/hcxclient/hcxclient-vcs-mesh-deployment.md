---

copyright:

  years:  2019, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX オンプレミスのサービス・メッシュ
{: #hcxclient-vcs-mesh-deployment}

以下のセクションでは、HCX クライアント・インスタンスを構成する手順について詳しく説明します。
  1. VMware ソリューション向け IBM Cloud 環境のサイト・ペアリング
  2. HCX オンプレミス・ネットワーク・プロファイルの作成
  3. HCX オンプレミス・コンピュート・プロファイルの作成
  4. HCX サービス・メッシュの作成
  5. ネットワークの拡張

## VMware ソリューション向け IBM Cloud 環境のサイト・ペアリング
{: #hcxclient-vcs-mesh-deployment-sitepair}

1. vSphere Web Client にログインします。
2. **「ホーム」**メニューから**「HCX」**オプションを選択します。
3. **「インフラストラクチャー」**->**「相互接続 (InterConnect)」**の下にある**「サイト・ペアの追加 (Add Site Pairing)」**をクリックします。
   1. サイト Url: HCX Cloud Manager の URL
     * 例: `https://x.x.x.x.x`
   2. ユーザー名およびパスワード: HCX Manager Admin の詳細
     * admin / password
   3. 上記の詳細は、IBM Cloud Portal の**「サービス」**で、IBM Cloud for VMware ソリューション・インスタンスの HCX on IBM Cloud** から取得できます。
4. **「接続」**をクリックします

### 結果
{: #hcxclient-vcs-mesh-deployment-sitepair-results}

サイト・ペアリングが正常に登録されて、UI に表示されています。

## HCX オンプレミス・プロファイルの作成
{: #hcxclient-vcs-mesh-deployment-profiles}

## オンプレミス・サービス・メッシュのネットワーク・プロファイル
{: #hcxclient-vcs-mesh-deployment-profiles-network}

1. vSphere Web Client にログインします。
2. **「ホーム」**メニューから**「HCX」**オプションを選択します。
3. **「インフラストラクチャー」**->**「相互接続 (InterConnect)」**の下
4. マルチサイト・サービス・メッシュの下で、**「ネットワーク・プロファイル (Network Profiles)」**をクリックします
5. **「ネットワーク・プロファイルの作成 (Create Network Profile)」**から
   1. 「分散ポート・グループ (Distributed Port Group)」(「外部 (External)」など) を選択します
   2. 外部 IP の IP アドレス範囲を指定します
   3. 外部サブネットの接頭部の長さを指定します
   4. 外部ゲートウェイを指定します
   5. DNS の詳細を指定します
   6. MTU を 1500 に設定します。
   7. 「作成」をクリックします。
6. 管理ネットワークおよび vMotion ネットワークについて、上記の手順を繰り返します。
注: MTU は 9000 に設定する必要があります。

## 結果
{: #hcxclient-vcs-mesh-deployment-profiles-network-results}

| ネットワーク名 | MTU |
| -----| ----|
| 外部 | 1500|
| 管理 | 9000|
| vMotion | 9000|

## オンプレミス・サービス・メッシュのコンピュート・プロファイル
{: #hcxclient-vcs-mesh-deployment-profiles-compute}

1. vSphere Web Client にログインします。
2. **「ホーム」**メニューから**「HCX」**オプションを選択します。
3. **「インフラストラクチャー」**->**「相互接続 (InterConnect)」**の下
4. マルチサイト・サービス・メッシュの下で、**「コンピュート・プロファイル (Compute Profiles)」**をクリックします
5. **「コンピュート・プロファイルの作成 (Create Compute Profile)」**から
   1. コンピュート・プロファイル名を指定します
   2. 有効にするすべてのサービスを選択し、**「続行」**をクリックします。
   3. クラスターを選択し、**「続行」**をクリックします。
   4. データ・ストアを選択し、**「続行」**をクリックします。
   5. 管理のネットワーク・プロファイルを選択し、**「続行」**をクリックします。
   6. 外部/アップリンクのネットワーク・プロファイルを選択し、**「続行」**をクリックします。
   7. vMotion のネットワーク・プロファイルを選択し、**「続行」**をクリックします。
   8. vSphere 複製 (管理) のネットワーク・プロファイルを選択し、**「続行」**をクリックします。
   9. 拡張用の分散スイッチを選択します (例: Private-Switch)。
   10. 「完了」をクリックします。

## 結果
{: #hcxclient-vcs-mesh-deployment-profiles-compute-results}

クラスター/ストレージの組み合わせのコンピュート・プロファイルが作成され、サービス・メッシュの作成時に使用可能になります。

## HCX オンプレミスのサービス・メッシュ
{: #hcxclient-vcs-mesh-deployment-servicemesh}

## オンプレミス・サービス・メッシュの作成
{: #hcxclient-vcs-mesh-deployment-servicemesh-creation}

1. vSphere Web Client にログインします。
2. **「ホーム」**メニューから**「HCX」**オプションを選択します。
3. **「インフラストラクチャー」**->**「相互接続 (InterConnect)」**の下
4. マルチサイト・サービス・メッシュの下で、**「サービス・メッシュ (Service Mesh)」**をクリックします
5. **「サービス・メッシュの作成 (Create Service Mesh)」**から
   1. オンプレミスのサイトおよび vCloud 組織のサイトを選択し、「続行」をクリックします。
   2. ソース・コンピュート・プロファイルを選択します
   3. リモート・コンピュート・プロファイルを選択します。例: CloudCompute。
   4. すべてのサービスを選択し、「続行」をクリックします。
   5. 「拡張構成-アップリンク・ネットワーク・プロファイルのオーバーライド (Advanced Configuration - Override Uplink Network profiles)」ページ (オプション) で「続行」をクリックします。
   6. 「続行」をクリックします
   7. 「続行」をクリックし、「拡張構成 - WAN 最適化サービス帯域幅制限の構成 (Advanced Configuration - Configure WAN Optimization Service Bandwidth Limit)」ページのデフォルト設定をそのままにします
   8. サービス名を指定して、**「完了」**をクリックします
6. サービス・メッシュ作成のタスク・リストを参照します。その末尾には、オンプレミス・ロケーションに 3 つの HCX アプライアンス、そしてクラウド・ロケーションに 3 つの HCX アプライアンスがあるはずです。

## 結果
{: #hcxclient-vcs-mesh-deployment-servicemesh-results}

HCX サービス・メッシュは、ソース・サイトと宛先サイトのための有効な HCX サービス構成です。サービス・メッシュは、両方のサイトに有効な計算プロファイルが作成されている接続済みのサイト・ペアに追加できます。

サービス・メッシュを追加すると、両方のサイトで HCX 相互接続の仮想アプライアンスのデプロイメントが開始されます。相互接続サービス・メッシュは常にソース・サイトで作成されます。

## ネットワーク・ストレッチ
{: #hcxclient-vcs-mesh-deployment-network-stretching}

## ネットワークをストレッチするためのプロセス
{: #hcxclient-vcs-mesh-deployment-stretching-process-stretch}

HCX を利用してネットワーク (VLAN または VXLAN) をストレッチするには、クライアント・サイドの vCenter Web UI から以下のステップを実行します。

1. vSphere Web Client にログインします。
2. **「ホーム」**メニューから**「HCX」**オプションを選択します。
3. **「サービス」**->**「ネットワーク拡張」**の下にある左側のメニュー
4. **「ネットワークの拡張 (Extend Network)」**をクリックします。
   1. 拡張するネットワークを選択します
   2. 現在のデフォルトのゲートウェイとサブネット・マスクを CIDR 形式で入力します。
   3. 画面下部にある**「Stretch」**をクリックし、ネットワーク・ストレッチ・ワークフローを開始します。

ネットワークの進行状況のモニターは、vCenter Client の「Tasks」ペインで行います。

## ネットワーク・ストレッチの概念とベスト・プラクティス
{: #hcxclient-vcs-mesh-deployment-stretching-best-practices-network}

クライアント・サイドのネットワークをクラウド・サイドの VXLAN に橋渡しするためのかぎとなるのは、独自の HCX テクノロジーで構成される高度なマルチトンネル VPN です。 これは NSX を基礎とするものではありませんが、NSX と連携し、その機能を拡張します。 このプロセスは、クライアント・サイドの vCenter Web ユーザー・インターフェース (UI) によって制御され、デプロイメントを自動化し、クライアントとクラウドの両サイドのエンドポイントを確立します。 ストレッチ対象のネットワークの選択は、個別または一括で行います。

さらに、ネットワーク・ストレッチ・ワークフローの一環として、クラウド・サイドの NSX が権限を取得して VXLAN を構築します。その後 VXLAN が、クラウド・サイドの指定された L3 デバイス (未接続状態のままの DLR または ESG) およびクラウド・サイドのネットワーク拡張アプライアンスで作成されたインターフェースに接続します。

通常、アプリケーションをマイグレーションする場合は、対象の仮想マシン (VM) によって使用されているすべてのネットワークを {{site.data.keyword.cloud}} インスタンスにストレッチする必要があります。

上の文で「常に」ではなく「通常」と書かれているのはなぜでしょうか? VM のマイグレーション後に特定のトラフィックをクライアント・サイドから切断すると役立つことがあります。 例えば、VM ゲスト・バックアップ・クライアントの場合、クラウドに移動するときに高帯域幅を使用することがあります。 この VM がマイグレーションされるときにゲスト内バックアップ・クライアントは不要です。クラウド・サイドの最新のブロック・レベル・バックアップによって自動選択されるためです。

クライアント・バックアップ・ネットワーク・アダプターにはアクセスしません。そのようにすると、各 VM にアクセスしてゲスト内クライアント・バックアップ・スケジュールをシャットオフすることになるからです。 したがって、バックアップ・ネットワークを使用すると、バックアップが失敗することがあります。 これは、すべての VM がマイグレーション後の処理に到達してゲスト内バックアップ・クライアントを無効化できるようになるまでの一時的な状態です。

単一のネットワーク拡張の帯域幅は理論上 4 Gbps ですが、これは 1 組のネットワーク拡張のペア内に設定されたすべてのストレッチ・ネットワークを合わせた限度となるため、単一のストレッチ・ネットワークではその数値に到達不可能です。アンダーレーの帯域幅が十分に割り振られていて、待ち時間が短い (およそ 10 ミリ秒以下) 場合には、単一のストレッチ・ネットワークで約 1 Gbps を実現可能です。

### 隣接ルーティング・オプション
{: #hcxclient-vcs-mesh-deployment-stretching-prox-routing}

どのタイプの経路最適化機能も使用されていない場合、あらゆる L3 アクセスにおいて拡張ネットワークはクライアント・サイドに戻るようにルーティングされます。 このトロンボーン現象により、非効率的なトラフィック・パターンが生じます。パケットがクライアント (ソース) とクラウド間で行ったり来たりする必要があるからです (ソースと宛先の両方の VM がクラウド内に存在する場合であっても同様です)。 HCX の隣接ルーティング・フィーチャーは、この問題に対処してトラフィックのローカル出口を設けるように設計されています。

## 関連リンク
{: #hcxclient-vcs-mesh-deployment-deployment-related}

* [HCX のコンポーネントと用語集](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [インストール環境の準備](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX クライアントのデプロイメント](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [VMware Hybrid Cloud のマイグレーション](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [パラメーターとコンポーネントのモニター](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX のトラブルシューティング](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
