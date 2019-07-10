---

copyright:

  years: 2016, 2019

lastupdated: "2019-05-31"

keywords: user IDs vCenter, PSC user, user ID service

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM ユーザー ID
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_short}} では、VMware インスタンスにホスト、クラスター、ストレージを追加するなどの操作をお客様が行った場合に {{site.data.keyword.cloud_notm}} の自動化機能で使用するために、お客様のアカウント内に一連のユーザーが維持されます。 お客様のアカウント内のユーザーは、{{site.data.keyword.cloud_notm}} サービスの自動化機能によるサービスのインストールと構成にも使用できます。以下のセクションで、{{site.data.keyword.cloud_notm}} の自動化機能のユーザー ID について説明します。

これらの IBM ユーザー ID が削除または無効化された場合、あるいはそのパスワードが変更された場合、VMware インスタンスの操作は失敗します。
{:important}

## vCenter および Platform Services Controller のユーザー ID
{: #audit_user_ids-vcenter-psc}

V2.5 以降、{{site.data.keyword.vmwaresolutions_short}} では、以下の ID を使用して、デフォルトで埋め込まれる ID ソースが vCenter に追加されます。

表 1. vCenter および Platform Services Controller のユーザー ID

| ユーザー     | ユーザー ID      | 方法 | 説明 |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | VMware 構成 (VMware 高可用性のセットアップや分散スイッチの作成など) に使用されます。 デプロイメント後に、vCenter Server のプライマリー・インスタンスとセカンダリー・インスタンスをペアにするために使用されます。 |
| お客様 | customerroot | SSH    | お客様専用に作成されます。 |
| IBM      | automation@``root_domain``<br/>(Active Directory ユーザー) | HTTP | デプロイメント後に、ホストとクラスターの追加/削除、およびアドオン・サービスの仮想マシンのデプロイと構成を行うために使用されます。 |
| お客様 | Administrator@vsphere.local | HTTP | お客様専用に作成されます。 |

HTTP は、vCenter のセットアップと構成のほかに、VMware の操作 (vCenter のリソース管理におけるホスト、クラスター、ストレージの追加など) にも使用されます。
{:note}

## NSX Manager のユーザー ID
{: #audit_user_ids-nsx-mgr}

表 2. NSX Manager のユーザー ID

| ユーザー     | ユーザー ID      | 説明 |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(Active Directory ユーザー) | デプロイメント後に、NSX VTEP の IP アドレスの管理、ホストとクラスターの追加/削除時のホストとクラスターの構成の管理、アドオン・サービス (パブリック・ネットワーク・アクセスを使用してライセンス交付、アクティベーション、使用状況報告を行う必要があるもの) のための ESG 構成の管理を行うために使用されます。 |
| お客様 | Admin        | お客様専用に作成されます。 |

## ESXi ホストのユーザー ID
{: #audit_user_ids-esxi}

表 3. ESXi ホストのユーザー ID

| ユーザー     | ユーザー ID      | 説明 |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | デプロイメント後に、NFS ストレージの追加、追加ストレージのルートの構成、すべてのサーバー検証コードの実行のために使用されます。 |
| お客様 | root         | お客様専用に作成されます。 |

## Microsoft Active Directory のユーザー ID
{: #audit_user_ids-ad}

表 4. Active Directory のユーザー ID

| ユーザー     | ユーザー ID       | 説明 |
|:---------|:------------- |:------------|
| IBM      | automation    | ホストの追加、サービスの仮想マシンの追加、および Active Directory と DNS エントリーのセットアップに使用されます。 |
| お客様 | 管理者 | お客様専用に作成されます。 |

## サービス・ユーザー ID
{: #audit_user_ids-services}

表 5. サービス・ユーザー ID

| ユーザー ID                                    | 説明 |
|:-------------------------------------------|:----------- |
| prod-BigIP-``dynamic_ID``-@``domain name`` | F5 on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-Caveonix-``dynamic_ID``-@``domain name`` | Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-Fortigate-``dynamic_ID``-@``domain name`` | FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-FortigateVM-``dynamic_ID``-@``domain name`` | FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-HyTrustCC-``5_letter_ID``-@``domain name`` | HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-HyTrustDC-``5_letter_ID``-@``domain name`` | HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-HyTrustKC-``5_letter_ID``-@``domain name`` | HyTrust KeyControl on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-KMIPAdapter-``dynamic_ID``-@``domain name`` | KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-ICP-``dynamic_ID``-@``domain name`` | {{site.data.keyword.cloud_notm}} Private Hosted サービスのインストールと構成に使用します。 |
| prod-SPPlus-``dynamic_ID``-@``domain name`` | IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-Veeam-``dynamic_ID``-@``domain name`` | Veeam on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-HCX-``dynamic_ID``-@``domain name`` | VMware HCX on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |
| prod-Zerto-``dynamic_ID``-@``domain name`` | Zerto on {{site.data.keyword.cloud_notm}} サービスのインストールと構成に使用します。 |

動的 ID の長さは 8 文字から 10 文字です。
{:note}

## 関連リンク
{: #audit_user_ids-related}

* [vCenter Server 成果物の変更に関する考慮事項](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker イベント](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
