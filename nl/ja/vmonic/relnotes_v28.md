---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-28"

---

# V2.8 のリリース・ノート

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Single-node Trial for Migration and App Modernization インスタンス

Single-node Trial for Migration and App Modernization を使用すると、VMware ワークロードを {{site.data.keyword.cloud_notm}} にマイグレーションしてから、コンテナーを使用してワークロードをモダナイズする、という {{site.data.keyword.cloud_notm}} のテスト・ドライブを簡単に行うことができます。 このトライアル版は、VMware vCenter Server on {{site.data.keyword.cloud_notm}} に置かれた {{site.data.keyword.icpfull_notm}} Hosted の 1 バージョンです。オンプレミス環境と同じ使い慣れたツールで管理できる Kubernetes コンテナー管理プラットフォームおよび単一テナント VMware プラットフォームが提供されます。

詳しくは、[Single-node Trial for Migration and App Modernization の概要](/docs/services/vmwaresolutions/vcenter/cloud_modern_bundle_overview.html)を参照してください。

## ネットワーク・ファイル・システム・ストレージの追加および削除

V2.8 リリース以降、ネットワーク・ファイル・システム (NFS) ストレージ共有を既存の NFS または vSAN vCenter Server クラスターに追加したり、NFS ファイル共有を既存の vCenter Server クラスターから削除したりできるようになりました。

カスタマイズ型のファイル・レベルの共有ストレージのために、以下のオプションを選択できるようになりました。

* 20GB から 12TB までの NFS 共有サイズ (GB 単位)
* 0.25 IOPS/GB

詳しくは、[vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservers.html#adding-nfs-storage-to-vcenter-server-instances)の *vCenter Server インスタンスへの NFS ストレージの追加*および *vCenter Server インスタンスからの NFS ストレージの削除*のセクションを参照してください。

## SAP 認定 Broadwell E5-2690 および E7-8890 サーバーのサポート

V2.8 リリース以降、VMware vCenter Server on {{site.data.keyword.cloud_notm}} と VMware vSphere on {{site.data.keyword.cloud_notm}} のインスタンスとクラスターのデプロイメントで、以下の新しい {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU モデルを使用できるようになりました。

* デュアル Intel Xeon E5-2690 v4 プロセッサー / 合計 28 コア、2.60 GHz / 512 GB RAM
* クワッド Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.20 GHz / 1024 GB RAM
* クワッド Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.20 GHz / 2048 GB RAM
* クワッド Intel Xeon E7-8890 v4 プロセッサー / 合計 96 コア、2.20 GHz / 4096 GB RAM

詳しくは、以下の資料にある『*{{site.data.keyword.baremetal_short_sing}}の設定*』セクションを参照してください。
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## Broadwell E7-4820 および E7-4850 サーバーのサポート

V2.8 リリース以降、vCenter Server、vCenter Server with Hybridity Bundle、Cloud Foundation、および vSphere on {{site.data.keyword.cloud_notm}} のインスタンスとクラスターのデプロイメントで、以下の新しい {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU モデルを使用できるようになりました。

* クワッド Intel Xeon E7-4820 v4 / 合計 40 コア、2.0 GHz
* クワッド Intel Xeon E7-4850 v4 / 合計 64 コア、2.1 GHz

詳しくは、以下の資料にある『*{{site.data.keyword.baremetal_short_sing}}の設定*』セクションを参照してください。
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html#bare-metal-server-settings)
* [vCenter Server with Hybridity Bundle インスタンスの注文](/docs/services/vmwaresolutions/vcenter/vc_hybrid_orderinginstance.html#bare-metal-server-settings)
* [Cloud Foundation インスタンスの注文](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html#bare-metal-server-settings)

## 組み込み Platform Services Controller

V2.8 リリース以降、vCenter Server は、組み込み PSC (Platform Services Controller) とともにデプロイされます。つまり、vCenter Server、vCenter Server コンポーネント、および PSC が単一の同じ仮想マシン上にデプロイされます。 この変更は、新しくデプロイされるすべての vCenter Server、vCenter Server with Hybridity、および NetApp インスタンスに適用されます。

旧リリースから V2.8 にインスタンスをアップグレードした場合に、PSC は vCenter Server に組み込まれません。 組み込み PSC を使用するには、手動で外部 PSC から組み込み PSC に変換する必要があります。

マルチサイト構成のプライマリー・インスタンスをアップグレードし、外部 PSC を組み込み PSC に手動で変換した場合、新たにデプロイする V2.8 のセカンダリー・インスタンスのすべてに PSC が組み込まれます。

詳しくは、[vCenter Server の概要](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html#vcenter-server-architecture)の『*vCenter Server アーキテクチャー*』セクションを参照してください。

## VMware vCenter Server インスタンスの更新

このリリースでは、以下のアップグレードと機能改善が適用されます。

* vSphere ESXi 6.5 Update P3 (ビルド 6.5.0-10884925)
* vCenter Server 6.5 U2d (ビルド 6.5.0-10964411)
* Platform Services Controller 6.5 U2d (ビルド 6.5.0-10964411)

## VMware Cloud Foundation インスタンスの更新

このリリースでは、以下のアップグレードと機能改善が適用されます。

* vSphere ESXi 6.5 Update EP11 (ビルド 6.5.0-10719125)
* vCenter Server 6.5 U2c (ビルド 6.5.0-9451637)
* Platform Services Controller 6.5 U2c (ビルド 6.5.0-9451637)

## アドオン・サービスの更新

### IBM Spectrum Protect Plus on IBM Cloud

現行リリースでは、新しくデプロイするすべてのインスタンスで、IBM Spectrum Protect™ Plus V10.1.2 がインストールされます。 IBM Spectrum Protect Plus V10.1.2 の新機能について詳しくは、[IBM Spectrum Protect Plus の更新](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}を参照してください。

### KMIP for VMware on IBM Cloud

これまでは、Cloud Foundation または vCenter Server インスタンスを注文するときに KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスを付けるか、初期デプロイメントの後に既存の Cloud Foundation または vCenter Server インスタンスにこのサービスを追加していました。

V2.8 リリース以降、このサービスは、VMware インスタンスと関連付けることなく、スタンドアロン・サービスとして使用できるようになりました。 このサービスのインスタンス 1 つで、1 つ以上の Cloud Foundation インスタンス、vCenter Server インスタンス、または vSphere クラスターに対応できます。

**注**: このリリースでは、KMIP for VMware on {{site.data.keyword.cloud_notm}} は vSphere 暗号化のみに限定されています。

詳しくは、[KMIP for VMware on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html)を参照してください。

## リファレンス・アーキテクチャー資料

KMIP for VMware on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャーについての新しい技術資料が、ユーザー資料の『*リファレンス*』セクションに用意されました。 詳しくは、[KMIP for VMware の概要](/docs/services/vmwaresolutions/archiref/kmip/overview.html)を参照してください。

## ユーザー・インターフェースの更新と向上

ユーザー・インターフェースが更新され、以下の拡張機能が備えられました。

* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改良が加えられました。
