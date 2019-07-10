---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX コンポーネントのアップグレード
{: #hcxclient-vcs-upgrade}

HCX のアップグレードは、クライアント・サイドの HCX Manager の更新にクライアント Web ユーザー・インターフェース (UI) を使用し、
クラウド・サイドの HCX Manager の更新にクラウド Web UI を使用する、シンプルなプロセスです。

アップグレードは両サイドで行う必要があります。いずれかのフリート・コンポーネントを更新すると、両サイドのフリート・コンポーネントが、HCX Manager にインストールされたコードのレベルで再デプロイされるためです。

VMware サポートからシステム ID を求められた場合は、クライアント・サイドとクラウド・サイドの両方を提示してください。 SSH を使用して HCX Manager (クライアントまたはクラウド) に接続し、`cat /common/location` を実行してシステム ID を見つけます。

## 関連リンク
{: #hcxclient-vcs-upgrade-related}

* [HCX のコンポーネントと用語集](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [インストール環境の準備](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX クライアントのデプロイメント](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX オンプレミスのサービス・メッシュ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud のマイグレーション](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [パラメーターとコンポーネントのモニター](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX のトラブルシューティング](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
