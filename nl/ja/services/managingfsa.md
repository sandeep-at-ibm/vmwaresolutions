---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Security Appliance on IBM Cloud の管理

FortiGate Security Appliance on {{site.data.keyword.cloud}} サービスが正常にインストールされると、FortiGate コンソールから FSA のファイアウォール・ルールの管理と構成を行えるようになります。

インターネットを介して {{site.data.keyword.cloud_notm}} インフラストラクチャー上の外部管理データベースと通信するために、Zerto Virtual Manager などの管理コンポーネントによって開始されるアウトバウンド HTTPS (TCP ポート 443) 通信を許可するように、FSA ファイアウォール・ルールを定義する必要があります。 アウトバウンド HTTPS (TCP ポート 443) 通信は、インスタンス内の管理サービス VMware NSX Edge Services Gateway (ESG) のパブリック IP アドレスから発信されます。
{:important}

## FortiGate 300 シリーズ・コンソールへのアクセス

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスを管理するには、以下のいずれかの方法で FortiGate® 300 シリーズのコンソールにアクセスする必要があります。
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスの詳細ページにある資格情報を使用して、FortiOS Web Client にログインします。
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスの詳細ページにある資格情報を使用して、SSH 接続を介してコンソールにアクセスします。

詳しくは、以下のトピックを参照してください。
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)

### 関連リンク

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services/fsa_considerations.html)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [よくある質問](/docs/services/vmwaresolutions/vmonic/faq.html)
* [fortinet.com Web サイト](https://www.fortinet.com/)
* [Fortinet 技術資料](http://docs.fortinet.com/fortigate/admin-guides)
