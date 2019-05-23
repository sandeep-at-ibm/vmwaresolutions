---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V3.0 のリリース・ノート
{: #relnotes_v30}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## VMware Cloud Foundation on IBM Cloud のサポートの終了
{: #relnotes_v30-vcf-eos}

オファリングを統合してカスタマー・エクスペリエンスを向上させるために、{{site.data.keyword.vmwaresolutions_short}} プラットフォームでは VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} の提供を 2019 年 5 月 13 日付けで終了します。

今後は、すべてのお客様が、{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}で提供される IBM の VMware Software-Defined Data Center の主力ソリューションである VMware vCenter Server on {{site.data.keyword.cloud_notm}} を使用することになります。

VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} をご利用の既存のお客様には、2019 年 5 月 13 日のサポート終了日までに VMware vCenter Server on {{site.data.keyword.cloud_notm}} に変換できるように支援を提供します。

5 月 13 日より後は、VMware vCenter Server on {{site.data.keyword.cloud_notm}} に変換されるまで、VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} の管理機能が {{site.data.keyword.vmwaresolutions_short}} コンソールから凍結されます。 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} インスタンスを VMware vCenter Server on {{site.data.keyword.cloud_notm}} に移行または変換しないお客様は、{{site.data.keyword.cloud_notm}} インフラストラクチャー・コンソールからインスタンスにアクセスできます。

