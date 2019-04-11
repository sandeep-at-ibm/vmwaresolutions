---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# VMware Federal インスタンスの要件と計画

VMware Federal インスタンスを注文する前に、以下の要件を確認してください。 ワークロードの容量要件に基づいてインスタンスを計画します。

## IBM Cloud アカウントの要件

使用する {{site.data.keyword.cloud}} アカウントは特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの要件](/docs/services/vmwaresolutions/vmonic/slaccountrequirement.html)を参照してください。

## IBM Cloud データ・センターの使用可否

VMware Federal on {{site.data.keyword.cloud_notm}} のデプロイメントには、物理インフラストラクチャーに関する厳密な要件があります。 VMware Federal インスタンスをデプロイできるのは、以下の {{site.data.keyword.CloudDataCents_notm}}だけになります。
- WDC03 - Washington, DC, POD2
- DAL08 - Dallas, TX, POD2

## 管理コンポーネントのバックアップ

ユーザーには、任意のバックアップ・ソリューションを使用して、すべてのインスタンス・コンポーネントの可用性を維持および確保する責務があります。 すべての管理コンポーネントのバックアップと高可用性について計画を立てることを強くお勧めします。 詳しくは、[コンポーネントのバックアップ](/docs/services/vmwaresolutions/archiref/solution/solution_backingup.html)を参照してください。

## VMware Federal インスタンスのサービス

VMware Federal on {{site.data.keyword.cloud_notm}} には、追加のサービスを注文できるオプションがありません。

## キャパシティーに関する考慮事項

キャパシティーに関する情報と考慮事項については、[キャパシティーの拡張](/docs/services/vmwaresolutions/archiref/solution/solution_scaling.html)を参照してください。

### 関連リンク

* [vCenter Server ソフトウェアの部品構成表](/docs/services/vmwaresolutions/vcenter/vc_bom.html)
* [VMware Federal on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/vcenter/vc_fed_overview.html)
* [VMware Federal インスタンスの注文](/docs/services/vmwaresolutions/vcenter/vc_fed_orderinginstance.html)
* [VMware Federal インスタンスの保護](/docs/services/vmwaresolutions/vcenter/vc_fed_securinginstance.html)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
