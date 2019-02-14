---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Veeam on IBM Cloud の管理

ご使用のインスタンスにこのサービスをデプロイすると、RDP を使用して Veeam コンソールにアクセスすることにより、ご使用の環境にあるすべての仮想マシンのバックアップとリストアを管理できるようになります。管理コンポーネントのバックアップとリストアも可能です。 また、Veeam Web サイトから Veeam 更新プログラムをダウンロードしてインストールすることにより、サービスをアップグレードすることもできます。

V1.8 より前のリリースでデプロイされたインスタンスでは、Veeam on {{site.data.keyword.cloud}} サービスを使用する場合は、インスタンス内の既存の Veeam VSI を置き換える必要があります。 詳しくは、『_V1.8 より前のインスタンスの Veeam VSI を Veeam on IBM Cloud に置き換える_』セクションを参照してください。

## RDP を使用した Veeam コンソールへのアクセス

Veeam on {{site.data.keyword.cloud_notm}} サービスを管理するには、以下のステップを実行して Veeam コンソールにアクセスします。
1. リモート・デスクトップ・プロトコル (RDP) を使用して、Windows IP アドレスに接続します。
2. Administrator 資格情報を使用して、Windows コンソールにログインします。
3. Administrator 資格情報を使用して、Windows コンソールから Veeam コンソールにアクセスします。

Windows IP アドレスと Administrator 資格情報は、Veeam on {{site.data.keyword.cloud_notm}} サービスの詳細ページに表示されます。

詳しくは、以下のトピックを参照してください。
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)

## Veeam on IBM Cloud がインストールされているインスタンスの管理コンポーネントのバックアップとリストア

Veeam コンソールを使用して管理コンポーネントをバックアップするように、Veeam on {{site.data.keyword.cloud_notm}} サービスを構成できます。 詳しくは、[コンポーネントのバックアップ](/docs/services/vmwaresolutions/archiref/solution/solution_backingup.html)を参照してください。

V1.8 以降のリリースでデプロイ (または V1.8 以降のリリースにアップグレード) されたインスタンスの場合、環境の構成変更の自動バックアップは行われません。 そのため、環境の構成を変更する前に、管理バックアップ・ジョブを Veeam コンソールで実行して、管理コンポーネントを手動でバックアップすることをお勧めします。 手動バックアップについて詳しくは、[Veeam 技術説明](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}を参照してください。

管理コンポーネント上で障害が発生した場合は、Veeam コンソールを使用して、管理コンポーネントを以前のバックアップにリストアできます。 手動リストアについて詳しくは、[Veeam 技術説明]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}を参照してください。

## Veeam on IBM Cloud への更新の適用

Veeam ソフトウェアを最新バージョンに更新する責任は、ユーザー側にあります。

### パブリック・ネットワークおよびプライベート・ネットワークを使用してデプロイされたインスタンスに更新を適用する

パブリック・ネットワークとプライベート・ネットワークを持つインスタンスに Veeam サービスがインストールされている場合は、Veeam ソフトウェア自体を使用して更新を確認およびダウンロードできます。

### プライベート・ネットワークのみを使用してデプロイされたインスタンスに更新を適用する

プライベート・ネットワークのみのインスタンスに Veeam サービスがインストールされている場合は、Veeam VSI はパブリック・ネットワーク・アクセスなしで構成されているため、Veeam ソフトウェア自体を使用して更新を確認またはダウンロードすることはできません。 その代わりに、Veeam Web サイトから更新をダウンロードし、Veeam VM に転送してからインストールする必要があります。

## Veeam ライセンスの更新

### パブリック・ネットワークおよびプライベート・ネットワークを使用してデプロイされたインスタンスの Veeam ライセンスを更新する

パブリック・ネットワークとプライベート・ネットワークを持つインスタンスに Veeam サービスがインストールされている場合は、Veeam ライセンスを自動で更新することも、[ライセンスの更新]( https://helpcenter.veeam.com/docs/backup/vsphere/license_update.html)にある Veeam の説明に従って手動で更新することもできます。

### プライベート・ネットワークのみを使用してデプロイされたインスタンスの Veeam ライセンスを更新する

プライベート・ネットワークのみのインスタンスに Veeam サービスがインストールされている場合は、ライセンスの有効期限をメモしておき、更新が必要になったら [IBM サポートに連絡](/docs/services/vmwaresolutions/vmonic/trbl_support.html)して、ライセンス・キーの更新を行ってください。

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

* [Veeam on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services/veeam_considerations.html)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [よくある質問](/docs/services/vmwaresolutions/vmonic/faq.html)
* [Veeam.com Web サイト](https://www.veeam.com/)
* [Veeam 技術資料](https://www.veeam.com/documentation-guides-datasheets.html)
