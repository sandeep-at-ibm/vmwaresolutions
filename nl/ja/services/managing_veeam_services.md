---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

subcollection: vmwaresolutions


---

# Veeam on IBM Cloud 用マネージド・サービスの要求
{: #managing_veeam_services}

Veeam on {{site.data.keyword.cloud}} サービスは、ご使用の VMware ハイパーバイザーとシームレスに統合され、企業が高可用性 (HA) を実現できるよう支援します。 このサービスを使用すると、アプリケーションとデータのリカバリー・ポイントと目標復旧時間を設定できます。 リカバリー・ポイントと目標復旧時間は、構成が完了してから 15 分以内に利用可能になります。 このサービスを使用して、ご使用のインフラストラクチャーに配置されたすべての仮想マシンのバックアップとリストアの両方を Veeam コンソールから直接制御します。

IBM Resiliency Backup as a Service は、オンサイト・クラウド、オフサイト・クラウド、ハイブリッド・クラウドを対象とした広範囲のデータ保護ソリューションを提供することによって、情報の回復力を高めます。 詳しくは、[IBM Resiliency Backup as a Service](https://www.ibm.com/us-en/marketplace/managed-backup-services) を参照してください。

Veeam on {{site.data.keyword.cloud_notm}} 用マネージド・サービスを要求するときに、Veeam バックアップ・ソフトウェアと IBM Resiliency Backup as a Service の両方を使用して、完全に管理されたバックアップ環境をデプロイします。 このように組み合わせて使用すると、以下の点で役立ちます。
* セキュリティー機能が充実した、重要なビジネス・データを自動的に保護する機能を有効にするためのソリューションを、いくつかの選択肢の中から選択できます。専用オンプレミス環境、{{site.data.keyword.cloud_notm}} インフラストラクチャー、IBM Resiliency Services Center の 1 次ロケーションと 2 次ロケーションすべてがデータ保護の対象になります。
* また、スケーラブルで柔軟なデータ保護ソリューションを使用できるので、総所有コスト (TCO) が削減され、コンプライアンス要件を管理できるようになります。

## Veeam on IBM Cloud 用マネージド・サービスを要求する手順
{: #managing_veeam_services-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「開始」**をクリックします。
2. ページをスクロールダウンし、**「追加マネージド・サービスの注文 (Order additional managed services)」**で、**「Veeam on IBM Cloud のマネージド・サービス (Managed Services for Veeam on IBM Cloud)」**カードをクリックします。
3. **「Veeam on IBM Cloud」**ページで、マネージド・サービスとしての Veeam on {{site.data.keyword.cloud_notm}} の説明と技術仕様を確認してから、**「作成」**をクリックします。
4. 要件に応じて構成設定値を指定するか、またはデフォルト値を受け入れます。
5. **「vCenter サーバー」**または**「Cloud Foundation」**をクリックして、このサービスをいずれかのインスタンスに追加します。
6. このサービスを新規インスタンスの注文中に追加するには、**「新規インスタンスに追加」**をクリックしてから、新規 [vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance) インスタンスまたは [vCenter Server with Hybridity](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance) インスタンスの注文を続けます。
7. このサービスを既存のインスタンスに追加するには、**「既存にインスタンスに追加 (Add to Existing Instance)」**をクリックし、リストから対象インスタンスを選択してから、**「プロビジョン」**をクリックして注文に進むことに同意します。

## 関連リンク
{: #managing_veeam_services-related}

* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Data Backup and Protection Services](https://www-935.ibm.com/services/business-continuity/backup-and-data-protection-services/)
