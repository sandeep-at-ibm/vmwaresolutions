---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-10"

---

# 詳細設計

## 共通サービス・コンポーネント
共通サービスは、クラウド管理プラットフォームの他のサービスによって使用されるサービスを提供します。 これには、ID およびアクセスのサービス、ドメイン・ネーム・サービス、NTP サービスが含まれます。

図 1. ICP 共通サービス

![ICP 共通サービス](vcsicp-icp-commonservices.svg)

### ID およびアクセス・サービス
VCS 自動化の一部として、ID 管理に Microsoft Active Directory (AD) が使用されます。単一の AD 仮想サーバー・インスタンス (VSI) がデプロイされます。vCenter は MS AD 認証を使用するように構成されるので、ICP を LDAP 認証用に構成することもできます。

###	ドメイン・ネーム・サービス
VCS デプロイメントでは、デプロイされた Microsoft Active Directory (AD) VSI をインスタンスの DNS サーバーとして使用します。デプロイされたコンポーネント (vCenter、PSC、NSX、ESXi ホスト) はすべて、MS AD をデフォルトの DNS としてポイントするように構成されます。

###	NTP サービス
VCS デプロイメントでは、IBM Cloud インフラストラクチャーの NTP サーバーを使用します。デプロイ済みのすべてのコンポーネントは、これらの NTP サーバーを使用するように構成されます。 設計内のすべてのコンポーネントが同じ NTP サーバーを使用するようにすることは、証明書と MS AD 認証が正しく機能するうえで必要不可欠です

## ネットワーキング

### NSX-V ネットワーキング

NSX-V は、単一の NSX-V マネージャー・プラットフォームが単一の vCenter Server インスタンスに結合されるように設計されています。vSphere 環境内で実行されるアプリケーションにネットワーク・サービスを提供します。

VCS デプロイメントに含まれる NSX-V ネットワーキングを使用して、ICP を VXLAN オーバーレイ・ネットワークにデプロイできます。

ICP は Kubernetes のデフォルトの Calico ネットワーキング・スタックと共にデプロイされ、このネットワーキング・スタックがクラスター内のネットワーク分離に使用されます。

図 2. NSX-V を使用する場合の ICP のネットワーキング

![NSX-V を使用する場合の ICP のネットワーキング](vcsicp-nsxv-networking.svg)

詳しくは、[IBM Cloud VCS ネットワーキング参照アーキテクチャー](../vcsnsxt/vcsnsxt-intro.html)を参照してください

### NSX-T ネットワーキング

NSX-T は、仮想マシンまたはコンテナー・ベースの任意のタイプのアプリケーションに接続できる単一のネットワーキング・プラットフォームが、vSphere 環境の内部または外部で実行されるように設計されています。

ICP には Calico ネットワーキングを NSX-T インスタンスに置き換えるオプションがあるので、ICP はネットワーキングとセキュリティーを管理するための単一のロケーションになります。

図 3. NSX-T を使用する場合の ICP のネットワーキング

![NSX-T を使用する場合の ICP のネットワーキング](vcsicp-icp-nsxt-networking.svg)

### 関連リンク

* [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
