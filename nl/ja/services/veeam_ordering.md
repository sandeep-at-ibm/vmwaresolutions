---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Veeam on IBM Cloud の注文

Veeam on {{site.data.keyword.cloud_notm}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの Veeam on IBM Cloud の注文

以下のいずれかの方法を使用して、新しいインスタンスで Veeam on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_full}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「Veeam on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} カタログから**「Veeam on {{site.data.keyword.cloud_notm}} service」**を選択し、サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの Veeam on IBM Cloud の注文

以下のいずれかの方法を使用して、既存のインスタンスに Veeam on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「サービスの追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} カタログから**「Veeam on IBM Cloud service」**を選択し、サービス設定を指定し、**「Add to Existing Instance」**を選択します。

## Veeam on IBM Cloud サービスの構成

このサービスを注文する際には、以下の設定を行います。

### ライセンス用の VM の数

ライセンス管理には 4 個以上の VM が必要です。

### ストレージ・サイズ

ストレージのニーズを満たす容量。 管理には 2,000 GB 以上のストレージが必要です。 ストレージ・サイズを見積もる際の考慮事項については、[Estimating Repository Capacity](https://bp.veeam.expert/resource_planning/repository_planning_sizing.html) を参照してください。

### ストレージ・パフォーマンス

ワークロードの要件に基づいた 1 GB あたりの IOPS (入出力操作/秒)。


## 関連リンク

* [Veeam on {{site.data.keyword.cloud_notm}} の概要](veeam_considerations.html)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理](managingveeam.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](../vcenter/vc_hybrid_addingremovingservices.html)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理対象サービスの要求](managing_veeam_services.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam の Web サイト](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
