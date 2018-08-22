---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# NetApp ONTAP Select インスタンスの表示

異なるユーザー・アカウントについてプロビジョンされた NetApp ONTAP Select インスタンスのサマリーと詳細情報を表示します。

## NetApp ONTAP Select インスタンスのサマリーの表示

1 つのユーザー・アカウントについてプロビジョンされたすべての NetApp ONTAP Select インスタンスのサマリーを表示するには、以下の手順を実行します。

1. {{site.data.keyword.vmwaresolutions_full}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. コンソールの右上隅でアバターをクリックし、**「アカウント」**フィールドをクリックして、インスタンスを確認するユーザー・アカウントを選択します。
3. **「NetApp ONTAP Select インスタンス」**の表で、選択されたユーザー・アカウントでプロビジョンされたインスタンスのリストを表示します。

表 1. NetApp ONTAP Select インスタンスの項目

| 項目        | 説明       |  
|:------------- |:--------------- |
| 名前 | インスタンスの名前。 |
| バージョン | インスタンスのバージョン。 |  
| ロケーション | インスタンスがホストされるデータ・センター。 |
| 作成時間 | インスタンスが作成された日時。 |   
| 状況 | インスタンスの状況。 状況は、以下のいずれかの値になります。<ul><li>作成中: インスタンスは作成中です。</li><li>構築中: インスタンスは構成中です。</li><li>使用可能: インスタンスは使用可能です。</li><li>変更中: インスタンスは変更中です。</li><li>失敗: 作成、構成、または変更のプロセスが失敗しました。</li><li>削除中: インスタンスは削除中です。</li><li>削除エラー: インスタンスの削除中にエラーが発生しました。</li><li>削除済み: インスタンスは削除されました。</li></ul>|

## NetApp ONTAP Select インスタンスのプロパティーの詳細の表示

インスタンスのプロパティーの詳細を表示するには、次の手順を実行します。

1. **「NetApp ONTAP Select インスタンス」**テーブルで、インスタンス名をクリックします。
2. **「プロパティー」**の下で、インスタンスの詳細を確認します。

表 2. NetApp ONTAP Select インスタンスのプロパティー

| プロパティー        | 説明       |
|:--------------- |:----------------- |
| 名前 | インスタンスの名前。 |
| ID | インスタンスの ID。 |
| ロケーション | インスタンスがホストされるデータ・センター。 |
| デプロイ済みのバージョン | デプロイ済みバージョンの {{site.data.keyword.vmwaresolutions_short}}。 |
| vCenter バージョン | VMware vCenter Server のバージョン。<br><br>**注**: {{site.data.keyword.vmwaresolutions_short}} コンソールと VMware vSphere Web Client では、vCenter Server バージョンの表示が若干異なります。 どちらも正しい表示です。 |
| NSX for vSphere | VMware NSX for vSphere 製品のバージョン。 |
| NSX ライセンス・エディション | VMware NSX ライセンスのバージョンとエディション。 |
| NetApp バージョン | NetApp ONTAP Select のバージョン。 |
| NetApp ライセンス・タイプ | NetApp ONTAP Select ライセンスのタイプ。 |
| DNS、ルート・ドメイン | ルート・ドメイン・ネームは、インスタンスの DNS (ドメイン・ネーム・システム) ドメイン・ネームと Microsoft Active Directory (AD) フォレスト・ルート名です。 |
| DNS、SSO ドメイン | SSO ドメインは、vSphere のシングル・サインオン・ドメインです。 デプロイされたすべての NetApp ONTAP Select インスタンスで、SSO ドメイン・ネームが値 `vsphere.local` に設定されています。 |
| DNS、サブドメイン | サブドメインは、ローカル NetApp ONTAP Select インスタンスのホスト名が存在するルート・ドメイン・ネームの DNS サブドメイン名です。 サブドメイン名の形式は `<subdomain_label>.<root_domain>` になります。 |
| 状況 | インスタンスの状況。 |

## NetApp ONTAP Select インスタンスのアクセス情報の表示

**「アクセス情報」**の下に、インスタンス関連コンポーネントのアクセス情報が表示されます。 以下のパスワードは、システムで生成される初期パスワードです。 それらを {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、インスタンスのサマリー・ページでは更新されません。

表 3. NetApp ONTAP Select インスタンス関連コンポーネントのアクセス情報

| コンポーネント        | 説明       |
|:---------------- |:----------------- |
| AD/DNS IP | 2 つの AD サーバーの IP アドレス。 |
| AD/DNS FQDN | AD/DNS サーバーの完全修飾ドメイン・ネーム。 |
| AD/DNS ADMIN (Remote Desktop) | リモート・デスクトップ接続を使って AD サーバーにアクセスするために使用できるユーザー名とパスワード。 |
| NSX Manager IP | NSX Manager の IP アドレス。 |
| NSX Manager FQDN | NSX Manager の完全修飾ドメイン・ネーム。 |
| NSX Manager HTTP | NSX Manager Web コンソールにアクセスするために使用できるユーザー名とパスワード。 |
| NetApp Cluster IP | NetApp ONTAP Select クラスターの IP アドレス。 |
| NetApp Cluster FQDN | NetApp ONTAP クラスターの完全修飾ドメイン・ネーム。 |
| NetApp Cluster HTTPS | NetApp ONTAP Select クラスターにアクセスするために使用できるユーザー名とパスワード。 |
| NetApp Deploy Tool IP | NetApp ONTAP Select Deploy 仮想マシンの IP アドレス。 |
| NetApp Deploy Tool FQDN | NetApp ONTAP Select Deploy の完全修飾ドメイン・ネーム。 |
| NetApp Deploy Tool HTTPS | NetApp ONTAP Select Deploy 仮想マシンにアクセスするために使用できるユーザー名とパスワード。 |
| PSC IP | Platform Services Controller の IP アドレス。 |
| PSC FQDN | PSC の完全修飾ドメイン・ネーム。 |
| PSC ADMIN | PSC Web コンソールにアクセスするために使用できる VMware vCenter シングル・サインオンのユーザー名とパスワード。 |
| PSC SSH | SSH 接続で PSC VM にアクセスするために使用できるユーザー名とパスワード。 |
| vCenter IP | vCenter Server の IP アドレス。 |
| vCenter FQDN | vCenter Server の完全修飾ドメイン・ネーム。 |
| vCenter ADMIN | vSphere Web Client を使用して vCenter Server にログインするために使用できる VMware vCenter Single Sign-On ユーザー名とパスワード。 |
| vCenter SSH | SSH 接続で vCenter Server VM にアクセスするために使用できるユーザー名とパスワード。 |

## NetApp ONTAP Select インスタンスのデプロイメント履歴の表示

左側のナビゲーション・ペインで**「デプロイメント履歴」**をクリックすると、インスタンスのデプロイメント履歴が表示されます。

表 4. NetApp ONTAP Select インスタンスのデプロイメント履歴

| 項目        | 説明       |  
|:------------|:------------- |
| 日付 | インスタンスの状況が変更された日時 |
| サマリー | 変更の詳細 |

インスタンスのデプロイメント中またはインスタンスの削除中にエラーが発生した場合、{{site.data.keyword.cloud_notm}} サポート・チームに自動的に通知されます。 チケットの状況については、[IBM サポートにお問い合わせください](../vmonic/trbl_support.html)。

## NetApp ONTAP Select クラスターの表示

1. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
2. **「クラスター」**の下で、NetApp ONTAP Select クラスターに関するサマリーを確認します。

	表 5: NetApp ONTAP Select クラスターの項目

	 <table>
	   <tr>
	     <th>項目</th>
	     <th>説明</th>
	   </tr>
	   <tr>
	     <td>名前</td>
	     <td>クラスターの名前。</td>
	   </tr>
	   <tr>
	     <td>ESXi サーバー</td>
	     <td>クラスター内の ESXi サーバーの数。</td>
	   </tr>
	   <tr>
	      <td>CPU</td>
	      <td>クラスター内の ESXi サーバーの CPU 仕様。</td>
	   </tr>
	   <tr>
	      <td>Effective storage</td>
	      <td>クラスター内の ESXi サーバーの合計ディスク容量。</td>
	   </tr>
	   <tr>
	      <td>メモリー</td>
	      <td>クラスター内の ESXi サーバーの合計メモリー・サイズ。</td>
	   </tr>
	   <tr>
	      <td>データ・センターの場所</td>
	      <td>クラスターがホストされるデータ・センター。 インスタンスのデータ・センターの場所と同じです。</td>
	   </tr>
		 <tr>
		   <td>ポッド</td>
			 <td>クラスターが作成されるポッド。</td>
		 </tr>
		 <tr>
		  <td>状況</td>
			<td>クラスターの状況。 状況は、以下のいずれかの値になります。<ul><li>初期化中: クラスターは作成され、構成されています。</li><li>変更中: クラスターは変更されています。</li><li>使用可能: クラスターは使用可能です。</li></ul></td>
		 </tr>
		 <tr>
		  <td>アクション</td>
			<td>クラスターを削除するには、**「削除」**アイコンをクリックします。</td>
		 </tr>
	 </table>

3. クラスター名をクリックして、その ESXi サーバーの詳細を表示します。

表 6. NetApp ONTAP Select クラスターの ESXi サーバーの詳細

| 項目        | 説明       |  
|:------------|:----------------- |
| 名前 | ESXi サーバーの名前は、`<host_prefix><n>.<subdomain_label>.<root_domain>` という形式です。各部の意味は次のとおりです。<br><br>`host_prefix` はホスト名接頭部、`n` はサーバーのシーケンス、`subdomain_label` はサブドメイン・ラベル、`root_domain` はルート・ドメイン・ネームです。 |
| バージョン | ESXi サーバーのバージョン。 |
| 資格情報 | ESXi サーバーにアクセスするために使用するユーザー名とパスワード。 |
| プライベート IP | ESXi サーバーのプライベート IP アドレス。 |
| 状況 | ESXi サーバーの状況。次の値のいずれかになります。<ul><li>アクティブ: ESXi サーバーを使用する準備ができています。</li><li>削除中: ESXi サーバーが削除されています。</li></ul> |

## 次に行うこと

{{site.data.keyword.vmwaresolutions_short}} コンソール、VMware vSphere Web クライアント、または NetApp コンソールからインスタンスを管理します。

**重要**: インスタンスのサマリー・ページで**「vCenter コンソール」**をクリックして vSphere Web Client にアクセスし、ESXi サーバーの管理を開始するには、その前に {{site.data.keyword.CloudDataCent_notm}}の VPN ポータルにログインしておく必要があります。 **「vCenter コンソール」**ボタンにマウスオーバーし、指示に従って、すべての要件を満たしていること、また、vSphere Web Client にアクセスするために必要な手順を実行したことを確認してください。

ログイン手順を実行するには、以下のトピックを参照してください。

*  vSphere Web Client にアクセスするための要件と必要な手順については、[Timeout reached while connecting to the vSphere Web Client](../vmonic/trbl_timeout_vc_console.html) を参照してください。
*  VPN を使用して {{site.data.keyword.cloud_notm}} インフラストラクチャーのプライベート・ネットワークにログインするためのアクセス・ポイントのリストについては、[VPN アクセス](http://www.softlayer.com/vpn-access){:new_window}を参照してください。
*  vSphere Web Client を使用して OVF (Open Virtualization Format) ファイルをデプロイする際に問題が発生した場合は、[vSphere Web Client を使用して OVF ファイルをデプロイする方法](../vmonic/trbl_deploy_ovf.html)を参照してください。

### 関連リンク

* [NetApp ONTAP Select インスタンスの注文](np_orderinginstances.html)
* [NetApp ONTAP Select インスタンスの削除](np_deletinginstance.html)
* [Attach dedicated storage to NetApp ONTAP Select deployments](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
