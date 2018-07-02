---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Veeam on IBM Cloud の管理

V1.8 より前のリリースでデプロイされたインスタンスでは、Veeam on {{site.data.keyword.cloud}} サービスを使用する場合は、インスタンス内の既存の Veeam VSI を置き換える必要があります。 ご使用のインスタンスにこのサービスをデプロイすると、RDP を使用して Veeam コンソールにアクセスすることにより、ご使用の環境にあるすべての仮想マシンのバックアップとリストアを管理できるようになります。管理コンポーネントのバックアップとリストアも可能です。 また、Veeam Web サイトから Veeam 更新プログラムをダウンロードしてインストールすることにより、サービスをアップグレードすることもできます。

## V1.8 より前のインスタンスの Veeam VSI を Veeam on IBM Cloud に置き換える

管理コンポーネントとワークロードの両方をバックアップできる Veeam on {{site.data.keyword.cloud_notm}} サービスは、管理コンポーネントのバックアップのみに対応していた以前の Veeam VSI を置き換えるものとして用意されました。Veeam VSI は、V1.8 より前のリリースで VMware Cloud Foundation と VMware vCenter Server に統合されていました。 この変更により、インスタンスの詳細ページにあった以前の**「バックアップとリストア」**タブが除去されました。V1.8 より前のインスタンス内の Veeam VSI は引き続き動作しますが、{{site.data.keyword.vmwaresolutions_short}} コンソールでインスタンスのバックアップ・ポイントを使用することはできなくなりました。 リストアを行うための支援を受けるには、{{site.data.keyword.cloud_notm}} サポート・チケットを作成する必要があります。 また、V1.8 より前のインスタンス内の Veeam VSI のライセンスは、2017 年 10 月 14 日に有効期限が切れています。 そのため、以前の Veeam VSI を新しい Veeam on {{site.data.keyword.cloud_notm}} サービスに置き換える必要があります。

以下のステップを実行します。
1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインにある**「デプロイ済みインスタンス」**をクリックしてから、ターゲット・インスタンスをクリックします。
2. インスタンスの詳細ページで、**「更新およびパッチ」**タブをクリックします。 インスタンスを必ず V1.8 リリースにアップグレードしてください。
3. **「サービス」**タブをクリックします。
4. **「サービスの追加」**タブで、Veeam on {{site.data.keyword.cloud_notm}} サービスをインストールします。

新しい Veeam on {{site.data.keyword.cloud_notm}} サービスがデプロイされ、管理コンポーネントのバックアップが正常に完了したら、{{site.data.keyword.cloud_notm}} サポート・チケットを作成することにより、アカウントから既存の Veeam VSI を削除できます。 IBM サポートは既存の Veeam VSI とストレージを識別して削除します。

## RDP を使用した Veeam コンソールへのアクセス

Veeam on {{site.data.keyword.cloud_notm}} サービスを管理するには、以下のステップを実行して Veeam コンソールにアクセスする必要があります。
1. リモート・デスクトップ・プロトコル (RDP) を使用して、Veeam on {{site.data.keyword.cloud_notm}} サービスの詳細ページにある Windows IP アドレスに接続します。
2. Veeam on {{site.data.keyword.cloud_notm}} サービスの詳細ページにある Administrator 資格情報を使用して、Windows コンソールにログインします。
3. Veeam on {{site.data.keyword.cloud_notm}} サービスの詳細ページにある Administrator 資格情報を使用して、Windows コンソールから Veeam コンソールにアクセスします。

詳しくは、以下のトピックを参照してください。
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)

## Veeam on IBM Cloud がインストールされているインスタンスの管理コンポーネントのバックアップとリストア

Veeam on {{site.data.keyword.cloud_notm}} サービスには、管理バックアップ・ジョブが事前構成されています。このジョブは、管理コンポーネントをバックアップするために毎日自動的に実行されます (最大 14 個の回復ポイントを使用可能)。

Veeam コンソールを使用して管理コンポーネントを手動でバックアップすることもできます。 V1.8 リリース以降、環境に対する構成変更の自動バックアップは行われなくなりました。 そのため、環境の構成を変更する前に、事前構成された管理バックアップ・ジョブを Veeam コンソールで実行して、管理コンポーネントの手動バックアップを行うことをお勧めします。 手動バックアップ・ジョブの実行方法について詳しくは、[Veeam 技術説明](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}を参照してください。

管理コンポーネント上で障害が発生した場合は、Veeam コンソールを使用して、管理コンポーネントを以前のバックアップにリストアできます。 手動リストア・ジョブの実行方法について詳しくは、[Veeam 技術説明]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}を参照してください。

## Veeam on IBM Cloud のアップグレード

Veeam on {{site.data.keyword.cloud_notm}} サービスをアップグレードするには、Veeam Web サイトから Veeam 更新をダウンロードし、Veeam VSI にコピーした後、インストールします。

## 関連リンク

* [Veeam on {{site.data.keyword.cloud_notm}} の概要](veeam_considerations.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam.com Web サイト](https://www.veeam.com/)
* [Veeam 技術資料](https://www.veeam.com/documentation-guides-datasheets.html)
