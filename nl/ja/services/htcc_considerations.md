---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# HyTrust CloudControl on IBM Cloud の概要

HyTrust CloudControl on {{site.data.keyword.cloud}} サービスは、セキュリティー規格を適用してコンプライアンスを統制し、詳細な役割ベースのアクセス制御 (RBAC)、承認、および監査の機能を提供します。 このサービスを HyTrust DataControl と組み合わせると、仮想マシンとワークロードのデータを特定の地域、クラスター、または {{site.data.keyword.CloudDataCent_notm}} の ESXi サーバーから外に出さないようにすることができます。

**利用可否:** このサービスは、vSphere 6.5 を実行する、V2.3 以降のリリースでデプロイ (または V2.3 以降のリリースにアップグレード) されたインスタンスでのみ利用できます。

## HyTrust CloudControl on IBM Cloud のコンポーネント

アクティブ-パッシブ・モードでは、デフォルトのクラスターに HyTrust CloudControl (HTCC) アプライアンスの高可用性 (HA) ペアがデプロイされます。

HTCC アプライアンスの各ペアは、NSX Manager、vCenter Server Appliance、Platform Services Controller などの管理仮想マシン (VM) に指定したプライベート・ポータブル・サブネットと同じサブネットにデプロイされます。

このアプライアンスのペアは、インスタンスの vSphere ホスト、vCenter Server Appliance、NSX Manager のプロキシーの役割を果たします。 したがってユーザーは、vSphere ホスト、vCenter Server Appliance、NSX Manager にアクセスする時に、{{site.data.keyword.cloud}} によって割り当てられる実際の IP アドレス (RIP) ではなく、管理者によって割り当てられる公開 IP アドレス (PIP) を使用します。

HTCC アプライアンスと Microsoft Active Directory を統合すれば、役割ベースのアクセス制御が可能になります。

## HyTrust CloudControl on IBM Cloud を削除する際の考慮事項

HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスを削除する前に、**Root Password Vaulting** を構成していた場合は無効にし、すべての保護ホストを HyTrust CloudControl から削除してください。

## 関連リンク

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} の注文](htcc_ordering.html)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} の管理](managinghtcc.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust Web サイト](https://www.hytrust.com/)
