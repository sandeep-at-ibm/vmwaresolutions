---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# VMware コンポーネント・エディションの比較チャート
{: #solution-appendix}

## VMware NSX エディションの比較
{: #solution-appendix-nsx-editions}

表 1 には、ソリューションによってサポートされる、VMware NSX の **Base**、**Advanced**、および **Enterprise** エディションで使用可能な機能をリストしています。

表 1. VMware NSX エディションの比較チャート

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

表 2 には、ソリューションによってサポートされる、VMware vSAN の **Advanced** および **Enterprise** エディションで使用可能な機能をリストしています。

表 2. VMware vSAN エディションの比較チャート

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
