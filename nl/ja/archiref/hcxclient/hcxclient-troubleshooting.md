---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX のトラブルシューティング
{: #hcxclient-troubleshooting}

HCX での一般的な問題と修正方法については、以下の情報を参照してください。

## HCX クライアント・ユーザー・インターフェースに関する問題
{: #hcxclient-troubleshooting-hcx-client-issues}

### HCX ユーザー・インターフェースのトークンのタイムアウト
{: #hcxclient-troubleshooting-hcx-ui-issues}

一般的に、vCenter ユーザー・インターフェース (UI) を一定時間開いたままにすると、HCX UI でタイムアウトが発生する可能性があります。 これは、HCX Manager サーバーに対するログイン・トークンのタイムアウトが原因で発生します。 vSphere Web UI からログアウトし、再度ログインして、トークンをリフレッシュしてください。

### HCX クライアント UI でダッシュボード画面上のすべてのメトリックに「NaN」が表示される
{: #hcxclient-troubleshooting-nan-display}

これは、現在ログイン中の vCenter アカウントの許可と関連した問題です。 HCX のクラウド・サイドのアプライアンス・マネージャー UI で、Enterprise Administrator グループが設定されていることを確認してください。

## マイグレーションの問題
{: #hcxclient-troubleshooting-mig-issues}

HCX の現行バージョンで発生するマイグレーションの問題は、通常、ライセンス交付、クラウド・ゲートウェイのネットワーキング接続、宛先ハードウェアの互換性という 3 つのカテゴリーに分類できます。

### ライセンス交付
{: #hcxclient-troubleshooting-licensing}

ライセンス交付の問題が原因でマイグレーションが失敗した場合、現行バージョンの HCX は、vCenter UI 内のクライアント Web UI で、この問題を明確に示したエラー・メッセージを表示します。

### ネットワーク (WAN) 接続
{: #hcxclient-troubleshooting-wan-connect}

WAN 接続に問題がある場合はいつでも、HCX UI 内の**「Interconnect」->「HCX Components」**画面で確認トンネル状況を確認してください。 通常、フリート・コンポーネントを再設定したりリブートしたりする必要はありません。 WAN 接続が復旧すると、自動的に再接続されます。

HCX Manager (クライアントおよびクラウド) にフィックスと更新が適用されていて、それらの更新によってフリート・コンポーネントの問題も修正されている場合は、デプロイ済みのクラウド・ゲートウェイとすべての L2C を再デプロイする必要があります。 SSH クライアント (ccli など) を使用して HCX Manager に接続することで、トンネル状況のデバッグをさらに行うことができます  

1. admin アカウントと指定パスワードを使用して、HCX Manager に SSH で接続します。
2. `su –` コマンドを実行し、`root` ユーザーのパスワード (admin パスワードと同じ) を入力して root に変更します。
3. ディレクトリーを `/opt/vmware/bin` に変更し、`./ccli` コマンドを実行します。 root の環境がセットアップされていないためにこの試行が失敗した場合は、`./ccliSetup.pl` コマンドを実行してください。
4. `ccli` シェル内で `list` コマンドを実行して、HCX Manager に登録されているフリート・コンポーネントをリストします。
5. リストされたフリート・コンポーネントの ID を入力して、`ccli` のフリート ID を指定します。 例えば、`go 8` と入力します。
6. SSH を使用して目的のフリート・コンポーネントに接続するために、`debug remoteaccess enable` コマンドを実行します。
7. `ccli` を終了し、SSH が有効になったフリート・コンポーネントの IP アドレスに、SSH を使用して接続します。
9. トラブルシューティングを続行します。
10. `ccli` に戻り、当該コンポーネントに対する `ssh` サービスを無効にします。
11. 必要に応じて、`hc` ccli コマンドを使用して、そのコンポーネントのヘルス・チェックを実行します。

## 宛先ハードウェアの互換性の問題
{: #hcxclient-troubleshooting-hw-compatibility}

クライアント・ソース・サイドのハードウェア・バージョンと vSphere リリースが、クラウドのものより新しい場合、vMotion のマイグレーションで問題が生じる可能性があります。 レプリケーション・ベースのマイグレーションでは、宛先サイドで新規作成された仮想マシン (VM) にデータをコピーするため、マイグレーション・タイプを「一括マイグレーション」に変更すれば、大多数のケースでマイグレーションが成功するはずです。

## ストレッチ L2 コンセントレーターの問題
{: #hcxclient-troubleshooting-stretched-l2}

L2 コンセントレーター (L2C) の操作で問題が発生することはほとんどありません。 CGW と同様、L2C は接続が失われても、ネットワーク接続が復旧すると自動的に再接続されます。 ccli シェルを使用して、ヘルス状況と動作状況を確認してください。 SSH が有効になり、L2C が接続された後に、`ip tunnel` コマンドと `ip link |grep t_` コマンドを実行して、トンネルの状況を確認してください。

## 関連リンク
{: #hcxclient-troubleshooting-related}

* [HCX のコンポーネントと用語集](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [インストール環境の準備](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX クライアントのデプロイメント](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX オンプレミスのサービス・メッシュ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud のマイグレーション](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [パラメーターとコンポーネントのモニター](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
