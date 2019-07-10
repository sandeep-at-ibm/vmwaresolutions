---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

keywords: planning vCenter Server, data center, vCenter Server data centers

subcollection: vmware-solutions


---

# vCenter Server インスタンスの要件と計画
{: #vc_planning}

VMware vCenter Server インスタンスを注文する前に、以下の要件を確認してください。 {{site.data.keyword.CloudDataCent}}のロケーション、ワークロードのキャパシティー要件、およびアドオン・サービス要件に基づいてインスタンスを計画します。

## IBM Cloud アカウントの要件
{: #vc_planning-account-req}

使用する {{site.data.keyword.cloud_notm}} アカウントは、特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの要件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)を参照してください。

## IBM Cloud データ・センターの使用可否
{: #vc_planning-dc-availability}

vCenter Server のデプロイメントには、物理インフラストラクチャーに関する厳密な要件があります。 そのため、要件を満たす {{site.data.keyword.CloudDataCents_notm}}にしかインスタンスはデプロイできません。 vCenter Server のデプロイメントには、以下の {{site.data.keyword.CloudDataCents_notm}}を使用できます。

表 1. vCenter Server インスタンスに使用可能な {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} | ロケーション | 地域 | サーバー・オプション |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | アムステルダム | ヨーロッパ | Skylake、Broadwell |
| CHE01 | チェンナイ | アジア太平洋 | Skylake、SAP 認定、Broadwell |
| DAL09 | ダラス | 北米南部 | Skylake、SAP 認定、Broadwell |
| DAL10 | ダラス | 北米南部 | Skylake、SAP 認定、Broadwell |
| DAL12 | ダラス | 北米南部 | Skylake、SAP 認定、Broadwell |
| DAL13 | ダラス | 北米南部 | Skylake、SAP 認定、Broadwell |
| FRA02 | フランクフルト | ヨーロッパ | Skylake、SAP 認定、Broadwell |
| FRA04 | フランクフルト | ヨーロッパ | Skylake、SAP 認定、Broadwell |
| FRA05 | フランクフルト | ヨーロッパ | Skylake、Broadwell |
| HKG02 | 香港 | アジア太平洋 | Skylake、Broadwell |
| LON02 | London (ロンドン) | ヨーロッパ | Skylake、Broadwell |
| LON04 | London (ロンドン) | ヨーロッパ | Skylake、SAP 認定、Broadwell |
| LON05 | London (ロンドン) | ヨーロッパ | Skylake、Broadwell |
| LON06 | London (ロンドン) | ヨーロッパ | Skylake、SAP 認定、Broadwell |
| MEL01 | メルボルン | アジア太平洋 | Skylake、SAP 認定、Broadwell |
| MEX01 | ケレタロ | 北米南部 | Skylake、SAP 認定、Broadwell |
| MIL01 | ミラノ | ヨーロッパ | Skylake、SAP 認定、Broadwell |
| MON01 | モントリオール | 北米東部 | Skylake、SAP 認定、Broadwell |
| OSL01 | オスロ | ヨーロッパ | Skylake、Broadwell |
| PAR01 | パリ | ヨーロッパ | Skylake、Broadwell |
| SAO01 | サンパウロ | 南米 | Skylake、SAP 認定、Broadwell |
| SEO01 | ソウル | アジア太平洋 | Skylake、SAP 認定、Broadwell |
| SJC03 | サンノゼ | 北米西部 | Skylake、Broadwell |
| SJC04 | サンノゼ | 北米西部 | Skylake、Broadwell |
| SNG01 | シンガポール | アジア太平洋 | Skylake、Broadwell |
| SYD01 | シドニー | アジア太平洋 | Skylake、Broadwell |
| SYD04 | シドニー | アジア太平洋 | Skylake、SAP 認定、Broadwell |
| TOK02 | 東京 | アジア太平洋 | Skylake、SAP 認定、Broadwell |
| TOR01 | トロント | 北米東部 | Skylake、SAP 認定、Broadwell |
| WDC04 | ワシントン、DC | 北米東部 | Skylake、SAP 認定、Broadwell |
| WDC06 | ワシントン、DC | 北米東部 | Skylake、SAP 認定、Broadwell |
| WDC07 | ワシントン、DC | 北米東部 | Skylake、SAP 認定、Broadwell |

入手可能状況と在庫状況によっては、デプロイメントの計画に役立つように、{{site.data.keyword.CloudDataCents_notm}}の {{site.data.keyword.vmwaresolutions_short}} コンソールに状況標識が表示される場合があります。

表 2. vCenter Server インスタンスの注文時の {{site.data.keyword.CloudDataCents_notm}}の状況標識

| 状況 | 状況の詳細 |
|:------------------------------|:--------------------------------------------------|
| 近日対応                   | 現在、{{site.data.keyword.CloudDataCent_notm}}は対応していません。 |
| 一時的な在庫切れ  | 現時点では、{{site.data.keyword.CloudDataCent_notm}}には在庫がありません。 |
| 限定在庫             | {{site.data.keyword.CloudDataCent_notm}}の在庫は限られているため、注文が満たされない可能性があります。 |

## 管理コンポーネントのバックアップ
{: #vc_planning-backup-mgmt-components}

すべてのインスタンス・コンポーネントの可用性を維持し、確保する作業は、お客様が行う必要があります。 すべての管理コンポーネントのバックアップと高可用性について計画を立てることを強くお勧めします。 詳しくは、[コンポーネントのバックアップ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)を参照してください。

## vCenter Server インスタンスのサービス
{: #vc_planning-addon-services}

それぞれのニーズに基づいて、インスタンスのアドオン・サービスを注文できます。例えば、災害復旧などがあります。 詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)を参照してください。

vCenter Server with NSX-T インスタンスのサービスはサポートされます。
{:note}

## キャパシティーに関する考慮事項
{: #vc_planning-capacity-considerations}

キャパシティーの考慮事項について詳しくは、[キャパシティーの拡張](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling)を参照してください。

## 関連リンク
{: #vc_planning-related}

* [vCenter Server の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
