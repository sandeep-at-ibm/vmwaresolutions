---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

keywords: Caveonix, Caveonix RiskForesight, tech specs Caveonix

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight on IBM Cloud の概要
{: #caveonix_considerations}

Caveonix RiskForesight on {{site.data.keyword.cloud}} サービスは、脅威から保護し、業界規制や政府規制を遵守するために、プロアクティブなモニターおよび自動ディフェンス制御によって、サイバーおよびコンプライアンスのリスクを管理します。

このサービスは、V2.9 以降のリリースでデプロイされた VMware vCenter Server on {{site.data.keyword.cloud_notm}} インスタンスでのみ利用可能です。 現在インストールされている Caveonix RiskForesight のバージョンは 2.2.1 です。
{:note}

## Caveonix RiskForesight on IBM Cloud の技術仕様
{: #caveonix_considerations-specs}

以下のコンポーネントが注文されて Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### vCenter リソース
{: #caveonix_considerations-tech-specs-vcenter}

* CPU: 8 vCPU
* RAM: 32 GB
* ディスク: 80 GB

### ネットワーク
{: #caveonix_considerations-tech-specs-network}

64 個の IP アドレスがある専用プライベート・サブネットが注文されます。

### ライセンスと料金
{: #caveonix_considerations-tech-specs-license-fee}

サービスのインスタンスごとに、Caveonix RiskForesight ライセンス・キーが注文されます。

## Caveonix RiskForesight on IBM Cloud をインストールする際の考慮事項
{: #caveonix_considerations-install}

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスをインストールする前に、サービス・インスタンスのデフォルト・クラスター内の CPU とメモリーが、Caveonix RiskForesight 仮想マシンを使用する上で十分であることを確認します。

## Caveonix RiskForesight on IBM Cloud を削除する際の考慮事項
{: #caveonix_considerations-remove}

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスを削除する前に、以下の考慮事項を確認してください。
* Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスを削除しても、Caveonix RiskForesight ライセンスは取り消されません。 {{site.data.keyword.vmwaresolutions_short}} コンソールの**「リソース」**ページで、Caveonix RiskForesight ライセンスを**「Caveonix RiskForesight Licenses」**テーブルから削除する必要があります。
* このサービスを削除すると、{{site.data.keyword.vmwaresolutions_short}} の自動処理機能によって、デプロイされた唯一の「オールインワン」Caveonix VM とそれに対して注文された専用プライベート・サブネットが削除されてしまいます。 そのため、以下の点を考慮してください。
   * Caveonix VM をスケールアウトして複数の VM にした場合、それらの追加の VM は削除されません。
   * 追加の VM で専用プライベート・サブネットの IP アドレスを使用していた場合、それらの VM が引き続き機能するために、新しい IP アドレスを割り当てる必要があります。
   * Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスがインストールされている vCenter Server インスタンス A を削除するときに、このサービス用に注文された専用プライベート・サブネットの IP アドレスを vCenter Server インスタンス B で使用していた場合は、vCenter Server インスタンス A の削除時に専用プライベート・サブネットが取り消されます。

## 関連リンク
{: #caveonix_considerations-related}

* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
