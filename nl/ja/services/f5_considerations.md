---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-24"

---

# F5 on IBM Cloud の概要

F5 on {{site.data.keyword.cloud}} サービス (F5 BIG-IP® Virtual Edition) は、ローカルとグローバルの規模でのインテリジェントな L4 から L7 までのロード・バランシング・サービスとトラフィック管理サービス、ネットワークと Web アプリケーションのための堅固なファイアウォール保護、セキュアなフェデレート・アプリケーション・アクセスを提供します。

必要に応じて、このサービスの複数のインスタンスをインストールできます。

**利用可否**: このサービスは、V1.9 以降のリリースでデプロイされたインスタンスでのみ利用可能です。

## F5 on IBM Cloud の技術仕様

以下のコンポーネントが F5 on {{site.data.keyword.cloud_notm}} サービスに含まれています。

### 仮想マシン
* すべてのオプションが使用可能な 2 つの仮想マシン (VM)。
* ライセンス・オプションに応じて仮想マシンあたり 2、4、または 8 つの vCPU。
* ライセンス・オプションに応じて仮想マシンあたり 4、8、または 16 GB の RAM。

### ネットワーキング
* 高可用性 (HA) 同期のためのプライベート仮想拡張可能 LAN (VXLAN)。
* プライベート管理ネットワーク経由のトラフィック管理シェル (TMSH) および管理コンソールへのアクセス。

### ライセンスと料金
各 VM のライセンス料は、ライセンス・オプション (Good、Better、または Best) と選択した帯域幅に応じて各請求サイクルに適用されます。

**重要:** サービスのインストール後にライセンス交付レベルを変更することはできません。 ライセンス交付レベルを変更するには、既存のサービスを削除し、別のライセンス交付オプションを使用してサービスを再インストールする必要があります。

## F5 on IBM Cloud のインストールの注意点

F5 on {{site.data.keyword.cloud_notm}} サービスをインストールする前に、以下の考慮事項を確認してください。

選択したライセンス・モデルと帯域幅に基づいて、次の構成の 2 つの BIG-IP VE VM (仮想マシン) がデプロイされます。

表 1. さまざまな帯域幅やライセンス・モデルを選択した場合の CPU と RAM のデプロイメント

| 最大帯域幅 | ライセンス・モデル: Good | ライセンス・モデル: Better | ライセンス・モデル: Best |
|:------------------|:--------------------|:----------------------|:--------------------|
| 25 Mbps           | 2 vCPU、4 GB RAM    | 4 vCPU、8 GB RAM      | 8 vCPU、16 GB RAM   |
| 200 Mbps          | 2 vCPU、4 GB RAM    | 4 vCPU、8 GB RAM      | 8 vCPU、16 GB RAM   |
| 1 Gbps            | 2 vCPU、4 GB RAM    | 4 vCPU、8 GB RAM      | 8 vCPU、16 GB RAM   |
| 3 Gbps            | 8 vCPU、16 GB RAM   | 8 vCPU、16 GB RAM     | 8 vCPU、16 GB RAM   |
| 5 Gbps            | 8 vCPU、16 GB RAM   | 8 vCPU、16 GB RAM     | 8 vCPU、16 GB RAM   |
| 10 Gbps           | 8 vCPU、16 GB RAM   | 8 vCPU、16 GB RAM     | 8 vCPU、16 GB RAM   |

**注:**

* F5 BIG–IP は、選択された最大帯域幅に基づいてアプライアンスのスループットを制限します。 ネットワーク・パフォーマンスは多くの要因の影響を受けるため、選択された最大帯域幅をすべての構成とトポロジーで達成できるとは限りません。
* デフォルト・クラスターにのみ BIG-IP VE VM の HA (高可用性) ペアがデプロイされます。

  また、2 つの BIG-IP VE VM 用に CPU と RAM が 100% 予約されます。これらの VM はネットワーク通信のデータ・プレーンに配置されているので、リソースを使用できるようにしておくことが重要だからです。

  単一の BIG-IP VE VM 用の CPU と RAM の予約を計算するには、次の数式を使用します。

  `CPU 予約 = ESXi サーバーの CPU 速度 * vCPU の数` (表 1 から)

  `RAM 予約 = RAM サイズ` (表 1 から)

