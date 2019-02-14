---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# 統合、IP アドレッシング、およびネットワーク・フロー

## IBM Cloud Private と VMware vCenter Server on IBM Cloud の統合

{{site.data.keyword.cloud}} Private は、vCenter Server インスタンス上の複数の仮想マシン (VM) にインストールされます。 vCenter Server インスタンス内に、専用の NSX Edge Services Gateway (ESG) および分散論理ルーター (DLR) と一緒にデプロイされる {{site.data.keyword.icpfull_notm}} インスタンスは、VXLAN を使用します。

アウトバウンド・トラフィックを許可するためのソース NAT ルール (SNAT) が ESG に構成されます。これにより、インターネット接続で {{site.data.keyword.icpfull_notm}} 前提条件をダウンロードし、GitHub および Docker に接続できるようになります。 代わりに、Web プロキシーを使用してインターネットに接続することもできます。 ESG には、DNS および NTP サービスにアクセスするためのプライベート接続が構成されています。 ESG には、{{site.data.keyword.cloud_notm}} 10.x ネットワークから {{site.data.keyword.icpfull_notm}} マスターおよびプロキシーの vIP へのアクセスを可能にする DNAT ルールも構成されています。

## IBM Cloud Kubernetes Service と vCenter Server の統合

現在、{{site.data.keyword.containerlong_notm}} と vCenter Server のネットワーキングを統合するには、以下のシナリオがあります。
- **共通 VLAN** - {{site.data.keyword.containerlong_notm}} ワーカー・ノードを vCenter Server インスタンスと同じ VLAN にデプロイする必要があります。 共通 VLAN により、ESG をワーカー・ノードの BGP ピアにすることができます。
- **strongSwan VPN** – このシナリオでは、{{site.data.keyword.containerlong_notm}} からエンタープライズに接続するための標準的なソリューションを使用します。 strongSwan コンテナーは、リモート・ゲートウェイへの IPSec トンネルを介してパケットをリモート・ネットワークに転送する VPN ゲートウェイをクラスターに提供します。 このリモート・ゲートウェイは vCenter Server インスタンス上の ESG です。 これらのゲートウェイには、すべてのクラスターとサービスの IP 範囲を strongSwan コンテナーに送信し、すべての vCenter Server BYOIP アドレスを ESG に送信するようにルートが構成されます。 ゲートウェイのターゲット IP アドレスは、strongSwan コンテナーに割り当てられたロード・バランサー・サービスのプライベート・ポータブル IP アドレスと、ESG のプライベート・ポータブル IP アドレスです。
- **静的ルートと NAT**。
- **BGP ピアリング** – BGP ピアリングは、{{site.data.keyword.cloud_notm}} のデフォルトのオファリングではないので、要求して承認を受ける必要があります。 BGP ピアリングを有効にすると、Calico vRouters および ESG が BCR へのルートを通知できるようになります。

## IBM Cloud Kubernetes Service と IBM Cloud Private の統合

{{site.data.keyword.containerlong_notm}} と {{site.data.keyword.icpfull_notm}} の統合では、{{site.data.keyword.icpfull_notm}} および {{site.data.keyword.containerlong_notm}} 内の strongSwan コンテナーとの strongSwan VPN 接続を使用します。

## IP アドレスの割り振り

管理の観点から見た場合、リファレンス・アーキテクチャーの概念的なネットワーク範囲は、以下のとおりです。
-	**{{site.data.keyword.containerlong_notm}} ポッド・ネットワーク** - ワーカー・ノードにデプロイされるすべてのポッドには、172.30.0.0/16 の範囲のプライベート IP アドレスが割り当てられ、ワーカー・ノード間でのみルーティングが行われます。 競合を避けるために、ご使用のワーカー・ノードと通信するノードにはこの IP 範囲を使用しないでください。 ワーカー・ノードとポッドは、プライベート IP アドレスを使用してプライベート・ネットワーク上で安全に通信できます。 しかし、ポッドが異常終了した場合やワーカー・ノードを再作成する必要がある場合は、新しいプライベート IP アドレスが割り当てられます。
-	**{{site.data.keyword.containerlong_notm}} サービス・ネットワーク** – {{site.data.keyword.containerlong_notm}} では、クラスター内のサービス・アドレスに 172.21.0.0/16 が使用されます。 そのほかに、以下の 2 つの IP アドレス範囲があります。
    - パブリック – {{site.data.keyword.cloud_notm}} から IP アドレス範囲が提供されるパブリック・ポータブル・サブネット。 この IP アドレス範囲は、ALB または Ingress サービスを介してアプリケーションをインターネットに公開するために使用されます。
    - プライベート – {{site.data.keyword.cloud_notm}} から IP アドレス範囲が提供されるプライベート・ポータブル・サブネット。 この IP アドレス範囲は、ALB または Ingress サービスを介してアプリケーションをプライベート・ネットワークに公開するために使用されます。
