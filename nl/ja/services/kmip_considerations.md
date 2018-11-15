---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud の概要

KMIP for VMware on {{site.data.keyword.cloud}} サービスは、{{site.data.keyword.cloud_notm}} 内の VMware によって使用される暗号鍵を管理するための、24 時間 365 日の高可用性サービスを提供します。 このサービスは、お客様が暗号鍵を作成、取得、活動化、取り消し、破棄できるようにするランタイム機能を提供します。 また、クライアントの資格情報と暗号鍵の関連付けを管理する管理機能も提供します。

このサービスは、V2.2 以降でデプロイされたインスタンスでのみ利用可能です。
{:note}

## KMIP for VMware on IBM Cloud の技術仕様

以下の仕様が KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスに含まれています。

* VMware と互換性のある Key Management Interoperability Protocol (KMIP)
* マネージド・サービス
* 世界各地にある複数の地理的領域で利用可能
* 各領域にある可用性の高い KMIP サービス・エンドポイント

## KMIP for VMware on IBM Cloud をインストールする際の考慮事項

KMIP for VMware on {{site.data.keyword.cloud_notm}} は、IBM Key Protect for {{site.data.keyword.cloud_notm}} サービスを使用して暗号鍵を作成、暗号化、復号します。 そのため、KMIP for VMware on {{site.data.keyword.cloud_notm}} をインストールする前に、以下を確認してください。
* 使用可能な Key Protect サービスを注文したこと。
* [サービス ID の作成](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id)で示されているステップに従って {{site.data.keyword.cloud_notm}} サービス ID が作成されたこと。 このサービス ID を使用して、作成した Key Protect サービス・インスタンスにアクセスできます。
* サービス ID に以下のアクセス・レベルを付与したこと。
   * プラットフォーム・アクセス・レベル: IBM Key Protect インスタンスに対する Viewer 権限
   * サービス・アクセス・レベル: IBM Key Protect インスタンスに対する Writer 権限
* 作成されたサービス ID の API 鍵を所持していること。 その鍵は、サービスを注文する際に必要になります。
* 少なくとも 1 つのカスタマー・ルート鍵 (CRK) を作成したこと。この CRK は、[ルート鍵の作成](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys)に示されているステップに従って Key Protect ユーザー・インターフェースから作成したものであるか、または [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect) の REST API を使用して作成したものでなければなりません。

   **重要:** CRK がなければサービスを注文することはできません。 既存の鍵素材を使用して CRK を作成するという方法を使用すると共に、作成している鍵素材のバックアップを取ることを強くお勧めします。 これにより、CRK の保管のために IBM Key Protect を適用しているデータ・センターの機能が障害によって失われた場合に、鍵をリカバリーできるようになります。

## KMIP for VMware on IBM Cloud を使用する際の考慮事項

* 注文した KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスを VMware vCenter Server に登録された鍵管理サーバー (KMS) として使用するには、vCenter Server から注文済み KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのエンドポイントへのネットワーク接続が機能することを確認してください。
* VMware vSAN 暗号化にサービスを使用するには、ターゲット vSAN 上のホストと注文済み KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのエンドポイントの間のネットワーク接続が機能することを確認してください。

## KMIP for VMware on IBM Cloud を削除する際の考慮事項

サービスの注文時または使用時に指定した VMware パブリック証明書が、サービス・インスタンスと通信するためのクライアント証明書として使用されます。 サービスを削除すると、このサービス・インスタンスによって作成された、関連する VMware パブリック証明書用のすべての暗号鍵も削除されます。

したがって、サービスを削除する前に、KMIP サービスによって作成された鍵を使用して暗号化されている仮想マシンも vSAN もないことを確認してください。

### 関連リンク

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} の注文](kmip_ordering.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere セキュリティについて](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [FAQ](../vmonic/faq.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
