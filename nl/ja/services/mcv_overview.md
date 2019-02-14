---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Mission Critical VMware on IBM Cloud の概要

Mission Critical VMware on {{site.data.keyword.cloud}} では、企業がクラウド・アプリケーションのダウン時間をなくし、クラウド領域内でのフェイルオーバーを自動化できるようにするための、マルチゾーン・クラウド・アーキテクチャーを提供しています。

ほとんどの場合、お客様がこのクラウド・アーキテクチャーを使用すると、オンプレミス環境または競合他社のクラウド・プラットフォームで VMware ユーザーが作業する場合より、高い可用性とフェイルオーバー成功率を実現できます。

このアーキテクチャーは、クラウド・ネイティブではないアプリケーションを含む既存のミッション・クリティカルなレガシー・ワークロードを、総計 99.99% という可用性目標でサポートします。IBM Cloud のマルチゾーン領域は、サイトに障害が発生した場合に基幹業務ワークロードをオンライン状態に保つように設計されています。 障害が発生したサイトのワークロードは、ほぼリアルタイムで自動的に再開しますが、隣接するサイトのワークロードはオンライン状態を保ち、引き続き使用できます。

このアーキテクチャーは、さまざまなエンタープライズ・サービスを網羅し、クラウド・ベースのアプリケーションの監視とトラブルシューティングを行うために作成されたネットワーク、ストレージ、回復力などのツールを備えています。 さらに、このアーキテクチャーは、{{site.data.keyword.cloud_notm}} 上に構築された IBM Services Platform with Watson と統合することができますので、より広範囲にサービスを利用できます。 お客様はプラットフォームのコグニティブ機能を使用して、継続的運用の維持に役立つ新しいビジネス洞察を得るために、より効率的にデータをマイニングできます。

## Mission Critical VMware on IBM Cloud の技術仕様

Mission Critical VMware on {{site.data.keyword.cloud_notm}} のアーキテクチャーは、お客様のワークロードの自動フェイルオーバーを提供するエンドツーエンドのリファレンス・アーキテクチャーです。 IBM マネージド・サービスによる {{site.data.keyword.cloud_notm}} マルチゾーン領域を使用して、以下の構成要素をカバーします。

* 計算アーキテクチャー (VMware vSphere)
* ネットワーク体系 (現在は NSX-V)
* ストレージ・アーキテクチャー (VMware vSAN)
* IBM Services Platform with Watson との統合によるサービス利用の有効化
* モニター、トラブルシューティング、パフォーマンス、およびキャパシティー管理のためのツール:
  * vRealize Suite パターン (Operations、Log Insight、および Network Insight)
  * Active Directory パターン
  * 自動チケット、アラート、およびイベント・エンリッチのための Netcool/Bluecare との統合
  * 回復力パターン (バックアップとリカバリー)

Mission Critical VMware on {{site.data.keyword.cloud_notm}} は、以下の地域で使用可能です。
* アメリカ: 北米南部地域: ダラスのすべての IBM Cloud データ・センター。北米東部地域: ワシントン DC のすべての IBM Cloud データ・センター
* ヨーロッパ: フランクフルトとロンドンのすべての IBM Cloud データ・センター
* アジア太平洋: シドニーと東京のすべての IBM Cloud データ・センター

### 基本インフラストラクチャー・アーキテクチャーの仕様

基のインフラストラクチャーには以下の仕様があります。
* 各サイトには専用のエッジおよび管理クラスターがあります
* リソース・クラスターは vSphere + vSAN の拡張クラスターです
* witness サイトには witness ESXi ホストが含まれます
* 単一 vCenter と NSX Manager のアーキテクチャーです
* L3 ネットワーク・アーキテクチャーを介して vCenter High Availability (HA) を使用する、組み込みプラットフォーム・サービス・コントローラー (PSC) を備えた vCenter Server Appliance
* NSX Manager のリカバリーでは、バックアップ・ファイルを同期するホット/スタンバイ方式を使用します

### ツールおよびテクノロジー・アーキテクチャーの仕様

ツールおよびテクノロジー・アーキテクチャーには以下の仕様があります。
* vRealize Operations、vRealize Log Insight、および vRealize Network Insight が、使用されている VMware 製品 (NSX、vSAN、vSphere など) に固有の操作と管理機能を提供します
* IBM Software Defined Environment Automation Tool Health Check (SAT HC) が、ベスト・プラクティスとセキュリティー・ポリシーに照らしてデプロイメントを検証します
* 地域外の {{site.data.keyword.cloud_notm}} サイトに振り向けるオプションの災害復旧 (DR)
* Fortigate Security Appliance などが、インターネット・アクセスを保護して、アクティブ/アクティブ・ネットワークとオンプレミス・ネットワークとの統合を実現します

### vSphere + vSAN 拡張クラスター・アーキテクチャーの仕様

vSphere + vSAN 拡張クラスター・アーキテクチャーには以下の仕様があります。
* このクラスターは、2 つのサイトにまたがるストレージおよび計算機能を提供し、可用性を強化します。
* 仮想マシン (VM) からの書き込み要求は両方のサイトに同期的に書き込まれ、サイト間ネットワーク待ち時間が発生します。
* VM からの読み取り要求は、VM が配置されている物理ロケーションに対してローカルに実行されるため、余分な待ち時間を回避できます。
* witness サイトと witness ホストはスプリット・ブレイン/クォーラムとして機能します。
* vSAN ネイティブ暗号化 (Rest 暗号化用) は、このアーキテクチャーと組み合わせて使用できます。

### ネットワーク体系の仕様

ネットワーク体系には以下の仕様があります。
* Edge/DLR/VXLAN を BGP メトリック・ベースのルーティングと組み合わせて使用すると、自動フェイルオーバーを使用したアクティブ/アクティブ・サイト設計が容易になります。
* 各サイトには、独自の Edges/DLR と VXLAN のセットに基づく概念があります。
* 通常の環境では、DLR-A に接続されたすべての VM (例えば VM-A) は、{{site.data.keyword.cloud_notm}} アベイラビリティー・ゾーン #1 に属し、トラフィックはローカルで出入りします。
* VM-A の vMotion アクティビティー時は、トラフィックは引き続き {{site.data.keyword.cloud_notm}} アベイラビリティー・ゾーン #1 を介して出入りします。
* サイトやエッジの障害時には、トラフィックが残りの使用可能なサイトからルーティングされます。

### 関連リンク

* [Mission Critical VMware on IBM Cloud の要求](/docs/services/vmwaresolutions/services/managing_mcv.html)
