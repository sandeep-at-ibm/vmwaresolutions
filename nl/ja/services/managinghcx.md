---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: HCX updates, HCX management console, login HCX console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}


# VMware HCX on IBM Cloud の管理
{: #managinghcx}

## HCX on IBM Cloud 管理コンソールへのアクセス
{: #managinghcx-accessing-consoles}

HCX on {{site.data.keyword.cloud}} サービスを管理するには、HCX Cloud Console または HCX Manager Admin Console にアクセスする必要があります。
1. {{site.data.keyword.cloud_notm}} インフラストラクチャー VPN またはジャンプ・サーバーを使用して、HCX Manager 仮想アプライアンス (HCX Manager) の IP アドレスへのアクセスを許可します。 この IP アドレスは、{{site.data.keyword.vmwaresolutions_short}} コンソールにある HCX on {{site.data.keyword.cloud_notm}} サービスの詳細ページで調べることができます。
2. HCX Cloud Console にアクセスするには、HCX on {{site.data.keyword.cloud_notm}} サービスの詳細ページで**「View HCX Cloud Console」**をクリックしてから、vCenter Server 資格情報を使用してログインします。
3. HCX Manager Admin Console にアクセスするには、HCX on {{site.data.keyword.cloud_notm}} サービスの詳細ページで**「View HCX Manager Admin Console」**をクリックしてから、同じサービス詳細ページにリストされる HCX Manager 資格情報を使用してログインします。

詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)を参照してください。

## HCX on IBM Cloud への更新の適用
{: #managinghcx-updates}

HCX on {{site.data.keyword.cloud_notm}} は、VMware Hybrid Cloud Extension テクノロジーのテスト済みの最新ビルドでデプロイされます。 VMware では、そうしたビルドの更新 (重要なフィックスや新機能など) が定期的に配信されます。 それらのビルドは、HCX on {{site.data.keyword.cloud}} のインストール済み環境に自動的にプッシュされます。オンプレミスの HCX インストール済み環境の場合も同様です。

ご使用の環境にプッシュされたメンテナンス・フィックスを適用するには、オンプレミスのデータ・センターと、vCenter Server on {{site.data.keyword.cloud_notm}} インスタンスで、HCX Manager の管理コンソールを使用する必要があります。

あるはずのビルド更新が表示されない場合や、HCX で問題が発生した場合や、最新の HCX ビルドをすぐにシステムにプッシュしてほしい場合は、[IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)のステップを実行してサポート・チケットを開いてください。

## 関連リンク
{: #managinghcx-related}

* [HCX on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [HCX の用語集](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [VMware Hybrid Cloud Extension の概要](https://cloud.vmware.com/vmware-hcx){:external}
* [VMware Hybrid Cloud Extension の資料](https://cloud.vmware.com/vmware-hcx/resources){:external}