## Broadwell 2-CPU サーバーのサポートの廃止
{: #relnotes_v30-broadwell}

V3.0 リリース以降、vCenter Server、vCenter Server with Hybridity Bundle、vCenter Server with NSX-T、および vSphere on {{site.data.keyword.cloud_notm}} の新規のインスタンスとクラスターのデプロイメントに、Broadwell 2-CPU サーバーは使用できなくなりました。 既存のクラスターには、これまでどおりサーバーを追加できます。

## ネットワーク・ファイル・システム操作の機能拡張
{: #relnotes_v30-nfs}

V3.0 リリース以降、**「使用可能」**状態にある複数のクラスターで、NFS ストレージと ESXi サーバーを同時に追加/削除できるようになりました。例えば、あるクラスターで ESXi サーバーを追加または削除したり、別のクラスターで NFS ストレージを追加または削除したりできます。これは、すべての vCenter Server と vCenter Server with NSX-T のインスタンスに適用されます。

## VMware vCenter Server インスタンスの更新
{: #relnotes_v30-vcs}

このリリースでは、以下のアップグレードと機能改善が適用されます。

* vSphere ESXi 6.7 Update 1 (ビルド 6.7.0-13004448)
* vSphere ESXi 6.5 Update 2 (ビルド 6.5.0-13004031)
* vCenter Server Appliance 6.7 Update 1b (ビルド 6.7.0-11727113)
* Platform Services Controller 6.7 Update 1b (build 6.7.0-11727113) 

詳しくは、[vCenter Server の部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)を参照してください。

Microsoft の Active Directory (AD) サービスと DNS (ドメイン・ネーム・システム) サービス用に注文される Windows ソフトウェアが、構成オプション (VSI (仮想サーバー・インスタンス) および 2 台構成の高可用性 Windows VM) のために Windows Server 2016 にアップグレードされました。 VMware コンポーネントの選択方法について詳しくは、[vCenter Server インスタンスのソフトウェアの BOM](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software) を参照してください。

### vSAN ストレージの機能拡張
{: #relnotes_v30-vcs-vsan}

* vSAN ストレージを使用する場合に、4 台を超えるベア・メタル・サーバーを注文できるようになりました。 これは、すべての vCenter Server、vCenter Server with Hybridity、および vCenter Server with NSX-T の各インスタンスに適用されます。
* V3.0 リリース以降、M.2 ソリッド・ステート・ドライブが vSAN ストレージ・インスタンスと一緒に注文されます。 **「High Performance with Intel Optaine」**オプションを選択すると、容量ディスクを最大 10 台または 12 台注文できます。

詳しくは、以下の資料にある『*ストレージ設定*』を参照してください。
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [vCenter Server with Hybridity Bundle インスタンスの注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [vCenter Server with NSX-T インスタンスの注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## アドオン・サービスの更新
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

現行リリースでは、新しくデプロイされるすべてのインスタンスに HyTrust CloudControl 5.5 がインストールされます。 HyTrust CloudControl 5.5 の新機能について詳しくは、[What's New in HyTrust CloudControl Version 5.5](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window} を参照してください。

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

現行リリースでは、新しくデプロイするすべてのインスタンスで、HyTrust DataControl 4.3 がインストールされます。 HyTrust DataControl 4.3 の新機能について詳しくは、[What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window} を参照してください。

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

現行リリースでは、新しくデプロイするすべてのインスタンスで、HyTrust KeyControl 4.3 がインストールされます。 HyTrust KeyControl 4.3 の新機能について詳しくは、[What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window} を参照してください。

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

現行リリースでは、新しくデプロイするすべてのインスタンスに、{{site.data.keyword.cloud_notm}} Private Hosted 3.1.2 と {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 が一緒にインストールされます。

{{site.data.keyword.cloud_notm}} Private v3.1.2 の新機能について詳しくは、[{{site.data.keyword.cloud_notm}} Private v3.1.2 の新機能](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}を参照してください。
{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 の新機能について詳しくは、[{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 の新機能](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}を参照してください。

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスの 2 つの新しいエンドポイントがロンドンと米国東部に用意されました。 詳しくは、[KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスの構成](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config)を参照してください。

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

現行リリースでは、新しくデプロイするすべてのインスタンスで、IBM Spectrum Protect™ Plus V10.1.3 がインストールされます。 IBM Spectrum Protect Plus V10.1.3 の新機能について詳しくは、[IBM Spectrum Protect Plus の更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}を参照してください。

### IBM Cloud での Zerto
{: #relnotes_v30-services-zerto}

Zerto on {{site.data.keyword.cloud_notm}} をプライベート専用のインスタンスに追加できるようになりました。 Zerto をプライベート専用のインスタンスにインストールする場合は、独自のプロキシー・サーバーをセットアップし、Zerto のコール・ホーム機能も構成する必要があります。 詳しくは、[プライベート・ネットワーク専用インスタンスのための Zerto on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only)を参照してください。

## 新規資料および更新された資料

* {{site.data.keyword.vmwaresolutions_short}} コンポーネントを VMware vSphere 6.7 にアップグレードするために役立つ資料が追加されました。 {{site.data.keyword.vmwaresolutions_short}} の自動化機能を今後も利用するためには、このアップグレードが必要です。 詳しくは、[VMware vSphere 6.5 から 6.7 への vCenter Server vSphere ソフトウェアのアップグレード](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade)を参照してください。
* {{site.data.keyword.cloud_notm}} の自動化機能で使用するために {{site.data.keyword.vmwaresolutions_short}} が維持するユーザー ID を記載した参照資料が追加されました。 インスタンスの履歴ログに表示される可能性があるメッセージも参照用に記載しています。 詳しくは、[IBM ユーザー ID](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) および[インスタンスの履歴メッセージ](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_messages)を参照してください。
* IBM Cloud インフラストラクチャー・アカウントに必要な権限を記載した表に、**リブート/コントロール**権限が追加されました。 詳しくは、[{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの権限](/docs/services/vmwaresolutions/services?topic=vmware-solutions-slaccountrequirement#slaccountrequirement-permissions)を参照してください。
* 以下の API に関する新しい参照資料が追加されました。 詳しくは、[API リファレンス](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}を参照してください。
  * 指定した VMware vCenter Server インスタンスのすべての履歴メッセージをリスト表示する
  * 指定したクラスターに共有ストレージを追加する
  * 指定したクラスターから NFS ストレージを削除する

## ユーザー・インターフェースの更新と向上
{: #relnotes_v30-ui}

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。

* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
