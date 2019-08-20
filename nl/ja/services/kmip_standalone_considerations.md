---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-18"

keywords: KMIP for VMware, KMIP stand-alone, tech specs KMIP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud の概要
{: #kmip_standalone_considerations}

KMIP for VMware on {{site.data.keyword.cloud}} サービスは、{{site.data.keyword.cloud_notm}} 内の VMware によって使用される暗号鍵を管理するための、24 時間 365 日の高可用性サービスを提供します。 このサービスは、お客様が暗号鍵を作成、取得、活動化、取り消し、破棄できるようにするランタイム機能を提供します。 また、クライアントの資格情報と暗号鍵の関連付けを管理する管理機能も提供します。

KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスは、VMware インスタンスに関連付けられていないスタンドアロン・サービスとして使用できます。 このサービスのインスタンス 1 つで、1 つ以上の vCenter Server インスタンスまたは vSphere クラスターに対応できます。

## KMIP for VMware on IBM Cloud の技術仕様
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

以下の仕様が KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスに含まれています。

* VMware と互換性のある Key Management Interoperability Protocol (KMIP)
* 2 つの管理対象サービス: [Key Protect](https://cloud.ibm.com/catalog/services/key-protect){:external} および [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services){:external}
* 世界各地にある複数の地理的領域で利用可能
* 高可用性のために各地域に 2 つ用意される KMIP ネットワーク・サービス・エンドポイント

## KMIP for VMware on IBM Cloud インスタンスをインストールする際の考慮事項
{: #kmip_standalone_considerations-install}

KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスをインストールする前に、以下の考慮事項を確認してください。

* KMIP for VMware on {{site.data.keyword.cloud_notm}} は、IBM Key Protect サービスまたは the Hyper Protect Crypto Services (HPCS) サービスを使用して、暗号鍵を作成、暗号化、および復号します。そのため、KMIP for VMware on {{site.data.keyword.cloud_notm}} をインストールする前に、以下を確認してください。
   * KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスをホストする {{site.data.keyword.cloud_notm}} の地域で使用可能な Key Protect または HPCS サービスを注文したこと。
      * Key Protect のインスタンスの作成について詳しくは、『[サービスのプロビジョニング](/docs/services/key-protect?topic=key-protect-provision)』を参照してください。
      * HPCS のインスタンスの作成について詳しくは、『[サービスのプロビジョニング](/docs/services/hs-crypto?topic=hs-crypto-provision#provision)』を参照してください。 HPCS サービスのプロビジョニングに加えて、HPCS が主要な関連機能を提供できるように[暗号インスタンスを初期化する](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm)必要もあります。
   * [サービス ID の作成](/docs/iam?topic=iam-serviceids)で示されているステップに従って {{site.data.keyword.cloud_notm}} サービス ID が作成されたこと。 このサービス ID を使用して、作成した Key Protect または HPCS サービス・インスタンスにアクセスできます。
   * サービス ID に以下のアクセス・レベルを付与したこと。
      * プラットフォーム・アクセス・レベル: Key Protect または HPCS サービス・インスタンスに対する Viewer 権限
      * サービス・アクセス・レベル: Key Protect または HPCS サービス・インスタンスに対する Manager 権限
   * 作成されたサービス ID の API 鍵を所持していること。 その鍵は、サービスを注文する際に必要になります。
   * Key Protect または HPCS の GUI または API を使用して、少なくとも 1 つのカスタマー・ルート鍵 (CRK) を作成したこと。
      * Key Protect GUI または API を使用してルート鍵を作成する方法について詳しくは、[ルート鍵の作成](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys)または [IBM Key Protect API](https://cloud.ibm.com/apidocs/key-protect){:external}を参照してください。
      * HPCS GUI または API を使用してルート鍵を作成する方法について詳しくは、[ルート鍵の作成](/docs/hs-crypto/get-started?topic=hs-crypto-create-root-keys)または [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto){:external} を参照してください。

     **重要:** CRK がなければサービスを注文することはできません。 既存の鍵素材を使用して CRK を作成するという方法を使用すると共に、作成している鍵素材のバックアップを取ることを強くお勧めします。 これにより、CRK の保管のために Key Protect または HPCS を適用しているデータ・センターの機能が障害によって失われた場合に、鍵をリカバリーできるようになります。
* {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの Virtual Routing and Forwarding (VRF) およびサービス・エンドポイントへの接続を有効にしたことを確認してください。 詳しくは、以下を参照してください。
   * [Virtual Routing and Forwarding (VRF) on IBM Cloud の概要](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [サービス・エンドポイントの有効化](/docs/account?topic=account-vrf-service-endpoint#service-endpoint)
* プライベート接続しかサポートされないので、vCenter Server から KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスのエンドポイントへのネットワーク接続のために、ファイアウォールや SNAT 規則を vCenter Server に構成する必要はありません。

詳しくは、[KMIP for VMware on IBM Cloud ソリューション・アーキテクチャー](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)を参照してください。

## KMIP for VMware on IBM Cloud インスタンスを削除する際の考慮事項
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

サービスを削除すると、暗号化されたバックアップを含め、KMIP for VMware on IBM Cloud サービスで保護されているすべてのデータが復号不能になります。

## 関連リンク
{: #kmip_standalone_considerations-related}

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスの注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [KMIP for VMware on IBM Cloud インスタンスの証明書の追加、表示、削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスの参照](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} インスタンスの削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker イベント](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
