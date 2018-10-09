---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-28"

---

# Cloud Foundation インスタンスの要件と計画

VMware Cloud Foundation インスタンスを注文する前に、以下の要件を確認してください。 {{site.data.keyword.CloudDataCent}}のロケーション、ワークロードのキャパシティー要件、およびサービス要件に基づいてインスタンスを計画します。

## IBM Cloud アカウントの要件

使用する {{site.data.keyword.cloud_notm}} アカウントは、特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの要件](../vmonic/slaccountrequirement.html)を参照してください。

## IBM Cloud データ・センターの使用可否

Cloud Foundation のデプロイメントには、物理インフラストラクチャーに関して厳密な要件があります。 そのため、要件を満たす {{site.data.keyword.CloudDataCents_notm}}にしかインスタンスはデプロイできません。 Cloud Foundation のデプロイメントには、以下の {{site.data.keyword.CloudDataCents_notm}}を使用できます。

表 1. Cloud Foundation インスタンスに使用できる {{site.data.keyword.CloudDataCents_notm}}と {{site.data.keyword.cloud_notm}} ベア・メタル・サーバーの構成

| {{site.data.keyword.CloudDataCent_notm}} | ロケーション | 地域 | サーバー構成 |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | アムステルダム | ヨーロッパ | Customized |
| CHE01 | チェンナイ | アジア太平洋 | Customized |
| DAL09 | ダラス | 北米南部 | Customized |
| DAL10 | ダラス | 北米南部 | Customized、Small、Large |
| DAL12 | ダラス | 北米南部 | Customized |
| DAL13 | ダラス | 北米南部 | Customized |
| FRA02 | フランクフルト | ヨーロッパ | Customized、Large |
| FRA04 | フランクフルト | ヨーロッパ | Customized |
| HKG02 | 香港 | アジア太平洋 | Customized |
| LON02 | London (ロンドン) | ヨーロッパ | Customized |
| LON04 | London (ロンドン) | ヨーロッパ | Customized |
| LON06 | London (ロンドン) | ヨーロッパ | Customized、Small、Large |
| MEL01 | メルボルン | アジア太平洋 | Customized |
| MEX01 | ケレタロ | 北米南部 | Customized |
| MIL01 | ミラノ | ヨーロッパ | Customized |
| MON01 | モントリオール | 北米東部 | Customized |
| OSL01 | オスロ | ヨーロッパ | Customized |
| PAR01 | パリ | ヨーロッパ | Customized |
| SAO01 | サンパウロ | 南米 | Customized |
| SEO01 | ソウル | アジア太平洋 | Customized |
| SJC03 | サンノゼ | 北米西部 | Customized |
| SJC04 | サンノゼ | 北米西部 | Customized |
| SNG01 | シンガポール | アジア太平洋 | Customized |
| SYD01 | シドニー | アジア太平洋 | Customized |
| SYD04 | シドニー | アジア太平洋 | Customized |
| TOK02 | 東京 | アジア太平洋 | Customized |
| TOR01 | トロント | 北米東部 | Customized、Small、Large |
| WDC04 | ワシントン、DC | 北米東部 | Customized、Small、Large |
| WDC06 | ワシントン、DC | 北米東部 | Customized |
| WDC07 | ワシントン、DC | 北米東部 | Customized |

入手可能状況と在庫状況によっては、デプロイメントの計画に役立つように、{{site.data.keyword.CloudDataCents_notm}}の {{site.data.keyword.vmwaresolutions_short}} コンソールに状況標識が表示される場合があります。

表 2. Cloud Foundation インスタンス注文時の {{site.data.keyword.CloudDataCents_notm}}の状況標識

| 状況 | 状況の詳細 |
|:------------------------------|:--------------------------------------------------|
| 近日対応                   | 現在、{{site.data.keyword.CloudDataCent_notm}}は対応していません。 |
| 一時的な在庫切れ  | 現時点では、{{site.data.keyword.CloudDataCent_notm}}には在庫がありません。|
| 限定在庫             | {{site.data.keyword.CloudDataCent_notm}}の在庫は限られているため、注文が満たされない可能性があります。 |

## 管理コンポーネントのバックアップ

すべてのインスタンス・コンポーネントの可用性を維持し、確保する作業は、お客様が行う必要があります。 すべての管理コンポーネントのバックアップと高可用性について計画を立てることをお勧めします。詳しくは、[コンポーネントのバックアップ](../archiref/solution/solution_backingup.html)を参照してください。

## Cloud Foundation インスタンス用サービス

それぞれのニーズに基づいて、インスタンスのアドオン・サービスを注文できます。例えば、災害復旧などがあります。 詳しくは、[Cloud Foundation インスタンスのサービスの注文、表示、削除](sd_addingremovingservices.html)を参照してください。

## キャパシティーに関する考慮事項

キャパシティーについて詳しくは、[キャパシティーの拡張](../archiref/solution/solution_scaling.html)を参照してください。

### 関連リンク

* [Cloud Foundation の概要](sd_cloudfoundationoverview.html)
* [Cloud Foundation インスタンスの注文](sd_orderinginstance.html)
* [Cloud Foundation インスタンスの容量の拡張と縮小](sd_addingremovingservers.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](sd_addingremovingservices.html)
