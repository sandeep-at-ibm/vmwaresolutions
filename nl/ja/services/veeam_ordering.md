---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud の注文
{: #veeam_ordering}

Veeam on {{site.data.keyword.cloud}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの Veeam on IBM Cloud の注文
{: #veeam_ordering-new}

以下のいずれかの方法を使用して、新しいインスタンスで Veeam on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「Veeam on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} カタログから**「Veeam on IBM Cloud」**を選択し、サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの Veeam on IBM Cloud の注文
{: #veeam_ordering-existing}

以下のいずれかの方法を使用して、既存のインスタンスに Veeam on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} カタログから**「Veeam on IBM Cloud」**を選択し、サービス設定を指定し、**「Add to Existing Instance」**を選択します。

## Veeam on IBM Cloud サービスの構成
{: #veeam_ordering-config}

このサービスを注文する際には、以下の設定を行います。

### ライセンス用の VM の数
{: #veeam_ordering-config-vms}

ライセンス管理には 10 個以上の VM が必要です。

### ストレージ・サイズ
{: #veeam_ordering-config-storage-size}

ストレージのニーズを満たす容量。 ストレージ・サイズを見積もるための考慮事項については、[Estimating Repository Capacity](https://bp.veeam.expert/resource_planning/repository_planning_sizing.html) を参照してください。

### ストレージ・パフォーマンス
{: #veeam_ordering-config-storage-performance}

ワークロードの要件に基づいた 1 GB あたりの IOPS (入出力操作/秒)。

## 関連リンク
{: #veeam_ordering-related}

* [Veeam on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Veeam on {{site.data.keyword.cloud_notm}} 用マネージド・サービスの要求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam の Web サイト](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
