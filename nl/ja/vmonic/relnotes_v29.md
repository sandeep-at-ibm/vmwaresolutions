---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V2.9 のリリース・ノート
{: #relnotes_v29}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## VMware vCenter Server on IBM Cloud with NSX-T
{: #relnotes_v29-vcs-nsx-t}

このリリースでは、VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T オファリングが、PoC (概念検証) またはサンドボックス・テスト用のオファリングとして導入されました。 vCenter Server with NSX-T は、専用のホスト・サービスを提供するクラウドで、VMware の次世代ネットワーキング・プラットフォームである NSX-T のテスト・ドライブを行うことができます。

詳しくは、以下のトピックを参照してください。

* [vCenter Server with NSX-T の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview)
* [vCenter Server with NSX-T インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## VMware Cloud Foundation on IBM Cloud のサポートの終了
{: #relnotes_v29-vcf-eos}

オファリングを統合してカスタマー・エクスペリエンスを向上させるために、{{site.data.keyword.cloud_notm}} では VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} のサポート提供を 2019 年 5 月 13 日で終了します。
 
今後、すべてのお客様は、ストレージとライセンスに関してより柔軟なオプションを備えた VMware vCenter Server on {{site.data.keyword.cloud_notm}} に誘導されます。
 
VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} をご利用の既存のお客様には、2019 年 5 月 13 日のサポート終了日までに VMware vCenter Server on {{site.data.keyword.cloud_notm}} へのマイグレーションを支援いたします。

5 月 13 日より後は、VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} の管理機能が {{site.data.keyword.vmwaresolutions_short}} コンソールから削除されます。 VMware vCenter Server on {{site.data.keyword.cloud_notm}} にマイグレーションされていないインスタンスは、IBM Cloud インフラストラクチャー・コンソールを使用してアクセスできます。

{{site.data.keyword.cloud_notm}} サポートでは、VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} からのマイグレーションを開始していただけるように、2019 年 3 月 25 日までにお客様に連絡をいたします。 既存のお客様のマイグレーション・オプションについて詳しくは、[{{site.data.keyword.vmwaresolutions_short}} Wiki ページ](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/Wf58c4c538dbf_45b4_b7a7_5003d0ceb79b/page/IBM%20Cloud%20for%20VMware%20Solutions){:new_window}を参照してください。
 
お客様は、既存の VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} インスタンスを [{{site.data.keyword.vmwaresolutions_short}} コンソール](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted)で表示することができます。

