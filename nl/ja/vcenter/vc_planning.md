---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# vCenter Server インスタンスの要件と計画

VMware vCenter Server インスタンスを注文する前に、以下の要件を確認してください。 {{site.data.keyword.CloudDataCent}}のロケーション、ワークロードのキャパシティー要件、およびアドオン・サービス要件に基づいてインスタンスを計画します。

## IBM Cloud アカウントの要件

使用する {{site.data.keyword.cloud_notm}} アカウントは、特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの要件](../vmonic/slaccountrequirement.html)を参照してください。

## IBM Cloud データ・センターの使用可否

vCenter Server のデプロイメントには、物理インフラストラクチャーに関する厳密な要件があります。 そのため、要件を満たす {{site.data.keyword.CloudDataCents_notm}}にしかインスタンスはデプロイできません。 vCenter Server のデプロイメントには、以下の {{site.data.keyword.CloudDataCents_notm}}を使用できます。

表 1. vCenter Server インスタンスに使用可能な {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} | ロケーション | 地域 | サーバー・オプション |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | アムステルダム | ヨーロッパ | Skylake、Broadwell |
| CHE01 | チェンナイ | アジア太平洋 | Skylake、Broadwell |
| DAL09 | ダラス | 北米南部 | Skylake、Broadwell |
| DAL10 | ダラス | 北米南部 | Skylake、Broadwell、スモール、ミディアム、ラージ |
| DAL12 | ダラス | 北米南部 | Skylake、Broadwell |
| DAL13 | ダラス | 北米南部 | Skylake、Broadwell |
| FRA02 | フランクフルト | ヨーロッパ | Skylake、Broadwell、スモール、ミディアム、ラージ |
| FRA04 | フランクフルト | ヨーロッパ | Skylake、Broadwell |
| HKG02 | 香港 | アジア太平洋 | Skylake、Broadwell |
| LON02 | London (ロンドン) | ヨーロッパ | Skylake、Broadwell |
| LON04 | London (ロンドン) | ヨーロッパ | Skylake、Broadwell |
| LON06 | London (ロンドン) | ヨーロッパ | Skylake、Broadwell、スモール、ミディアム、ラージ |
| MEL01 | メルボルン | アジア太平洋 | Skylake、Broadwell |
| MEX01 | ケレタロ | 北米南部 | Skylake、Broadwell |
| MIL01 | ミラノ | ヨーロッパ | Skylake、Broadwell |
| MON01 | モントリオール | 北米東部 | Skylake、Broadwell |
| OSL01 | オスロ | ヨーロッパ | Skylake、Broadwell |
| PAR01 | パリ | ヨーロッパ | Skylake、Broadwell |
| SAO01 | サンパウロ | 南米 | Skylake、Broadwell |
| SEO01 | ソウル | アジア太平洋 | Skylake、Broadwell |
| SJC03 | サンノゼ | 北米西部 | Skylake、Broadwell、スモール、ミディアム、ラージ |
| SJC04 | サンノゼ | 北米西部 | Skylake、Broadwell |
| SNG01 | シンガポール | アジア太平洋 | Skylake、Broadwell |
| SYD01 | シドニー | アジア太平洋 | Skylake、Broadwell |
| SYD04 | シドニー | アジア太平洋 | Skylake、Broadwell |
| TOK02 | 東京 | アジア太平洋 | Skylake、Broadwell |
| TOR01 | トロント | 北米東部 | Skylake、Broadwell、スモール、ミディアム、ラージ |
| WDC04 | ワシントン、DC | 北米東部 | Skylake、Broadwell、スモール、ミディアム、ラージ |
| WDC06 | ワシントン、DC | 北米東部 | Skylake、Broadwell |
| WDC07 | ワシントン、DC | 北米東部 | Skylake、Broadwell |

ベア・メタル・サーバーのオプションとして事前構成型の**「スモール」**、**「ミディアム」**、および**「ラージ」**が提供されているのは、ごく一部の {{site.data.keyword.CloudDataCents_notm}} です。 入手可能状況と在庫状況によっては、デプロイメントの計画に役立つように、{{site.data.keyword.CloudDataCents_notm}}の {{site.data.keyword.vmwaresolutions_short}} コンソールに状況標識が表示される場合があります。

表 2. vCenter Server インスタンスの注文時の {{site.data.keyword.CloudDataCents_notm}}の状況標識

| 状況 | 状況の詳細 |
|:------------------------------|:--------------------------------------------------|
| 近日対応                   | 現在、{{site.data.keyword.CloudDataCent_notm}}は対応していません。 |
| 一時的な在庫切れ  | 現時点では、{{site.data.keyword.CloudDataCent_notm}}には在庫がありません。 |
| 限定在庫             | {{site.data.keyword.CloudDataCent_notm}}の在庫は限られているため、注文が満たされない可能性があります。 |

## 管理コンポーネントのバックアップ

すべてのインスタンス・コンポーネントの可用性を維持し、確保する作業は、お客様が行う必要があります。 すべての管理コンポーネントのバックアップと高可用性について計画を立てることを強くお勧めします。 詳しくは、[コンポーネントのバックアップ](../archiref/solution/solution_backingup.html)を参照してください。

## vCenter Server インスタンスのサービス

それぞれのニーズに基づいて、インスタンスのアドオン・サービスを注文できます。例えば、災害復旧などがあります。 詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](vc_addingremovingservices.html)を参照してください。

## キャパシティーに関する考慮事項

キャパシティーの考慮事項について詳しくは、[キャパシティーの拡張](../archiref/solution/solution_scaling.html)を参照してください。

### 関連リンク

* [vCenter Server の概要](vc_vcenterserveroverview.html)
* [vCenter Server インスタンスの注文](vc_orderinginstance.html)
* [vCenter Server インスタンスの容量の拡張と縮小](vc_addingremovingservers.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](vc_addingremovingservices.html)
