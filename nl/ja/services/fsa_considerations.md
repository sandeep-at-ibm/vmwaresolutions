---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# FortiGate Security Appliance on IBM Cloud の概要

FortiGate Security Appliance on {{site.data.keyword.cloud}} サービスでは、FortiGate Security Appliance (FSA) 300 シリーズのデバイスのペアが高可用性モードでデプロイされます。これを使って、ファイアウォール、ルーティング、NAT、VPN の各サービスが提供され、ご使用のインスタンスのパブリック VLAN 上のすべてのサーバーと仮想マシンが保護されます。

このサービスの管理には、FortiOS Web Client、または SSH を介したコマンド・ライン・インターフェースを使用します。

**利用可否**: このサービスは、V1.8 以降のリリースでデプロイされたインスタンスでのみ利用可能です。

## FortiGate Security Appliance on IBM Cloud のコンポーネント

ご使用のインスタンス用に FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスを注文すると、FortiGate 300 シリーズの Security Appliance の HA ペアが元のインスタンスまたはクラスターのデフォルトのパブリック VLAN にデプロイされます。インスタンスのパブリック VLAN へのすべてのトラフィックが FortiGate Security Appliance 経由でルーティングされます。

**注:** 追加のクラスターを注文した場合、その新たに追加されたクラスターのためのパブリック VLAN には、Security Appliance の HA ペアが配置されません。

## FortiGate Security Appliance on IBM Cloud をインストールする際の考慮事項

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスをインストールする前に、以下の考慮事項を確認してください。
* 使用する {{site.data.keyword.cloud_notm}} アカウントには、**「ハードウェア・ファイアウォール」**権限が必要です。 この権限は、ご使用のインスタンスの FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスのファイアウォールのログと設定を編集したり表示したりする場合に必要になります。
* デプロイ済みのインスタンスに FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスを追加する場合は、インスタンスのパブリック VLAN に {{site.data.keyword.cloud_notm}} インフラストラクチャー上の他のファイアウォールが既に配置されていないことを確認してください。
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスをインストールすると、新しいパブリック VLAN が追加されます。
* サービスのデプロイメント中、インスタンスは一時的にインターネットにアクセスできないことがあります。
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスが正常にインストールされると、FortiGate コンソールから FSA のファイアウォール・ルールの管理と構成を行えるようになります。 IBM CloudDriver 仮想マシンや Zerto Virtual Manager などの管理コンポーネントによって開始されるアウトバウンド HTTPS (TCP ポート 443) 通信がインターネットを介して {{site.data.keyword.cloud_notm}} 上の外部管理データベースと通信できるように、FSA ファイアウォール・ルールを定義しておく必要があります。 アウトバウンド HTTPS (TCP ポート 443) 通信は、インスタンス内の管理サービス VMware NSX Edge Services Gateway (ESG) のパブリック IP アドレスから発信されます。
* 新規インスタンスの一部として FortiGate Security Appliance デバイスのペアをデプロイした場合は、インスタンスからパブリック・ネットワークへの必要なアウトバウンド通信のみを許可し、他の通信はすべて拒否するように FortiGate Security Appliance デバイスが構成されます。
* 既存のインスタンスの一部として FortiGate Security Appliance デバイスのペアをデプロイした場合は、インスタンスからパブリック・ネットワークへの必要なアウトバウンド管理通信をすべて許可する明示的ルールが FortiGate Security Appliance デバイスで構成されます。 また、既存のアプリケーション・トラフィックの妨げにならないように、他の通信をすべて許可する追加のルールが FortiGate Security Appliance デバイスで構成されます。 必要な通信のみを許可し、他の通信はすべて拒否するよう、注意して FortiGate Security Appliance 構成を管理する必要があります。

## FortiGate Security Appliance on IBM Cloud を削除する際の考慮事項

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスを削除する前に、以下の考慮事項を確認してください。
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスを削除すると、追加されたパブリック VLAN も削除されます。
* サービスの削除中、インスタンスは一時的にインターネットにアクセスできないことがあります。
* NAT トラフィックの許可、インスペクション、ブロック、ルーティングに関するすべての FortiGate ルールが、Fortinet サービスと一緒に削除されます。 何らかの NAT ルールが構成されている場合は、再構成する必要があります。

## 関連リンク

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} の注文](fsa_ordering.html)
* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} の管理](managingfsa.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet Web サイト](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
