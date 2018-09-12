---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Veeam on IBM Cloud の管理

ご使用のインスタンスにこのサービスをデプロイすると、RDP を使用して Veeam コンソールにアクセスすることにより、ご使用の環境にあるすべての仮想マシンのバックアップとリストアを管理できるようになります。管理コンポーネントのバックアップとリストアも可能です。 また、Veeam Web サイトから Veeam 更新プログラムをダウンロードしてインストールすることにより、サービスをアップグレードすることもできます。

V1.8 より前のリリースでデプロイされたインスタンスでは、Veeam on {{site.data.keyword.cloud}} サービスを使用する場合は、インスタンス内の既存の Veeam VSI を置き換える必要があります。 詳しくは、このトピックの『_V1.8 より前のインスタンスの Veeam VSI を Veeam on IBM Cloud に置き換える_』セクションを参照してください。

## RDP を使用した Veeam コンソールへのアクセス

Veeam on {{site.data.keyword.cloud_notm}} サービスを管理するには、以下のステップを実行して Veeam コンソールにアクセスします。
1. リモート・デスクトップ・プロトコル (RDP) を使用して、Windows IP アドレスに接続します。
2. Administrator 資格情報を使用して、Windows コンソールにログインします。
3. Administrator 資格情報を使用して、Windows コンソールから Veeam コンソールにアクセスします。

Windows IP アドレスと Administrator 資格情報は、Veeam on {{site.data.keyword.cloud_notm}} サービスの詳細ページに表示されます。

詳しくは、以下のトピックを参照してください。
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)

## Veeam on IBM Cloud がインストールされているインスタンスの管理コンポーネントのバックアップとリストア

Veeam コンソールを使用して管理コンポーネントをバックアップするように、Veeam on {{site.data.keyword.cloud_notm}} サービスを構成できます。 詳しくは、[コンポーネントのバックアップ](../archiref/solution/solution_backingup.html)を参照してください。

V1.8 以降のリリースでデプロイ (または V1.8 以降のリリースにアップグレード) されたインスタンスの場合、環境の構成変更の自動バックアップは行われません。 そのため、環境の構成を変更する前に、管理バックアップ・ジョブを Veeam コンソールで実行して、管理コンポーネントを手動でバックアップすることをお勧めします。 手動バックアップについて詳しくは、[Veeam 技術説明](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}を参照してください。

管理コンポーネント上で障害が発生した場合は、Veeam コンソールを使用して、管理コンポーネントを以前のバックアップにリストアできます。 手動リストアについて詳しくは、[Veeam 技術説明]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}を参照してください。

## Veeam on IBM Cloud への更新の適用

Veeam を最新バージョンに更新する責任は、ユーザー側にあります。 Veeam を最新バージョンにアップグレードするには、Veeam Web サイトから Veeam 更新プログラムをダウンロードし、Veeam VSI にコピーした後、インストールします。

## Veeam ライセンスの更新

オンデマンドで Veeam ライセンスを手動で更新するには、以下のステップを完了します。
1. [RDP を使用して Veeam Backup および Replication のコンソールにアクセスします](../services/managingveeam.html#accessing-the-veeam-console-by-using-rdp)。
2. メインメニューから、**「ライセンス」**をクリックします。
3. **「ライセンス情報」**ウィンドウで**「今すぐ更新」**をクリックします。
4. 手動ライセンスの更新プロセスの統計情報を表示するには、**「履歴」**ビューを開き、**「システム」**ノードをクリックします。

詳しくは、[手動によるライセンスの更新](https://helpcenter.veeam.com/docs/backup/vsphere/license_update_manual.html?ver=95)を参照してください。

## V1.8 より前のインスタンスの Veeam VSI を Veeam on IBM Cloud に置き換える

管理コンポーネントとワークロードの両方をバックアップできる Veeam on {{site.data.keyword.cloud_notm}} サービスは、管理コンポーネントのバックアップのみに対応していた以前の Veeam VSI を置き換えるものとして用意されました。Veeam VSI は、V1.8 より前のリリースで VMware Cloud Foundation と VMware vCenter Server に統合されていました。

この変更により、インスタンスの詳細ページにあった以前の**「バックアップとリストア」**タブが除去されました。V1.8 より前のインスタンス内の Veeam VSI は引き続き動作しますが、{{site.data.keyword.vmwaresolutions_short}} コンソールでインスタンスのバックアップ・ポイントを使用することはできなくなりました。

リストアを行うための支援を受けるには、{{site.data.keyword.cloud_notm}} サポート・チケットを作成する必要があります。 また、V1.8 より前のインスタンス内の Veeam VSI のライセンスは、2017 年 10 月 14 日に有効期限が切れています。 そのため、以前の Veeam VSI を新しい Veeam on {{site.data.keyword.cloud_notm}} サービスに置き換える必要があります。

以下のステップを実行します。
1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインにある**「デプロイ済みインスタンス」**をクリックしてから、ターゲット・インスタンスをクリックします。
2. インスタンスの詳細ページで、**「更新およびパッチ」**タブをクリックします。 インスタンスを必ず V1.8 リリースにアップグレードしてください。
3. **「サービス」**タブをクリックします。
4. **「サービスの追加」**タブで、Veeam on {{site.data.keyword.cloud_notm}} サービスをインストールします。

新しい Veeam on {{site.data.keyword.cloud_notm}} サービスがデプロイされ、管理コンポーネントのバックアップが正常に完了したら、{{site.data.keyword.cloud_notm}} サポート・チケットを作成することにより、アカウントから既存の Veeam VSI を削除できます。 IBM サポートは既存の Veeam VSI とストレージを識別して削除します。

### 関連リンク

* [Veeam on {{site.data.keyword.cloud_notm}} の概要](veeam_considerations.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam.com Web サイト](https://www.veeam.com/)
* [Veeam 技術資料](https://www.veeam.com/documentation-guides-datasheets.html)
