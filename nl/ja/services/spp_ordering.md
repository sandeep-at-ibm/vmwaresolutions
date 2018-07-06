---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-15"

---

# IBM Spectrum Protect Plus on IBM Cloud の注文

IBM Spectrum Protect Plus on {{site.data.keyword.cloud}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの IBM Spectrum Protect Plus on IBM Cloud の注文

以下のいずれかの方法を使用して、新しいインスタンスで IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} を注文できます。
* {{site.data.keyword.vmwaresolutions_full}} コンソールから新しいインスタンスを注文する時に、**「サービス」**セクションで**「IBM Spectrum Protect Plus on IBM Cloud」**を選択します。
* {{site.data.keyword.cloud_notm}} カタログから**「IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service」**を選択し、サービス設定を指定し、**「Add to New Instance」**を選択します。

## 既存のインスタンスでの IBM Spectrum Protect Plus on IBM Cloud の注文

以下のいずれかの方法を使用して、既存のインスタンスに IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスを追加できます。
* {{site.data.keyword.vmwaresolutions_short}} コンソールから、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「サービスの追加」**をクリックします。
* {{site.data.keyword.cloud_notm}} カタログから**「IBM Spectrum Protect Plus on IBM Cloud service」**を選択し、サービス設定を指定し、**「Add to Existing Instance」**を選択します。

## IBM Spectrum Protect Plus on IBM Cloud サービスの構成

このサービスを注文する際には、以下の設定を行います。

### ストレージ・ボリュームの数

ストレージのニーズを満たすボリュームの数。

### ボリュームあたりのストレージ・サイズ

ボリュームあたりのストレージ容量。 管理にはボリュームあたり 500 GB 以上が必要です。

### ストレージ・パフォーマンス

ワークロードの要件に基づいた 1 GB あたりの IOPS (入出力操作/秒)。
* IBM Spectrum Protect Plus のライセンスを注文する場合は、**「ライセンスの注文」**タブで**「ライセンスに対する VM の数」**を指定します。 ライセンス管理には 10 個以上の仮想マシン (VM) が必要です。
* ライセンス持ち込み (BYOL) を行う場合は、**「IBM Spectrum Protect Plus licenses」**タブをクリックし、次に**「ライセンス・ファイルの追加」**をクリックして、お持ちの IBM Spectrum Protect Plus ライセンス・ファイルをアップロードします。

## IBM Spectrum Protect Plus on IBM Cloud のデプロイメント・プロセス

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} のデプロイメントは自動化されています。 このサービスを組み込む形でインスタンスを注文する場合でも、このサービスを後でインスタンスにデプロイする場合でも、{{site.data.keyword.vmwaresolutions_short}} の自動化プロセスによって以下の手順が実行されます。

1. 指定した設定に基づいて、IBM Spectrum Protect Plus バックアップ・リポジトリー用のエンデュランス NFS ストレージが {{site.data.keyword.cloud_notm}} インフラストラクチャーに注文されます。
2. 指定した設定に基づいて、IBM Spectrum Protect Plus のためのいくつかのライセンスが {{site.data.keyword.cloud_notm}} インフラストラクチャーに注文されます。ライセンスは、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスの注文時に指定した、ライセンスを受ける VM の数に基づいて、VM ライセンス・パックが 10 個単位で注文されます。既存の IBM Spectrum Protect Plus ライセンスを持ち込む場合、{{site.data.keyword.cloud_notm}} インフラストラクチャーへのライセンス注文は行われません。
3. このサービス用に注文した NFS ストレージが、インスタンスのデフォルト・クラスター内のすべての ESXi サーバーにマウントされます。その際、ストレージのプライベート・サブネットへの正しい静的ルートが各 ESXi サーバーで追加されます。
4. ESXi サーバーにマウントされたすべての NFS ストレージ・ボリューム用の NFS データ・ストアが vCenter Server で作成されます。
5. インスタンスのデフォルト・クラスターに IBM Spectrum Protect Plus VM がデプロイされ、アクティブ化されて、構成されます。
6. このサービス用に注文した NFS ストレージが IBM Spectrum Protect Plus VM に接続され、バックアップ・リポジトリーが構成されます。
7. IBM Spectrum Protect Plus VM のホスト名と IP アドレスが、インスタンスの DNS サーバーに登録されます。
8. (V2.3 以降のインスタンスの場合) IBM Spectrum Protect Plus にデフォルトの管理バックアップ・ジョブが作成されます。詳しくは、[IBM Spectrum Protect Plus on IBM Cloud の管理](managingspp.html)を参照してください。

## 関連リンク

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} の概要](spp_considerations.html)
* [IBM Spectrum Protect Plus on IBM Cloud Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html) の管理
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Spectrum Protect Plus の資料](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
