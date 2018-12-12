---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---

# アーキテクチャーの概要

{{site.data.keyword.vmwaresolutions_full}} オファリングは、世界中の {{site.data.keyword.CloudDataCents_notm}}に VMware テクノロジー・コンポーネントをデプロイできる自動化機能を備えています。
このアーキテクチャーは単一のクラウド領域で構成されます。また、別の地域にある追加のクラウド領域、または同じデータ・センター内の別の {{site.data.keyword.cloud_notm}} ポッド (あるいはその両方) に拡張する機能をサポートします。

{{site.data.keyword.cloud_notm}} Private (ICP) および Cloud Automation Manager (CAM) 製品は、オンプレミスの仮想化プラットフォームに手動でデプロイできるので、オンプレミス・ロケーションからクラウド管理を行うことができます。また、ICP および CAM は、既存または新規の VMware vCenter Server on {{site.data.keyword.cloud_notm}} デプロイメントのサービス拡張として提供されているので、自動化機能を使用して {{site.data.keyword.cloud_notm}} からクラウドを管理することもできます。

ICP は、オンプレミスのコンテナー化されたアプリケーションを開発および管理するためのアプリケーション・プラットフォームです。 ICP は、コンテナー・オーケストレーター Kubernetes、プライベート・イメージ・リポジトリー、管理コンソール、モニター・フレームワークを含む、コンテナーを管理するための統合環境です。

IBM Multi-Cluster Manager (MCM) は、複数のクラウドおよびクラスターにおけるユーザー可視性、アプリケーション中心の管理 (ポリシー、デプロイメント、正常性、操作)、ポリシー・ベースのコンプライアンスを提供します。 MCM を使用することで、Kubernetes クラスターを制御できます。 クラスターを安全かつ効率的に運用できるうえに、ビジネス要求を満たそうとしている開発者と管理者を支援する、ICP 上で実行されるサービス管理プラットフォームを提供できます。
Cloud Automation Manager Service Composer を使用すると、ICP カタログ内のハイブリッド・クラウド・サービスを表示できます。

## IBM Cloud サイドのクラウド管理プラットフォーム

以下の図は、{{site.data.keyword.cloud_notm} インフラストラクチャーに ICP および CAM をデプロイした例を示しています。これらはオンプレミスの vCenter および {{site.data.keyword.cloud_notm} にデプロイされた IBM Kubernetes Service (IKS) サービスに接続されています。ユーザーは仮想マシン (VM) をオンプレミスにも vCenter Server インスタンスにもデプロイできます。また、コンテナーを ICP クラスターと IKS クラスターにデプロイできます。

図 1. クラウド・サイドからのクラウド管理

![クラウド上 - クラウド管理](vcsicp-oncloud-cloudmgt.svg)

この図では、CAM は、vCenter、クラウド・プロバイダー、ICP、IKS 環境へのクラウド接続を論理的に作成します。 ICP クラスターは各データ・センターのクラウド環境にデプロイし、MCM が ICP クラスターを単一の管理ビューに接続するメカニズムを提供するようにする必要があります。

ICP は NSX-V または NSX-T コンポーネントとともにデプロイできます。NSX-V とともに ICP をデプロイすると、VXLAN ネットワーク上で ICP VM を実行して Kubernetes Calico 内部ネットワーキングを使用できるようになります。

NSX-T とともに ICP をデプロイすると、ユーザーはネットワーキング、サブネット、ポリシーを中央 UI (NSX-T Manager) から制御および構成できるようになります。 NSX-V と NSX-T の違いについては、[vCenter Server ネットワーキング・ガイド](../vcsnsxt/vcsnsxt-intro.html)を参照してください。

## オンプレミスのクラウド管理プラットフォーム

以下の図は、オンプレミスのインフラストラクチャーに ICP および CAM をデプロイした例です。これらは {{site.data.keyword.cloud_notm} にデプロイされた vCenter および IKS に接続されています。ユーザーは VM とコンテナーをオンプレミスに、VM を vCenter Server インスタンスに、そしてコンテナーを IKS クラスターにデプロイできます。

図 2. オンプレミス・サイドからのクラウド管理
![オンプレミスのクラウド管理](vcsicp-onprem-cloudmgt.svg)

デプロイ済みの IKS コンテナーとの接続を確立するために strongSwan VPN が使用されています。 strongSwan VPM は Direct Link 接続に置き換えることができます。

この図では、CAM は、vCenter、クラウド・プロバイダー、ICP、IKS 環境へのクラウド接続を論理的に作成します。 ICP クラスターは各データ・センターのクラウド環境にデプロイし、MCM が ICP クラスターを単一の管理ビューに接続するメカニズムを提供するようにする必要があります。

### 関連リンク

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](../vcs/vcs-hybridity-intro.html)
