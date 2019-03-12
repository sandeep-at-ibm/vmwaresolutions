---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# HCX コンポーネントのアップグレード
{: #vcshcx-upgrade}

HCX のアップグレードは、クライアント・サイドの HCX Manager の更新にクライアント Web ユーザー・インターフェース (UI) を使用し、
クラウド・サイドの HCX Manager の更新にクラウド Web UI を使用する、シンプルなプロセスです。 アップグレードは両サイドで行う必要があります。
いずれかのフリート・コンポーネントを更新すると、両サイドのフリート・コンポーネントが、マネージャーによってインストールされたコードのレベルで再デプロイされるためです。 VMware サポートからシステム ID を求められた場合は、クライアント・サイドとクラウド・サイドの両方を提示してください。 SSH を使用して HCX Manager (クライアントまたはクラウド) に接続し、`cat
/common/location` を実行してシステム ID を見つけます。

## 関連リンク
{: #vcshcx-upgrade-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle の概要](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
