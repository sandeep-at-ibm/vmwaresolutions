---

copyright:

  years: 2016, 2019

lastupdated: "2019-04-16"

keywords: IBM Cloud for VMware Solutions, getting started, vmware solutions offerings, add-on services for vmwaresolutions, vmwaresolutions use cases

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# 入門チュートリアル
{: #getting-started}

この入門チュートリアルでは、インスタンスおよびそれに使用するいくつかのアドオン・サービスを注文するプロセスについて説明します。
{:shortdesc}

## 始める前に
{: #getting-started-prereqs}

{{site.data.keyword.vmwaresolutions_full}} での作業を始める前に、ブラウザー要件、ユーザー・アカウント、デプロイメント・オプション、およびアドオン・サービスに関する以下の重要な情報を確認してください。

### ブラウザー要件
{: #getting-started-browser-req}

以下のブラウザーがサポートされています。
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

Microsoft Internet Explorer はサポートされていません。
{:note}

{{site.data.keyword.vmwaresolutions_short}} コンソールの表示と操作を最適化するために、画面解像度を幅 1024 ピクセル以上、高さ 500 ピクセル以上に設定してください。

### ユーザー・アカウント
{: #getting-started-user-accts}

{{site.data.keyword.cloud_notm}} アカウントおよび {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントが必要です。 これらのアカウントは特定の要件を満たしている必要があります。

   表 1. 必要なユーザー・アカウント
   <table>
   <tr>
      <th>アカウント</th>
      <th>説明</th>
   </tr>
   <tr>
      <td>IBMid</td>
      <td>**IBMid** を使用すると、1 つのログイン・ユーザー名を、{{site.data.keyword.cloud_notm}} など、お客様が使用する IBM のすべての製品およびサービスに使用できます。 {{site.data.keyword.vmwaresolutions_short}} は、{{site.data.keyword.cloud_notm}} カタログの中でインフラストラクチャー・ソリューションとして提供されています。 {{site.data.keyword.vmwaresolutions_short}} コンソールにアクセスするには、**IBMid** が必要です。<br><br>**IBMid** を使用して {{site.data.keyword.vmwaresolutions_short}} コンソールにログインするために、{{site.data.keyword.cloud_notm}} アカウントに **IBMid** を関連付ける必要があります。 コンソールに初めてログインするときに、既存の **IBMid** を {{site.data.keyword.cloud_notm}} アカウントに関連付けるか、新規 {{site.data.keyword.cloud_notm}} アカウントを登録するように指示されます。 新規 {{site.data.keyword.cloud_notm}} アカウントは **IBMid** に自動的に関連付けられます。 このプロセスを行う必要があるのは 1 回だけです。<br><br>**IBMid** と {{site.data.keyword.cloud_notm}} アカウントの関連付けに問題がある場合は、[{{site.data.keyword.cloud_notm}} へのアクセスに関するトラブルシューティング](/docs/account?topic=account-accessing#accessing)を参照してください。</td>
   </tr>
   <tr>
      <td>IBM Cloud アカウント</td>
      <td>{{site.data.keyword.cloud_notm}} サービスを注文および使用するには、{{site.data.keyword.cloud_notm}} アカウントが必要です。 請求情報は {{site.data.keyword.cloud_notm}} アカウントに関連付けられています。 物理インフラストラクチャーと仮想インフラストラクチャーのコスト、最終的に使用されたライセンスは、{{site.data.keyword.cloud_notm}} アカウントに請求されます。</td>
   </tr>
   <tr>
      <td>IBM Cloud インフラストラクチャー・アカウント</td>
      <td>{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの要件について詳しくは、[{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの要件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement)を参照してください。<br><br>{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントと {{site.data.keyword.cloud_notm}} アカウントをリンクして、Infrastructure as a Service (IaaS) リソースと Platform as a Service (PaaS) リソースを組み合わせて使用できます。 その後、単一のログインから IaaS リソースと PaaS リソースにアクセスできます。 さらに、アカウントをリンクする場合は、使用するすべての PaaS リソースおよび IaaS リソースに対して単一の請求書が提供されます。<ul><li>{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントがない場合は、[IBM Cloud インフラストラクチャー・アカウントの登録](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account#signing_softlayer_account-infra)の手順に従ってアカウントを要求し、[IBMid への切り替えとアカウントのリンク](/docs/account?topic=account-unifyingaccounts#unifyingaccounts)の手順に従って {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントとご使用の {{site.data.keyword.cloud_notm}} アカウントをリンクします。</li><li>{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントを持っている場合は、それを [IBMid への切り替えとアカウントのリンク](/docs/account?topic=account-unifyingaccounts#unifyingaccounts)の手順に従って {{site.data.keyword.cloud_notm}} アカウントにリンクします。</li></ul></td>
   </tr>
   </table>

### デプロイメント・オファリング
{: #getting-started-depl-offerings}

デプロイメント・オファリングを確認して選択します。

  表 2. デプロイメント・オファリング
  <table>
    <tr>
       <th>デプロイメント・オファリング</th>
       <th>説明</th>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)</td>
       <td>この vCenter Server オファリングでは、ビジネス・ニーズに最適なカスタムのコンピュート、ストレージ、ネットワークのリソースを使用して、VMware 仮想環境をデプロイできます。</td>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)</td>
       <td>この vCenter Server with Hybridity オファリングは、オンプレミスのインフラストラクチャーを素早く簡単にクラウドに拡張できるホステッド・プライベート・クラウドです。 この VMware 環境は、IBM 提供の VMware Software Defined Data Center ライセンスに基づくものであり、VMware Hybrid Cloud Extension (HCX) が含まれています。 HCX を使用すると、オンプレミスの vSphere 5.0+ 環境と {{site.data.keyword.cloud_notm}} サイトを安全に接続して、インフラストラクチャーのシームレスなハイブリッド化と真のアプリケーション・モビリティーを実現できます。</td>
    </tr>
    <tr>
       <td>[VMware vSphere on IBM Cloud](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)</td>
       <td>この vSphere on {{site.data.keyword.cloud_notm}} オファリングで提供されるカスタマイズ可能な仮想化サービスを使用すると、VMware 互換の{{site.data.keyword.baremetal_short}}、ハードウェア・コンポーネント、ライセンスを組み合わせて、IBM でホストされる独自の VMware 環境を構築できます。</td>
    </tr>
    <tr>
       <td>[NetApp  ONTAP  Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)</td>
       <td>NetApp ONTAP Select オファリングでは、NetApp ONTAP Select をベースとする可用性の高い専用ストレージ・アプライアンスを必要とするニーズに対応するソフトウェア定義ストレージ・クラスターをデプロイできます。</td>
    </tr>
  </table>

### アドオン・サービス
{: #getting-started-add-on-services}

デプロイメント・オファリングのアドオン・サービスを確認して選択します。

  表 3. デプロイメント・オファリングで使用可能なアドオン・サービス
  <table>
    <tr>
       <th>サービス名</th>
       <th>説明</th>
    </tr>
    <tr>
       <td>[F5 on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)</td>
       <td>F5 on {{site.data.keyword.cloud_notm}} サービス (F5 BIG-IP® Virtual Edition) は、ローカルとグローバルの規模でのインテリジェントな L4 から L7 までのロード・バランシング・サービスとトラフィック管理サービス、ネットワークと Web アプリケーションのための堅固なファイアウォール保護、セキュアなフェデレート・アプリケーション・アクセスを提供します。</td>
    </tr>
    <tr>
       <td>[FortiGate Security Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)</td>
       <td>FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} サービスでは、FortiGate Security Appliance (FSA) 300 シリーズのデバイスのペアが高可用性モードでデプロイされます。これを使って、ファイアウォール、ルーティング、NAT、VPN の各サービスが提供され、ご使用のインスタンスのパブリック VLAN 上のすべてのサーバーと仮想マシンが保護されます。</td>
    </tr>
    <tr>
       <td>[FortiGate Virtual Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)</td>
       <td>FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスでは、ご使用の環境に FortiGate Virtual Appliances のペアがデプロイされます。これによって、仮想インフラストラクチャー内に重要なセキュリティー管理が実装されるので、リスクを軽減するのに役立ちます。</td>
    </tr>
    <tr>
       <td>[HyTrust CloudControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)</td>
       <td>HyTrust CloudControl on {{site.data.keyword.cloud_notm}} サービスは、セキュリティー規格を適用してコンプライアンスを統制し、詳細な役割ベースのアクセス制御 (RBAC)、承認、および監査の機能を提供します。 このサービスを HyTrust DataControl と組み合わせると、仮想マシンとワークロードのデータを特定の地域、クラスター、または {{site.data.keyword.CloudDataCent_notm}} の ESXi サーバーから外に出さないようにすることができます。</td>
    </tr>
    <tr>
       <td>[HyTrust DataControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)</td>
       <td>HyTrust DataControl on {{site.data.keyword.cloud_notm}} サービスでは、鍵管理機能が組み込まれた強い暗号を使用して、ワークロードをライフサイクルにわたって保護できます。 このサービスは、オペレーティング・システム・レベルとデータ・レベルの両方で暗号化を実行できます。つまり、ワークロード内で任意のディレクトリー、フォルダー、またはファイルを暗号化/復号できます。</td>
    </tr>
    <tr>
       <td>[HyTrust KeyControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)</td>
       <td>HyTrust KeyControl on {{site.data.keyword.cloud_notm}} サービスは、暗号鍵のライフサイクルを自動化および単純化することによって、暗号化ワークロードの管理を単純化します。 このサービスでは、FIPS 140-2 準拠の暗号化を使用することで、暗号鍵を簡単に一括して管理できるようになります。</td>
    </tr>
    <tr>
       <td>[IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)</td>
       <td>{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} サービスは、マイクロサービスとコンテナーの機能を {{site.data.keyword.cloud_notm}} 上の VMware 環境で利用できるようにします。 このサービスを利用することで、使い慣れたオンプレミスの VMware と {{site.data.keyword.cloud_notm}} Private の操作モデルとツールを、{{site.data.keyword.cloud_notm}} に拡張できます。</td>
    </tr>
    <tr>
       <td>[IBM Spectrum Protect Plus on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)</td>
       <td>IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスは、仮想環境のデータ保護、データ再使用、データ・リカバリーのための効率的でスケーラブルなソリューションを提供します。 サービスをスタンドアロン・ソリューションとして実装することも、お客様の IBM Spectrum Protect 環境と統合して長期保管とデータ・ガバナンスのためにコピーをオフロードすることもできます。</td>
    </tr>
    <tr>
       <td>[KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)</td>
       <td>KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスは、{{site.data.keyword.cloud_notm}} 内の VMware によって使用される暗号鍵を管理するための高可用性サービスを提供します。 このサービスは、お客様が暗号鍵を作成、取得、活動化、取り消し、破棄できるようにするランタイム機能を提供します。 また、クライアントの資格情報と暗号鍵の関連付けを管理する管理機能も提供します。</td>
    </tr>
    <tr>
       <td>[IBM Cloud での Veeam](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)</td>
       <td>Veeam on {{site.data.keyword.cloud_notm}} サービスは VMware ハイパーバイザーに直接、シームレスに統合され、企業での高可用性の実現を支援します。 このサービスを使用すると、アプリケーションとデータのリカバリー・ポイントと目標復旧時間を利用できます。 リカバリー・ポイントと目標復旧時間は、構成が完了してから 15 分以内に利用可能になります。 このサービスを使用することにより、ご使用のインフラストラクチャーに配置されたすべての仮想マシンのバックアップとリストアの両方を Veeam コンソールから直接制御できます。</td>
    </tr>
    <tr>
       <td>[VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)</td>
       <td>HCX on {{site.data.keyword.cloud_notm}} サービスでは、オンプレミス・データ・センターのネットワークを {{site.data.keyword.cloud_notm}} にシームレスに拡張できるので、変換も変更も行わずに {{site.data.keyword.cloud_notm}} との間で仮想マシン (VM) をマイグレーションできます。</td>
    </tr>
    <tr>
       <td>[IBM Cloud での Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)</td>
       <td>Zerto on {{site.data.keyword.cloud_notm}} サービスは、複製と災害復旧の機能を提供します。これらの機能をデプロイメント・オファリングに組み込むことで、{{site.data.keyword.cloud_notm}} 上の VMware 仮想環境内のデータの保護と復旧を行えます。</td>
    </tr>
   </table>

## ステップ 1: IBM Cloud for VMware Solutions コンソールへのアクセス
{: #getting-started-step1}

{{site.data.keyword.vmwaresolutions_short}} コンソールは、デプロイメントの注文と管理を行うインターフェースです。 コンソールでは、各デプロイメントがインスタンスとして管理されます。 このコンソールは、{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータルとは別のスタンドアロンのユーザー・インターフェースです。

{{site.data.keyword.vmwaresolutions_short}} コンソールにアクセスするには、以下のようにします。
1. https://cloud.ibm.com/infrastructure/vmware-solutions/console にアクセスします。
2. **IBMid** でコンソールにログインします。

## ステップ 2: ユーザー・アカウントと設定の構成
{: #getting-started-step2}

インスタンスを注文する前に、コンソールの**「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントのユーザー名と API 鍵を入力する必要があります。

ユーザーアカウントと設定を構成する方法については、「[ユーザー・アカウントと設定の管理](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)」を参照してください。

## ステップ 3: インスタンスの注文
{: #getting-started-step3}

コンソールでインスタンスとして管理されるデプロイメント・オファリングを決定したら、注文プロセスを開始します。

インスタンスを注文する方法について詳しくは、選択したデプロイメント・オファリングに応じて以下のトピックを参照してください。
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server with Hybridity Bundle インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [NetApp ONTAP Select インスタンスの注文](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## ステップ 4: インスタンスの表示
{: #getting-started-step4}

**ステップ 3** でインスタンスの注文を行うと、インスタンスのデプロイメントが自動的に開始されます。 デプロイメントの状況を追跡するには、インスタンスの詳細を表示します。 インスタンスのデプロイメントが完了したら、インスタンスの詳細ページでも、インスタンスとそのアドオン・サービスの要約と詳細情報を表示できます。

注文したインスタンスを表示する方法について詳しくは、以下のトピックを参照してください。
* [vCenter Server インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [vCenter Server with Hybridity Bundle インスタンスの表示](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [NetApp ONTAP Select インスタンスの表示](/docs/services/vmwaresolutions/services?topic=vmware-solutions-np_viewinginstances#np_viewinginstances)
