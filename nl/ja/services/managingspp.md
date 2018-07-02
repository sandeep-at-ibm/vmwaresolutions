---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# IBM Spectrum Protect Plus on IBM Cloud の管理

## IBM Spectrum Protect Plus 管理コンソールへのアクセス

IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} サービスを管理するには、以下のステップを実行して IBM Spectrum Protect Plus 管理コンソールにアクセスする必要があります。
1. {{site.data.keyword.cloud_notm}} インフラストラクチャー VPN またはジャンプ・サーバーを使用して、IBM Spectrum Protect Plus 仮想マシンの IP アドレスへのアクセスを許可します。 この IP アドレスは、{{site.data.keyword.vmwaresolutions_short}} コンソールの IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} のサービスの詳細ページで調べることができます。
2. IBM Spectrum Protect Plus 管理コンソールにアクセスするには、IBM Spectrum Protect Plus on {{site.data.keyword.cloud}} のサービスの詳細ページで**「IBM Spectrum Protect Plus コンソールの表示」**をクリックしてから、同じサービス詳細ページにリストされる資格情報を使用してログインします。

## IBM Spectrum Protect Plus on IBM Cloud のフィックスの適用

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスは、ユーザーの責任で最新バージョンに維持する必要があります。 必要な更新は、[IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サポート](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus)のページからダウンロードできます。

詳しくは、以下のトピックを参照してください。
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)

## IBM Spectrum Protect Plus 仮想マシンのオペレーティング・システムの更新

IBM Spectrum Protect Plus 仮想マシンのオペレーティング・システムを更新するには、**root** ユーザーとしてログインする必要があります。 **root** ユーザーのパスワードは、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} のサービスの詳細ページに表示されるパスワードと同じです。

## IBM Spectrum Protect Plus on IBM Cloud がインストールされているインスタンスの管理コンポーネントのバックアップとリストア

 **注**: 次の情報は、V2.3 以降でデプロイ (または、V2.3 以降にアップグレード) されたインスタンスへの IBM Spectrum Protect Plus のインストールに適用されます。 V2.2 インスタンスの場合、このサービスはワークロード仮想マシンのデータのみを保護します。

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスには、管理バックアップ・ジョブが事前構成されています。このジョブは、次の管理コンポーネントをバックアップするために毎日自動的に実行されます (最大 7 個の回復ポイントを使用可能)。
* VMware vCenter Server
* Platform Services Controller (PSC)
* IBM CloudDriver
* **Cloud Foundation インスタンスのみ**: VMware SDDC Manager
* **HA AD/DNS を使用する vCenter Server インスタンスのみ**: AD/DNS の高可用性ペア

管理コンポーネントで障害が発生した場合は、[IBM サポートに連絡](../vmonic/trbl_support.html)してチケットを開き、管理コンポーネントを前のバックアップにリストアするよう要求できます。

## 関連リンク

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} の概要](spp_considerations.html)
* [How to increase vsnap storage for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)
* [IBM Spectrum Protect Plus の資料](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
