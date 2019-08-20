---

copyright:

  years:  2019

lastupdated: "2019-07-09"

keywords: about vmware solutions, product overview, benefits

subcollection: vmware-solutions

---
{:external: target="_blank" .external}

# IBM Cloud for VMware Solutions: 内部の詳しい仕組み
{: #under_the_hood}

## VMware 仮想化環境のデプロイと管理
{: #under_the_hood-deploy}

VMware 仮想化環境をデプロイして管理できる {{site.data.keyword.cloud_notm}} オファリング、{{site.data.keyword.vmwaresolutions_full}} のアーキテクチャーについて詳しく見ていきましょう。 このチュートリアルでは、このオファリングの各コンポーネントの連携によって、パブリック・クラウドでの環境のプロビジョンと管理が可能になっていることを理解できるように、各コンポーネントについて説明します。

## 2 社による、1 つの合理化されたソリューション
{: #under_the_hood-two-companies}

これまで長い間、ユーザーは自力に頼るかプロフェッショナル・サービスによる支援を受けて VMware 仮想化環境を IBM パブリック・クラウドにデプロイしてきました。 2016 年 2 月、{{site.data.keyword.cloud_notm}} に VMware ソフトウェアと VMware 環境をデプロイするプロセスを自動化するために [IBM と VMware がパートナーシップを結ぶことが発表されました](https://www-03.ibm.com/press/us/en/pressrelease/49154.wss){:external}。 このパートナーシップの成果として早期に現れた成果の 1 つは、さまざまな VMware 製品のデプロイメントやライセンスを {{site.data.keyword.vmwaresolutions_short}} コンソールから注文できるようになったことです。その後、[VMware Horizon Air](https://www-03.ibm.com/press/us/en/pressrelease/49932.wss){:external} も {{site.data.keyword.cloud_notm}} で提供されるようになりました。 さらに、IBM と VMware は、IBM パブリック・クラウドにおける [VMware の標準リファレンス・アーキテクチャーおよびデプロイメント規定](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture){:external}を共同で作成しました。

2016 年の秋、IBM と VMware は共同で {{site.data.keyword.vmwaresolutions_short}} をリリースしました。 このオファリング・セットは、仮想化コンピュート (VMware vSphere)、ネットワーキング (VMware NSX)、オプションの仮想化ストレージ (VMware vSAN) など、VMware のさまざまな仮想化テクノロジーを基盤にして構築されています。 これらの環境は、ソフトウェア定義データ・センターと呼ぶにふさわしい環境です。

{{site.data.keyword.vmwaresolutions_short}} は VMware テクノロジーを基盤としているので、IBM パブリック・クラウドにこれらのソフトウェア定義データ・センターをデプロイして管理する作業は大幅に合理化されています。 {{site.data.keyword.vmwaresolutions_short}} を使用することで、現在は標準リファレンス・アーキテクチャーの各部分を手動ではなく自動で {{site.data.keyword.cloud_notm}} にデプロイできるようになりました。 以前は数週間かけてデプロイして構成していた環境を、数時間でプロビジョンできるようになったのです。

このように簡単にデプロイできるようになったので、お客様は環境構築ではなく VMware 上にソリューションを実装することに専念できます。 思いのままに素早く利用できる環境で、プライベート・クラウドと IBM パブリック・クラウドにまたがるハイブリッド・クラウド・ソリューションを構築することも、IBM パブリック・クラウドでクラウド・ネイティブ・ソリューションを構築することもできます。 複数のデプロイメントを組み合わせれば、災害復旧や高可用性の機能をソリューションに簡単に追加できます。

それでは、{{site.data.keyword.vmwaresolutions_short}} アーキテクチャーの内部について詳しく見ていきましょう。 このソリューションに含まれている多様なコンポーネントについて理解し、各コンポーネントの連携によって {{site.data.keyword.cloud_notm}} でのソフトウェア定義データ・センターのプロビジョンと管理が可能になっていることを理解できるようになるはずです。 また、ネットワーク・トポロジーとお客様環境に接続する方法についても学習します。

## IBM Cloud for VMware Solutions の基礎

ソフトウェア定義データ・センターのプロビジョンと管理は、[{{site.data.keyword.vmwaresolutions_short}} コンソール](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}で行います。 このコンソールには、IBMid アカウントを使用してログインします。

VMware Solutions カタログから、いくつかの種類の仮想化環境の 1 つをプロビジョンできます。 主要な仮想化ソリューションは *VMware vCenter Server on {{site.data.keyword.cloud_notm}}* です。このソリューションでは、VMware の vSphere ハイパーバイザー、VMware vCenter Server、VMware NSX、およびオプションで VMware vSAN を利用できます。 この環境をプロビジョンするときには、バックアップ、災害復旧、マイグレーション、セキュリティー、コンプライアンス、ネットワーキングのサービスを提供するアドオン・サービスを追加することもできます。

vCenter Server インスタンスを注文する前に、VMware Solutions カタログで {{site.data.keyword.cloud_notm}} インフラストラクチャーの API キーを構成しておく必要があります。 これを行うには、コンソールの左側にあるメニューで[「設定」](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings){:external}リンクをクリックします。そして、{{site.data.keyword.cloud_notm}} インフラストラクチャー資格情報を求められたらユーザー名と API キーを入力します。 インスタンスをデプロイするための適切な許可と設定が API キーとアカウントにあるかどうかがシステムによって検証されます。

vCenter Server インスタンスを注文するときには、まずインスタンス名と VMware vSphere のバージョンを選択します。 すべての VMware インスタンスは Microsoft Active Directory ドメイン・コントローラーとともにデプロイされます。シングル・サインオンのために、インスタンスをプライマリー・サイトまたはセカンダリー・サイトのどちらにするかを指定する必要があります。 プライマリー・インスタンスは、シングル・サインオン・ドメインの 1 番目のインスタンスまたは唯一のインスタンスです。 追加のセカンダリー・インスタンスをデプロイし、それらを既存のプライマリー・インスタンスと同じシングル・サインオン・ドメインに関連付けることができます。 次に、独自の VMware ライセンスを持ち込むかどうか選択します。または、{{site.data.keyword.cloud_notm}} からレンタルするライセンスのエディションを選択します。 最後に、インスタンスの {{site.data.keyword.cloud_notm}} 地域とデータ・センター、クラスター内のホストの CPU とメモリーの特性を選択します。

注文ページの次の部分で、インスタンスのストレージとネットワーキングの特性を入力します。 クラスターのストレージとして vSAN ストレージまたは NFS ストレージを選択できます。そして、vSAN フラッシュ・ディスクのサイズと数、vSAN ライセンス・エディション、または、NFS ストレージ・ボリュームのサイズと数とパフォーマンスを選択できます。 ネットワーキングについては、ホストのホスト名接頭部と、クラスターのサブドメインおよびドメインを選択します。 Active Directory コントローラーは、1 つの {{site.data.keyword.cloud_notm}} 仮想サーバー・インスタンス (VSI) としてデプロイできます。または、2 つの仮想マシン (VM) としてクラスター内にデプロイすることもできます (この場合、これらの VM のライセンス交付とアクティベーションが必要です)。

vCenter Server 注文ページの下部で、VMware インスタンスにデプロイ可能な各種アドオン・サービスを選択できます。選択したアドオン・サービスは {{site.data.keyword.cloud_notm}} アカウントに請求されます。 追加の構成が必要なサービスの場合は、その構成を注文フォームの一部として指定します。

選択内容に基づいて推定料金が計算され、注文フォームに表示されます。 この推定料金と各種使用条件を確認してから注文することができます。

### デプロイメント・オプション
{: #under_the_hood-deploy-options}

vCenter Server の注文フォームには、インスタンスの CPU、メモリー、ストレージに関するさまざまなオプションが表示されます。 定期的に新しいオプションが導入されるので、{{site.data.keyword.cloud_notm}} カタログをチェックして最新の情報を確認してください。

{{site.data.keyword.cloud_notm}} は、3 つの VLAN (パブリック 1 つとプライベート 2 つ) を使用して vCenter Server インスタンスをデプロイします。 パブリック VLAN はデュアル 10 GbE インターフェースに接続されており、お客様のワークロード・デプロイメントのためのパブリック接続やトンネリングに自由に利用できるように広い範囲が予約されています。 ただし、デプロイメント時には、NSX Edge Services Gateway ペアがパブリック VLAN にデプロイされており、一部のアドオン・サービスがライセンス登録と課金の目的でパブリック・ネットワークに接続することを許可されています。 2 つのプライベート VLAN は別々のデュアル 10 GbE インターフェースに接続されます。1 つ目のプライベート VLAN は管理通信と NSX VTEP のために使用され、もう 1 つは vMotion と NFS ストレージ・トラフィックのために使用されます。

VMware インスタンスは 35 カ所の {{site.data.keyword.CloudDataCents_notm}} にプロビジョンできます。 {{site.data.keyword.cloud_notm}} は、随時、新しいデータ・センターをプロビジョンしています。 {{site.data.keyword.cloud_notm}} カタログで、利用可能なロケーションの最新リストを確認してください。

### インスタンスのデプロイメント
{: #under_the_hood-inst-deploy}

新規 VMware vCenter インスタンスを注文するときには、インスタンスのロケーションと仕様を選択します。 {{site.data.keyword.vmwaresolutions_short}} は、その前に選択されていた {{site.data.keyword.cloud_notm}} のユーザー名と API キーを使用して、仮想化環境の注文、インストール、構成のプロセス全体を調整します。 これには以下の処理が含まれます。

1. ネットワーキングのための VLAN とサブネットの注文。
2. vSphere Hypervisor をインストールした {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} の注文。
3. 組み込み Platform Services Controller が構成された VMware vCenter Server、VMware NSX Manager、VMware NSX Controller、VMware NSX Edge Services Gateway のデプロイと構成。
4. VMware vSAN または {{site.data.keyword.cloud_notm}} エンデュランス・ストレージを含む、クラスター・ストレージの注文と構成。
5. IBM CloudDriver という IBM 管理コンポーネントのデプロイ。
6. インスタンスのために選択したアドオン・サービスのデプロイと構成。
7. 環境のインストールおよび構成の妥当性検査。

インスタンスをプロビジョンする {{site.data.keyword.CloudDataCent_notm}}を選択します。 選択した {{site.data.keyword.CloudDataCent_notm}}にハードウェアがある場合は、通常、インスタンスのプロビジョニング・プロセスは 24 時間以内に終わります。

VPN 経由で {{site.data.keyword.cloud_notm}} アカウントに接続している場合は、インスタンスがプロビジョンされたら、ワークステーションの Web ブラウザーから直接 vCenter サーバーに接続できます。

インスタンスのコンポーネントには、通常、IP アドレスではなくホスト名を使用してアクセスします。 vCenter に接続して認証を受けるには、vCenter と Platform Services Controller (PSC) のホスト名をワークステーションで解決できるようにする必要があります。そのためには、リスト 1 に示すように、ホスト名をワークステーションの hosts ファイルに追加します。ホスト名と IP アドレスは、{{site.data.keyword.vmwaresolutions_short}} コンソールの対象インスタンスの**「サマリー」**タブで確認できます。 一般には、各 vSphere ホストのホスト名と IP アドレスを hosts ファイルに追加する必要もあります。

*リスト 1. Hosts ファイル*

<pre># Dallas site vCenter and Platform Services Controller (PSC)
10.208.85.196  vcenter-dallas.dallas.example.com
# Dallas site hosts
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com</pre>

デプロイされたインスタンスは、コンソールから管理できます。 管理機能には、以下のような操作を行う機能があります。

* クラスターのノードをデプロイ/削除する
* 同じデータ・センター、同じポッドで追加クラスターをデプロイ/削除する。別のデータ・センター、別のポッドで追加クラスターをデプロイ/削除する
* インスタンスのアドオン・サービスをデプロイ/削除する
* インスタンスの特定のライセンス・エディションをアップグレードする

{{site.data.keyword.vmwaresolutions_short}} コンソールで、各 vCenter Server インスタンスの詳細を確認できます。 インスタンスごとに、**「サマリー」**タブに、vCenter コンソールへのリンクと、インスタンスおよび管理コンポーネントに関するその他の詳細が表示されます。 **「インフラストラクチャー」**タブには、インスタンスのクラスター、ホスト、ストレージ、およびネットワーキングに関する詳細が表示されます。このタブで、クラスター、ホスト、およびストレージを追加または削除できます。 **「更新およびパッチ」**タブでは、特定のライセンス・エディションをアップグレードできます。 **「サービス」**タブでは、インスタンスにデプロイされているアドオン・サービスを表示および管理できます。 **「デプロイ履歴」**タブには、インスタンスで実行されたすべてのアクションの履歴が表示されます。

## IBM Cloud for VMware Solutions のコンポーネント
{: #under_the_hood-comp}

多様なコンポーネントの連携によって、環境のプロビジョンと管理が可能になっています。 これらのコンポーネントのほとんどは、{{site.data.keyword.cloud_notm}} アカウントにデプロイされます。 このソリューションは、これらのすべてのコンポーネントが連携することで成立しているので、どのコンポーネントも {{site.data.keyword.cloud_notm}} アカウントから変更したりキャンセルしたりしてはいけません。 実行中のインスタンスを削除する正しい方法は、個々のコンポーネントをキャンセルするのではなく、コンソールを使用する方法です。

このソリューションは統合された 1 つの仮想化環境ですが、{{site.data.keyword.cloud_notm}} から受け取る請求書では、各種の仮想化コンポーネント(VMware ライセンスなど)、インフラストラクチャー・コンポーネント (ベアメタル・サーバー、VLAN、サブネット、ストレージ)、管理コンポーネントの費用が項目別に分かれています。

### IBM Cloud for VMware Solutions コンソール
{: #under_the_hood-console}

インスタンスを作成および管理するには、[{{site.data.keyword.vmwaresolutions_short}} コンソール](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}にログインします。 このソリューションのこの部分で、最初に環境を注文してプロビジョニングする作業と、環境の継続的な管理作業を行います。 デプロイされたインスタンスは、{{site.data.keyword.cloud_notm}} プライベート・ネットワークを使用してこのコンソールと通信します。

### IBM CloudBuilder コンポーネント
{: #under_the_hood-ibm-cb}

新規インスタンスをプロビジョンすると、コンソールによって一時的な仮想サーバー・インスタンス (VSI) が {{site.data.keyword.cloud_notm}} アカウントにデプロイされます。 この仮想サーバーを IBM CloudBuilder と呼びます。 これが、インスタンスのすべてのコンポーネントのインストールと構成を実行し、環境を検証します。 プロビジョニングが完了すると、CloudBuilder は削除されます。

### IBM CloudDriver コンポーネント
{: #under_the_hood-ibm-cd}

CloudBuilder とよく似た IBM CloudDriver は、プロビジョニング後にインスタンスに対して操作を実行するために {{site.data.keyword.cloud_notm}} アカウントにデプロイされる一時的な仮想サーバー・インスタンス (VSI) です。 インスタンス内のホスト、クラスター、ストレージ、またはサービスを構成または削除するために、必要に応じてデプロイされます。

### VMware のコンポーネント
{: #under_the_hood-vmware-comp}

どのインスタンスでも、vSphere Hypervisor はベアメタル・サーバーにインストールされます。 次に、{{site.data.keyword.cloud_notm}} は、組み込み Platform Services Controller (PSC) が構成された vCenter Server アプライアンス 1 つ、NSX Manager 1 つ、NSX Controller 3 つ、NSX Edge Services Gateway ペア 2 つを VMware 管理クラスターにデプロイします。

### 追加のコンポーネント
{: #under_the_hood-add-comp}

選択内容に応じて、管理コンポーネント用の Active Directory サーバーとして、1 つの Microsoft Windows VSI または 2 つの Microsoft Windows VM がクラスター内にデプロイされます。 オプションで、管理アクセス用の追加 ID ソースとして、独自の Active Directory サーバーを追加することもできます。

お客様がどのような方法でワークロードの事業継続性を確保していようと、{{site.data.keyword.cloud_notm}} では、インスタンスの管理コンポーネントをバックアップすることを強くお勧めします。 {{site.data.keyword.vmwaresolutions_short}} コンソールでは、統合型の IBM Spectrum Protect Plus バックアップ・サーバーまたは Veeam Backup & Replication バックアップ・サーバーをインスタンスとともにデプロイできます。 これらのバックアップ・サービスは、インスタンスの[包括的なバックアップ・ソリューション](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup)の一部として使用できます。

### ライセンス
{: #under_the_hood-licenses}

{{site.data.keyword.cloud_notm}} は、さまざまな VMware ライセンス (vCenter Server や NSX など) を提供しています。これらはインスタンスにインストールされ、{{site.data.keyword.cloud_notm}} アカウントに請求されます。

## IBM Cloud for VMware Solutions のネットワーク・アーキテクチャー
{: #under_the_hood-network}

vCenter Server インスタンスは、お客様がデプロイするワークロードで使用できるように、パブリック VLAN に接続されます。 パブリック VLAN はお客様が利用できるように広い範囲が予約されています。ただし、NSX Edge Services Gateway ペアがパブリック VLAN に接続されており、一部のアドオン・サービスがライセンス登録と課金の目的でアウトバウンド通信を行うことを許可されています。 パブリック・ネットワークを使用せずにインスタンスをデプロイすることも可能です。その場合は、一部のアドオン・サービスがサポートされなくなるので、特定のアドオン・サービスを使用するために Web プロキシーを用意しなければならないことがあります。

vCenter Server インスタンスは 2 つのプライベート VLAN に接続され、それらの VLAN はハイパーバイザーのプライベート・ネットワーク・インターフェースに一緒にトランク接続されます。 1 つ目のプライベート VLAN は、管理接続 (vCenter とハイパーバイザーの通信など) のために使用されます。また、デプロイされたワークロードのすべての VXLAN トラフィックをトンネリングするために NSX によっても使用されます。 2 つ目のプライベート VLAN は、vMotion とストレージ・トラフィックのために使用されます。 ストレージ・トラフィックは、NFS プロトコルまたは vSAN プロトコルのどちらかです。

{{site.data.keyword.cloud_notm}} は、これらのプライベート VLAN を使用して、いくつかの追加のサービスを提供します。 Active Directory サーバーは、プライベート管理 VLAN を介して {{site.data.keyword.cloud_notm}} DNS サーバーと通信します。 ホストおよび他のコンポーネントは、プライベート管理 VLAN を介して {{site.data.keyword.cloud_notm}} NTP サーバーと通信します。 IBM CloudBuilder および CloudDriver も、この VLAN を介して {{site.data.keyword.vmwaresolutions_short}} コンソールと通信します。 ホストは、プライベート・ストレージ VLAN を介して {{site.data.keyword.cloud_notm}} エンデュランス・ストレージに接続します。

### インスタンスへの接続
{: #under_the_hood-connect-inst}

お客様のインスタンスに接続する方法としては、いくつかの選択肢があります。 [{{site.data.keyword.cloud_notm}} VPN](https://www.softlayer.com/VPN-Access){:external} を使用して、インスタンス (vCenter など) のプライベート IP アドレスに直接接続することができます。 また、[{{site.data.keyword.cloud_notm}} ネットワーク・アプライアンス](https://www.ibm.com/cloud/network-appliances){:external}と [{{site.data.keyword.cloud_notm}} ハードウェアまたは仮想ファイアウォール](https://www.ibm.com/cloud/network-security) (FortiGate や vSRX など) をアカウントで注文することもできます。 さらに {{site.data.keyword.cloud_notm}} は、お客様のネットワークと {{site.data.keyword.cloud_notm}} アカウントの VLAN を接続する [Direct Link](https://www.ibm.com/cloud/direct-link){:external} も提供しています。

デプロイした VM にアクセスするために、パブリック IP アドレスを VM に直接適用できます。 一方、{{site.data.keyword.cloud_notm}} ネットワーク・アプライアンスやファイアウォール機能を利用して、NAT とファイアウォールによるセキュリティーの高い VM へのパブリック・アクセスをセットアップすることもできます。 また、NSX Edge サーバーをデプロイし、それらのサーバーを使用して、VM に対する VPN 接続や NAT 接続をセットアップすることもできます。

## まとめ
{: #under_the_hood-conclusion}

このチュートリアルでは、標準化された VMware 仮想化環境をパブリック・クラウドでデプロイして管理するための {{site.data.keyword.vmwaresolutions_short}} の基本機能について学びました。 それらの環境をかつてないほど素早くプロビジョンできるので、お客様は、アプリケーションやソリューションを環境の上にデプロイすること、また、災害復旧または高可用性を確保するためにクラウド同士を接続することに専念できます。

{{site.data.keyword.cloud_notm}} アカウントにデプロイされる多様なコンポーネントについて詳しく見てきました。 {{site.data.keyword.cloud_notm}} の請求書の明細に記載されるこれらのコンポーネントの連携によって、お客様の環境は稼働し続けることができます。 最後に、このソリューションのネットワーク・アーキテクチャーと、環境への接続を確立する方法について考察しました。通信の機密を維持するためにセキュア接続を実現する多様な方法や、パブリック・インターネット接続を行う多様な方法がありました。

これで、作業を開始するために必要な知識が得られたので、早速、次の VMware 仮想化環境を {{site.data.keyword.cloud_notm}} にデプロイしてみましょう。

## 関連リンク
{: #under_the_hood-related}

* [概説](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [VMware Solutions のアーキテクチャー](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
