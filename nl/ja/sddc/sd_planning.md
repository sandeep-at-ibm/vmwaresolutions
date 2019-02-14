---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Cloud Foundation インスタンスの要件と計画

VMware Cloud Foundation インスタンスを注文する前に、以下の要件を確認してください。 {{site.data.keyword.CloudDataCent}}のロケーション、ワークロードのキャパシティー要件、およびサービス要件に基づいてインスタンスを計画します。

## IBM Cloud アカウントの要件

使用する {{site.data.keyword.cloud_notm}} アカウントは、特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの要件](/docs/services/vmwaresolutions/vmonic/slaccountrequirement.html)を参照してください。

## IBM Cloud データ・センターの使用可否

Cloud Foundation のデプロイメントには、物理インフラストラクチャーに関して厳密な要件があります。 そのため、要件を満たす {{site.data.keyword.CloudDataCents_notm}}にしかインスタンスはデプロイできません。 Cloud Foundation のデプロイメントには、以下の {{site.data.keyword.CloudDataCents_notm}}を使用できます。

表 1. Cloud Foundation インスタンスに使用できる {{site.data.keyword.CloudDataCents_notm}}と {{site.data.keyword.cloud_notm}} ベア・メタル・サーバーの構成

| {{site.data.keyword.CloudDataCent_notm}} | ロケーション | 地域 | サーバー構成 |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | アムステルダム | ヨーロッパ | Skylake、Broadwell |
| CHE01 | チェンナイ | アジア太平洋 | Skylake、Broadwell |
| DAL09 | ダラス | 北米南部 | Skylake、Broadwell |
| DAL10 | ダラス | 北米南部 | Skylake、Broadwell |
| DAL12 | ダラス | 北米南部 | Skylake、Broadwell |
| DAL13 | ダラス | 北米南部 | Skylake、Broadwell |
| FRA02 | フランクフルト | ヨーロッパ | Skylake、Broadwell |
| FRA04 | フランクフルト | ヨーロッパ | Skylake、Broadwell |
| HKG02 | 香港 | アジア太平洋 | Skylake、Broadwell |
| LON02 | London (ロンドン) | ヨーロッパ | Skylake、Broadwell |
| LON04 | London (ロンドン) | ヨーロッパ | Skylake、Broadwell |
| LON06 | London (ロンドン) | ヨーロッパ | Skylake、Broadwell |
| MEL01 | メルボルン | アジア太平洋 | Skylake、Broadwell |
| MEX01 | ケレタロ | 北米南部 | Skylake、Broadwell |
| MIL01 | ミラノ | ヨーロッパ | Skylake、Broadwell |
| MON01 | モントリオール | 北米東部 | Skylake、Broadwell |
| OSL01 | オスロ | ヨーロッパ | Skylake、Broadwell |
| PAR01 | パリ | ヨーロッパ | Skylake、Broadwell |
| SAO01 | サンパウロ | 南米 | Skylake、Broadwell |
| SEO01 | ソウル | アジア太平洋 | Skylake、Broadwell |
| SJC03 | サンノゼ | 北米西部 | Skylake、Broadwell |
| SJC04 | サンノゼ | 北米西部 | Skylake、Broadwell |
| SNG01 | シンガポール | アジア太平洋 | Skylake、Broadwell |
| SYD01 | シドニー | アジア太平洋 | Skylake、Broadwell |
| SYD04 | シドニー | アジア太平洋 | Skylake、Broadwell |
| TOK02 | 東京 | アジア太平洋 | Skylake、Broadwell |
| TOR01 | トロント | 北米東部 | Skylake、Broadwell |
| WDC04 | ワシントン、DC | 北米東部 | Skylake、Broadwell |
| WDC06 | ワシントン、DC | 北米東部 | Skylake、Broadwell |
| WDC07 | ワシントン、DC | 北米東部 | Skylake、Broadwell |

入手可能状況と在庫状況によっては、デプロイメントの計画に役立つように、{{site.data.keyword.CloudDataCents_notm}}の {{site.data.keyword.vmwaresolutions_short}} コンソールに状況標識が表示される場合があります。

表 2. Cloud Foundation インスタンス注文時の {{site.data.keyword.CloudDataCents_notm}}の状況標識

| 状況 | 状況の詳細 |
|:------------------------------|:--------------------------------------------------|
| 近日対応                   | 現在、{{site.data.keyword.CloudDataCent_notm}}は対応していません。 |
| 一時的な在庫切れ  | 現時点では、{{site.data.keyword.CloudDataCent_notm}}には在庫がありません。 |
| 限定在庫             | {{site.data.keyword.CloudDataCent_notm}}の在庫は限られているため、注文が満たされない可能性があります。 |

## 管理コンポーネントのバックアップ

すべてのインスタンス・コンポーネントの可用性を維持し、確保する作業は、お客様が行う必要があります。 すべての管理コンポーネントのバックアップと高可用性について計画を立てることをお勧めします。 詳しくは、[コンポーネントのバックアップ](/docs/services/vmwaresolutions/archiref/solution/solution_backingup.html)を参照してください。

## Cloud Foundation インスタンス用サービス

それぞれのニーズに基づいて、インスタンスのアドオン・サービスを注文できます。例えば、災害復旧などがあります。 詳しくは、[Cloud Foundation インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)を参照してください。

## キャパシティーに関する考慮事項

キャパシティーについて詳しくは、[キャパシティーの拡張](/docs/services/vmwaresolutions/archiref/solution/solution_scaling.html)を参照してください。

### 関連リンク

* [Cloud Foundation の概要](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)
* [Cloud Foundation インスタンスの注文](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [Cloud Foundation インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/sddc/sd_addingremovingservers.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
