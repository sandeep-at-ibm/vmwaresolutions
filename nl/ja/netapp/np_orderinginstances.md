---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: NetApp order instance, order NetApp ONTAP, order NetApp

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select インスタンスの注文
{: #np_orderinginstances}

ソフトウェアで定義できる可用性の高い専用ストレージ・アプライアンスを備えた VMware 仮想化プラットフォームをデプロイするには、NetApp ONTAP Select インスタンスを注文してください。

## 要件
{: #np_orderinginstances-req}

以下の作業を完了していることを確認してください。
*  **「設定」**ページで {{site.data.keyword.cloud}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定の管理](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)を参照してください。
*  [NetApp ONTAP Select インスタンスの要件と計画](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning)に記載されている要件と考慮事項を確認した。

インスタンスの注文時およびデプロイ時に設定した値は変更しないでください。 変更すると、インスタンスを使用できなくなります。 例えば、パブリック・ネットワークがシャットダウンしたり、プロビジョニング中にサーバーや仮想サーバー・インスタンス (VSI) が Vyatta の内側に移動したり、IBM CloudBuilder VSI が停止したり、削除されたりすることがあります。
{:important}

## システム設定
{: #np_orderinginstances-sys-settings}

NetApp ONTAP Select インスタンスを注文する際には、以下の基本設定を指定する必要があります。

### Instance name
{: #np_orderinginstances-instance-name}

インスタンス名は、次の要件を満たす必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* インスタンス名の先頭は英字、末尾は英数字でなければなりません。
* インスタンス名の最大の長さは 10 文字です。
* インスタンス名はアカウント内で固有である必要があります。

## ネットワーク・インターフェースの設定
{: #np_orderinginstances-network-interface-settings}

NetApp ONTAP Select インスタンスを注文する際には、以下のネットワーク・インターフェース設定を指定する必要があります。

### Host name prefix
{: #np_orderinginstances-host-name-prefix}

ホスト名接頭部は、次の要件を満たす必要があります。
*  英数字とダッシュ (-) の文字だけを使用できます。
*  ホスト名接頭部の先頭と末尾は英数字である必要があります。
*  ホスト名接頭部の最大長は 10 文字です。

### Subdomain label
{: #np_orderinginstances-subdomain-label}

サブドメイン・ラベルは、次の要件を満たす必要があります。
*  英数字とダッシュ (-) の文字だけを使用できます。
*  サブドメイン・ラベルの先頭は英字、末尾は英数字でなければなりません。
*  サブドメイン・ラベルの最大長は 10 文字です。

### Domain name
{: #np_orderinginstances-domain-name}

ルート・ドメイン・ネームは、次の要件を満たす必要があります。
* ドメイン・ネームは、ピリオド (.) で区切られた 2 つ以上のストリングで構成されていなければなりません。
* 最初の文字列は、英字で始まり英数字で終わらなければなりません。
* 最後のストリングを除き、ストリングで使用できるのは、英数字とダッシュ (-) のみです。
* 最後のストリングには、英字しか使用できません。
* 最後の文字列の長さは、2 文字から 24 文字までの範囲でなければなりません。

ホストと VM (仮想マシン) の FQDN (完全修飾ドメイン・ネーム) の最大長は 50 文字です。 この最大長に対応するドメイン・ネームにする必要があります。
{:note}

## ライセンス交付の設定
{: #np_orderinginstances-licensing-settings}

4 つの{{site.data.keyword.baremetal_short}}にそれぞれ 1 つのライセンスが必要であるため、4 つの NetApp ライセンス交付ファイルをアップロードする必要があります。 高性能または大容量のデプロイメントの場合は、NetApp 営業チームに問い合わせて、該当するライセンス交付を得てください。

## ベア・メタル・サーバーの設定
{: #np_orderinginstances-bare-metal-settings}

### データ・センターの場所
{: #np_orderinginstances-dc-location}

インスタンスがホストされる {{site.data.keyword.CloudDataCent_notm}}を選択する必要があります。

### Bare Metal Server configuration
{: #np_orderinginstances-bare-metal-config}

要件に応じてベア・メタル・サーバー構成を選択します。
* **ハイパフォーマンス (ミディアム)** – プレミアム・ライセンス / Dual Intel Xeon E5-2650 v4 (合計 24 コア、2.2 GHz) / 128 GB RAM / ノードあたり 22 個の 1.9 TB SSD ドライブ容量 / 4 ノード・クラスターの実効容量 – 59 TB
* **ハイパフォーマンス (ラージ)** – プレミアム・ライセンス / Dual Intel Xeon E5-2650 v4 (合計 24 コア、2.2 GHz) / 128 GB RAM / ノードあたり 22 個の 3.8 TB SSD ドライブ容量 / 4 ノード・クラスターの実効容量 – 118 TB
* **大容量** – 標準ライセンス / Dual Intel Xeon E5-2650 v4 (合計 24 コア、2.2 GHz) / 64 GB RAM / ノード当たり 34 個の 4 TB SATA ドライブ容量 / 4 ノード・クラスターの有効容量 – 190 TB

3.8 TB SSD (ソリッド・ステート・ディスク) ドライブは、{{site.data.keyword.CloudDataCent_notm}}内で一般出荷可能になったときにサポートされます。
{:note}

### ベア・メタル・サーバーの数
{: #np_orderinginstances-bare-metal-number}

NetApp ONTAP Select インスタンスの ESXi サーバーの数は、デフォルトで 4 台です。 これは変更できません。 すべての ESXi サーバーが構成を共有します。

## 注文のサマリー
{: #np_orderinginstances-order-summary}

選択した構成に基づいて、見積もりコストがすぐに生成され、右側のペインの**「注文の要約」**に表示されます。  **「料金詳細」**をクリックすると、{{site.data.keyword.vmwaresolutions_short}} リソースのコスト・サマリーが記載された PDF 文書を生成できます。

また、**「見積もりに追加」**をクリックして、プロビジョン済みリソースを {{site.data.keyword.cloud_notm}} 見積もりツールに追加することもできます。 この操作は、購入を検討している他の {{site.data.keyword.cloud_notm}} リソースと一緒に、選択した {{site.data.keyword.vmwaresolutions_short}}リソースのコストを見積もる場合に役立ちます。

## NetApp ONTAP Select インスタンスを注文する手順
{: #ordering-netapp-ontap-select-instances}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware 仮想データ・センター」**セクションの**「NetApp ONTAP Select」**カードをクリックします。
2. **「NetApp ONTAP Select」**ページで、**「作成」**をクリックします。
3. **「NetApp ONTAP」**ページで、インスタンス名を入力します。
4. **「ホスト名接頭部」**、**「サブドメイン・ラベル」**、および**「ドメイン・ネーム」**を入力して、ネットワーク・インターフェースの設定を完了します。
5. **「ライセンス・ファイルの追加」**をクリックし、4 台の{{site.data.keyword.baremetal_short}}に必要な 4 つの NetApp ライセンス・ファイルをアップロードして、ライセンス設定を実行します。
6. ベア・メタル・サーバーの設定を次の手順で実行します。
   1. インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}}を選択します。
   2. ベア・メタル・サーバー構成を選択します。
7. **「発注要約」**ペインで、インスタンス構成を確認してから注文を実行します。
    1. インスタンスの設定を確認します。
    2. インスタンスの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの**「印刷」**アイコンまたは**「ダウンロード」**アイコンをクリックします。
    3. 課金されるアカウントが正しいことを確認した後、**「下にリストされているアカウントが課金されることを確認しました」**チェック・ボックスを選択します。
    4. 注文に適用される使用条件のリンクをクリックします。 それらの使用条件に同意してから、**「以下に表示されるサード・パーティー・サービス契約を読み、同意します」**チェック・ボックスを選択します。
    5. **「プロビジョン」**をクリックします。

## NetApp ONTAP インスタンスを注文した結果
{: #np_orderinginstances-results}

* インスタンスのデプロイメントが自動的に開始され、注文が処理中であることを示す確認を受け取ります。 「インスタンスの詳細」の**「デプロイメント履歴 (Deployment History)」**セクションを表示すると、注意すべき問題を含め、デプロイメント状況を確認できます。
* インスタンスが正常にデプロイされると、[NetApp ONTAP Select インスタンスの技術仕様](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#specs)に記述されているコンポーネントが VMware 仮想プラットフォームにインストールされます。
* インスタンスが使用可能になると、インスタンスの状況が**「使用可能」**に変わり、E メールで通知されます。

## 次に行うこと
{: #np_orderinginstances-next}

注文した NetApp ONTAP Select インスタンスを表示して管理します。

{{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。 {{site.data.keyword.vmwaresolutions_short}} コンソール以外で変更した場合、変更がコンソールと同期されません。
{:important}

**注意:** インスタンスを注文したときに {{site.data.keyword.cloud_notm}} アカウントにインストールされた {{site.data.keyword.vmwaresolutions_short}} コンポーネントを、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で管理すると、環境が不安定になる可能性があります。 これには以下の管理アクティビティーが該当します。
*  コンポーネントの追加、変更、返却、または削除
*  コンポーネントのパワーオフ

   {{site.data.keyword.slportal}}での共有ストレージのファイル共有の管理は、上記アクティビティーに該当しません。 これには、共有ストレージのファイル共有の注文、削除 (マウントされている場合はデータ・ストアに影響する可能性があります)、承認、マウントなどのアクティビティーが含まれます。

## 関連リンク
{: #np_orderinginstances-related}

* [NetApp ONTAP Select インスタンスの表示](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)
* [NetApp ONTAP Select インスタンスの削除](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_deletinginstance)
* [NetApp ONTAP ドキュメント・センター](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html){: external}
* [Attach dedicated storage to NetApp ONTAP Select deployments](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/){: external}
