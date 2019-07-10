---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: view vCenter Server, view instance, view instance details

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server インスタンスの表示
{: #vc_viewinginstances}

さまざまなユーザー・アカウントに対してプロビジョンされる vCenter Server インスタンスのサマリーおよび詳細情報を表示します。

## vCenter Server インスタンスのサマリーを表示する手順
{: #vc_viewinginstances-procedure-view-inst-summary}

ユーザー・アカウントに対してプロビジョンされるすべての vCenter Server インスタンスのサマリーを表示するには、以下の手順を実行します。

1. {{site.data.keyword.vmwaresolutions_full}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. コンソール・バナーのユーザー・アカウント・アイコンをクリックし、**「アカウント」**フィールドをクリックして、インスタンスの確認対象となるユーザー・アカウントを選択します。  
3. **vCenter Server インスタンス**の表で、選択したユーザー・アカウントでプロビジョンされているインスタンスのリストを表示します。

表 1. vCenter Server インスタンスの項目

| 項目        | 説明       |  
|:------------- |:------------- |
| 名前 | インスタンスの名前 |
| タイプ | vCenter Server インスタンスのタイプ |
| バージョン | インスタンスがデプロイまたはアップグレードされたリリース・バージョン。 |  
| ロケーション | インスタンスがホストされている {{site.data.keyword.CloudDataCent_notm}}。 |  
| 作成時間 | インスタンスが作成された日時 |
| 状況 | インスタンスの状況 |   

インスタンスにはさまざまな状況があります。

表 2. vCenter Server インスタンスの状況の説明

| 状況        | 説明       |
|:------------- |:------------- |
| 作成中 | インスタンスは作成中です。 |
| 構築中 | インスタンスは構成中です。 |
| 使用可能 | インスタンスは使用可能です。 |
| 変更中 | インスタンスは変更中です。 |
| 失敗 | 作成、構成、または変更のプロセスが失敗しました。 |
| Deleting | インスタンスは削除中です。 |
| 削除エラー | インスタンスの削除中にエラーが発生しました。 |
| 削除済み | インスタンスは削除されました。 |

## vCenter Server インスタンスのプロパティーの詳細を表示する手順
{: #vc_viewinginstances-procedure-view-inst-property}

インスタンスのプロパティーの詳細を表示するには、次の手順を実行します。

1. **「vCenter Server インスタンス」**テーブルで、インスタンス名をクリックします。
2. **「プロパティー」**の下で、インスタンスの詳細を確認します。

表 3. vCenter Server インスタンスのプロパティー

| プロパティー        | 説明       |
|:------------- |:------------- |
| 名前 | インスタンスの名前。 |
| ID | インスタンスの ID。 |
| ロケーション | インスタンスがホストされている {{site.data.keyword.CloudDataCent_notm}}。 |
| 現行バージョン | {{site.data.keyword.vmwaresolutions_short}} の現行バージョン。 |
| vCenter バージョン | VMware vCenter Server のバージョン。<br><br>**注:** {{site.data.keyword.vmwaresolutions_short}} コンソールと VMware vSphere Web Client では、vCenter Server バージョンの表示が若干異なります。 どちらも正しい表示です。 |
| NSX for vSphere | VMware NSX for vSphere 製品のバージョン。 |
| _VMware コンポーネント_のライセンス | インスタンスを注文したときに**「ライセンス適用」**ページで、所有している VMware ライセンスを VMware コンポーネントに使用することを選択した場合は、その VMware コンポーネント名と、コンポーネントに対して入力したライセンス・キーが表示されます。<br><br>VMware コンポーネント・ライセンスには、**NSX ライセンス**、**vCenter Server ライセンス**、**vSAN ライセンス** などがあります。 |
| NSX ライセンス・エディション | VMware NSX ライセンスのバージョンとエディション。 |
| DNS、ルート・ドメイン | ルート・ドメイン・ネームは、DNS (ドメイン・ネーム・システム) ドメイン・ネームと Microsoft Active Directory (AD) フォレストのルート名です。 |
| DNS、SSO ドメイン | SSO ドメインは、vSphere のシングル・サインオン・ドメインです。 SSO ドメイン・ネームは、デプロイされたすべての vCenter Server インスタンスで <samp class="ph codeph">vsphere.local</samp> という値に固定されています。 |
| DNS、サブドメイン | サブドメインは、ローカル vCenter Server インスタンスのホスト名が存在するルート・ドメイン・ネームの DNS サブドメイン・ネームです。 サブドメイン名の形式は <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp> になります。 |
| Hybridity Bundle | vCenter Server with Hybridity Bundle がインストールされているかどうかを示します。 |
| 状況  | インスタンスの状況。<br><br>デプロイメント、またはインスタンスで実行したアクションの進行状況を示す情報が表示され、更新されます。 問題がある場合は、問題の調査と解決に役立つメッセージが表示されることがあります。 |

## vCenter Server インスタンスのアクセス情報を表示する手順
{: #vc_viewinginstances-procedure-view-access-info}

**「アクセス情報」**の下に、インスタンス関連コンポーネントのアクセス情報が表示されます。 表示されるパスワードは、システムによって生成される初期パスワードです。 それらを {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、インスタンスのサマリー・ページでは更新されません。

表 4. インスタンス関連コンポーネントの vCenter Server アクセス情報

| コンポーネント        | 説明       |
|:------------- |:------------- |
| AD/DNS IP | 2 つの AD サーバーの IP アドレス。 |
| AD/DNS FQDN | AD/DNS サーバーの完全修飾ドメイン・ネーム。<br><br>**注:** すべての AD/DNS サーバーに同じ管理者パスワードを使用してリモート・デスクトップ接続を確立できます。 |
| AD/DNS ADMIN (リモート・デスクトップ)  | プライマリー・インスタンスの場合は、リモート・デスクトップ接続を介して AD サーバーにアクセスするためのユーザー名とパスワードが表示されます。<br><br>セカンダリー・インスタンスの場合は、**「プライマリー・インスタンスで表示」**リンクをクリックして、プライマリー・インスタンスのユーザー名とパスワード情報に移動します。<br><br>**注:** セカンダリー・インスタンスがプライマリー DNS ドメインに追加され、レプリケーションが行われると、セカンダリー・インスタンスのローカル管理者パスワードがプライマリー・インスタンスのローカル管理者パスワードで上書きされることがあります。 **「プライマリー・インスタンスで表示」**リンクをクリックすると、正しい管理者パスワードにアクセスできます。  
| NSX Manager IP  | NSX Manager の IP アドレス。  |
| NSX Manager FQDN  | NSX Manager の完全修飾ドメイン・ネーム (FQDN)。  |
| NSX Manager HTTP  | NSX Manager Web コンソールにアクセスするために使用されるユーザー名とパスワード。 |
| vCenter IP  | vCenter Server の IP アドレス。  |
| vCenter FQDN  | vCenter Server の完全修飾ドメイン・ネーム (FQDN)。  |
| vCenter ADMIN  | vSphere Web Client を使用して vCenter Server にログインするために使用できる VMware vCenter Single Sign-On ユーザー名とパスワード。  |
| vCenter SSH  | SSH 接続で vCenter Server VM にアクセスするために使用できるユーザー名とパスワード。  |

## vCenter Server インスタンスのデプロイメント履歴を表示する手順
{: #vc_viewinginstances-procedure-view-deploy-history}

左側のナビゲーション・ペインで**「デプロイメント履歴」**をクリックすると、インスタンスのデプロイメント履歴が表示されます。

表 5. vCenter Server インスタンスのデプロイメント履歴

| 項目        | 説明       |  
|:------------- |:------------- |
| 日付 | インスタンスの状況が変更された日時 |
| サマリー | 変更の詳細 |

## エラーが発生した場合の対処方法
{: #vc_viewinginstances-if-errors-occur}

インスタンスのデプロイメント中またはインスタンスの削除中にエラーが発生した場合、{{site.data.keyword.cloud_notm}} サポート・チームに自動的に通知されます。 チケットの状況については、[IBM サポートにお問い合わせください](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。

## 次に行うこと
{: #vc_viewinginstances-next}

{{site.data.keyword.vmwaresolutions_short}} コンソールまたは VMware vSphere Web Client からインスタンスを管理します。

インスタンスのサマリー・ページで**「vCenter コンソール」**をクリックして vSphere Web Client にアクセスし、ESXi サーバーの管理を開始するには、その前に {{site.data.keyword.CloudDataCent_notm}}の VPN ポータルにログインしておく必要があります。 **「vCenter コンソール」**ボタンにマウスオーバーし、指示に従って、すべての要件を満たしていること、また、vSphere Web Client にアクセスするために必要な手順を実行したことを確認してください。
{:important}

ログイン手順を実行するには、以下のトピックを参照してください。
*  vSphere Web Client にアクセスするための要件と必要な手順については、[Timeout reached while connecting to the vSphere Web Client](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console) を参照してください。
*  VPN を使用して {{site.data.keyword.cloud_notm}} インフラストラクチャーのプライベート・ネットワークにログインするためのアクセス・ポイントのリストについては、[VPN アクセス](http://www.softlayer.com/vpn-access){:new_window}を参照してください。
*  vSphere Web Client を使用して OVF (Open Virtualization Format) ファイルをデプロイする際に問題が発生した場合は、[vSphere Web Client を使用して OVF ファイルをデプロイする方法](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_deploy_ovf)を参照してください。

## 関連リンク
{: #vc_viewinginstances-related}

* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)
* [vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [vCenter Server インスタンスの削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance)
