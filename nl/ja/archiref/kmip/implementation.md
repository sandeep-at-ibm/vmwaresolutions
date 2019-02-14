---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware の実装と管理

**注**: このリリースでは、KMIP for VMware on {{site.data.keyword.cloud_notm}} は vSphere 暗号化のみに限定されています。

## 鍵管理サーバーの接続

KMIP for VMware on {{site.data.keyword.cloud_notm}} を使用して vSphere 暗号化または vSAN 暗号化を有効にするには、以下の作業を実行する必要があります。

1. [アカウントのサービス・エンドポイントを有効にします](/docs/services/service-endpoint/enable-servicepoint.html#getting-started)。
2. [IBM Key Protect](/docs/services/key-protect/index.html) インスタンスを作成します。
3. IBM Key Protect の中にカスタマー・ルート鍵 (CRK) を作成します。
4. KMIP for VMware に使用する Identity and Access Management (IAM) の[サービス ID と API キー](/docs/iam/serviceid_keys.html)を作成します。 このサービス ID に、Key Protect インスタンスに対するプラットフォームのビューアー・アクセス権限とサービスの書き込みアクセス権限を付与します。
5. {{site.data.keyword.cloud_notm}} カタログから [KMIP for VMware](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html) インスタンスを作成します。
6. VMware vCenter で、2 つのサーバーで構成される鍵管理サーバー (KMS) クラスターを作成します。サーバーは、選択した領域内の KMIP for VMware エンドポイント 1 つにつき 1 つです。
7. VMware の方式の 1 つを選択して、vCenter 内に KMS クライアント証明書を生成するかインストールします。
8. その証明書のパブリック・バージョンをエクスポートし、許可されたクライアントの証明書として KMIP for VMware インスタンスに構成します。

## 暗号化の有効化

vSAN 暗号化を使用するには、vCenter クラスターの vSAN の一般設定を編集し、暗号化のチェック・ボックスを選択します。

vSphere 暗号化を使用するには、仮想マシンのストレージ・ポリシーを編集し、ディスクの暗号化を必須にします。

## 鍵のローテーション

{{site.data.keyword.cloud_notm}} コンソールまたは API を使用して、
[Key Protect のカスタマー・ルート鍵 (CRK) のローテーション](/docs/services/key-protect/rotate-keys.html)を行います。

VMware vSAN 暗号化の場合は、vCenter クラスターの vSAN の一般設定で、VMware の鍵暗号化鍵 (KEK) およびオプションでデータ暗号化鍵 (DEK) のローテーションを行います。

VMware vSphere 暗号化の場合は、PowerShell コマンド **Set-VMEncryptionKey** を使用して、VMware の KEK および DEK (オプション) のローテーションを行います。

## 鍵の無効化

選択した CRK を Key Protect から削除することで、KMIP for VMware で使用しているすべての鍵を無効にすることができます。

鍵を無効にするという方法により、無効にした鍵および KMIP for VMware インスタンスで保護されていたすべてのデータが暗号的に廃棄されます。 ESXi ホストの稼働中は VMware が一部の鍵を保護するので、確実にすべての暗号化データを使用させないようにするには、vSphere クラスターを再始動する必要があります。
{:important}

KMIP for VMware は、VMware に認識されている鍵 ID に関連付けられている名前を使用して、ラップされた KEK を Key Protect インスタンスに個々に保管します。 個々の鍵を削除すると、個々のディスクまたはドライブの暗号化を無効にすることができます。

暗号化ディスクを持つ VM をインベントリーから削除しても、VMware は KMS から鍵を削除しません。 これは、その VM をバックアップからリカバリーしたり、インベントリーにリストアしたりできるようにするためです。 これらの鍵を再利用しつつ、すべてのバックアップを暗号的に無効にする場合は、VM を削除した後に鍵を Key Protect から削除する必要があります。
{:note}

### 関連リンク

* [ソリューションの概要](/docs/services/vmwaresolutions/archiref/kmip/overview.html)
* [ソリューションの設計](/docs/services/vmwaresolutions/archiref/kmip/design.html)
* [IBM Key Protect](/docs/services/key-protect/index.html)
