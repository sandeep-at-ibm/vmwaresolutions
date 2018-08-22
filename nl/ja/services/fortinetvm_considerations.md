---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# FortiGate Virtual Appliance on IBM Cloud の概要

FortiGate Virtual Appliance on {{site.data.keyword.cloud}} サービスでは、ご使用の環境に FortiGate Virtual Appliances のペアがデプロイされます。これによって、仮想インフラストラクチャー内に重要なセキュリティー管理が実装されるので、リスクを軽減するのに役立ちます。

必要に応じて、このサービスのインスタンスを複数インストールできます。 このサービスの管理には、FortiOS Web Client、または SSH を介したコマンド・ライン・インターフェースを使用します。

**利用可否**: このサービスは、V2.0 以降のリリースでデプロイされたインスタンスでのみ利用可能です。

## FortiGate Virtual Appliance on IBM Cloud の技術仕様

以下のコンポーネントが注文され、FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

### 仮想マシン

* すべてのオプションには、仮想マシンの高可用性 (HA) ペアが含まれます
* デプロイメント・サイズとサブスクリプション・タイプに応じて、仮想マシンあたり 2、4、または 8 個の vCPU
* デプロイメント・サイズとサブスクリプション・タイプに応じて、仮想マシンあたり 4、6、または 12 GB の RAM

### 高可用性

2 台の仮想マシンがデプロイされ、HA または Virtual Router Redundancy Protocol (VRRP) の構成ができる状態になっています。

### ネットワーキング

FortiGate® コンソールへのアクセス権限がプライベート管理ネットワークを介して提供されます。

### ライセンスと料金

選択したデプロイメント・サイズと月ごとのサブスクリプション・ライセンス・モデルに応じて、各仮想マシンのライセンス料金が各課金サイクルに適用されます。

**重要:** サービスのインストール後にライセンス交付レベルを変更することはできません。ライセンス交付レベルを変更するには、既存のサービスを削除し、別のライセンス交付オプションを使用してサービスを再インストールする必要があります。

## FortiGate Virtual Appliance on IBM Cloud をインストールする際の考慮事項

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスをインストールする前に、以下の考慮事項を確認してください。
* FortiGate 仮想マシン (VM) はデフォルト・クラスターにのみデプロイされます。
* 2 つの FortiGate VM 用に CPU と RAM が 100% 予約されます。これらの VM はネットワーク通信のデータ・プレーンに配置されているので、
  それらのためにリソースを使用できるようにしておくことが重要だからです。

  単一の FortiGate VM 用の CPU と RAM の予約を計算するには、次の数式を使用します。
   * `CPU 予約 = ESXi サーバーの CPU 速度 * vCPU の数`
   * `RAM 予約 = RAM サイズ`
* ご使用のインスタンスに FortiGate Virtual Appliance の HA ペアをデプロイすると、Management NSX Edge Services Gateway (ESG) 上に SNAT とファイアウォールのルールが定義されるとともに、FortiGate Virtual Appliance 上に静的経路が定義されます。これにより、ライセンス・アクティベーションの場合や、最新のセキュリティー・ポリシーとコンテンツを取得する場合に、インスタンスからパブリック・ネットワークへのアウトバウンド HTTPS 通信が可能になります。
* サービスのインストール後にライセンス・レベルを変更することはできません。 ライセンス・レベルを変更するには、既存のサービスを削除してから、別のライセンス・オプションを選択してサービスを再インストールする必要があります。
* FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} での失敗を避けるために、以下の要件を満たす必要があります。
   * 各 VM を別々のサーバーに配置するというアンチアフィニティー・ルールに従ってデプロイされる 2 つの FortiGate VM に、少なくとも 2 台のアクティブ ESXi サーバーを使用できる。
   * CPU と RAM が 100% 予約されるという条件で、ESXi サーバーごとに 1 つの FortiGate VM をホストできるだけのリソースを 2 つのアクティブ ESXi サーバーで使用できる。
   * CPU と RAM を 100% 使用する 2 つの FortiGate VM をホストできるだけのリソースが VMware vSphere HA にある。

  これらの要件を考慮して、FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} に必要なスペースの計画を注意深く立てる必要があります。 必要であれば、FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} を注文する前に、インスタンスに ESXi サーバーを 1、2 台追加するか、フェイルオーバー用の vSphere HA CPU 予約を減らす、あるいはその両方を行ってください。

## FortiGate Virtual Appliance on IBM Cloud の注文例

16 コア (それぞれ 2.10 GHz) で 128 GB RAM という構成の 2 台の ESXi サーバーを持つ VMware vCenter Server の**「スモール」**インスタンスを注文するとします。 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} では、デプロイメント・サイズとして**「ラージ」**(8 vCPU / 12 GB RAM) を選択し、任意のサブスクリプション・ライセンス・モデルを選択します。

このケースでは、1 つの FortiGate VM はサーバーごとに以下のリソースを必要とします。
* 2.1 GHz * 8 vCPU = 16.8 GHz の CPU、および
* 12 GB RAM

合計で、FortiGate VM 2 つ分として 33.6 GHz CPU と 24 GB RAM になります。

各 ESXi サーバーには 16 コア * 2.1 GHz = 33.6 GHz の能力があります。したがって、両方のサーバーがアクティブであり、各サーバーで少なくとも 16.8 GHz の CPU と 12 GB RAM を使用できれば、最初の 2 つの要件を満たすことになります。

ただし、デフォルトでは、2 台の ESXi サーバーとともに最初にデプロイされた vCenter Server インスタンスでのフェイルオーバーに備えて、vSphere HA のために CPU と RAM が 50% 予約されます。そのため、実際には次のようになります。

`2 * 16 コア * 2.1 GHz の 50% = 33.6 GHz を使用可能`

ESXi サーバー上には、IBM CloudDriver、VMware NSX Controller、VMware NSX Edge などの他のワークロードも存在するようになるため、これらのリソースを使用しても 3 番目の要件を満たすことができません。 なぜなら、2 つの FortiGate VM 用に 33.6 GHz の CPU と 24 GB RAM が必要になるためです。

このケースでは、環境に ESXi サーバーを少なくとも 1 つ追加し、vShpere HA フェイルオーバー予約を適切に更新して 2 つの FortiGate VM 用の十分なリソースを確保しない限り、FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} のインストールは失敗する可能性があります。

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスを実行するために追加のリソースが必要な場合は、サービスをインストールする前に、さらに ESXi サーバーを追加できます。

## FortiGate Virtual Appliance on IBM Cloud を削除する際の考慮事項

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスを削除する前に、既存の FortiGate Virtual Appliance の構成を正しく削除しておく必要があります。 特に、ネットワーク・トラフィックは、FortiGate Virtual Appliance を経由するのではなく、FortiGate Virtual Appliance を迂回してルーティングする必要があります。 そうしないと、ご使用の環境内の既存のデータ・トラフィックが影響を受ける可能性があります。

### 関連リンク

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の注文](fortinetvm_ordering.html)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} の管理](managingfortinetvm.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet Web サイト](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
