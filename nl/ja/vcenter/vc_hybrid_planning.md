---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# vCenter Server with Hybridity Bundle インスタンスの要件と計画
{: #vc_hybrid_planning}

Hybridity Bundle インスタンスを使用して、VMware vCenter Server on {{site.data.keyword.cloud}} を注文する前に、以下の要件を確認してください。 {{site.data.keyword.CloudDataCent_notm}}のロケーション、ワークロードのキャパシティー要件、および追加のサービス要件に基づいてインスタンスを計画します。

## IBM Cloud アカウントの要件
{: #vc_hybrid_planning-account-req}

使用する {{site.data.keyword.cloud_notm}} アカウントは、特定の要件を満たしている必要があります。 詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの要件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement)を参照してください。

## IBM Cloud データ・センターの使用可否
{: #vc_hybrid_planning-dc-availability}

vCenter Server with Hybridity Bundle のデプロイメントには、物理インフラストラクチャーに関する厳密な要件があります。 そのため、要件を満たす {{site.data.keyword.CloudDataCents_notm}}にしかインスタンスはデプロイできません。 vCenter Server with Hybridity Bundle のデプロイメントには、以下の {{site.data.keyword.CloudDataCents_notm}}を使用できます。

表 1. vCenter Server with Hybridity Bundle インスタンスに使用可能な {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} | ロケーション | 地域 |
|:-----|:----------------|
| AMS03 | アムステルダム | ヨーロッパ |
| CHE01 | チェンナイ | アジア太平洋 |
| DAL09 | ダラス | 北米南部 |
| DAL10 | ダラス | 北米南部 |
| DAL12 | ダラス | 北米南部 |
| DAL13 | ダラス | 北米南部 |
| FRA02 | フランクフルト | ヨーロッパ |
| FRA04 | フランクフルト | ヨーロッパ |
| HKG02 | 香港 | アジア太平洋 |
| LON02 | London (ロンドン) | ヨーロッパ |
| LON04 | London (ロンドン) | ヨーロッパ |
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

入手可能状況と在庫状況によっては、デプロイメントの計画に役立つように、{{site.data.keyword.CloudDataCents_notm}}の {{site.data.keyword.vmwaresolutions_short}} コンソールに状況標識が表示される場合があります。

表 2. vCenter Server with Hybridity Bundle インスタンスの注文時の {{site.data.keyword.CloudDataCents_notm}}の状況標識

| 状況 | 状況の詳細 |
|:------------------------------|:--------------------------------------------------|
| 近日対応                   | 現在、{{site.data.keyword.CloudDataCent_notm}}は対応していません。 |
| 一時的な在庫切れ  | 現時点では、{{site.data.keyword.CloudDataCent_notm}}には在庫がありません。 |
| 限定在庫             | {{site.data.keyword.CloudDataCent_notm}}の在庫は限られているため、注文が満たされない可能性があります。 |

## 管理コンポーネントのバックアップ
{: #vc_hybrid_planning-backup-mgmt-components}

すべてのインスタンス・コンポーネントの可用性を維持し、確保する作業は、お客様が行う必要があります。 すべての管理コンポーネントのバックアップと高可用性について計画を立てることを強くお勧めします。 詳しくは、[コンポーネントのバックアップ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)を参照してください。

## vCenter Server with Hybridity Bundle インスタンス用のサービス
{: #vc_hybrid_planning-addon-services}

vCenter Server with Hybridity Bundle インスタンスには VMware Hybrid Cloud Extension (HCX) のライセンスが含まれているので、VMware HCX on {{site.data.keyword.cloud_notm}} サービスを利用できます。 このサービスは、オンプレミス・データ・センターのネットワークを {{site.data.keyword.cloud_notm}} にシームレスに拡張します。これにより、変換や変更を行わずに仮想マシン (VM) を {{site.data.keyword.cloud_notm}} との間で移行できるようになります。

このサービスをデプロイする際には、以下の設定を行います。
* **「HCX interconnect type」**を指定します。以下のいずれかのオプションを選択します。
  * **Public network**: HCX がパブリック・ネットワークでサイト間の暗号化接続を作成します。
  * **Private network**: HCX がプライベート・ネットワークでサイト間の暗号化接続を作成します。
* **「Public endpoint certificate type」**を指定します。 **「CA 証明書」**を選択する場合、以下の設定を構成してください。
  * **証明書の内容**: CA 証明書の内容を入力します。
  * **秘密鍵**: CA 証明書の秘密鍵を入力します。
  * (オプション) **パスワード**: 秘密鍵が暗号化されている場合は、秘密鍵のパスワードを入力します。
  * (オプション) **パスワードの再入力**: 秘密鍵のパスワードをもう一度入力します。
  * (オプション) **ホスト名**: CA 証明書の共通名 (CN) にマップするホスト名を入力します。 HCX on {{site.data.keyword.cloud_notm}} には、NSX Edge で受け入れられる形式の CA 証明書を使用する必要があります。 NSX Edge の証明書の形式について詳しくは、[SSL 証明書のインポート](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html)を参照してください。

それぞれのニーズに基づいて、インスタンスの他のアドオン・サービスを注文できます。例えば、災害復旧などがあります。 詳しくは、[vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)を参照してください。

## キャパシティーに関する考慮事項
{: #vc_hybrid_planning-capacity-considerations}

キャパシティーの考慮事項について詳しくは、[キャパシティーの拡張](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling)を参照してください。

## 関連リンク
{: #vc_hybrid_planning-related}

* [vCenter Server with Hybridity Bundle の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [vCenter Server with Hybridity Bundle インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [vCenter Server with Hybridity Bundle インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
