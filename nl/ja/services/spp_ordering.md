---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-13"

---

# IBM Spectrum Protect Plus on IBM Cloud の注文

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスを注文するには、そのサービスを組み込む形で新しいインスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

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
* IBM Spectrum Protect Plus のライセンスを注文する場合は、**「ライセンスの注文」**タブで**「ライセンスに対する VM の数」**を指定します。 ライセンス管理には 10 個以上の VM が必要です。
* ライセンス持ち込み (BYOL) を行う場合は、**「IBM Spectrum Protect Plus licenses」**タブをクリックし、次に**「ライセンス・ファイルの追加」**をクリックして、お持ちの IBM Spectrum Protect Plus ライセンス・ファイルをアップロードします。

## IBM Spectrum Protect Plus on IBM Cloud のデプロイメント・プロセス

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} のデプロイメントは自動化されています。 このサービスを組み込む形でインスタンスを注文する場合でも、このサービスを後でインスタンスにデプロイする場合でも、{{site.data.keyword.vmwaresolutions_short}} の自動化プロセスによって以下の手順が実行されます。

1. IBM Spectrum Protect Plus バックアップ・リポジトリーのために、ユーザー入力に基づいて {{site.data.keyword.cloud_notm}} インフラストラクチャーからエンデュランス NFS ストレージを注文します。
2. ユーザー入力に基づいて {{site.data.keyword.cloud_notm}} インフラストラクチャーから、IBM Spectrum Protect Plus のライセンスを特定の数だけ注文します。 ライセンスは、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスの注文時にユーザーが指定した、ライセンスを受ける VM の数に基づいて、VM ライセンス・パック 10 個単位で注文されます。 既存の IBM Spectrum Protect Plus ライセンスの持ち込みをユーザーが選択した場合は、{{site.data.keyword.cloud_notm}} インフラストラクチャーからのライセンスの注文は行われません。
3. このサービスのために注文したすべての NFS ストレージを、インスタンスのデフォルト・クラスターにあるすべての ESXi サーバーにマウントします。これには、各 ESXi サーバーでストレージのプライベート・サブネットへの正しい静的ルートを追加することも含まれます。
4. ESXi サーバーにマウントされたすべての NFS ストレージ・ボリューム用に、vCenter Server で NFS データ・ストアを作成します。
5. インスタンスのデフォルト・クラスターで IBM Spectrum Protect Plus 仮想マシンをデプロイし、アクティブ化し、構成します。
6. このサービスのために注文したすべての NFS ストレージを IBM Spectrum Protect Plus 仮想マシンに接続し、バックアップ・リポジトリーを構成します。
7. IBM Spectrum Protect Plus 仮想マシンのホスト名と IP アドレスを、インスタンスの DNS サーバーに登録します。
8. (V2.3 以降のインスタンスの場合) IBM Spectrum Protect Plus でデフォルトの管理バックアップ・ジョブを作成します。 詳しくは、[IBM Spectrum Protect Plus on IBM Cloud の管理](managingspp.html)を参照してください。

## 関連リンク

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} の概要](spp_considerations.html)
* [IBM Spectrum Protect Plus on IBM Cloud Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html) の管理
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Spectrum Protect Plus の資料](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
