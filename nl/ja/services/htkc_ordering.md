---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# HyTrust KeyControl on IBM Cloud の注文

HyTrust KeyControl on {{site.data.keyword.cloud}} サービスを注文するには、HyTrust KeyControl アプライアンスの HA ペアを組み込む形で新しいインスタンスを注文するか、HyTrust KeyControl アプライアンスを既存のインスタンスに追加します。

## 新しいインスタンスでの HyTrust KeyControl on IBM Cloud の注文

以下のいずれかの方法を使用して、新しいインスタンスで HyTrust KeyControl on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「HyTrust KeyControl on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} カタログから**「HyTrust KeyControl on IBM Cloud」**を選択し、サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの HyTrust KeyControl on IBM Cloud の注文

以下のいずれかの方法を使用して、既存のインスタンスに HyTrust KeyControl on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} カタログから**「HyTrust KeyControl on IBM Cloud」**を選択し、サービス設定を指定し、**「Add to Existing Instance」**を選択します。

## HyTrust KeyControl on IBM Cloud サービスの構成

このサービスを注文する際には、以下の設定を行います。

2 ノードの高可用性 KeyControl クラスターを作成するかどうかを指定します。
* このオプションを選択した場合は、2 つの KeyControl ノードがデプロイされ、新しいアクティブ-アクティブ高可用性クラスターが作成されます。 これはデフォルト・オプションです。
* このオプションを選択しなかった場合は、2 つのスタンドアロン KeyControl ノードがデプロイされ、クラスターは作成されません。 スタンドアロン・ノードは、デプロイメント後に手動でクラスター化するか、既存の KeyControl クラスターに追加することができます。

### 関連リンク

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} の概要](htkc_considerations.html)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} の管理](managinghtkc.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust Web サイト](https://www.hytrust.com/)
