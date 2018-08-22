---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# vCenter Server インスタンスの要件と計画

VMware vCenter Server インスタンスを注文する前に、以下の要件を確認してください。 {{site.data.keyword.CloudDataCent}}のロケーション、ワークロードのキャパシティー要件、および追加のサービス要件に基づいてインスタンスを計画します。

## IBM Cloud アカウントの要件

使用する {{site.data.keyword.cloud_notm}} アカウントは、特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの要件](../vmonic/slaccountrequirement.html)を参照してください。

## IBM Cloud データ・センターの使用可否

vCenter Server のデプロイメントには、物理インフラストラクチャーに関する厳密な要件があります。 そのため、要件を満たす {{site.data.keyword.CloudDataCents_notm}}にしかインスタンスはデプロイできません。 vCenter Server のデプロイメントには、以下の {{site.data.keyword.CloudDataCents_notm}}を使用できます。

表 1. vCenter Server インスタンスに使用可能な {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} | ロケーション | 地域 | サーバー・オプション |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | アムステルダム | ヨーロッパ | カスタマイズ型 |
| CHE01 | チェンナイ | アジア太平洋 | カスタマイズ型 |
| DAL09 | ダラス | 北米南部 | カスタマイズ型 |
| DAL10 | ダラス | 北米南部 | カスタマイズ型、スモール、ミディアム、ラージ |
| DAL12 | ダラス | 北米南部 | カスタマイズ型 |
| DAL13 | ダラス | 北米南部 | カスタマイズ型 |
| FRA02 | フランクフルト | ヨーロッパ | カスタマイズ型、スモール、ミディアム、ラージ |
| FRA04 | フランクフルト | ヨーロッパ | カスタマイズ型 |
| HKG02 | 香港 | アジア太平洋 | カスタマイズ型 |
| LON02 | London (ロンドン) | ヨーロッパ | カスタマイズ型 |
| LON04 | London (ロンドン) | ヨーロッパ | カスタマイズ型 |
| LON06 | London (ロンドン) | ヨーロッパ | カスタマイズ型、スモール、ミディアム、ラージ |
| MEL01 | メルボルン | アジア太平洋 | カスタマイズ型 |
| MEX01 | ケレタロ | 北米南部 | カスタマイズ型 |
| MIL01 | ミラノ | ヨーロッパ | カスタマイズ型 |
| MON01 | モントリオール | 北米東部 | カスタマイズ型 |
| OSL01 | オスロ | ヨーロッパ | カスタマイズ型 |
| PAR01 | パリ | ヨーロッパ | カスタマイズ型 |
| SAO01 | サンパウロ | 南米 | カスタマイズ型 |
| SEO01 | ソウル | アジア太平洋 | カスタマイズ型 |
| SJC03 | サンノゼ | 北米西部 | カスタマイズ型、スモール、ミディアム、ラージ |
| SJC04 | サンノゼ | 北米西部 | カスタマイズ型 |
| SNG01 | シンガポール | アジア太平洋 | カスタマイズ型 |
| SYD01 | シドニー | アジア太平洋 | カスタマイズ型 |
| SYD04 | シドニー | アジア太平洋 | カスタマイズ型 |
| TOK02 | 東京 | アジア太平洋 | カスタマイズ型 |
| TOR01 | トロント | 北米東部 | カスタマイズ型、スモール、ミディアム、ラージ |
| WDC04 | ワシントン、DC | 北米東部 | カスタマイズ型、スモール、ミディアム、ラージ |
| WDC06 | ワシントン、DC | 北米東部 | カスタマイズ型 |
| WDC07 | ワシントン、DC | 北米東部 | カスタマイズ型 |

ベア・メタル・サーバーのオプションとして事前構成型の**「スモール」**、**「ミディアム」**、および**「ラージ」**が提供されているのは、ごく一部の {{site.data.keyword.CloudDataCents_notm}} です。入手可能状況と在庫状況によっては、デプロイメントの計画に役立つように、{{site.data.keyword.CloudDataCents_notm}}の {{site.data.keyword.vmwaresolutions_short}} コンソールに状況標識が表示される場合があります。

表 2. vCenter Server インスタンスの注文時の {{site.data.keyword.CloudDataCents_notm}}の状況標識

| 状況 | 状況の詳細 |
|:------------------------------|:--------------------------------------------------|
| 近日対応                   | 現在、{{site.data.keyword.CloudDataCent_notm}}は対応していません。 |
| 一時的な在庫切れ  | 現時点では、{{site.data.keyword.CloudDataCent_notm}}には在庫がありません。 |
| 限定在庫             | {{site.data.keyword.CloudDataCent_notm}}の在庫は限られているため、注文が満たされない可能性があります。 |

## 管理コンポーネントのバックアップ

すべてのインスタンス・コンポーネントの可用性を維持し、確保する作業は、お客様が行う必要があります。すべての管理コンポーネントのバックアップと高可用性について計画を立てることを強くお勧めします。詳しくは、[コンポーネントのバックアップ](../archiref/solution/solution_backingup.html)を参照してください。

## vCenter Server インスタンスのサービス

それぞれのニーズに基づいて、インスタンスのアドオン・サービスを注文できます。例えば、災害復旧などがあります。 詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](vc_addingremovingservices.html)を参照してください。

## キャパシティーに関する考慮事項

キャパシティーに関する情報と考慮事項については、[キャパシティーの拡張](../archiref/solution/solution_scaling.html)を参照してください。

### 関連リンク

* [vCenter Server の概要](vc_vcenterserveroverview.html)
* [vCenter Server インスタンスの注文](vc_orderinginstance.html)
* [vCenter Server インスタンスの容量の拡張と縮小](vc_addingremovingservers.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](vc_addingremovingservices.html)
