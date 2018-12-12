---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# 共通サービス・コンポーネント

共通サービスは、クラウド管理プラットフォームの他のサービスによって使用されるサービスを提供します。 共通サービスには、ID およびアクセスのサービス、ドメイン・ネーム・サービス、NTP サービスなどがあります。

図 1. {{site.data.keyword.cloud}} Private (ICP) の共通サービス
![ICP の共通サービス](vcscar-common-services.svg)

## ID およびアクセス・サービス

VMware vCenter Server on {{site.data.keyword.cloud_notm}} 自動化機能の一部として、ID 管理に Microsoft Active Directory (AD) が使用されます。単一の AD 仮想サーバー・インスタンス (VSI) がデプロイされます。 vCenter は AD 認証を使用するように構成されるため、ICP にも LDAP 認証を構成できます。

## 　ドメイン・ネーム・サービス

デプロイメント環境では、デプロイ済みの AD VSI をインスタンスのドメイン・ネーム・システム (DNS) サーバーとして使用します。デプロイされたコンポーネントはすべて、AD をデフォルトの DNS としてポイントするように構成されます。 デプロイ済みのコンポーネントの例には、vCenter、PSC、NSX、ESXi ホストなどがあります。

## Network Time Protocol サービス

vCenter Server のデプロイメントでは、{{site.data.keyword.cloud_notm}} インフラストラクチャーの Network Time Protocol (NTP) サーバーを使用します。デプロイ済みのすべてのコンポーネントは、これらの NTP サーバーを使用するように構成されます。
証明書と AD 認証が正常に機能するためには、すべてのコンポーネントで同じ NTP サーバーを使用することが必要不可欠です。

### 関連リンク

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](../vcs/vcs-hybridity-intro.html)
