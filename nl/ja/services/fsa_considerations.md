---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: FortiGate security, FortiGate Sirtual Appliance, tech specs FortiGate

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Security Appliance on IBM Cloud の概要
{: #fsa_considerations}

FortiGate Security Appliance on {{site.data.keyword.cloud}} サービスでは、FortiGate Security Appliance (FSA) 300 シリーズのデバイスのペアが高可用性モードでデプロイされます。これを使って、ファイアウォール、ルーティング、NAT、VPN の各サービスが提供され、ご使用のインスタンスのパブリック VLAN 上のすべてのサーバーと仮想マシンが保護されます。

このサービスの管理には、FortiOS Web Client、または SSH を介したコマンド・ライン・インターフェースを使用します。

このサービスは、V1.8 以降のリリースでデプロイされたインスタンスでのみ利用可能です。
{:note}

## FortiGate Security Appliance on IBM Cloud の技術仕様
{: #fsa_considerations-specs}

以下のコンポーネントが注文され、FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### ハードウェア
{: #fsa_considerations-hardware}

FortiGate 300 シリーズの Security Appliance。

### 高可用性
{: #fsa_considerations-ha}

アクティブ-パッシブ構成で、2 つのアプライアンスがデプロイされます。

### ネットワーキング
{: #fsa_considerations-networking}

* アップストリームとダウンストリームの両方のネットワークに結合された Dual 1 GbE
* 1 つの新しいアップストリーム {{site.data.keyword.cloud_notm}} パブリック VLAN
* 1 つの既存のダウンストリーム {{site.data.keyword.cloud_notm}} パブリック VLAN

## FortiGate Security Appliance on IBM Cloud をインストールする際の考慮事項
{: #fsa_considerations-install}

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスをインストールする前に、以下の考慮事項を確認してください。
* 使用する {{site.data.keyword.cloud_notm}} アカウントには、**「ハードウェア・ファイアウォール」**権限が必要です。 この権限は、ご使用のインスタンスの FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスのファイアウォールのログと設定を編集したり表示したりする場合に必要になります。
* デプロイ済みのインスタンスに FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスを追加する場合は、インスタンスのパブリック VLAN に {{site.data.keyword.cloud_notm}} インフラストラクチャー上の他のファイアウォールが既に配置されていないことを確認してください。
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスをインストールすると、新しいパブリック VLAN が追加されます。
* サービスのデプロイメント中、インスタンスは一時的にインターネットにアクセスできないことがあります。
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスが正常にインストールされると、FortiGate コンソールから FSA のファイアウォール・ルールの管理と構成を行えるようになります。 Zerto Virtual Manager などの管理コンポーネントによって開始されるアウトバウンド HTTPS (TCP ポート 443) 通信がインターネットを介して {{site.data.keyword.cloud_notm}} 上の外部管理データベースと通信できるように、FSA ファイアウォール・ルールを定義しておく必要があります。 アウトバウンド HTTPS (TCP ポート 443) 通信は、インスタンス内の管理サービス VMware NSX Edge Services Gateway (ESG) のパブリック IP アドレスから発信されます。
* 必要な通信のみを許可し、他の通信はすべて拒否するよう、注意して FortiGate Security Appliance 構成を管理する必要があります。
* 追加のクラスターを注文した場合、その新たに追加されたクラスターのためのパブリック VLAN には、Security Appliance の HA ペアが配置されません。

## FortiGate Security Appliance on IBM Cloud を削除する際の考慮事項
{: #fsa_considerations-remove}

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスを削除する前に、以下の考慮事項を確認してください。
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスを削除すると、追加されたパブリック VLAN も削除されます。
* サービスの削除中、インスタンスは一時的にインターネットにアクセスできないことがあります。
* NAT トラフィックの許可、インスペクション、ブロック、ルーティングに関するすべての FortiGate ルールが、Fortinet サービスと一緒に削除されます。 何らかの NAT ルールが構成されている場合は、再構成する必要があります。

## 関連リンク
{: #fsa_considerations-related}

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} の注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Fortinet Web サイト](https://www.fortinet.com/){:external}
* [Fortinet Document Library](https://docs.fortinet.com/product/fortigate/6.2){:external}
