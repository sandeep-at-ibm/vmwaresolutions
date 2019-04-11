---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-01"

subcollection: vmwaresolutions


---

# V2.6 のリリース・ノート
{: #relnotes_v26}

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Spectre および Meltdown への対処
{: #relnotes_v26-spectre}

{{site.data.keyword.vmwaresolutions_short}} は、Spectre および Meltdown に関連する脆弱性 (CVE-2017-5753、CVE-2017-5715、CVE-2017-5754) に対して VMware から提供されたパッチをリリースしました。

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## High Performance with Intel Optane オプション
{: #relnotes_v26-optane}

このリリースでは、新しいインスタンスの注文時、または初期デプロイメント後に新しい vSAN クラスターを追加するときに、vSAN ストレージ用のハイパフォーマンス・キャッシュを追加するオプションが提供されます。

このオプションを使用すると、今まで 8 台であったストレージ容量ディスクの数を最大 10 台まで増やすことができます。

High Performance with Intel Optane オプションは、Dual Intel Xeon Gold 5120 プロセッサーおよび Dual Intel Xeon Gold 6140 プロセッサーを使用したカスタマイズ構成でのみ使用できます。

詳しくは、インスタンスまたはクラスターのタイプに対応した注文トピックを参照してください。

## パブリック・ネットワークまたはプライベート・ネットワークの有効化
{: #relnotes_v26-pub-private-network}

パブリックとプライベートのネットワーク・インターフェース・カード (NIC) を有効にして、またプライベートのみの NIC を有効にして、vCenter Server インスタンスと vCenter Server with Hybridity Bundle インスタンスを、VMware vSphere クラスターとともにデプロイできるようになりました。 このオプションは、vCenter Server インスタンスおよび vCenter Server with Hybridity Bundle インスタンスに新しいクラスターを追加する場合にも使用できます。

一部のアドオン・サービスはパブリック NIC を必要とするため、プライベートのみのネットワークを有効にするように選択した場合は利用できません。

詳しくは、以下のトピックの『_ネットワーク・インターフェースの設定_』セクションを参照してください。

* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#network-interface-settings)
* [vCenter Server with Hybridity Bundle インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#network-interface-settings)
* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#network-interface-settings)

## ESXi サーバーの削除
{: #relnotes_v26-delete-esxi}

インスタンスの最小要件を満たしている場合は、vCenter Server インスタンス、vCenter Server with Hybridity Bundle インスタンス、または Cloud Foundation インスタンスから ESXi サーバーを削除できるようになりました。

ESXi サーバーの要件について詳しくは、以下のトピックを参照してください。

* [vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [vCenter Server with Hybridity Bundle インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)

## VMware vCenter Server インスタンスの更新
{: #relnotes_v26-vcs}

このリリースでは、以下のアップグレードと機能改善が適用されます。

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## VMware vCenter Server with Hybridity Bundle の更新
{: #relnotes_v26-vcs-hybrid}

### vCenter Server インスタンスからの Hybridity Bundle の削除
{: #relnotes_v26-remove-bundle}

vCenter Server インスタンスから Hybridity Bundle ライセンスを削除できるようになりました。 これを行うには、VMware NSX および VMware vSAN のレンタル・ライセンス・キーをライセンス持ち込み (BYOL) キーに置き換え、レンタル・ライセンスの料金を取り消すためのサポート・チケットを開く必要があります。

詳しくは、[vCenter Server インスタンスからの Hybridity Bundle の削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletingbundle)を参照してください。

### vCenter Server with Hybridity Bundle の可用性
{: #relnotes_v26-bundle-available}

ビジネス・パートナーが、vCenter Server with Hybridity Bundle インスタンスを注文できるようになりました。 ビジネス・パートナーは、既存の vCenter Server インスタンスを vCenter Server with Hybridity Bundle インスタンスにアップグレードすることはできません。また、vCenter Server with Hybridity Bundle インスタンスから Hybridity Bundle を削除することもできません。

詳しくは、以下のトピックを参照してください。

* [vCenter Server with Hybridity Bundle の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [vCenter Server with Hybridity Bundle インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## VMware Cloud Foundation インスタンスの更新
{: #relnotes_v26-vcf}

このリリースでは、以下のアップグレードと機能改善が適用されます。

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## アドオン・サービスの更新
{: #relnotes_v26-services}

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v26-htkc}

V2.3 以降のリリースでデプロイまたは V2.3 以降のリリースにアップグレードされた VMware Cloud Foundation インスタンスと VMware vCenter Server インスタンスで vSphere 6.5 を実行する場合、HyTrust KeyControl on {{site.data.keyword.cloud_notm}} サービスを使用できるようになりました。 このサービスは、暗号鍵のライフサイクルを自動化および単純化することによって、暗号化ワークロードの管理を単純化します。 このサービスでは、FIPS 140-2 準拠の暗号化を使用することで、暗号鍵を簡単に一括して管理できるようになります。 このサービスを使用すると、すべての仮想マシンと暗号化データ・ストアの暗号鍵を管理することや、大規模なデプロイメントで何千もの暗号化ワークロードをサポートするように拡張することができます。

このサービスを組み込んだ形でインスタンスを注文することも、後から既存のインスタンスにこのサービスを追加することもできます。

詳しくは、以下のトピックを参照してください。
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} のコンポーネントと考慮事項](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v26-htcc}

現行リリースでは、新しくデプロイするすべてのインスタンスで、HyTrust CloudControl 5.4 がインストールされます。 HyTrust CloudControl 5.4 の新機能について詳しくは、[HyTrust CloudControl v 5.4 Online Documentation Set](https://docs.hytrust.com/CloudControl/5.4.0/Online/index.html) を参照してください。

### HyTrust DataControl on IBM Cloud
{: #relnotes_v26-htdc}

現行リリースでは、新しくデプロイするすべてのインスタンスで、HyTrust DataControl 4.2 がインストールされます。 HyTrust DataControl 4.2 の新機能について詳しくは、[What's New in HyTrust DataControl 4.x](https://docs.hytrust.com/DataControl/4.2/Admin_Guide-4.2/Content/Books/aaCommon/New-Changed-4x.htm) を参照してください。

### Veeam on IBM Cloud による vSphere ESXi V6.5 Update 2c のサポート
{: #relnotes_v26-veeam}

V2.6 以降では、vSphere ESXi V6.5 Update 2c を使用して新しいインスタンスと新しいホストがプロビジョニングされるようになりました。 Veeam Backup and Replication を使用している場合は、Veeam on {{site.data.keyword.cloud_notm}} インスタンスを V9.5u3a 以降に更新して vSphere ESXi 6.5 Update 2c との互換性を最大限に高めることが Veeam によって推奨されています。

Veeam on {{site.data.keyword.cloud_notm}} がインストールされている既存の Cloud Foundation インスタンスも V9.5u3a 以降に更新することが推奨されています。

Veeam on {{site.data.keyword.cloud_notm}} について詳しくは、[Veeam on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)を参照してください。

### VMware HCX on IBM Cloud
{: #relnotes_v26-hcx}

現行リリースでは、新しくデプロイするすべてのインスタンスで、VMware HCX 3.5.1 がインストールされます。 HCX 3.5.1 の新機能について詳しくは、[VMware NSX Hybrid Connect 資料](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/index.html)を参照してください。

### Zerto on IBM Cloud による vSphere ESXi V6.5 Update 2c のサポート
{: #relnotes_v26-zerto}

以前に Zerto を {{site.data.keyword.cloud_notm}} 上にインストールしており、既存のホストを vSphere ESXi V6.5 Update 2 に更新した場合、Zerto Virtual Replication コンソールの Zerto Virtual Replication Appliance (VRA) 状況に、`「Unsupported ESX Version」`という警告メッセージが表示されることがあります。

この警告メッセージの解決方法について詳しくは、以下を参照してください。

* [Zerto Virtual Replication Interoperability Matrix](http://s3.amazonaws.com/zertodownload_docs/6.0_Latest/Zerto%20Virtual%20Replication%20Operability%20Matrix.pdf)
* [Updating a ZVM to Support Zerto-Approved Host Releases Prior to a Full ZVR Update](https://www.zerto.com/myzerto/knowledge-base/updating-a-zvm-to-support-zerto-approved-host-releases-prior-to-a-full-zvr-update/)

## 新規資料および更新された資料
{: #relnotes_v26-new-docs}

### リファレンス・アーキテクチャー資料
{: #relnotes_v26-ref-archi}

{{site.data.keyword.vmwaresolutions_short}} アーキテクチャー資料が更新され、VMware インスタンスの管理と運用に関する責任を理解するための重要な考慮事項が記載されています。

詳しくは、[デプロイメント後の VMware インスタンスの考慮事項](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_considerations)を参照してください。

## ユーザー・インターフェースの更新と向上
{: #relnotes_v26-ui}

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。

* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
