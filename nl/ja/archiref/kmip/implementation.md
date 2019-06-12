---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware の実装と管理
{: #kmip-implementation}

## 鍵管理サーバーの接続
{: #kmip-implementation-connecting-kms}

KMIP for VMware on {{site.data.keyword.cloud_notm}} を使用して vSphere 暗号化または vSAN 暗号化を有効にするには、以下の作業を実行する必要があります。

1. [IBM Cloud CLI を使用してアカウントでサービス・エンドポイントを使用できるようにします](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)。
2. [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial) または [IBM Cloud Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started) を使用して鍵マネージャー・インスタンスを作成します。 Hyper Protect Crypto Services を使用している場合は、Hyper Protect Crypto Services が鍵関連機能を提供できるようにするため、必ず[暗号インスタンスを初期化](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm)します。
3. 鍵マネージャー・インスタンスの中にカスタマー・ルート鍵 (CRK) を作成します。
4. KMIP for VMware に使用する Identity and Access Management (IAM) の[サービス ID と API キー](/docs/iam?topic=iam-serviceidapikeys)を作成します。 このサービス ID に、鍵マネージャー・インスタンスに対するプラットフォームのビューアー・アクセス権限とサービスの書き込みアクセス権限を付与します。
5. {{site.data.keyword.cloud_notm}} カタログから [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering) インスタンスを作成します。
6. VMware vCenter で、2 つのサーバーで構成される鍵管理サーバー (KMS) クラスターを作成します。サーバーは、選択した領域内の KMIP for VMware エンドポイント 1 つにつき 1 つです。
7. VMware の方式の 1 つを選択して、vCenter 内に KMS クライアント証明書を生成するかインストールします。
8. その証明書のパブリック・バージョンをエクスポートし、許可されたクライアントの証明書として KMIP for VMware インスタンスに構成します。

## 暗号化の有効化
{: #kmip-implementation-enable-encrypt}

vSAN 暗号化を使用するには、vCenter クラスターの vSAN の一般設定を編集し、暗号化のチェック・ボックスを選択します。

vSAN ヘルス・チェックを実行する時に、1 つ以上の vSphere ホストから KMS クラスターに接続できないという警告が周期的に出されることがあります。 こうした警告が出されるのは、vSAN ヘルス・チェックの接続が短時間でタイムアウトになる場合です。 このような警告は無視してかまいません。 詳しくは、[vSAN KMS Health Check intermittently fails with SSL Handshake Timeout error](https://kb.vmware.com/s/article/67115){:new_window} を参照してください。
{:note}

vSphere 暗号化を使用するには、仮想マシンのストレージ・ポリシーを編集し、ディスクの暗号化を必須にします。

## 鍵のローテーション
{: #kmip-implementation-key-rotation}

{{site.data.keyword.cloud_notm}} コンソールまたは API を使用して、[Key Protect](/docs/services/key-protect?topic=key-protect-rotate-keys#rotate-keys) または [Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-rotating-keys) のカスタマー・ルート鍵 (CRK) のローテーションを行います。

VMware vSAN 暗号化の場合は、vCenter クラスターの vSAN の一般設定で、VMware の鍵暗号化鍵 (KEK) およびオプションでデータ暗号化鍵 (DEK) のローテーションを行います。

VMware vSphere 暗号化の場合は、PowerShell コマンド **Set-VMEncryptionKey** を使用して、VMware の KEK および DEK (オプション) のローテーションを行います。

## 鍵の無効化
{: #kmip-implementation-key-revocation}

選択した CRK を鍵マネージャーから削除することで、KMIP for VMware で使用しているすべての鍵を無効にすることができます。

鍵を無効にするという方法により、無効にした鍵および KMIP for VMware インスタンスで保護されていたすべてのデータが暗号的に廃棄されます。 ESXi ホストの稼働中は VMware が一部の鍵を保護するので、確実にすべての暗号化データを使用させないようにするには、vSphere クラスターを再始動する必要があります。
{:important}

KMIP for VMware は、VMware に認識されている鍵 ID に関連付けられている名前を使用して、ラップされた KEK を Key Protect インスタンスまたは Hyper Protect Crypto Services インスタンスに個々に保管します。 個々の鍵を削除すると、個々のディスクまたはドライブの暗号化を無効にすることができます。

暗号化ディスクを持つ VM をインベントリーから削除しても、VMware は KMS から鍵を削除しません。 これは、その VM をバックアップからリカバリーしたり、インベントリーにリストアしたりできるようにするためです。 これらの鍵を再利用しつつ、すべてのバックアップを暗号的に無効にする場合は、VM を削除した後に鍵を鍵マネージャー・インスタンスから削除する必要があります。
{:note}

## 関連リンク
{: #kmip-implementation-related}

* [ソリューションの概要](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)
* [ソリューションの設計](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)
* [IBM Cloud Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started#get-started)
