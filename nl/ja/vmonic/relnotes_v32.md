---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: release notes, what's new, version 3.2

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V3.2 のリリース・ノート
{: #relnotes_v32}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:external}を参照してください。

## VMware HCX for IBM Cloud の可用性
{: #relnotes_v32-HCX}

3.2 リリース以降、VMware vCenter Server インスタンスとともに VMware HCX on {{site.data.keyword.cloud_notm}} サービスを注文するオプションを利用できるようになっています。以前は、vCenter Server with Hybridity Bundle インスタンスで HCX on {{site.data.keyword.cloud_notm}} サービスを注文することしかできませんでした。vCenter Server with Hybridity Bundle インスタンスは使用できなくなりました。

HCX on {{site.data.keyword.cloud_notm}} サービスを注文する際は、12 カ月間のコミットメントが必要です。12 カ月のコミットメント期間が満了した後は、HCX on {{site.data.keyword.cloud_notm}} サービスのインストールとアンインストール、およびホストやクラスターの追加と削除を制限なしで行うことができます。アカウントには 1 カ月単位で料金が請求されます。また、アカウントは随時、キャンセルできます。

詳しくは、 [VMware HCX on IBM Cloud の概要](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations)を参照してください。

## VMware vSphere 6.7 Update 2 のサポート
{: #relnotes_v32-vsphere-v67}

VMware vCenter Server、VMware vCenter Server with NSX-T、VMware vSphere on IBM Cloud の各インスタンスとともに VMware vSphere バージョン 6.7 Update 2 を注文するオプションを利用できるようになりました。vSphere Enterprise Plus 6.7u2 は、新規インスタンスで vSphere Enterprise Plus 6.7u1 を注文するオプションに置き換わるものです。さらに、vSphere Enterprise Plus 6.7u2 で、Single-node Trial for Migration and App Modernization インスタンスと Single-node Trial for Data Protection and Disaster Recovery インスタンスを注文できるようになりました。

vSphere Enterprise Plus 6.7u2 は、Skylake、Cascade Lake、および Broadwell {{site.data.keyword.cloud_notm}} の{{site.data.keyword.baremetal_short}}で使用できます。

既存のインスタンスで vSphere Enterprise Plus 6.7u1 を使用している場合、vSphere Enterprise Plus 6.7u1 または vSphere Enterprise Plus 6.7u2 のいずれかを使用して新規ホストを追加することができます。ただし、新規 6.7u1 ホストを追加すると非セキュアです。できるだけ早くホストを最新の ESXi サーバー・バージョンに更新することをお勧めします。
{:note}

## Cascade Lake のサポート
{: #relnotes_v32-cascade}

V3.2 リリース以降、VMware vSphere 6.7 Update 2 を使用したインスタンスおよびクラスターのデプロイメントで、以下の新しい {{site.data.keyword.baremetal_short_sing}} CPU モデルを使用できるようになりました。これは、vCenter Server、vCenter Server with NSX-T、および VMware vSphere に適用されます。


* Dual Intel Xeon Gold 4210 Processor / 合計 20 コア、2.3 GHz
* Dual Intel Xeon Gold 5218 Processor / 合計 32 コア、2.3 GHz
* Dual Intel Xeon Gold 6248 Processor / 合計 40 コア、2.5 GHz

Cascade Lake {{site.data.keyword.baremetal_short}} は、マルチゾーン領域
{{site.data.keyword.CloudDataCents_notm}} で使用可能です。詳しくは、[マルチゾーン領域 (MZR) の概要
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview) を参照してください。


{{site.data.keyword.baremetal_short_sing}}の設定について詳しくは、以下を参照してください。

* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-cascade)
* [vCenter Server with NSX-T インスタンスの注文](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-cascade)
* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstance-cascade)

## VMware vCenter Server インスタンスの更新
{: #relnotes_v32-vcs}

このリリースでは、新しくデプロイされるインスタンス、クラスター、ホストに対して、以下のアップグレードと機能改善が適用されます。

* VMware NSX for vSphere 6.4.5 (ビルド 13282012)
* vSphere ESXi 6.7 EP 10 (ビルド 6.7.0-13981272)
* vCenter Server Appliance 6.7 Update 2b (6.7.0.-13843469)
* Platform Services Controller 6.7 Update 2b (6.7.0.-13843469)

詳しくは、[vCenter Server の部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)を参照してください。

### 初期クラスターの命名
{: #relnotes_v32-vcs-initial-cluster}

インスタンスを注文すると同時に作成される初期クラスターの名前を指定できるようになりました。詳しくは、以下を参照してください。

* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server with NSX-T インスタンスの注文](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## VMware vSphere インスタンスの更新
{: #relnotes_v32-vss}

プライベート・ネットワークのみを使用する新しい vSphere クラスターを注文する場合、パブリック VLAN は不要になりました。

詳しくは、[新規 vSphere クラスターの注文](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-network-interface-settings) の『*ネットワーク・インターフェースの設定*』セクションを参照してください。 

## アドオン・サービスの更新
{: #relnotes_v32-services}

このリリースでは、新しくデプロイされるインスタンスに以下のサービス・バージョンがインストールされます。

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Update 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Update 4

### VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

V3.2 以降のリリースでデプロイ (またはそのリリースにアップグレード) された VMware vCenter Server インスタンスで、vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} サービスを使用できるようになりました。

このサービスにより、VMware vRealize Log Insight (vRLI) と vRealize Operations Manager (vROps) が統合されるため、仮想化環境の健全性とパフォーマンスをモニタリングしてプロアクティブに管理できます。さらに、ログをフィルタリングおよび検索して、問題の根本原因を分析することもできます。

vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} を組み込んだ形で vCenter Server インスタンスを注文できます。または、インスタンスの詳細ページの「サービス」タブを使用して、既存のインスタンスに後からこのサービスを追加することもできます。

vRealize Operations および vRealize Log Insight の Enterprise ライセンスをクラウドに持ち込むことも (CPU または OSI ごと)、IBM Cloud のレンタル・ライセンスを利用することもできます。

詳しくは、[VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vrops_overview)を参照してください。

## 新規資料および更新された資料
{: #relnotes_v32-updated-doc}

* Activity Tracker の資料が更新されました。詳しくは、[Activity Tracker イベント](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events)を参照してください。

## ユーザー・インターフェースの更新と向上
{: #relnotes_v32-ui}

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。

* インスタンス名の要件が変更されました。詳しくは、注文するインスタンス・タイプに応じたトピックを参照してください。
* 完全修飾 ESXi サーバー名の形式が変更されました。詳しくは、注文するインスタンス・タイプに応じたトピックを参照してください。
* 適切にソートできるように、ホスト名とクラスター名に先行ゼロが追加されました。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