### 計画時の考慮事項
F5 on {{site.data.keyword.cloud_notm}} での失敗を避けるために、以下の要件を満たす必要があります。
* 各 VM を別々のサーバーに配置するというアンチアフィニティー・ルールに従ってデプロイされる 2 つの BIG-IP VE VM に、少なくとも 2 台のアクティブ ESXi サーバーを使用できる。
* CPU と RAM が 100% 予約されるという条件で、ESXi サーバーごとに 1 つの BIG-IP VE VM をホストできるだけのリソースを 2 つのアクティブ ESXi サーバーで使用できる。
* CPU と RAM を 100% 使用する 2 つの BIG-IP VM をホストできるだけのリソースが VMware vSphere HA にある。

これらの要件を考慮して、F5 on {{site.data.keyword.cloud_notm}} に必要なスペースの計画を立てる必要があります。 必要であれば、F5 on {{site.data.keyword.cloud_notm}} を注文する前に、インスタンスに ESXi サーバーを 1、2 台追加するか、フェイルオーバー用の vSphere HA CPU 予約を減らす、あるいはその両方を行ってください。

## F5 on IBM Cloud の注文例

16 コア (それぞれ 2.10 GHz) で 128 GB RAM という構成の 2 台の ESXI サーバーを持つ VMware vCenter Server の**「スモール」**インスタンスを注文するとします。 F5 on {{site.data.keyword.cloud_notm}} では、**「Best」**ライセンス・モデルを選択し、**「最大帯域幅」**の値として 5 Gbps を選択します。

このケースでは、1 つの BIG-IP VM はサーバーごとに以下のリソースを必要とします。
* 2.1 GHz * 8 vCPU = 16.8 GHz の CPU、および
* 16 GB RAM

合計で、BIG-IP VM 2 つ分として 33.6 GHz CPU と 32 GB RAM になります。

各 ESXi サーバーには 16 コア * 2.1 GHz = 33.6 GHz の能力があります。したがって、両方のサーバーがアクティブであり、各サーバーで少なくとも 16.8 GHz の CPU と 16 GB RAM を使用できれば、最初の 2 つの要件を満たすことになります。

ただし、デフォルトでは、2 台の ESXi サーバーとともに最初にデプロイされた vCenter Server インスタンスでのフェイルオーバーに備えて、vSphere HA のために CPU と RAM が 50 % 予約されます。この例の場合、次のように計算されます。

`2 * 16 コア * 2.1 GHz の 50% = 33.6 GHz を使用可能`

ESXi サーバー上には、VMware vCenter Server、VMware NSX Controller、VMware NSX Edge など、他のワークロードも存在するようになるため、これらのリソースを使用しても 3 番目の要件を満たすことができません。2 つの BIG-IP VM 用に 33.6 GHz の CPU と 32 GB RAM が必要だからです。

このケースでは、環境に ESXi サーバーを少なくとも 1 つ追加し、vShpere HA フェイルオーバー予約を適切に更新して 2 つの BIG-IP VE VM 用の十分なリソースを確保しない限り、F5 on {{site.data.keyword.cloud_notm}} のインストールは失敗する可能性があります。 F5 on {{site.data.keyword.cloud_notm}} サービスを実行するために追加のリソースが必要な場合は、F5 on {{site.data.keyword.cloud_notm}} をインストールする前に、さらに ESXi サーバーを追加できます。

## F5 on IBM Cloud を削除する際の考慮事項

F5 on {{site.data.keyword.cloud_notm}} サービスを削除する前に、既存の BIG-IP VE 構成を正しく削除しておく必要があります。 特に、ネットワーク・トラフィックは、BIG-IP VE を経由するのではなく、BIG-IP VE を迂回してルーティングする必要があります。 そうしないと、ご使用の環境からの既存のデータ・トラフィックが影響を受ける可能性があります。

### 関連リンク

* [F5 on {{site.data.keyword.cloud_notm}} の注文](f5_ordering.html)
* [F5 on {{site.data.keyword.cloud_notm}} の管理](managing_f5.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [F5 Web サイト](https://f5.com/){:new_window}
