---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-31"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware vSphere on IBM Cloud の要件と計画

VMware vSphere on {{site.data.keyword.cloud}} を注文する前に、以下の要件を確認してください。 {{site.data.keyword.CloudDataCent_notm}}のロケーションとワークロードの容量要件に基づいて、VMware vSphere クラスターの計画を立ててください。

ESXi サーバーがデプロイされた後は、お客様が、環境をセットアップし、さまざまな VMware コンポーネントをインストールして構成する必要があります。 VMware コンポーネントの例としては、VMware vCenter Server、VMware NSX、および VMware vSAN があります。
{:note}

## IBM Cloud アカウントの要件

使用する {{site.data.keyword.cloud_notm}} アカウントは、特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの要件](../vmonic/slaccountrequirement.html)を参照してください。

## IBM Cloud データ・センターの使用可否

vSphere のデプロイメントには、物理インフラストラクチャーに関する厳密な要件があります。 そのため、要件を満たす {{site.data.keyword.CloudDataCents_notm}}にしかクラスターはデプロイできません。 vSphere のデプロイメントには、以下の {{site.data.keyword.CloudDataCent_notm}}を使用可能です。

vSAN コンポーネントを選択した場合は、SSD (ソリッド・ステート・ディスク) の使用可否によってロケーション・リストがフィルタリングされます。
{:note}

表 1. vSphere クラスターに使用可能な {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} | ロケーション | 地域 |
|:----------------------|:---------|:-------|
| AMS03 | アムステルダム | ヨーロッパ |
| CHE01 | チェンナイ | アジア太平洋 |
| DAL09 | ダラス | 北米南部 |
| DAL10 | ダラス | 北米南部 |
| DAL12 | ダラス | 北米南部 |
| DAL13 | ダラス | 北米南部 |
| FRA02 | フランクフルト | ヨーロッパ |
| FRA04 | フランクフルト | ヨーロッパ |
| FRA05 | フランクフルト | ヨーロッパ |
| HKG02 | 香港 | アジア太平洋 |
| LON02 | London (ロンドン) | ヨーロッパ |
| LON04 | London (ロンドン) | ヨーロッパ |
| LON05 | London (ロンドン) | ヨーロッパ |
| LON06 | London (ロンドン) | ヨーロッパ |
| MEL01 | メルボルン | アジア太平洋 |
| MEX01 | ケレタロ | 北米南部 |
| MIL01 | ミラノ | ヨーロッパ |
| MON01 | モントリオール | 北米東部 |
| OSL01 | オスロ | ヨーロッパ |
| PAR01 | パリ | ヨーロッパ |
| SAO01 | サンパウロ | 南米 |
| SEO01 | ソウル | アジア太平洋 |
| SJC03 | サンノゼ | 北米西部 |
| SJC04 | サンノゼ | 北米西部 |
| SNG01 | シンガポール | アジア太平洋 |
| SYD01 | シドニー | アジア太平洋 |
| SYD04 | シドニー | アジア太平洋 |
| TOK02 | 東京 | アジア太平洋 |
| TOR01 | トロント | 北米東部 |
| WDC04 | ワシントン、DC | 北米東部 |
| WDC06 | ワシントン、DC | 北米東部 |
| WDC07 | ワシントン、DC | 北米東部 |

### 関連リンク

* [新規 vSphere クラスターの注文](vs_orderinginstances.html)
* [既存クラスターの拡張](vs_scalingexistingclusters.html)
* [コンソール以外で作成された既存クラスターの拡張](vs_orderingforclustersoutside.html)
