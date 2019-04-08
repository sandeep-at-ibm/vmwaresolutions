---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# VMware コンポーネント・エディションの比較チャート
{: #solution-appendix}

## VMware NSX エディションの比較
{: #solution-appendix-nsx-editions}

この設計では、ライセンスの必要なコンポーネントが複数あります。環境を適切に運用するのに必要な最小限のライセンスをここにまとめます。

表 1. ライセンス要件

コンポーネント | 目的 | 使用許諾条件
----------|---------|-------------
**vSphere** | コンピュートの仮想化 | vSphere 6.7 Enterprise Plus
**vCenter Server** | インフラストラクチャー管理 | vCenter Server 6.7 Standard
**NSX** | ネットワークの仮想化 | NSX Base for Service Providers 6.4
**vSAN** | ストレージの仮想化 | vSAN 6.6 Advanced  

NSX Base for Service Providers エディションを使用できるのは、VMware vCloud Air Network (vCAN) を使用するサービス・プロバイダーの場合に限られます。このエディションの機能を以下の表にまとめます。
{:note}

表 2. VMware NSX エディションの比較チャート

| NSX 機能                                   | Base | Advanced | Enterprise |
|-----------------------------------------------|------|----------|------------|
| 分散スイッチングとルーティング             | •    | •        | •          |
| NSX Edge ファイアウォール                             | •    | •        | •          |
| NAT                                           | •    | •        | •          |
| NSX Edge ロード・バランシング                       | •    | •        | •          |
| VPN (IPsec)                                   | •    | •        | •          |
| VPN (SSL)                                     | •    | •        | •          |
| API 主導の自動化                         | •    | •        | •          |
| vRealize および OpenStack との統合\*     | •    | •        | •          |
| vRealize によるセキュリティー・ポリシーの自動化 |      | •        | •          |
| 物理環境への SW L2 ブリッジング        |      | •        | •          |
| ECMP による動的ルーティング (アクティブ - アクティブ)     |      | •        | •          |
| 分散ファイアウォール                       |      | •        | •          |
| Active Directory との統合             |      | •        | •          |
| サーバー活動のモニター                    |      | •        | •          |
| サービス挿入 (サード・パーティー統合)     |      | •        | •          |
| 分散ロード・バランシング                    |      |          | •          |
| クロス vCenter NSX                             |      |          | •          |
| マルチサイト NSX 最適化                  |      |          | •          |
| リモート・ゲートウェイ                                |      |          | •          |
| HW VTEP との統合                     |      |          | •          |
\*L2、L3 & NSX Edge の統合のみ。 セキュリティー・グループは使用されません

## VMware vSAN エディションの比較
{: #solution-appendix-vsan-editions}

以下の表には、ソリューションによってサポートされる、VMware vSAN の **Advanced** および **Enterprise** エディションで使用可能な機能をリストしています。

表 3. VMware vSAN エディションの比較チャート

| vSAN 機能                                    | Advanced | Enterprise |
|-------------------------------------------------|----------|------------|
| ストレージ・ポリシー・ベースの管理                 | •        | •          |
| フラッシュの読み取り/書き込みキャッシュ                        | •        | •          |
| 分散 RAID                                | •        | •          |
| 仮想分散スイッチ                      | •        | •          |
| ラック認識                                  | •        | •          |
| vSphere 複製                             | •        | •          |
| ソフトウェア・チェックサム                               | •        | •          |
| オールフラッシュ・ハードウェア                              | •        | •          |
| iSCSI ターゲット・サービス                            | •        | •          |
| IOPS 制限                                      | •        | •          |
| 重複排除および圧縮                   | •        | •          |
| RAID-5/6 消去コーディング                         | •        | •          |
| Data at Rest (保存されたデータ) の暗号化                         |          | •          |
| ローカル障害保護のある拡張クラスター |          | •          |

## 関連リンク
{: #solution-appendix-related}

* [ソリューションの概要](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [設計の概要](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [コンポーネントのバックアップ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
