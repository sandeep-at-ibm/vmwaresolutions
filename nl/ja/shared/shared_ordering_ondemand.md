---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Shared On-demand の注文
{: #shared_ordering_ondemand}

{{site.data.keyword.vmwaresolutions_full}} Shared は試験的オファリングとして提供されます。
{:note}

オンデマンドの場合、仮想データ・センターの vCPU および RAM は必要に応じて割り振られ、割り振りに必要な時間は、仮想データ・センターの vCPU および RAM のグローバルな使用量に応じて異なります。
* vCPU および RAM のサイズに関して設定される制限は、いずれかの時点で取り込むことのできる最大値です。
* vCPU および RAM リソースは、必要に応じて後に拡大または縮小することができます。
* コストは時間ごとに計算され、それは仮想データ・センターのリソース使用量に基づいています。
* 仮想データ・センターに割り振り、使用できるストレージのサイズには制限がありません。料金は割り振られたストレージの GB に基づいて、時間ごとに請求されます。
* インバウンドおよびアウトバウンドのパブリック・ネットワーキングのサイズに制限はありません。パブリック帯域幅は、GB 単位で課金されます。

## IBM Cloud for VMware Solutions Shared の要件
{: #shared_ordering_ondemand-req}

### IBM Cloud インフラストラクチャー・アカウント
{: #shared_ordering_ondemand-account-req}

{{site.data.keyword.vmwaresolutions_short}} を使用して IBM Cloud for VMware Solutions Shared を注文するには、**「従量制課金 (PAYG)」**または**「サブスクリプション」**の {{site.data.keyword.cloud_notm}} アカウントが必要です。注文したリソースの料金は、その {{site.data.keyword.cloud_notm}} アカウントに請求されます。

### 仮想データ・センターの名前の要件
{: #shared_ordering_ondemand-vdc-name-req}

仮想データ・センターの名前は、以下の要件を満たす*必要があります*。将来は命名要件が強制適用されます。
* 英字の小文字、数字、およびダッシュ (-) の文字だけを使用できます。
* 名前の先頭は英小文字でなければなりません。
* 名前の末尾は英小文字または数字でなければなりません。
* 仮想データ・センター名の最大の長さは 10 文字です。
* 仮想データ・センター名は、アカウント内で固有でなければなりません。

## Shared On-demand を注文する手順
{: #shared_ordering_ondemand-procedure}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware 仮想データ・センター」**セクションの**「IBM Cloud for VMware Solutions Shared」**カードをクリックします。
2. **「IBM Cloud for VMware Solutions Shared」**ページで、**「オンデマンド」**カードをクリックして、**「作成」**をクリックします。
3. **「IBM Cloud for VMware Solutions Shared - On-demand」**ページで、仮想データ・センターの名前を入力します。オファリングを使用可能な {{site.data.keyword.CloudDataCent_notm}} が事前選択されています。
4. 要件に応じて、vCPU および RAM の制限を選択します。
5. **「発注要約」**ペインで、構成および費用の見積もりを確認してから注文を実行します。
6. **「プロビジョン」**をクリックします。

## Shared On-demand を注文した結果
{: #shared_ordering_ondemand-results}

* リソースのデプロイメントが自動的に開始され、注文が処理中であることを示す確認を受け取ります。 **「仮想データ・センターの状況 (Virtual Data Center Status)」**セクションを表示すると、注意すべき問題を含め、デプロイメント状況を確認できます。
* リソースが正常にデプロイされると、[{{site.data.keyword.cloud_notm}} for VMware Solutions Shared の技術仕様](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs)に記述されているコンポーネントが VMware 仮想プラットフォームにインストールされます。
* リソースを使用する準備ができると、状況は**「使用可能」**に変わります。

## 関連リンク
{: #shared_ordering_ondemand-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Shared Reserved の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
