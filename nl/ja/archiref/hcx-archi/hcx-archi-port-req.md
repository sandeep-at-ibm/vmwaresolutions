---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# VMware HCX on IBM Cloud ポートのアクセス要件
{: #hcx-archi-port-req}

HCX は、公衆インターネットと専用回線を経由して、ネットワーク、スイッチ、ポート・グループなどのデータ・センターのコンポーネントに接続する必要があります。

次の表に、ハイブリッド・クラウド・サービスの仮想アプライアンスを正常にインストールするために開く必要があるポートを示します。 vSphere 環境と IBM Cloud 環境の両方で、vSphere オンプレミス・デバイスと IBM Cloud デバイスが Network Time Protocol (NTP) のクロック同期を実行できなければなりません。 UDP ポート 123 に、ハイブリッド・クラウド・サービスの仮想アプライアンスとネットワークがアクセスできる必要があります。 インストールされている NTP サーバーを、ハイブリッド・クラウド・サービス・アプライアンスのインストール時に指定できます。

表 1. ポートのアクセス要件

| ソース | ターゲット       | ポート | プロトコル | 目的         | サービス |
|--------|--------------|------|----------|-----------------|----------|
| HCX    | カスタマー DNS | 53   | TCP/UDP  | 名前解決 | DNS      |
| HCX    | IBM Cloud 内の NSX LB | 443 | TCP | 登録サービス | HTTPS |
| HCX    | IBM Cloud 内の vCenter | 443 | TCP | HCX REST サービス | HTTPS |
| HCX    | IBM Cloud 内の PSC | 443 | TCP | HCX REST サービス | HTTPS |
| HCX    | connect.hcx.vmware.com | 443 | TCP | 登録サービス | HTTPS |
| Web ブラウザー | HCX | 9443 | TCP | HCX システム構成用の HCX 仮想アプライアンス管理インターフェース | HTTPS |
| 管理ネットワーク | HCX | 22 | SSH | ハイブリッド・クラウド・サービスへの管理者の SSH アクセス | SSH |
| HCX | ESXi ホスト | 902 | TCP | HCX から IBM Cloud 内の ESXi ホストに管理とプロビジョニングの命令を送信します。 | 内部 |
| HCX | vCenter SSO サーバー | 7444 | TCP | vSphere ルックアップ・サービス |  |
| HCX | NTP サーバー | 123 | UDP | 時刻同期 | |
| HCX | Syslog |   | ユーザー設定 | HCX (クライアント) と Syslog サーバーの間の接続。 Syslog ポートとプロトコルの値は、vSphere Web Client で指定します。 例えば、UDP プロトコルの場合はポート 514 です。 | |
| HCX | クラウド・ゲートウェイ | 8123 | TCP | ハイブリッド・クラウド・ゲートウェイにホスト・ベースのレプリケーション・サービスの命令を送信します。 | HTTP |
| HCX | クラウド・ゲートウェイ | 9443 | TCP | REST API を使用して、ローカルのハイブリッド・クラウド・ゲートウェイに管理の命令を送信します。 | HTTP</br>HTTPS |
| クラウド・ゲートウェイ | L2C | 443 | TCP | L2C でハイブリッド・クラウド・ゲートウェイと同じパスを使用する場合に、クラウド・ゲートウェイから L2C に管理の命令を送信します。 | HTTP</br>HTTPS |
| クラウド・ゲートウェイ | L2C | 8443 | TCP | L2C で別のデータ・パスを使用する場合に、クラウド・ゲートウェイから L2C への双方向管理の命令。 | HTTP</br>HTTPS |
| L2C | L2C (リモート) | 443 | TCP | L2C で別のデータ・パスを使用する場合に、クラウド・ゲートウェイから L2C への双方向管理の命令。 | HTTP</br>HTTPS |
| クラウド・ゲートウェイ | ESXi ホスト | 80、902  | TCP | 管理および OVF デプロイメント | 内部 |
| ESXi ホスト | クラウド・ゲートウェイ | 31031、44046 | TCP | ホスト・ベースのレプリケーションの内部トラフィック | 内部 |
| クラウド・ゲートウェイ | ESXi ホスト | 8000  | TCP | vMotion (ゼロ・ダウン時間マイグレーション) |  |
| Cloud Gateway (ローカル) | クラウド・ゲートウェイ</br>(リモート) | 4500  | UDP | 双方向トンネルでワークロードをカプセル化するための Internet Key Exchange (IKEv2) | IPSEC |
| Cloud Gateway (ローカル) | クラウド・ゲートウェイ</br>(リモート) | 500  | UDP | 双方向トンネルの Internet Key Exchange (ISAKMP) | IPSEC |

## 関連リンク
{: #hcx-archi-port-req-related}

* [ソースでの HCX の構成およびインストール](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
