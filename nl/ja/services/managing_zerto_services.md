---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-04"

---

# Zerto on IBM Cloud 用マネージド・サービスの要求

Zerto on {{site.data.keyword.cloud}} サービスは、複製と災害復旧の機能を提供します。これらの機能をデプロイメント・オファリングに組み込むことで、{{site.data.keyword.cloud_notm}} 上の VMware 仮想環境内のデータの保護と復旧を行えます。

Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービスを要求すると、Zerto DR ソフトウェアと IBM Resiliency Services の両方を使用して、完全に管理された災害復旧 (DR) 環境をデプロイできます。

Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービスでは、以下のモデルを使用できます。

## IBM Orchestrated Managed Services for Zerto

このモデルは、Zerto on {{site.data.keyword.cloud_notm}} オファリングを使用する場合に適しています。

このモデルでは、{{site.data.keyword.cloud_notm}} Resiliency Orchestration サービスが Zerto on {{site.data.keyword.cloud_notm}} 用にプロビジョンされます。 このモデルでは、{{site.data.keyword.cloud_notm}} 上の仮想マシン、オペレーティング・システム、データの継続的保護が可能です。DR テストが中断なしで行われ、RTO/RPO (目標復旧時間/目標復旧時点) が可視化され、フェイルオーバーとファイルバックの機能を備えています。

すべての機能は、{{site.data.keyword.cloud_notm}} Resiliency Orchestration ダッシュボードを介して IBM Resiliency Services Global Command Center によって管理されます。

詳しくは、[IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration) を参照してください。

## IBM Managed Services for Zerto (Orchestration なし)

このモデルでは、完全に管理される DR ソリューションが Zerto on {{site.data.keyword.cloud_notm}} 用にプロビジョンされます。 必要なのは Zerto Virtual Replication 用マネージド・サービスのみで、{{site.data.keyword.cloud_notm}} 上の{{site.data.keyword.cloud_notm}} Resiliency Orchestration サービスは使用しない場合に、このモデルは適しています。

詳しくは、[IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top) を参照してください。

## 手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「開始」**をクリックします。
2. ページをスクロールダウンし、**「追加マネージド・サービスの注文」**で、**「Zerto on IBM Cloud のマネージド・サービス」**カードをクリックします。
3. **「Zerto on IBM Cloud のマネージド・サービス」**ページで、マネージド・サービスとしての Zerto on {{site.data.keyword.cloud_notm}} の説明と技術仕様を確認してから、**「作成」**をクリックします。
4. 要件に応じて構成設定値を指定するか、またはデフォルト値を受け入れます。
5. **「vCenter サーバー」**または**「Cloud Foundation」**をクリックして、このサービスをいずれかのインスタンスに追加します。
6. このサービスを新規インスタンスの注文中に追加するには、**「新規インスタンスに追加」**をクリックしてから、新規 [vCenter Server](../vcenter/vc_orderinginstance.html) インスタンス、[vCenter Server with Hybridity](../vcenter/vc_hybrid_orderinginstance.html) インスタンス、または [Cloud Foundation](../sddc/sd_orderinginstance.html) インスタンスの注文を続けます。
7. このサービスを既存のインスタンスに追加するには、**「デプロイ済みインスタンスに追加」**をクリックし、対象インスタンスをリストで選択してから、**「プロビジョン」**をクリックして注文に進むことを確認します。

## 関連リンク

* [vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
