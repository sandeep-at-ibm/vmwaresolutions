---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: IBM Spectrum Protect Plus, SPP configuration, order SPP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# IBM Spectrum Protect Plus on IBM Cloud の注文
{: #spp_ordering}

{{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの IBM Spectrum Protect Plus on IBM Cloud の注文
{: #spp_ordering-new}

以下のいずれかの方法を使用して、新しいインスタンスで IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「IBM Spectrum Protect Plus on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware サービス」**セクションの**「IBM Spectrum Protect Plus on IBM Cloud」**カードをクリックします。サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの IBM Spectrum Protect Plus on IBM Cloud の注文
{: #spp_ordering-existing}

以下のいずれかの方法を使用して、既存のインスタンスに IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware サービス」**セクションの**「IBM Spectrum Protect Plus on IBM Cloud」**カードをクリックします。サービス設定を指定し、**「Add to Existing Instance」**を選択します。

## IBM Spectrum Protect Plus on IBM Cloud サービスの構成
{: #spp_ordering-config}

このサービスを注文する際には、以下の設定を行います。

### ストレージ・ボリュームの数
{: #spp_ordering-config-number-vol}

ストレージのニーズを満たすボリュームの数。

### ボリュームあたりのストレージ・サイズ
{: #spp_ordering-config-size}

ボリュームあたりのストレージ容量。

### ストレージ・パフォーマンス
{: #spp_ordering-config-performance}

ワークロードの要件に基づいた 1 GB あたりの IOPS (入出力操作/秒)。
* IBM Spectrum Protect Plus のライセンスを注文する場合は、**「ライセンスの注文」**タブで**「ライセンスに対する VM の数」**を指定します。
* ライセンス持ち込み (BYOL) を行う場合は、**「IBM Spectrum Protect Plus licenses」**タブをクリックし、次に**「ライセンス・ファイルの追加」**をクリックして、お持ちの IBM Spectrum Protect Plus ライセンス・ファイルをアップロードします。

## IBM Spectrum Protect Plus on IBM Cloud のデプロイメント・プロセス
{: #spp_ordering-deploy}

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} のデプロイメントは自動化されています。 このサービスを組み込む形でインスタンスを注文する場合でも、このサービスを後でインスタンスにデプロイする場合でも、{{site.data.keyword.vmwaresolutions_short}} の自動化プロセスによって以下の手順が実行されます。

1. 指定した設定に基づいて、IBM Spectrum Protect Plus バックアップ・リポジトリー用のエンデュランス NFS ストレージが {{site.data.keyword.cloud_notm}} インフラストラクチャーに注文されます。
2. 指定した設定に基づいて、IBM Spectrum Protect Plus のためのいくつかのライセンスが {{site.data.keyword.cloud_notm}} インフラストラクチャーに注文されます。 ライセンスは、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスの注文時に指定した、ライセンスを受ける仮想マシン (VM) の数に基づいて、VM ライセンス・パックが 10 個単位で注文されます。 既存の IBM Spectrum Protect Plus ライセンスを持ち込む場合、{{site.data.keyword.cloud_notm}} インフラストラクチャーへのライセンス注文は行われません。
3. このサービス用に注文した NFS ストレージが、インスタンスのデフォルト・クラスター内のすべての ESXi サーバーにマウントされます。その際、ストレージのプライベート・サブネットへの正しい静的ルートが各 ESXi サーバーで追加されます。
4. ESXi サーバーにマウントされたすべての NFS ストレージ・ボリューム用の NFS データ・ストアが vCenter Server で作成されます。
5. インスタンスのデフォルト・クラスターに IBM Spectrum Protect Plus VM がデプロイされ、アクティブ化されて、構成されます。
6. このサービス用に注文した NFS ストレージが IBM Spectrum Protect Plus VM に接続され、バックアップ・リポジトリーが構成されます。
7. IBM Spectrum Protect Plus VM のホスト名と IP アドレスが、インスタンスの DNS サーバーに登録されます。

## 関連リンク
{: #spp_ordering-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Preventive Service Planning](https://www-01.ibm.com/support/docview.wss?uid=swg22012650){:external}
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp) の管理
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [IBM Spectrum Protect Plus の資料](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html){:external}
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
