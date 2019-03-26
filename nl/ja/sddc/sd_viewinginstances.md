---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cloud Foundation インスタンスの表示
{: #sd_viewinginstances}

異なるユーザー・アカウントについてプロビジョンされた VMware Cloud Foundation インスタンスのサマリーと詳細情報を表示します。

## Cloud Foundation インスタンスのサマリーを表示する手順
{: #sd_viewinginstances-procedure-view-inst-summary}

1 つのユーザー・アカウントについてプロビジョンされたすべての Cloud Foundation Select インスタンスのサマリーを表示するには、以下の手順を実行します。

1. {{site.data.keyword.vmwaresolutions_full}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. コンソール・バナーのユーザー・アカウント・アイコンをクリックし、**「アカウント」**フィールドをクリックして、インスタンスの確認対象となるユーザー・アカウントを選択します。
3. **「Cloud Foundation インスタンス」**の表で、インスタンスのリストを表示します。

表 1. Cloud Foundation インスタンスの項目

| 項目        | 説明       |  
|:------------- |:------------- |
| 名前 | インスタンスの名前 |
| バージョン | インスタンスがデプロイまたはアップグレードされたリリース・バージョン。 |
| ロケーション | インスタンスがホストされている {{site.data.keyword.CloudDataCent_notm}}。 |
| 作成時間 | インスタンスが作成された日時 |
| 状況 | インスタンスの状況 |

インスタンスにはさまざまな状況があります。

表 2. Cloud Foundation インスタンスの状況の説明

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

## Cloud Foundation インスタンスのプロパティーの詳細を表示する手順
{: #sd_viewinginstances-procedure-view-inst-property}

インスタンスのプロパティーの詳細を表示するには、次の手順を実行します。

1. **「Cloud Foundation インスタンス」**テーブルで、インスタンス名をクリックします。
2. **「プロパティー」**の下で、インスタンスの詳細を確認します。

表 3. Cloud Foundation インスタンスのプロパティー

| プロパティー        | 説明       |
|:------------- |:------------- |
| 名前 | インスタンスの名前 |
| ID | インスタンスの ID |
| ロケーション | インスタンスがホストされている {{site.data.keyword.CloudDataCent_notm}}。 |
| 現行バージョン | {{site.data.keyword.vmwaresolutions_short}} の現行バージョン |
| vCenter バージョン | VMware vCenter Server のバージョン<br><br>**注:** {{site.data.keyword.vmwaresolutions_short}} コンソールと VMware vSphere Web Client では、vCenter Server バージョンの表示が若干異なります。 どちらも正しい表示です。 |
| NSX for vSphere | VMware NSX for vSphere 製品のバージョン |
| _VMware component_ license | インスタンスを注文したときに**「ライセンス適用」**ページで、所有している VMware ライセンスを VMware コンポーネントに使用することを選択した場合は、その VMware コンポーネント名と、コンポーネントに対して入力したライセンス・キーが表示されます。<br><br>VMware コンポーネント・ライセンスの例としては、**vCenter Server License** や **NSX License** があります。 |
| NSX ライセンス・エディション | VMware NSX ライセンスのバージョンとエディション |
| DNS、ルート・ドメイン | ルート・ドメイン・ネームは、DNS (ドメイン・ネーム・システム) ドメイン・ネームと Microsoft Active Directory (AD) フォレストのルート名です。 |
| DNS、SSO ドメイン | SSO ドメインは、vSphere のシングル・サインオン・ドメインです。 デプロイされたすべての Cloud Foundation インスタンスで、SSO ドメイン・ネームが値 <samp class="ph codeph">vsphere.local</samp> に固定されています。 |
| DNS、サブドメイン | サブドメインは、ローカル Cloud Foundation インスタンスのホスト名が存在するルート・ドメイン・ネームの DNS サブドメイン名です。 サブドメイン名の形式は <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp> になります。 |
| SDDC Manager version  |  インスタンスの SDDC Manager のバージョン |
| 状況  | インスタンスの状況<br><br>デプロイメント、またはインスタンスで実行したアクションの進行状況を示す情報が表示され、更新されます。 問題がある場合は、問題の調査と解決に役立つメッセージが表示されることがあります。 |

## Cloud Foundation インスタンスのアクセス情報を表示する手順
{: #sd_viewinginstances-procedure-view-access-info}

**「アクセス情報」**の下に、インスタンス関連コンポーネントのアクセス情報が表示されます。 表示されるパスワードは、システムによって生成される初期パスワードです。 それらを {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、インスタンスのサマリー・ページでは更新されません。

表 4. インスタンス関連コンポーネントに関する Cloud Foundation アクセス情報

| コンポーネント        | 説明       |
|:------------- |:------------- |
| AD/DNS IP | 2 台の AD サーバーの IP アドレス |
| AD/DNS FQDN | AD/DNS サーバーの完全修飾ドメイン・ネーム<br><br>**注:** すべての AD/DNS サーバーに同じ管理者パスワードを使用してリモート・デスクトップ接続を確立できます。 |
| AD/DNS ADMIN (リモート・デスクトップ)  | プライマリー・インスタンスの場合は、リモート・デスクトップ接続を介して AD サーバーにアクセスするためのユーザー名とパスワードが表示されます。<br><br>セカンダリー・インスタンスの場合は、**「プライマリー・インスタンスで表示」**リンクをクリックして、プライマリー・インスタンスのユーザー名とパスワード情報に移動します。<br><br>**注:** セカンダリー・インスタンスがプライマリー DNS ドメインに追加され、レプリケーションが行われると、セカンダリー・インスタンスのローカル管理者パスワードがプライマリー・インスタンスのローカル管理者パスワードで上書きされることがあります。 **「プライマリー・インスタンスで表示」**リンクをクリックすると、正しい管理者パスワードにアクセスできます。  |
| NSX Manager IP  | NSX Manager の IP アドレス  |
| NSX Manager FQDN  | NSX Manager の完全修飾ドメイン・ネーム  |
| NSX Manager HTTP  | NSX Manager Web コンソールにアクセスするために使用されるユーザー名とパスワード |
| NSX Manager SSH | SSH 接続を介して NSX Manager にアクセスするために使用できるユーザー名とパスワード |
| PSC IP  | Platform Services Controller の IP アドレス  |
| PSC FQDN  | PSC の完全修飾ドメイン・ネーム  |    
| PSC SSH  | SSH 接続で PSC VM にアクセスするために使用できるユーザー名とパスワード。  |
| PSC ADMIN  | PSC Web コンソールにアクセスするために使用できる VMware vCenter シングル・サインオンのユーザー名とパスワード。  |
| vCenter IP  | vCenter Server の IP アドレス  |
| vCenter FQDN  | vCenter Server の完全修飾ドメイン・ネーム  |
| vCenter SSH  | SSH 接続で vCenter Server VM にアクセスするために使用できるユーザー名とパスワード。 |
| vCenter ADMIN  | vSphere Web Client を使用して vCenter Server にログインするために使用できる VMware vCenter Single Sign-On ユーザー名とパスワード  |

## Cloud Foundation インスタンスのデプロイメント履歴を表示する手順
{: #sd_viewinginstances-procedure-view-deploy-history}

左側のナビゲーション・ペインで**「デプロイメント履歴」**をクリックすると、インスタンスのデプロイメント履歴が表示されます。

表 5. Cloud Foundation インスタンスのデプロイメント履歴

| 項目        | 説明       |  
|:------------- |:------------- |
| Date | インスタンスの状況が変更された日時 |
| Summary | 変更の詳細 |

## エラーが発生した場合の対処方法
{: #sd_viewinginstances-if-errors-occur}

インスタンスのデプロイメント中またはインスタンスの削除中にエラーが発生した場合、{{site.data.keyword.cloud_notm}} サポート・チームに自動的に通知されます。 チケットの状況については、[IBM サポートにお問い合わせください](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。

## 次に行うこと
{: #sd_viewinginstances-next}

{{site.data.keyword.vmwaresolutions_short}} コンソールまたは vSphere Web クライアントからインスタンスを管理します。

インスタンスのサマリー・ページで**「vCenter コンソール」**をクリックして vSphere Web Client にアクセスし、ESXi サーバーの管理を開始するには、その前に {{site.data.keyword.CloudDataCent_notm}}の VPN ポータルにログインしておく必要があります。 vSphere Web クライアントにアクセスする前に、「vCenter コンソール」ボタンの上にカーソルを移動し、指示に従って、すべての要件を満たしており必要なステップを完了したことを確認してください。
{:important}

ログイン手順を実行するには、以下のトピックを参照してください。

* vSphere Web Client にアクセスするための要件と必要な手順については、[Timeout reached while connecting to the vSphere Web Client](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console) を参照してください。
* VPN を使用して {{site.data.keyword.cloud_notm}} のプライベート・ネットワークにログインするためのアクセス・ポイントのリストについては、[VPN アクセス](http://www.softlayer.com/vpn-access){:new_window}を参照してください。
* vSphere Web Client を使用して OVF (Open Virtualization Format) ファイルをデプロイする際に問題が発生した場合は、[vSphere Web Client を使用して OVF ファイルをデプロイする方法](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_deploy_ovf)を参照してください。

## 関連リンク
{: #sd_viewinginstances-related}

* [Cloud Foundation インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Cloud Foundation インスタンスの削除](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance)
