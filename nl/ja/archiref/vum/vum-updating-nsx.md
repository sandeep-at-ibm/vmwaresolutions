---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

# NSX の更新
{: #vum-updating-nsx}

ここでは、NSX の更新プロセスの例を紹介します。 アップグレード先の NSX バージョンの更新プロセスについては、VMware のガイドを参照してください。

NSX と vSphere の両方をアップグレードする必要がある場合、NSX VIB がホストにインストールされている ESXi のバージョンに固有であることから、VMware で最初に NSX アップグレードを完了した後に vSphere アップグレードを完了することをお勧めします。 ただし、手動で行った場合には、本書で説明しているように、以下のワークフローを使用して一度に 1 つのホストで VUM を使用することをお勧めします。

1. **ESXi をアップグレードする** - ESXi のアップグレードが完了すると、ホストは保守モードから出ますが、次の手順が完了するまで、論理スイッチに接続されている VM をホストに移動してはいけません。
2. **NSX VIB をアップグレードする** - VIB がアップグレードされ、ホストが保守モードから出たら、論理スイッチに接続されている VM をホストに移動できます。

NSX は、_my.vmware.com_ からのダウンロードを使用して NSX Manager を更新することで更新されます。 したがって、更新をダウンロードするにはアカウントが必要です。 VMware vCenter Server on {{site.data.keyword.cloud_notm}} インスタンスで {{site.data.keyword.cloud}} サブスクリプション・ライセンスを使用している場合、**my.vmware.com** アカウントを使用して更新をダウンロードすることはできません。 そのため、[IBM サポートに連絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)する必要があります。

更新を開始する前に、NSX ノートでアップグレードに関する問題や回避策を確認してください。 リリース・ノートを使用して、vCenter が NSX の新しいシステム要件を満たしていることを確認します。

VMware ビジネス・パートナーから追加のソフトウェアをインストールした場合は、互換性およびアップグレードの詳細についてビジネス・パートナーの資料を参照してください。 vCenter Server のプライマリー・インスタンスとセカンダリー・インスタンスをデプロイしており、vCenter をまたぐ NSX 環境を使用している場合は、リリース・ノートを参照して適切なアップグレード・プロセスを確認してください。

Cross-vCenter NSX 環境では、最初に NSX Manager のプライマリー・アプライアンスが更新された後、NSX Manager のすべてのセカンダリー・アプライアンスが更新されます。
**ダウングレードはサポートされていない**ため、アップグレードに進む前に NSX Manager のバックアップを取ります。これにより、すべての NSX Edge 構成、論理ルーター、および Edge Services Gateway が、NSX Manager のバックアップの一部としてバックアップされます。

NSX Manager が正常にアップグレードされた後に NSX をダウングレードすることはできません。 保守アクティビティーは合意した保守ウィンドウで実行することをお勧めします。そのため、企業のガイダンスに従ってください。 ダウン時間を最小化し、機能に関する問題を減らすために、すべての NSX コンポーネントを単一の停止ウィンドウでアップグレードすることをお勧めします。 NSX アップグレード・プロセスには時間がかかることがあるため、NSX デプロイメントのアップグレード順序を理解することが重要です。
* NSX Manager
* NSX Controller クラスター
* NSX ホスト・クラスター
* Edge Services Gateway は、NSX Manager をアップグレードした後にいつでもアップグレードできます。
* ゲスト・イントロスぺクションを使用する場合は、リリース・ノートの指示に従ってください。

ワークフローは、以下のとおりです。
1. ジャンプ・サーバーにログインしてから、ブラウザーを開きます。
2. _my.vmware.com_ 資格情報を使用してダウンロード・セクションにナビゲートし、_NSX for vSphere_ を検索します。
3. 必要なバージョンを選択します。
4. ダウンロード・ページで、**「Upgrade Bundle, Download Now」**を選択します。
5. 適切なフォルダーにダウンロードします。
6. **NSX Manager をアップグレードします**。
  - IBM Cloud for VMware Solutions コンソールに記載されている IP アドレスと資格情報を使用して NSX Manager 仮想アプライアンスにログインし、ホーム・ページの「Upgrade」ボタンをクリックします。
  - NSX Manager にログインします。
  - **「Appliance Management」**で、**「Backups & Restore」**をクリックします。
  - 「Backup」をクリックして、適切なファイル名を入力します。 VMware は、NSX Manager データを復元する前に NSX Manager 装置を再インストールすることを推奨しています。 既存の NSX Manager アプライアンスでのリストア操作は機能しますが、正式にはサポートされていません。 ベスト・プラクティスは、新しくデプロイされた NSX Manager アプライアンスの IP 情報とバックアップ・ロケーション情報を指定する際に使用できるように、NSX Manager アプライアンスの IP 設定をメモしておくことです。
  - 右上の**「Upload Bundle」**をクリックして、_my.vmware.com_ からダウンロードしたファイルをアップロードします。
  - アップグレード情報を読み、SSH を有効にして VMware カスタマー・エクスペリエンス向上プログラムに参加するかどうかを選択します。
  - **「Upgrade」**をクリックします。
  - アップロードが完了すると、NSX Manager ログイン・ページにリダイレクトされます。 再度ログインして、現在のソフトウェア・バージョンの表示が正しいことを確認します。
7. **NSX Controller クラスターをアップグレードします。**:
  - vSphere Web Client を開き、VCSA にログインします。
  - **「Home」** > **「Networking & Security」** > **「Installation」**にナビゲートし、**「Management」**タブを選択して、「Controller Cluster Status」列で**「Upgrade Available」**を選択します。
  - 環境内のコントローラーは、一度に 1 つずつアップグレードおよびリブートされます。 アップグレードを開始すると、システムではアップグレード・ファイルをダウンロードして各コントローラーをアップグレードし、各コントローラーを再始動して、各コントローラーのアップグレード状況を更新します。
8. **NSX ホスト・クラスターをアップグレードします**。
  - NSX Manager と NSX Controller をアップグレードした後、ホスト・クラスターでは vSphere ESXi ホスト上の NSX VIB が更新されます。
  - vSphere Web Client で、**「Home」** > **「Networking & Security」** > **「Installation」**にナビゲートし、**「Host Preparation」**タブを選択します。 アップグレードするクラスターごとに、**「Upgrade available」**をクリックします。 「Installation Status」に「Installing」と表示されます。
  - クラスターの「Installation Status」には、_「Not Ready」_と表示されます。 詳細を表示するには**「Not Ready」**をクリックし、VIB インストールの完了を試行するには**「Resolve all」**をクリックします。 アップグレードを完了するために、ホストは保守モードになり、必要に応じてリブートされます。 「Installation Status」列に「Installing」と表示されます。 アップグレードが完了すると、「Installation Status」列に緑色のチェック・マークとアップグレードされた NSX バージョンが表示されます。
9. **Edge Services Gateway** では、次のようになります。
  - アップグレード・プロセス中に、新しい Edge 仮想アプライアンスが既存のものと一緒にデプロイされます。 新しい Edge の準備ができると、古い Edge の vNIC は切断され、新しい Edge の vNIC が接続されます。 次に、新しい Edge により無償の ARP (GARP) パケットが送信され、接続されたスイッチの ARP キャッシュが更新されます。 HA がデプロイされている場合、アップグレード・プロセスは 2 回実行されます。 このプロセスは、パケット転送に一時的に影響を与える可能性があります。
  - vSphere Web Client で、**「Networking & Security」** > **「NSX Edges」**を選択します。 NSX Edge インスタンスごとに、**「Actions」**メニューから**「Upgrade Version」**を選択します。
  - NSX Edge が正常にアップグレードされると、「Status」は「Deployed」になり、「Version」列に新しい NSX バージョンが表示されます。 Edge がアップグレードに失敗し、古いバージョンにロールバックされない場合は、**「Redeploy NSX Edge」**アイコンをクリックしてから、アップグレードを再試行します。

## 関連リンク
{: #vum-updating-nsx-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_full}} デモ](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (デモンストレーション)