## VMware vSphere 6.7 Update 1 のサポート
{: #relnotes_v29-vsphere}

VMware vCenter Server、VMware vCenter Server with Hybridity Bundle、および VMware vSphere on {{site.data.keyword.cloud_notm}} の各インスタンスとともに、VMware vSphere バージョン 6.7 Update 1 を注文するオプションができました。

さらに、Single-node Trial for Migration and App Modernization インスタンスを vSphere Enterprise Plus 6.7u1 とともに注文できるようになりました。

vSphere Enterprise Plus 6.7u1 は Broadwell および Skylake の {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} でのみ使用可能です。

詳しくは、以下のトピックの『_ライセンス設定_』セクションを参照してください。

* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server with Hybridity Bundle インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## VLAN スパンニングのサポートの終了
{: #relnotes_v29-vlan}

2019 年 8 月より、{{site.data.keyword.vmwaresolutions_short}} では VLAN スパンニングがサポートされなくなります。 2019 年 7 月末までに、ご使用の {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントを Virtual Routing and Forwarding (VRF) に変換し、アカウントのサービス・エンドポイントを有効にする必要があります。

詳しくは、以下を参照してください。

* [Virtual Routing and Forwarding (VRF) on IBM Cloud の概要](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [アカウントでサービス・エンドポイントを使用できるようにする方法](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)

## アプリケーション・プログラミング・インターフェースのサポート
{: #relnotes_v29-api}

インスタンスのデプロイ、インスタンスの削除、ESXi サーバーとクラスターの追加と削除で、アプリケーション・プログラミング・インターフェース (API) を使用できるようになりました。

REST API 資料も、ユーザー資料の『*リファレンス*』セクションに用意されています。 詳しくは、[{{site.data.keyword.vmwaresolutions_short}} API](https://cloud.ibm.com/apidocs/vmware-solutions) を参照してください。

## VMware vCenter Server インスタンスの更新
{: #relnotes_v29-vcs}

このリリースでは、以下のアップグレードと機能改善が適用されます。

* vSphere ESXi 6.7 Update 1 (ビルド 6.7.0-11675023)
* vSphere ESXi 6.5 Update 2 (ビルド 6.5.0-11925212)
* vSphere 6.7 Distributed vSwitch 6.6.0
* vSphere 6.5 Distributed vSwitch 6.5.0
* vCenter Server Appliance 6.7 U1 (ビルド 6.7.0-10244745)
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4 (ビルド 11197766)
* NSX-T for vSphere 2.4

VMware コンポーネントの選択について詳しくは、[vCenter Server の部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)を参照してください。

### データ・センターの更新
{: #relnotes_v29-dc}

新しいデータ・センター (**FRA-05 - フランクフルト**と **LON-05 - ロンドン**) でのデプロイメントが可能になりました。 詳しくは、[vCenter Server インスタンスの要件と計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)を参照してください。

### ESXi サーバーの機能拡張
{: #relnotes_v29-vcs-esxi}

* インスタンス配信前の ESXi サーバーでセキュア・シェル (SSH) プロトコルが使用不可になりました。 SSH を有効にするには、[Enable SSH from the vSphere Web Client](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vcli.getstart.doc%2FGUID-C3A44A30-EEA5-4359-A248-D13927A94CCE.html) を参照してください。
* V2.9 リリース以降で、以下の ESXi サーバー操作が可能です。

   * サーバーが保守モードの間に、新規 ESXi サーバーを既存のクラスターに追加する。 仮想マシンは、保守モードを解除するまで新規サーバーにマイグレーションされません。
   * インスタンス内の複数のクラスター間で同時に ESXi サーバーを追加または削除する。

詳しくは、[vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)を参照してください。

### ネットワーク・ファイル・システムのストレージ・サイズ
{: #relnotes_v29-vcs-nfs}

vCenter Server インスタンスの注文の場合、パフォーマンス・レベルが 0.25、2、および 4 IOPS/GB のネットワーク・ファイル・システム (NFS) 共有ストレージを最大 24 TB まで追加できます。

10 IOPS/GB パフォーマンス・レベルは、引き続きファイル共有あたり最大 4 TB の容量に制限されています。
{:note}

## アドオン・サービスの更新
{: #relnotes_v29-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v29-services-caveonix}

V2.9 以降のリリースでデプロイ (またはそのリリースにアップグレード) された VMware vCenter Server インスタンスで、Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスを使用できるようになりました。 このサービスは、脅威から保護し、業界規制や政府規制を遵守するために、プロアクティブなモニターおよび自動ディフェンス制御によって、サイバーおよびコンプライアンスのリスクを管理します。

Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスを組み込んだ形で vCenter Server インスタンスを注文することもできますし、このサービスを後からインスタンスの詳細ページの**「サービス」**タブで既存の vCenter Server インスタンスに追加することもできます。

また、スタンドアロン Caveonix RiskForesight ライセンスを VMware インスタンスと関連付けずに注文して、オンプレミス・ワークロードのライセンス交付とアクティベーションを行うこともできます。

詳しくは、以下を参照してください。
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} に関する考慮事項](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Caveonix ライセンスに関する考慮事項](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_considerations)
* [Caveonix ライセンスの注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

現行リリースでは、新しくデプロイされるすべてのインスタンスに F5-BigIP VE V14.1.0.2 がインストールされます。 F5-BigIP VE V14.1.0.2 の新機能について詳しくは、[Release Note: BIG-IP 14.1.0 New and Installation](https://support.f5.com/kb/en-us/products/big-ip_ltm/releasenotes/product/relnote-bigip-14-1-0.html){:new_window} を参照してください。

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

現行リリースでは、新しくデプロイされるすべてのインスタンスに HyTrust CloudControl 5.4.2 がインストールされます。 HyTrust CloudControl 5.4.2 の新機能について詳しくは、[HyTrust CloudControl Release Notes Version 5.4.2](https://docs.hytrust.com/CloudControl/5.4.2/Online/index.html#HTCC_Admin_Guide/_FrontMatter/Whats-New.html%3FTocPath%3D_____2){:new_window} を参照してください。

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

シドニーでは、KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスの 2 つの新しいエンドポイントが使用可能になりました。 詳しくは、[KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスの構成](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering#kmip_standalone_ordering-config)を参照してください。

(2019 年 4 月 9 日に更新) これまでの KMIP for VMware on {{site.data.keyword.cloud_notm}} では、暗号鍵の作成、暗号化、復号化に IBM Key Protect for {{site.data.keyword.cloud_notm}} を使用していました。V2.9 リリース以降の KMIP for VMware on {{site.data.keyword.cloud_notm}} では、暗号化サービスと鍵管理サービスを一式備えた {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services を使用して、{{site.data.keyword.cloud_notm}} の VMware で使用する暗号鍵を管理することも可能です。詳しくは、[KMIP for VMware on IBM Cloud の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)および [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started) を参照してください。

### IBM Cloud での Veeam
{: #relnotes_v29-services-veeam}

現行リリースでは、新しくデプロイされるすべてのインスタンスに Veeam Backup and Replication 9.5 Update 4 がインストールされます。 Veeam 9.5u4 の新機能について詳しくは、[Release information for Veeam Backup and Replication 9.5 Update 4](https://www.veeam.com/kb2878){:new_window} を参照してください。

### IBM Cloud での Zerto
{: #relnotes_v29-services-zerto}

現行リリースでは、新しくデプロイされるすべてのインスタンスに Zerto Virtual Replication 6.5 update 3 がインストールされます。 Zerto Virtual Replication 6.5 update 3 の新機能について詳しくは、[Release notes for Zerto Virtual Replication V6.5 Update 3](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Release%20Notes.pdf){:new_window} を参照してください。

## ユーザー・インターフェースの更新と向上
{: #relnotes_v29-ui}

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。

* **「インフラストラクチャー」**ページの新しい**「ネットワーク・インターフェース」**表で、クラスターの VLAN、サブネット、および IP アドレスの詳細情報が提供されます。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
