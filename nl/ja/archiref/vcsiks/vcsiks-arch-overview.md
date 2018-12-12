---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# アーキテクチャーの概要
{{site.data.keyword.vmwaresolutions_full}} オファリングは、世界中の {{site.data.keyword.CloudDataCents_notm}}に VMware テクノロジー・コンポーネントをデプロイできる自動化機能を備えています。
このアーキテクチャーは単一のクラウド領域で構成されます。また、別の地域にある追加のクラウド領域、または同じデータ・センター内の別の {{site.data.keyword.cloud_notm}} ポッド (あるいはその両方) に拡張する機能をサポートします。

{{site.data.keyword.cloud_notm}} Private (ICP) および Cloud Automation Manager (CAM) 製品は、オンプレミスの仮想化プラットフォームに手動でデプロイできるので、オンプレミス・ロケーションからクラウド管理を行うことができます。また、ICP および CAM は、既存または新規の VMware vCenter Server on {{site.data.keyword.cloud_notm}} デプロイメントのサービス拡張として自動化機能によって提供され、{{site.data.keyword.cloud_notm}} からのクラウド管理を可能にします。

ICP は、オンプレミスのコンテナー化されたアプリケーションを開発および管理するためのアプリケーション・プラットフォームです。 ICP は、コンテナー・オーケストレーター Kubernetes、プライベート・イメージ・リポジトリー、管理コンソール、モニター・フレームワークを含む、コンテナーを管理するための統合環境です。

IBM Multi-Cluster Manager は、複数のクラウドおよびクラスターにおけるユーザー可視性、アプリケーション中心の管理 (ポリシー、デプロイメント、正常性、操作)、ポリシー・ベースのコンプライアンスを提供します。 IBM Multi-Cluster Manager を使用することで、Kubernetes クラスターを制御できます。 クラスターを安全かつ効率的に運用できるうえに、アプリケーションに必要なサービス・レベルの提供を保証できます。

{{site.data.keyword.cloud_notm}} Automation Manager は、{{site.data.keyword.cloud_notm}} Private 上で実行されるマルチクラウド・セルフサービス管理プラットフォームであり、開発者と管理者がビジネス要求に対応できるようにします。 Cloud Automation Manager Service Composer を使用すると、IBM Cloud Private カタログ内のハイブリッド・クラウド・サービスを公開できます。

## IBM Cloud サイドのクラウド管理プラットフォーム

以下の図は、{{site.data.keyword.cloud_notm}}
インフラストラクチャーにデプロイされた ICP と CAM を表しています。これらは、オンプレミスの vCenter と、{{site.data.keyword.cloud_notm}} にデプロイされた IBM
Kubernetes Service (IKS) サービスに接続されています。ユーザーは仮想マシン (VM) をオンプレミスにも vCenter Server インスタンスにもデプロイできます。また、コンテナーを ICP クラスターと IKS クラスターにデプロイできます。

図 1. クラウド・サイドからのクラウド管理
![クラウド上 - クラウド管理](vcsiks-oncloud-cloudmgt.svg)

この図では、CAM は、vCenter、クラウド・プロバイダー、ICP、IKS 環境へのクラウド接続を論理的に作成します。 ICP クラスターは各データ・センターまたはクラウド環境にデプロイし、MCM が ICP クラスターを単一の管理ビューに接続するメカニズムを提供するようにする必要があります。

ICP は、NSX-V または NSX-T コンポーネントとともにデプロイできます。 NSX-V とともに ICP をデプロイすると、VXLAN ネットワーク上で ICP VM を実行して Kubernetes Calico 内部ネットワーキングを使用できるようになります。

NSX-T とともに ICP をデプロイすると、ユーザーはネットワーキング、サブネット、ポリシーを中央 UI (NSX-T Manager) から制御および構成できるようになります。 NSX-V と NSX-T の違いについては、[{{site.data.keyword.cloud_notm}}
VCS ネットワーキング・リファレンス・アーキテクチャー](../vcsnsxt/vcsnsxt-intro.html) を参照してください。

## オンプレミスのクラウド管理プラットフォーム

以下の図は、オンプレミス・インフラストラクチャーにデプロイされた ICP と CAM を表しています。これらは、{{site.data.keyword.cloud_notm}} にデプロイされた vCenter と IKS に接続されています。ユーザーは VM とコンテナーをオンプレミスに、VM を vCenter Server インスタンスに、そしてコンテナーを IKS クラスターにデプロイできます。

図 2. オンプレミス・サイドからのクラウド管理
![オンプレミスのクラウド管理](vcsiks-onprem-cloudmgt.svg)

デプロイ済みの IKS コンテナーとの接続を確立するために strongSwan VPN が使用されています。 strongSwan は最終的に Direct Link 接続に置き換えられる場合があります。


この図では、CAM は、vCenter、クラウド・プロバイダー、ICP、IKS 環境へのクラウド接続を論理的に作成します。 ICP クラスターは各データ・センターまたはクラウド環境にデプロイし、MCM が ICP クラスターを単一の管理ビューに接続するメカニズムを提供するようにする必要があります。

### 関連リンク

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](../vcs/vcs-hybridity-intro.html)
