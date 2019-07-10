---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: release notes, what's new, version 3.1

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V3.1 のリリース・ノート
{: #relnotes_v31}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Single-node Trial for Data Protection and Disaster Recovery インスタンス
{: #relnotes_v31-dr-bundle}

Single-node Trial for Data Protection and Disaster Recovery は、VMware ワークロードをマイグレーションしてから {{site.data.keyword.cloud_notm}} にリカバリーする、という {{site.data.keyword.cloud_notm}} のテスト・ドライブを簡単に行うための手段です。このトライアル版は、オンプレミス環境と同じ使い慣れたツールで管理できる単一テナントの VMware プラットフォームである VMware vCenter Server on IBM Cloud の 1 つのバージョンです。このトライアル版には、Veeam on {{site.data.keyword.cloud_notm}}、VMware HCX on {{site.data.keyword.cloud_notm}}、および Zerto on {{site.data.keyword.cloud_notm}} のサービスが含まれます。

詳しくは、[Single-node Trial for Disaster Recovery の概要](/docs/services/vmwaresolutions?topic=vmware-solutions-dr_backup_bundle_overview)を参照してください。

## IBM Cloud Expert Services
{: #relnotes_v31-expert-services}

IBM Expert Services がご利用いただけるようになりました。IBM Expert Services は、計画から最新化までのすべてのステージにおいて、お客様の社内チームと協力して、お客様の {{site.data.keyword.cloud_notm}} ソリューションのデプロイ、マイグレーション、および保守を行います。


**「開始」**ページからコンサルテーションを要求することにより、いつでも {{site.data.keyword.cloud_notm}} Expert Services をインスタンス注文に追加できます。詳しくは、[{{site.data.keyword.cloud_notm}} Expert Services の要求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_ices)を参照してください。

## IBM Cloud コスト見積もりツールとの統合

{{site.data.keyword.cloud_notm}} フレームワークに備わっている統一された見積もりツールを使用して、{{site.data.keyword.vmwaresolutions_short}} リソースのコストを見積もることができるようになりました。この機能を使用すると、{{site.data.keyword.cloud_notm}} カタログにあるリソースのスナップショットを取って、それを単一の PDF ファイルに格納し、それを後ほどダウンロードして参照することができます。コスト見積もりツールの結果は、契約でも正式な見積書でもなく、合計コストの推定額に過ぎません。

コスト見積もりツールの詳細については、[コストの見積もり](/docs/billing-usage?topic=billing-usage-cost)を参照してください。

## VMware vCenter Server インスタンスの更新
{: #relnotes_v31-vcs}

このリリースでは、新しくデプロイされるインスタンス、クラスター、ホストに関して、以下のアップグレードと機能改善が適用されます。

* vSphere ESXi 6.5 Update 2 (ビルド 6.5.0-13635690)
* vCenter Server Appliance 6.5 Update 2g (ビルド 6.5.0-13638625)

詳しくは、[vCenter Server の部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)を参照してください。

### クラスターの代替 ESXi サーバー構成
{: #relnotes_v31-esxi-config}

既存のクラスターに新しい ESXi サーバーを追加できるようになりました。その場合には、既存の構成か、クラスター内の既存のホストとは別の代替の構成を選択します。**「サーバーの追加」**ウィンドウから新しいサーバーを注文する際は、簡単にクラスター内の既存の構成を選択するか、新しい {{site.data.keyword.baremetal_short_sing}} 構成を選択できます。これは、すべての vCenter Server、vCenter Server with Hybridity、および vCenter Server with NSX-T の各インスタンスに適用されます。

パフォーマンスや安定性で問題が生じるのを避けるため、CPU、RAM、ストレージに関しては、すべてのクラスターで同じか類似した構成を使用することをお勧めします。この機能は、同じクラスター内でハードウェア更新を行うときに役立ちます。

詳しくは、[vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers)を参照してください。

### ポリシー構成の更新
{: #relnotes_v31-policy-config}

vCenter Server プライマリー・インスタンス用に生成される vCenter パスワードの長さが 15 文字になり、パスワードとロックアウトに関する以下のポリシー構成が追加されました。

* vCenter パスワードのポリシーとして、vCenter パスワードの最小長が 15 文字になりました。
* vCenter ロックアウト・ポリシーで許容される失敗ログイン試行最大回数が 3 回になりました。
* vCenter ロックアウト・ポリシーで許容される失敗間の間隔が 900 秒になりました。

vCenter Server プライマリー・インスタンス用に生成される NSX Manager パスワードの長さが 15 文字になりました。以前は、生成されるパスワードの長さは 8 文字でした。

 詳しくは、[vCenter Server インスタンスのコンプライアンス情報](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-default-policy-config)を参照してください。

## アドオン・サービスの更新
{: #relnotes_v31-services}

### HyTrust ライセンスの自動更新
{: #relnotes_v31-services-ht}

{{site.data.keyword.vmwaresolutions_short}} では、Call Home 機能が有効な HyTrust ライセンスの自動更新のサポートが提供されるようになりました。このサポートは、次のバージョン以降で提供されます。

* HyTrust CloudControl 5.5.1 以降
* HyTrust DataControl 4.3.2 以降
* HyTrust KeyControl 4.3.2 以降

ライセンスが自動更新されるようにするには、ご利用の HyTrust 仮想マシン (VM) のインターネット・アクセスを有効にする手順を完了する必要があります。この手順を実行しないかぎり、ライセンスはこれまでどおり 1 年ごとに有効期限切れとなります。
{:important}

詳しくは、以下を参照してください。

* [HyTrust CloudControl VM のインターネット・アクセスの有効化](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc#managinghtcc-internet-access)
* [HyTrust DataControl VM のインターネット・アクセスの有効化](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc#managinghtdc-internet-access)
* [HyTrust KeyControl VM のインターネット・アクセスの有効化](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc#managinghtkc-internet-access)

### IBM Cloud での Veeam
{: #relnotes_v31-services-veeam}

現行リリースでは、新しくデプロイされるすべてのインスタンスに Veeam Availability Suite 9.5 がインストールされます。 また、Veeam VSI と Veeam の構成リポジトリーに対していくつかの更新が加えられています。詳しくは、[Veeam on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)を参照してください。

### IBM Cloud での Zerto
{: #relnotes_v31-services-zerto}

V3.1 以降でデプロイされた新しいインスタンスでは、Zerto on {{site.data.keyword.cloud_notm}} のインストールのために {{site.data.keyword.cloud_notm}} 請求可能アカウントが必要になります。VM レプリケーションの料金に、{{site.data.keyword.cloud_notm}} インフラストラクチャー請求ではなく {{site.data.keyword.cloud_notm}} 請求可能プランが使用されるようになりました。

Zerto on {{site.data.keyword.cloud_notm}} を注文するには、{{site.data.keyword.cloud_notm}} アカウントが特定の要件を満たしている必要があります。既存の Zerto on {{site.data.keyword.cloud_notm}} インストールがある場合には、Zerto VM 請求タイプを請求可能に変換することができます。詳しくは、[Zerto レプリケーションの請求](/docs/services/vmwaresolutions?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing)を参照してください。

## 新規資料および更新された資料
{: #relnotes_v31-updated-doc}

* Activity Tracker インスタンス管理のイベントと KMIP for VMware on IBM Cloud サービスのイベントが更新されました。詳しくは、[Activity Tracker イベント](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events)を参照してください。
* ユーザー ID のリファレンス資料に、{{site.data.keyword.cloud_notm}} サービスの自動化機能によるサービスのインストールと構成で使用されるユーザー ID に関連した更新が加えられました。詳しくは、[IBM ユーザー ID](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) の*サービス・ユーザー ID* のセクションを参照してください。
* ``クラスター API のネットワーク・インターフェース詳細の取得`` に関する新しいリファレンス資料が用意されました。詳しくは、[API リファレンス](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}を参照してください。
* ユーザー資料の*リファレンス*のセクションに、新しく以下の技術資料が追加されました。
  * [運用管理](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)
  * [Day 2 運用手順](/docs/services/vmwaresolutions?topic=vmware-solutions-opsprocs-intro)

## ユーザー・インターフェースの更新と向上
{: #relnotes_v31-ui}

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。
* **「クラスター」**詳細ページに、クラスターが使用しているストレージのタイプが表示されるようになりました。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
