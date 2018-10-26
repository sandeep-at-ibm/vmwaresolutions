---

copyright:

  years: 2016, 2018

lastupdated: "2018-09-07"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# IBM Cloud for VMware Solutions の概説

この概説チュートリアルでは、インスタンスおよびそれに使用するいくつかのアドオン・サービスを注文するプロセスについて説明します。
{:shortdesc}

## 始める前に
{: #prereqs}

{{site.data.keyword.vmwaresolutions_full}} での作業を始める前に、ブラウザー要件、ユーザー・アカウント、デプロイメント・オプション、およびアドオン・サービスに関する以下の重要な情報を確認してください。

### ブラウザー要件

以下のブラウザーがサポートされています。
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

**注**: Microsoft Internet Explorer はサポートされていません。

{{site.data.keyword.vmwaresolutions_short}} コンソールの表示と操作を最適化するために、画面解像度を幅 1024 ピクセル以上、高さ 500 ピクセル以上に設定してください。

### ユーザー・アカウント

{{site.data.keyword.cloud_notm}} アカウントおよび {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントが必要です。 これらのアカウントは特定の要件を満たしている必要があります。

   表 1. 必要なユーザー・アカウント
   <table>
   <tr>
      <th>アカウント</th>
      <th>説明</th>
   </tr>
   <tr>
      <td>IBMid</td>
      <td>**IBMid** を使用すると、1 つのログイン・ユーザー名を、{{site.data.keyword.cloud_notm}} など、お客様が使用する IBM のすべての製品およびサービスに使用できます。 {{site.data.keyword.vmwaresolutions_short}} は、{{site.data.keyword.cloud_notm}} カタログの中でインフラストラクチャー・ソリューションとして提供されています。 {{site.data.keyword.vmwaresolutions_short}} コンソールにアクセスするには、**IBMid** が必要です。<br><br>**IBMid** を使用して {{site.data.keyword.vmwaresolutions_short}} コンソールにログインするために、{{site.data.keyword.cloud_notm}} アカウントに **IBMid** を関連付ける必要があります。 コンソールに初めてログインするときに、既存の **IBMid** を {{site.data.keyword.cloud_notm}} アカウントに関連付けるか、新規 {{site.data.keyword.cloud_notm}} アカウントを登録するように指示されます。 新規 {{site.data.keyword.cloud_notm}} アカウントは **IBMid** に自動的に関連付けられます。 このプロセスを行う必要があるのは 1 回だけです。<br><br>**IBMid** と {{site.data.keyword.cloud_notm}} アカウントの関連付けに問題がある場合は、[{{site.data.keyword.cloud_notm}} へのアクセスに関するトラブルシューティング](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html)を参照してください。</td>
   </tr>
   <tr>
      <td>IBM Cloud アカウント</td>
      <td>{{site.data.keyword.cloud_notm}} サービスを注文および使用するには、{{site.data.keyword.cloud_notm}} アカウントが必要です。 請求情報は {{site.data.keyword.cloud_notm}} アカウントに関連付けられています。 物理インフラストラクチャーと仮想インフラストラクチャーのコスト、最終的に使用されたライセンスは、{{site.data.keyword.cloud_notm}} アカウントに請求されます。</td>
   </tr>
   <tr>
      <td>IBM Cloud インフラストラクチャー (SoftLayer) アカウント</td>
      <td>{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントは、以前は IBM SoftLayer アカウントと呼ばれていました。  アカウントが満たす必要のある要件について詳しくは、[{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの要件](vmonic/slaccountrequirement.html)を参照してください。<br><br>{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントと {{site.data.keyword.cloud_notm}} アカウントをリンクして、Infrastructure as a Service (IaaS) リソースと Platform as a Service (PaaS) リソースを組み合わせて使用できます。 その後、単一のログインから IaaS リソースと PaaS リソースにアクセスできます。 さらに、アカウントをリンクする場合は、使用するすべての PaaS リソースおよび IaaS リソースに対して単一の請求書が提供されます。<ul><li>{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントがない場合は、[IBM Cloud インフラストラクチャー (SoftLayer) アカウントの登録](vmonic/signing_softlayer_account.html)の手順に従ってアカウントを要求し、[IBMid アカウントのリンク](https://console.bluemix.net/docs/account/softlayerlink.html)の手順に従って {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントとご使用の {{site.data.keyword.cloud_notm}} アカウントをリンクします。</li><li>{{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントを持っている場合は、それを [IBMid アカウントのリンク](https://console.bluemix.net/docs/account/softlayerlink.html)の手順に従って {{site.data.keyword.cloud_notm}} アカウントにリンクします。</li></ul></td>
   </tr>
   </table>

詳しくは、以下のトピックを参照してください。
* [必要なアカウントの登録](vmonic/signing_softlayer_account.html)
* [{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの要件](vmonic/slaccountrequirement.html)

### デプロイメント・オファリング

デプロイメント・オファリングを確認して選択します。

  表 2. デプロイメント・オファリング
  <table>
    <tr>
       <th>デプロイメント・オファリング</th>
       <th>説明</th>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud](vcenter/vc_vcenterserveroverview.html)</td>
       <td>この vCenter Server オファリングでは、ビジネス・ニーズに最適なカスタムのコンピュート、ストレージ、ネットワークのリソースを使用して、VMware 仮想環境をデプロイできます。</td>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud with Hybridity Bundle](vcenter/vc_hybrid_overview.html)</td>
       <td>この vCenter Server with Hybridity オファリングは、オンプレミスのインフラストラクチャーを素早く簡単にクラウドに拡張できるホステッド・プライベート・クラウドです。 この VMware 環境は、IBM 提供の VMware Software Defined Data Center ライセンスに基づくものであり、VMware Hybrid Cloud Extension (HCX) が含まれています。 HCX を使用すると、オンプレミスの vSphere 5.0+ 環境と {{site.data.keyword.cloud_notm}} サイトを安全に接続して、インフラストラクチャーのシームレスなハイブリッド化と真のアプリケーション・モビリティーを実現できます。</td>
    </tr>
    <tr>
       <td>[VMware Cloud Foundation on IBM Cloud](sddc/sd_cloudfoundationoverview.html)</td>
       <td>この Cloud Foundation オファリングでは、標準的な {{site.data.keyword.cloud_notm}} コンピュート、ストレージ、ネットワークのリソースを各ユーザー・デプロイメントに専用で使用して、統一された VMware 仮想環境を実現できます。</td>
    </tr>
    <tr>
       <td>[VMware vSphere on IBM Cloud](vsphere/vs_vsphereclusteroverview.html)</td>
       <td>この vSphere on {{site.data.keyword.cloud_notm}} オファリングで提供されるカスタマイズ可能な仮想化サービスを使用すると、VMware 互換の{{site.data.keyword.baremetal_short}}、ハードウェア・コンポーネント、ライセンスを組み合わせて、IBM でホストされる独自の VMware 環境を構築できます。</td>
    </tr>
    <tr>
       <td>[NetApp  ONTAP  Select](netapp/np_netappoverview.html)</td>
       <td>NetApp ONTAP Select オファリングでは、NetApp ONTAP Select をベースとする可用性の高い専用ストレージ・アプライアンスを必要とするニーズに対応するソフトウェア定義ストレージ・クラスターをデプロイできます。</td>
    </tr>
    <tr>
       <td>[VMware Federal on IBM Cloud](vcenter/vc_fed_overview.html)</td>
       <td>VMware Federal on {{site.data.keyword.cloud_notm}} のオファリングでは、基本 vCenter Server インスタンスを注文できるだけでなく、デプロイしたインスタンスを保護する (つまり、機密情報を削除し、インスタンスに継続的にアクセスして管理機能を操作することが可能になる開いた状態の管理接続を除去する) ためのオプションも用意されています。</td>
    </tr>
  </table>

### アドオン・サービス

デプロイメント・オファリングのアドオン・サービスを確認して選択します。

  表 3. デプロイメント・オファリングで使用可能なアドオン・サービス
  <table>
    <tr>
       <th>サービス名</th>
       <th>説明</th>
    </tr>
    <tr>
       <td>[F5 on IBM Cloud](services/f5_considerations.html)</td>
       <td>F5 on {{site.data.keyword.cloud_notm}} サービス (F5 BIG-IP® Virtual Edition) は、ローカルとグローバルの規模でのインテリジェントな L4 から L7 までのロード・バランシング・サービスとトラフィック管理サービス、ネットワークと Web アプリケーションのための堅固なファイアウォール保護、セキュアなフェデレート・アプリケーション・アクセスを提供します。</td>
    </tr>
    <tr>
       <td>[FortiGate Security Appliance on IBM Cloud](services/fsa_considerations.html)</td>
       <td>FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスでは、FortiGate Security Appliance (FSA) 300 シリーズのデバイスのペアが高可用性モードでデプロイされます。これを使って、ファイアウォール、ルーティング、NAT、VPN の各サービスが提供され、ご使用のインスタンスのパブリック VLAN 上のすべてのサーバーと仮想マシンが保護されます。</td>
    </tr>
    <tr>
       <td>[FortiGate Virtual Appliance on IBM Cloud](services/fortinetvm_considerations.html)</td>
       <td>FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスでは、ご使用の環境に FortiGate Virtual Appliances のペアがデプロイされます。これによって、仮想インフラストラクチャー内に重要なセキュリティー管理が実装されるので、リスクを軽減するのに役立ちます。</td>
    </tr>
    <tr>
       <td>[HyTrust CloudControl on IBM Cloud](services/htcc_considerations.html)</td>
       <td>HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスは、セキュリティー規格を適用してコンプライアンスを統制し、詳細な役割ベースのアクセス制御 (RBAC)、承認、および監査の機能を提供します。 このサービスを HyTrust DataControl と組み合わせると、仮想マシンとワークロードのデータを特定の地域、クラスター、または {{site.data.keyword.CloudDataCent_notm}} の ESXi サーバーから外に出さないようにすることができます。</td>
    </tr>
    <tr>
       <td>[HyTrust DataControl on IBM Cloud](services/htdc_considerations.html)</td>
       <td>HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスでは、鍵管理機能が組み込まれた強い暗号を使用して、ワークロードをライフサイクルにわたって保護できます。 このサービスは、オペレーティング・システム・レベルとデータ・レベルの両方で暗号化を実行できます。つまり、ワークロード内で任意のディレクトリー、フォルダー、またはファイルを暗号化/復号できます。</td>
    </tr>
    <tr>
       <td>[HyTrust KeyControl on IBM Cloud](services/htkc_considerations.html)</td>
       <td>HyTrust KeyControl on {{site.data.keyword.cloud_notm}} サービスは、暗号鍵のライフサイクルを自動化および単純化することによって、暗号化ワークロードの管理を単純化します。 このサービスでは、FIPS 140-2 準拠の暗号化を使用することで、暗号鍵を簡単に一括して管理できるようになります。</td>
    </tr>
    <tr>
       <td>[IBM Cloud Private Hosted](services/managing_icp.html)</td>
       <td>{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} サービスは、マイクロサービスとコンテナーの機能を {{site.data.keyword.cloud_notm}} 上の VMware 環境で利用できるようにします。 このサービスを利用することで、使い慣れたオンプレミスの VMware と {{site.data.keyword.cloud_notm}} Private の操作モデルとツールを、{{site.data.keyword.cloud_notm}} に拡張できます。</td>
    </tr>
    <tr>
       <td>[IBM Spectrum Protect Plus on IBM Cloud](services/spp_considerations.html)</td>
       <td>IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスは、仮想環境のデータ保護、データ再使用、データ・リカバリーのための効率的でスケーラブルなソリューションを提供します。 サービスをスタンドアロン・ソリューションとして実装することも、お客様の IBM Spectrum Protect 環境と統合して長期保管とデータ・ガバナンスのためにコピーをオフロードすることもできます。</td>
    </tr>
    <tr>
       <td>[KMIP for VMware on IBM Cloud](services/kmip_considerations.html)</td>
       <td>KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスは、{{site.data.keyword.cloud_notm}} 内の VMware によって使用される暗号鍵を管理するための高可用性サービスを提供します。 このサービスは、お客様が暗号鍵を作成、取得、活動化、取り消し、破棄できるようにするランタイム機能を提供します。 また、クライアントの資格情報と暗号鍵の関連付けを管理する管理機能も提供します。</td>
    </tr>
    <tr>
       <td>[Veeam on IBM Cloud](services/veeam_considerations.html)</td>
       <td>Veeam on {{site.data.keyword.cloud_notm}} サービスは VMware ハイパーバイザーに直接、シームレスに統合され、企業での高可用性の実現を支援します。 このサービスを使用すると、アプリケーションとデータのリカバリー・ポイントと目標復旧時間を利用できます。 リカバリー・ポイントと目標復旧時間は、構成が完了してから 15 分以内に利用可能になります。 このサービスを使用することにより、ご使用のインフラストラクチャーに配置されたすべての仮想マシンのバックアップとリストアの両方を Veeam コンソールから直接制御できます。</td>
    </tr>
    <tr>
       <td>[VMware HCX on IBM Cloud](services/hcx_considerations.html)</td>
       <td>HCX on {{site.data.keyword.cloud_notm}} サービスでは、オンプレミス・データ・センターのネットワークを {{site.data.keyword.cloud_notm}} にシームレスに拡張できるので、変換も変更も行わずに {{site.data.keyword.cloud_notm}} との間で仮想マシン (VM) をマイグレーションできます。</td>
    </tr>
    <tr>
       <td>[Zerto on IBM Cloud](services/addingzertodr.html)</td>
       <td>Zerto on {{site.data.keyword.cloud_notm}} サービスは、複製と災害復旧の機能を提供します。これらの機能をデプロイメント・オファリングに組み込むことで、{{site.data.keyword.cloud_notm}} 上の VMware 仮想環境内のデータの保護と復旧を行えます。</td>
    </tr>
   </table>

## ステップ 1: IBM Cloud for VMware Solutions コンソールへのアクセス

{{site.data.keyword.vmwaresolutions_short}} コンソールは、デプロイメントの注文と管理を行うインターフェースです。 コンソールでは、各デプロイメントがインスタンスとして管理されます。 このコンソールは、{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータルとは別のスタンドアロンのユーザー・インターフェースです。

{{site.data.keyword.vmwaresolutions_short}} コンソールにアクセスするには、以下のようにします。
1. https://console.ng.bluemix.net/infrastructure/vmware-solutions/console にアクセスします。
2. **IBM ID** でコンソールにログインします。

## ステップ 2: ユーザー・アカウントと設定の構成

インスタンスを注文する前に、コンソールの**「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャー (SoftLayer) アカウントのユーザー名と API 鍵を入力する必要があります。

ユーザーアカウントと設定を構成する方法については、「[ユーザー・アカウントと設定の管理](vmonic/useraccount.html)」を参照してください。

## ステップ 3: インスタンスの注文

コンソールでインスタンスとして管理されるデプロイメント・オファリングを決定したら、注文プロセスを開始します。

インスタンスを注文する方法について詳しくは、選択したデプロイメント・オファリングに応じて以下のトピックを参照してください。
* [vCenter Server インスタンスの注文](vcenter/vc_orderinginstance.html)
* [vCenter Server with Hybridity Bundle インスタンスの注文](vcenter/vc_hybrid_orderinginstance.html)
* [Cloud Foundation インスタンスの注文](sddc/sd_orderinginstance.html)
* [新規 vSphere クラスターの注文](vsphere/vs_orderinginstances.html)
* [NetApp ONTAP Select インスタンスの注文](netapp/np_orderinginstances.html)  
* [VMware Federal インスタンスの注文](vcenter/vc_fed_orderinginstance.html)

## ステップ 4: インスタンスの表示

**ステップ 3** でインスタンスの注文を行うと、インスタンスのデプロイメントが自動的に開始されます。 デプロイメントの状況を追跡するには、インスタンスの詳細を表示します。 インスタンスのデプロイメントが完了したら、インスタンスの詳細ページでも、インスタンスとそのアドオン・サービスの要約と詳細情報を表示できます。

注文したインスタンスを表示する方法について詳しくは、以下のトピックを参照してください。
* [vCenter Server インスタンスの表示](vcenter/vc_viewinginstances.html)
* [vCenter Server with Hybridity Bundle インスタンスの表示](vcenter/vc_hybrid_viewinginstances.html)
* [Cloud Foundation インスタンスの表示](sddc/sd_viewinginstances.html)
* [NetApp ONTAP Select インスタンスの表示](netapp/np_viewinginstances.html)
* [VMware Federal インスタンスの表示](vcenter/vc_fed_viewinginstance.html)

## ステップ 5: インスタンスのアドオン・サービスの管理

インスタンスのアドオン・サービスを注文した場合、サービスも管理できます。

サービスを管理する方法について詳しくは、以下のトピックを参照してください。
* [vCenter Server インスタンスのサービスの注文、表示、削除](vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](vcenter/vc_hybrid_addingremovingservices.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](sddc/sd_addingremovingservices.html)

## 次のステップ

{{site.data.keyword.vmwaresolutions_short}} コンソールまたは VMware vSphere Web Client からインスタンスを管理します。
