---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# KMIP for VMware on IBM Cloud の概要

KMIP for VMware on {{site.data.keyword.cloud}} サービスは、{{site.data.keyword.cloud_notm}} 内の VMware によって使用される暗号鍵を管理するための、24 時間 365 日の高可用性サービスを提供します。 このサービスは、お客様が暗号鍵を作成、取得、有効化、取り消し、破棄できるようにするランタイム機能を提供します。また、クライアントの資格情報と暗号鍵の関連付けを管理する管理機能も提供します。

**利用可否**: このサービスは、V2.2 以降のリリースでデプロイされたインスタンスでのみ利用可能です。

## KMIP for VMware on IBM Cloud をインストールする際の考慮事項

KMIP for VMware on {{site.data.keyword.cloud_notm}} は、IBM Key Protect for IBM Cloud サービスを使用して暗号鍵を作成、暗号化、復号します。 そのため、サービスをインストールする前に、使用可能な Key Protect サービスを注文しておいてください。 一方、[サービス ID の作成](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id)で示されているステップを実行すると {{site.data.keyword.cloud_notm}} サービス ID が作成されるので、それを使用して、作成した Key Protect サービス・インスタンスにアクセスできます。

サービス ID に対して以下のアクセス・レベルを付与しておく必要があります。
* プラットフォーム・アクセス・レベル: IBM Key Protect インスタンスに対する Viewer 権限
* サービス・アクセス・レベル: IBM Key Protect インスタンスに対する Writer 権限

サービスを注文する際に、作成したサービス ID の API 鍵が必要になります。

サービスは、カスタマー・ルート鍵 (CRK) が少なくとも 1 つ既に作成されていることを前提としています。この CRK は、[ルート鍵の作成](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys)に示されているステップに従って Key Protect ユーザー・インターフェースから作成されたものであるか、または [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect) の RESTful API を使用して作成されたものでなければなりません。

CRK がなければサービスを注文することはできません。 既存の鍵素材を使用して CRK を作成するという方法を使用するとともに、作成している鍵素材のバックアップを取ることを強くお勧めします。 そうすれば、CRK の保管のために IBM Key Protect を適用しているデータ・センターの機能が障害によって完全に失われたとしても、鍵をリカバリーできるようになります。

## KMIP for VMware on IBM Cloud を使用する際の考慮事項

* 注文した KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスを VMware vCenter Server に登録された鍵管理サーバー (KMS) として使用するには、vCenter Server から注文済み KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのエンドポイントへのネットワーク接続が機能するように構成しておく必要があります。
* VMware vSAN 暗号化にサービスを使用するには、ターゲット vSAN 上のホストと注文済み KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのエンドポイントの間のネットワーク接続が機能するようにしておく必要があります。


## KMIP for VMware on IBM Cloud を削除する際の考慮事項

サービスの注文時または使用時に指定した VMware パブリック証明書が、サービス・インスタンスと通信するためのクライアント証明書として使用されます。サービスを削除すると、このサービス・インスタンスによって作成された、関連する VMware パブリック証明書用のすべての暗号鍵も一緒に削除されます。

したがって、サービスを削除する前に、KMIP サービスによって作成された鍵を使用して暗号化されている仮想マシンも vSAN もないことを確認する必要があります。

## 関連リンク

* [KMIP for VMware on IBM Cloud の注文](kmip_ordering.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere セキュリティについて](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [FAQ](../vmonic/faq.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
