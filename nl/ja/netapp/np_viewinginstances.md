---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-25"

keywords: view NetApp, view instance, view instance details

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select インスタンスの表示
{: #np_viewinginstances}

異なるユーザー・アカウントについてプロビジョンされた NetApp ONTAP Select インスタンスのサマリーと詳細情報を表示します。

## NetApp ONTAP Select インスタンスのサマリーを表示する手順
{: #np_viewinginstances-procedure-view-inst-summary}

1 つのユーザー・アカウントについてプロビジョンされたすべての NetApp ONTAP Select インスタンスのサマリーを表示するには、以下の手順を実行します。

1. {{site.data.keyword.vmwaresolutions_full}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. コンソール・バナーのユーザー・アカウント・アイコンをクリックし、**「アカウント」**フィールドをクリックして、インスタンスの確認対象となるユーザー・アカウントを選択します。
3. **「NetApp ONTAP Select インスタンス」**の表で、選択されたユーザー・アカウントでプロビジョンされたインスタンスのリストを表示します。

| 項目        | 説明       |  
|:------------- |:--------------- |
| 名前 | インスタンスの名前。 |
| バージョン | インスタンスのバージョン。 |  
| ロケーション | インスタンスがホストされるデータ・センター。 |
| 作成時間 | インスタンスが作成された日時。 |   
| 状況 | インスタンスの状況。 状況は、以下のいずれかの値になります。<br>作成中: インスタンスは作成中です。<br>構築中: インスタンスは構成中です。<br>使用可能: インスタンスは使用可能です。<br>変更中: インスタンスは変更中です。<br>失敗: 作成、構成、または変更のプロセスが失敗しました。<br>削除中: インスタンスは削除中です。<br>削除エラー: インスタンスの削除中にエラーが発生しました。<br>削除済み: インスタンスは削除されました。 |
{: caption="表 1. NetApp ONTAP Select インスタンスの項目" caption-side="top"}

## NetApp ONTAP Select インスタンスのプロパティーの詳細を表示する手順
{: #np_viewinginstances-procedure-view-inst-property}

インスタンスのプロパティーの詳細を表示するには、次の手順を実行します。

1. **「NetApp ONTAP Select インスタンス」**テーブルで、インスタンス名をクリックします。
2. **「プロパティー」**の下で、インスタンスの詳細を確認します。

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
{: caption="表 2. NetApp ONTAP Select インスタンスのプロパティー" caption-side="top"}

## NetApp ONTAP Select インスタンスのアクセス情報を表示する手順
{: #np_viewinginstances-procedure-view-inst-access-info}

**「アクセス情報」**の下に、インスタンス関連コンポーネントのアクセス情報が表示されます。 以下のパスワードは、システムで生成される初期パスワードです。 それらを {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、インスタンスのサマリー・ページでは更新されません。

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
| vCenter IP | vCenter Server の IP アドレス。 |
| vCenter FQDN | vCenter Server の完全修飾ドメイン・ネーム。 |
| vCenter ADMIN | vSphere Web Client を使用して vCenter Server にログインするために使用できる VMware vCenter Single Sign-On ユーザー名とパスワード。 |
| vCenter SSH | SSH 接続で vCenter Server VM にアクセスするために使用できるユーザー名とパスワード。 |
{: caption="表 3. NetApp ONTAP Select インスタンス関連コンポーネントのアクセス情報" caption-side="top"}

## NetApp ONTAP Select インスタンスのデプロイメント履歴を表示する手順
{: #np_viewinginstances-procedure-view-inst-deploy-history}

左側のナビゲーション・ペインで**「デプロイメント履歴」**をクリックすると、インスタンスのデプロイメント履歴が表示されます。

| 項目        | 説明       |  
|:------------|:------------- |
| 日付 | インスタンスの状況が変更された日時 |
| サマリー | 変更の詳細 |
{: caption="表 4. NetApp ONTAP Select インスタンスのデプロイメント履歴" caption-side="top"}

インスタンスのデプロイメント中またはインスタンスの削除中にエラーが発生した場合、{{site.data.keyword.cloud_notm}} サポート・チームに自動的に通知されます。 チケットの状況については、[IBM サポートにお問い合わせください](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。

## NetApp ONTAP Select クラスターを表示する手順
{: #np_viewinginstances-procedure-view-cluster}

1. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
2. **「クラスター」**の下で、NetApp ONTAP Select クラスターに関するサマリーを確認します。

| 項目 | 説明 |
|:---- | :-----------|
| 名前 | クラスターの名前。 |
| ESXi サーバー | クラスター内の ESXi サーバーの数。 |
| CPU | クラスター内の ESXi サーバーの CPU 仕様。 |
| Effective storage | クラスター内の ESXi サーバーの合計ディスク容量。 |
| メモリー | クラスター内の ESXi サーバーの合計メモリー・サイズ。 |
| データ・センターの場所 | クラスターがホストされるデータ・センター。 インスタンスのデータ・センターの場所と同じです。 |
| ポッド | クラスターが作成されるポッド。 |
| 状況 | クラスターの状況。 状況は、以下のいずれかの値になります。<br>初期化中: クラスターは作成され、構成されています。<br>変更中: クラスターは変更されています。<br>使用可能: クラスターは使用可能です。 |
| アクション | クラスターを削除するには、**「削除」**アイコンをクリックします。 |
{: caption="表 5. NetApp ONTAP Select クラスターの項目" caption-side="top"}

3. クラスター名をクリックして、その ESXi サーバーの詳細を表示します。

| 項目        | 説明       |  
|:------------|:----------------- |
| 名前 | ESXi サーバーの名前は、`<data_center>-<host_prefix><n>.<subdomain_label>.<root_domain>` という形式です。ここで、`n` は ESXi サーバーのシーケンスです。|
| バージョン | ESXi サーバーのバージョン。 |
| 資格情報 | ESXi サーバーにアクセスするために使用するユーザー名とパスワード。 |
| プライベート IP | ESXi サーバーのプライベート IP アドレス。 |
| 状況 | ESXi サーバーの状況。次の値のいずれかになります。<ul><li>アクティブ: ESXi サーバーを使用する準備ができています。</li><li>削除中: ESXi サーバーが削除されています。</li></ul> |
{: caption="表 6. NetApp ONTAP Select クラスターの ESXi サーバーの詳細" caption-side="top"}

## 次に行うこと
{: #np_viewinginstances-next}

{{site.data.keyword.vmwaresolutions_short}} コンソール、VMware vSphere Web クライアント、または NetApp コンソールからインスタンスを管理します。

インスタンスのサマリー・ページで**「vCenter コンソール」**をクリックして vSphere Web Client にアクセスし、ESXi サーバーの管理を開始するには、その前に {{site.data.keyword.CloudDataCent_notm}}の VPN ポータルにログインしておく必要があります。 **「vCenter コンソール」**ボタンにマウスオーバーし、指示に従って、すべての要件を満たしていること、また、vSphere Web Client にアクセスするために必要な手順を実行したことを確認してください。
{:important}

ログイン手順を実行するには、以下のトピックを参照してください。

*  vSphere Web Client にアクセスするための要件と必要な手順については、[Timeout reached while connecting to the vSphere Web Client](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console) を参照してください。
*  VPN を使用して {{site.data.keyword.cloud_notm}} インフラストラクチャーのプライベート・ネットワークにログインするためのアクセス・ポイントのリストについては、[VPN アクセス](http://www.softlayer.com/vpn-access){: external}を参照してください。
*  vSphere Web Client を使用して OVF (Open Virtualization Format) ファイルをデプロイする際に問題が発生した場合は、[vSphere Web Client を使用して OVF ファイルをデプロイする方法](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_deploy_ovf)を参照してください。

## 関連リンク
{: #np_viewinginstances-related}

* [NetApp ONTAP Select インスタンスの注文](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)
* [NetApp ONTAP Select インスタンスの削除](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_deletinginstance)
* [Attach dedicated storage to NetApp ONTAP Select deployments](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/){: external}
