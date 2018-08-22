---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}

# IBM Cloud for VMware Solutions の概説
{: #gettingstarted}

{{site.data.keyword.vmwaresolutions_full}} コンソールは、デプロイメントの注文と管理を行うインターフェースです。 コンソールでは、各デプロイメントがインスタンスとして管理されます。 このコンソールは、{{site.data.keyword.slportal}}とは別のスタンドアロンのユーザー・インターフェースです。

## 始める前に

{{site.data.keyword.vmwaresolutions_short}} での作業を始める前に、ブラウザーの要件とユーザー・アカウントに関する重要な情報を確認してください。

### ブラウザーと解像度の要件

以下のブラウザーがサポートされています。
*  Mozilla Firefox
*  Google Chrome
*  Apple Safari

**注**: Microsoft Internet Explorer はサポートされていません。

{{site.data.keyword.vmwaresolutions_short}} コンソールの表示と操作を最適化するために、画面解像度を幅 1024 ピクセル以上、高さ 500 ピクセル以上に設定してください。

### IBMid

**IBMid** を使用すると、1 つのログイン・ユーザー名を、{{site.data.keyword.cloud_notm}} など、お客様が使用する IBM のすべての製品およびサービスに使用できます。 {{site.data.keyword.vmwaresolutions_short}} は、{{site.data.keyword.cloud_notm}} カタログの中でインフラストラクチャー・ソリューションとして提供されています。 したがって、{{site.data.keyword.vmwaresolutions_short}} コンソールにアクセスするには、**IBMid** が必要です。

**IBMid** を使用して {{site.data.keyword.vmwaresolutions_short}} コンソールにログインするために、{{site.data.keyword.cloud_notm}} アカウントに **IBMid** を関連付ける必要があります。 コンソールに初めてログインするときに、既存の **IBMid** を {{site.data.keyword.cloud_notm}} アカウントに関連付けるか、**IBMid** に自動的に関連付けられる新規 {{site.data.keyword.cloud_notm}} アカウントを登録するように指示されます。 このプロセスを行う必要があるのは 1 回だけです。

**IBMid** と {{site.data.keyword.cloud_notm}} アカウントの関連付けに問題がある場合は、[{{site.data.keyword.cloud_notm}} へのアクセスに関するトラブルシューティング](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html)を参照してください。

### IBM Cloud アカウント

{{site.data.keyword.cloud_notm}} アカウントは、IBM Cloud サービスの注文および使用に必要です。請求情報は IBM Cloud アカウントに関連付けられています。したがって、{{site.data.keyword.vmwaresolutions_short}} のデプロイメント・オファリングを注文および使用するには、{{site.data.keyword.cloud_notm}} アカウントが必要です。物理インフラストラクチャーと仮想インフラストラクチャーのコスト、最終的に使用されたライセンスは、{{site.data.keyword.cloud_notm}} アカウントに請求されます。 {{site.data.keyword.cloud_notm}} アカウントが満たす必要のある要件について詳しくは、[{{site.data.keyword.cloud_notm}} アカウントの要件](vmonic/slaccountrequirement.html)を参照してください。

### IBM Cloud インフラストラクチャー (SoftLayer) アカウント

{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントは、以前は IBM SoftLayer アカウントと呼ばれていました。

{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントと {{site.data.keyword.cloud_notm}} アカウントをリンクして、Infrastructure as a Service (IaaS) リソースと Platform as a Service (PaaS) リソースを組み合わせて使用できます。その後、単一のログインから IaaS リソースと PaaS リソースにアクセスできます。 さらに、アカウントをリンクする場合は、使用するすべての PaaS リソースおよび IaaS リソースに対して単一の請求書が提供されます。 

* {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントがない場合は、[IBM Cloud インフラストラクチャー (SoftLayer) アカウントの登録](../vmonic/signing_softlayer_account.html)の手順に従ってアカウントを要求し、[IBMid アカウントのリンク](https://console.bluemix.net/docs/account/softlayerlink.html)の手順に従って {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントとご使用の {{site.data.keyword.cloud_notm}} アカウントをリンクします。
* すでに {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントを持っている場合は、それを [IBMid アカウントのリンク](https://console.bluemix.net/docs/account/softlayerlink.html)の手順に従って {{site.data.keyword.cloud_notm}} アカウントにリンクします。

## IBM Cloud for VMware Solutions コンソールへのアクセス

{{site.data.keyword.cloud_notm}} カタログからコンソールにアクセスするには、[{{site.data.keyword.vmwaresolutions_short}} コンソールへのアクセス](vmonic/loginmethod.html)を参照してください。

### 関連リンク

* [{{site.data.keyword.vmwaresolutions_short}} について](vmonic/prod_overview.html)
* [Cloud Foundation の概要](sddc/sd_cloudfoundationoverview.html)
* [vCenter Server の概要](vcenter/vc_vcenterserveroverview.html)
* [Fortinet on IBM Cloud](services/fsa_considerations.html)
* [Veeam on IBM Cloud](services/veeam_considerations.html)
* [Zerto on IBM Cloud](services/addingzertodr.html)
