---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# NSX Edge Services Gateway について

VMware NSX Edge Services Gateway (ESG) ソリューションは、{{site.data.keyword.cloud_notm}} で現在使用可能な VMware Cloud Foundation on {{site.data.keyword.cloud}} および vCenter Server on {{site.data.keyword.cloud_notm}} オファリングの拡張です。 Cloud Foundation および vCenter Server のソリューション・アーキテクチャーに、このソリューションの各コンポーネントと、設計での各コンポーネントの構成概要が詳しく示されます。

Cloud Foundation および vCenter Server の設計について詳しくは、[ソリューションの概要](../solution/solution_overview.html)を参照してください。

## NSX Edge Services Gateway の概要

NSX Edge Services Gateway は、動的ホスト構成プロトコル (DHCP)、仮想プライベート・ネットワーク (VPN)、ネットワーク・アドレス変換 (NAT)、動的ルーティング、ロード・バランシングなどの共通ゲートウェイ・サービスを提供することにより、分離されたスタブ・ネットワークを共有 (アップリンク) ネットワークに接続します。 NSX Edge の一般的なデプロイメントには、非武装地帯 (DMZ)、VPN エクストラネット、およびテナント、ワークロード、または管理コンポーネントごとに NSX Edge が仮想境界を作成するマルチテナント・クラウド環境が含まれます。 NSX Edge Service Gateway では、以下の機能を使用できます。

表 1. NSX Edge Service Gateway で使用可能な機能

| 機能 | 説明 |
|:------- |:----------- |
| NSX Edge サービス・ルーティング | レイヤー 2 ブロードキャスト・ドメイン間で必要な転送情報を提供します。レイヤー 2 ブロードキャスト・ドメインを減らし、ネットワークの効率とスケールを向上させることができます。 NSX は、この情報を、東西ルーティングを行うためのワークロードがある場所に拡張します。 これにより、コストをかけず、タイムリーなホップの拡張を必要とせずに、より直接的な仮想マシン間通信が可能になります。 同時に、NSX は南北接続も提供するため、テナントがパブリック・ネットワークにアクセスできるようになります。|
| ファイアウォール | サポートされるファイアウォールのルールには、すべてのプロトコルのステートフル・インスペクション用の IP とポートの範囲を持つ IP 5 タプル構成が含まれます。 |
| NAT | ソース IP アドレスと宛先 IP アドレス、およびポート変換を個別に制御します。|
| DHCP | IP プール、ゲートウェイ、DNS サーバー、および検索ドメインの構成を提供します。 |
| サイト間 VPN | 標準化された IPSec プロトコル設定を使用して、すべての主要な VPN ベンダーと相互運用します。 |
| L2VPN | L3 トポロジーをまたいで L2 ネットワークを拡張します。|
| SSL VPN-Plus |  SSL VPN-Plus により、リモート・ユーザーは NSX Edge Gateway の内側にあるプライベート・ネットワークに安全に接続できます。 |
| ロード・バランシング | 単純で動的に構成可能な仮想 IP アドレスおよびサーバー・グループを提供します。 |
| 高可用性 | プライマリー NSX Edge 仮想マシンが使用不可の場合に、ネットワーク上にアクティブな NSX Edge を確保します。 |

### 関連リンク

* [ソリューションの概要](../solution/solution_overview.html)