- **{{site.data.keyword.containerlong_notm}} ワーカー・ノード・ネットワーク** - 以下の 2 つのワーカー・ノード・ネットワーク IP アドレス範囲があります。
    - パブリック – {{site.data.keyword.cloud_notm}} から IP アドレス範囲が提供されるパブリック・プライマリー・サブネット。
    - プライベート – {{site.data.keyword.cloud_notm}} から IP アドレス範囲が提供されるプライベート・プライマリー・サブネット。
-	**vCenter Server ホスト・ネットワーク** - 以下の 2 つの vCenter Server ホスト・ネットワーク IP アドレス範囲があります。
    - パブリック – {{site.data.keyword.cloud_notm}} から IP アドレス範囲が提供されるパブリック・プライマリー・サブネット。
    - プライベート – {{site.data.keyword.cloud_notm}} から IP アドレス範囲が提供されるプライベート・プライマリー・サブネット。
-	**vCenter Server ESG ネットワーク** - 以下の 2 つの vCenter Server ESG ネットワーク IP アドレス範囲があります。
    - パブリック – {{site.data.keyword.cloud_notm}} から IP アドレス範囲が提供されるパブリック・ポータブル・サブネット。
    - プライベート – {{site.data.keyword.cloud_notm}} から IP アドレス範囲が提供されるプライベート・ポータブル・サブネット。
-	**vCenter Server VM ネットワーク** – {{site.data.keyword.cloud_notm}} 提供のサブネットと競合しない BYOIP 範囲を使用するエンタープライズ IP アドレス範囲。
-	**{{site.data.keyword.icpfull_notm}} ポッド・ネットワーク** – {{site.data.keyword.cloud_notm}} 提供のサブネットと競合しない BYOIP 範囲を使用するエンタープライズ IP アドレス範囲。 ポッドとサービスの IP アドレス範囲は、cluster/config.yaml で構成できます。
-	**{{site.data.keyword.icpfull_notm}} サービス・ネットワーク** – {{site.data.keyword.cloud_notm}} 提供のサブネットと競合しない BYOIP 範囲を使用するエンタープライズ IP アドレス範囲。 ポッドとサービスの IP アドレス範囲は、cluster/config.yaml で構成できます。
-	**{{site.data.keyword.icpfull_notm}} ワーカー・ノード・ネットワーク** – いずれの {{site.data.keyword.cloud_notm}} 提供サブネットとも競合しない BYOIP 範囲を使用するエンタープライズ IP アドレス範囲。

## ネットワーク・トラフィック・フロー

以下のトラフィック・フローについて説明します。
-	インターネット上の外部ユーザーから {{site.data.keyword.containerlong_notm}} のコンテナーでホストされる Web 層まで。
-	インターネット上の外部ユーザーから {{site.data.keyword.icpfull_notm}} のコンテナーでホストされる Web 層まで。
-	{{site.data.keyword.containerlong_notm}} のコンテナーでホストされる Web 層から vCenter Server の VM でホストされるデータベース層まで
-	{{site.data.keyword.icpfull_notm}} のコンテナーでホストされる Web 層から vCenter Server の VM でホストされるデータベース層まで
-	企業ネットワーク・アクセスが可能なエンタープライズ・ユーザーから vCenter Server の VM まで。

### インターネット上の外部ユーザーから IBM Cloud Kubernetes Service のコンテナーでホストされる Web 層まで

1.	外部ユーザーが URL を使用して Web 層に要求を出します。
2.	DNS を使用して IP アドレスが判別されます。 この IP アドレスは、ALB または Ingress サービスに割り当てられたポータブル・サブネット上の {{site.data.keyword.cloud_notm}} パブリック・アドレスです。
3.	パブリック・ネットワークは、ALB または Ingres サービスをホストするワーカー・ノードに要求を自動的に転送します。
4.	ワーカー・ノードが要求を ALB または Ingress サービスの内部クラスター IP アドレスおよびポート番号に転送します。 この内部クラスター IP アドレスはクラスター内でのみアクセス可能です。
5.	ワーカー・ノード内で、kube-proxy が要求を ALB または Ingress サービスにルーティングします。
6.	同じワーカー・ノード上にアプリケーションがある場合は、iptables を使用して、要求の転送に使用される内部インターフェースが判別されます。 別のワーカー・ノード上にアプリケーションがある場合は、Calico vRouter が IP-in-IP カプセル化を使用して該当するワーカー・ノードにルーティングしますが、これは、そのワーカー・ノードが別のサブネット上にある場合に限られます。

### インターネット上の外部ユーザーから IBM Cloud Private のコンテナーでホストされる Web 層まで

1.	外部ユーザーが URL を使用して Web 層に要求を出します。
2.	DNS を使用して IP アドレスが判別されます。 この IP アドレスは、vCenter Server インスタンスに割り当てられるポータブル・サブネット上の {{site.data.keyword.cloud_notm}} パブリック・アドレスです。
3.	パブリック・ネットワークは、ESG をホストする vSphere ESXi ホストに、要求を自動的に転送します。
4.	ESG が要求を ALB または Ingress サービスの内部クラスター IP アドレスおよびポート番号に転送します。 ESG と ALB または Ingress サービスが別々の vSphere ESXi ホスト上にある場合、IP パケットは VXLAN フレームにカプセル化されます。 この内部クラスター IP アドレスはクラスター内でのみアクセス可能です。
5.	ワーカー・ノード内で、kube-proxy が要求を ALB または Ingress サービスにルーティングします。
6.	同じワーカー・ノード上にアプリケーションがある場合は、iptables を使用して、要求の転送に使用される内部インターフェースが判別されます。 別のワーカー・ノード上にアプリケーションがある場合は、Calico vRouter が IP-in-IP カプセル化を使用して、該当するワーカー・ノードにルーティングします。 IP-in-IP パケットは、ワーカー・ノードが置かれている vSphere ESXi ホストへの転送のために、VXLAN フレームにカプセル化されます。

