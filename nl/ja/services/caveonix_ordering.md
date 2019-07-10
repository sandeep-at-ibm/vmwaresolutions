---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: Caveonix RiskForesight, Caveonix configuration, order Caveonix

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight on IBM Cloud の注文
{: #caveonix_ordering}

Caveonix RiskForesight on {{site.data.keyword.cloud}} サービスを注文するには、そのサービスを組み込む形で新しい VMware vCenter Server インスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの Caveonix RiskForesight on IBM Cloud の注文
{: #caveonix_ordering-new}

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} を組み込む形で新しい VMware vCenter Server on {{site.data.keyword.cloud_notm}} インスタンスを注文する場合は、{{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンスを注文する時に、**「サービス」**セクションで**「Caveonix RiskForesight on IBM Cloud」**を選択します。

## 既存のインスタンスでの Caveonix RiskForesight on IBM Cloud の注文
{: #caveonix_ordering-existing}

既存の VMware vCenter Server on {{site.data.keyword.cloud_notm}} インスタンスに Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスを追加する場合は、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。

## Caveonix RiskForesight on IBM Cloud の構成
{: #caveonix_ordering-config}

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスを注文する際には、以下の設定を行います。

### ライセンス名
{: #caveonix_ordering-config-license-name}

ライセンスに対して固有の名前を指定してください。

### ライセンス・メモ
{: #caveonix_ordering-config-license-notes}

サービス・インスタンスに関するメモを入力します。 メモは後でライセンス詳細ページで編集できます。

### ライセンス用の VM の数
{: #caveonix_ordering-config-vms}

ライセンスを交付する VM 数を選択します (10 個単位で増分可能な、10 個から 1000 個までの VM ライセンス)。 ライセンス管理には 10 個以上の VM が必要です。

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスを注文した後、注文で指定した数より多くの VM にライセンスを交付する場合は、Caveonix RiskForesight ライセンスを置き換えることができます。その方法として、より大きなライセンスを注文し、ライセンスを Caveonix RiskForesight コンソールにコピーしてから以前のライセンスを {{site.data.keyword.vmwaresolutions_short}} コンソールから削除します。 詳しくは、[Caveonix RiskForesight ライセンスを注文する手順](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure)および [Caveonix RiskForesight ライセンスを削除する手順](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete)を参照してください。
{:note}

## 関連リンク
{: #caveonix_ordering-related}

* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
