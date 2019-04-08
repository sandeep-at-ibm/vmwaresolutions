---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight on IBM Cloud の管理
{: #managingcaveonix}

## Caveonix RiskForesight コンソールへのアクセス
{: #managingcaveonix-access-console}

Caveonix RiskForesight on {{site.data.keyword.cloud}} サービスを管理するには、以下の手順を実行して Caveonix RiskForesight コンソールにアクセスする必要があります。

1. IBM Cloud インフラストラクチャー VPN またはジャンプ・サーバーを使用して、Caveonix RiskForesight 仮想マシン (VM) の IP アドレスへのアクセスを許可します。 この IP アドレスは、{{site.data.keyword.vmwaresolutions_short}} コンソールの Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} のサービスの詳細ページで調べることができます。 具体的には、以下のようにします。
   1. {{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータルから VPN パスワードを作成します。
   2. {{site.data.keyword.cloud_notm}} インフラストラクチャー VPN 資格情報を使用して、データ・センターの VPN ポータルにログインします。
   3. ローカル・コンピューターから、IP アドレスとホスト名のマッピングを `hosts` ファイルに追加します。以下のフォーマットを使用します。

      ```javascript
      RiskForesight_VM_IP_Address      RiskForesight_FQDN
      ```
2. Caveonix RiskForesight コンソールにアクセスするには、Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} のサービスの詳細ページで**「RiskForesight コンソールの表示」**をクリックしてから、同じサービス詳細ページにリストされる資格情報を使用してログインします。

## Caveonix RiskForesight on IBM Cloud への更新の適用
{: #managingcaveonix-update}

Caveonix RiskForesight を最新バージョンに更新する責任は、ユーザー側にあります。 必要な更新は、[Caveonix Service Provider Portal](https://support.caveonix.com) からダウンロードできます。

## Caveonix RiskForesight ライセンスの更新

Caveonix RiskForesight ライセンスは 1 年間有効です。 有効期限が切れたら、以下の手順に従って Caveonix RiskForesight ライセンスを更新できます。
1. 新規 Caveonix RiskForesight ライセンスを注文し、それを Caveonix RiskForesight コンソールにコピーします。 詳しくは、[Caveonix RiskForesight ライセンスを注文する手順](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure)を参照してください。
2. 期限切れのライセンスを {{site.data.keyword.vmwaresolutions_short}} コンソールの**「Caveonix RiskForesight Licenses」**テーブルから削除します。 詳しくは、[Caveonix RiskForesight ライセンスを削除する手順](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete)を参照してください。

## 関連リンク
{: #managingcaveonix-related}

* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