### IBM Cloud Kubernetes Service のコンテナーでホストされる Web 層から vCenter Server の VM でホストされるデータベース層まで

ESG と vRouter 内の経路テーブルにどのようにデータが取り込まれるかは、統合方式によって異なります。 「{{site.data.keyword.containerlong_notm}} と vCenter Server の統合」を参照してください。
1.	{{site.data.keyword.containerlong_notm}} のコンテナーで実行されている Web 層が、vCenter Server インスタンス内の VM 上で実行されているデータベースに要求を出します。
2.	DNS を使用して、要求がデータベースの IP アドレスとして解決されます。
3.	コンテナーが Calico vRouter に要求を送信します。
4.	vRouter の経路テーブルには、vCenter Server インスタンスでホストされている IP アドレス範囲が取り込まれています。
5.	vRouter が要求を転送しますが、SNAT を使用して、ソース IP アドレスをポッドの IP アドレスからワーカー・ノードの IP アドレスに変更します。
6.	vRouter をホストするワーカー・ノードが要求を BCR に送信します。
7.	BCR が ESG に要求を転送します。
8.	その後 ESG は DLR に転送します。
9.	DLR が要求を必要な VXLAN 上に置きます。
10.	データベース VM が要求を受け取ります。

### IBM Cloud Private のコンテナーでホストされる Web 層から vCenter Server の VM でホストされるデータベース層まで

ESG と vRouter 内の経路テーブルにどのようにデータが取り込まれるかは、統合方式によって異なります。 「{{site.data.keyword.icpfull_notm}} と vCenter Server の統合」を参照してください。
1.	{{site.data.keyword.icpfull_notm}} のコンテナーで実行されている Web 層が、同じ vCenter Server インスタンス内の VM 上で実行されているデータベースに要求を出します。
2.	DNS を使用して、要求がデータベースの IP アドレスとして解決されます。
3.	コンテナーが Calico vRouter に要求を送信します。
4.	vRouter の経路テーブルには、vCenter Server インスタンスでホストされている IP アドレス範囲が取り込まれています。
5.	vRouter が要求を転送しますが、SNAT を使用して、ソース IP アドレスをポッドの IP アドレスからワーカー・ノードの IP アドレスに変更します。
6.	vRouter をホストするワーカー・ノードが要求を ESG に送信します。
7.	その後 ESG は DLR に転送します。
8.	DLR が要求を必要な VXLAN 上に置きます。
9.	データベース VM が要求を受け取ります。

### 企業ネットワーク・アクセスが可能なエンタープライズ・ユーザーから vCenter Server の VM まで

1.	企業の社内ネットワークに接続されているエンタープライズ・ユーザーが、vCenter Server でホストされている VM 上のリソースの要求を行います。
2.	DNS を使用して VM の IP アドレスが判別されます。 この IP アドレスは、{{site.data.keyword.cloud_notm}} まで拡張されたネットワーク上にあります。
3.	オンプレミス・ルーターが、L2 コンセントレーターをホストしている vSphere ホストにトラフィックを送信します。
4.	L2 コンセントレーターがセキュア・トンネルで要求をカプセル化し、{{site.data.keyword.cloud_notm}} でホストされているリモート L2 コンセントレーターにオンプレミス・ルーター経由で転送します。このとき、デバイスに割り当てられたプライベート・ポータブル・サブネット IP アドレスが使用されます。
5.	オンプレミス経路では、そのルーティング・テーブルを調べて、リモート L2 コンセントレーターの IP アドレスを WAN インターフェースに送信する必要があることを認識し、BCR 経由で {{site.data.keyword.cloud_notm}} XCR ルーターを介して WAN 上で転送します。
6.	L2 コンセントレーターが要求を受信し、拡張ネットワークをホストする VXLAN 上に置きます。
7.	VM が要求を受け取ります。

### その他のリソース

* [{{site.data.keyword.cloud_notm}} ネットワーク](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [コンテナーのホワイト・ペーパー](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf) (PDF ダウンロード)
* [VMware HCX on {{site.data.keyword.cloud_notm}} ブログ](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [VMware HCX on {{site.data.keyword.cloud_notm}} データ・シート](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [NSX for vSphere 6.4.3 構成の最大値](https://configmax.vmware.com/guest)
* [{{site.data.keyword.cloud_notm}} プラットフォームの資料](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [{{site.data.keyword.containerlong_notm}}](/docs/containers/container_index.html)
* [Project Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)
