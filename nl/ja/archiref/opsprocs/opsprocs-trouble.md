---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-07"

---

# トラブルシューティング
{: #opsprocs-trouble}

vCenter Server インスタンスの問題をトラブルシューティングするには、システム管理者が問題の症状を見極め、影響を受けているソリューションのコンポーネントを特定し、解決策または回避策を調査して提案し、解決策をテストする必要があります。

* 症状の特定 - インスタンスのパフォーマンスが低下する原因またはパフォーマンスが出ない原因はいくつも考えられます。 効率的なトラブルシューティングの第 1 段階は、症状を正確に見極めることです。 このような症状は、vSphere のイベントとアラーム、{{site.data.keyword.cloud}} の Operations Management から報告されたり、ユーザーの 1 人からサービス・デスクを介して報告されたりする場合があります。
* 影響を受けているコンポーネントの切り分け - 問題の症状を見極めたら、ソフトウェアまたはハードウェアのコンポーネントのうち、影響を受けているもの、問題の原因である可能性があるもの、関係のないものを特定する必要があります。 {{site.data.keyword.cloud_notm}} の vCenter Operations Management などのツールが、この段階の役に立ちます。
* 解決策または回避策の提案 - 症状を把握してコンポーネントを切り分けたら、解決策や回避策を調査できます。 また、システム管理者は、この資料のトラブルシューティング・シナリオを含む {{site.data.keyword.cloud_notm}} ポータル、IBM ServiceNow、および VMware ナレッジベースを利用します。さらに、役に立つ可能性がある多数の Wiki やブログもあります。非常に迅速な解決策として、{{site.data.keyword.cloud_notm}} の Operations Management には、特定された問題への対処策が含まれています。
* ソリューション候補のテスト - 問題の症状と関係するコンポーネントが判明し、解決策/回避策を提案したら、システム管理者は問題が解決されるまで各ソリューションを体系的にテストします。

vSphere にはユーザーが構成できるイベントとアラームのサブシステムが含まれており、このサブシステムは vSphere 環境全体の発生イベントを追跡してログ・ファイルと vCenter データベースにデータを保管します。 このサブシステムでは、システム管理者がアラームのトリガー条件を指定することもできます。 アラームの状態は、システムの状態の変化に応じて「警告」からさらに重大な「アラート」に変わります。また、アラームの状態によって、システム管理者チームに E メールを送信するなどの自動化されたアラーム・アクションをトリガーできます。 この機能は、インベントリーの特定のオブジェクトまたはオブジェクト・グループに特定のイベントや状態が発生した際に通知が必要な場合や、すぐに対処しなければならない場合に便利です。

Operations Management on {{site.data.keyword.cloud_notm}} アーキテクチャーの組み込みツールなどの追加のツールを使用すると、症状の見極め、影響を受けているコンポーネントの切り分け、解決策または回避策の提案に非常に役立ちます。

## ガイドライン
{: #opsprocs-trouble-guidelines}

以下のガイドラインは、{{site.data.keyword.vmwaresolutions_short}} の問題をトラブルシューティングするためのベスト・プラクティスと見なされています。
* トラブルシューティングと問題解決に体系的に取り組みます。
* 状態、使用率、または構成のどれに関する症状なのかを見極めます。
 *  状態 - これはハードウェアとソフトウェアのコンポーネントの状態に関する症状であり、代表的な症状は「応答なし」です。 多くの場合は、高可用性設計にすることで、このような問題を隠し、ワークロードやユーザーに直接的な影響が出ないようにします。
 * 使用率 - これは容量とパフォーマンスに関する症状であり、代表的な症状は「実行速度が遅い」や「ロードできない」です。 プロアクティブに容量を管理することで、これらの問題は大幅に削減できます。
 * 構成 - 通常、この問題は新しいサービスのプロビジョン時に検出されるか、変更を適用した結果として検出されます。 誤った設定が、状態に関する症状または使用率に関する症状として表面化します。 例えば、IP アドレスが誤っていると状態に関する問題が現れますが、仮想マシン (VM) の RAM 設定が低すぎると使用率に関する症状が出ます。
* 環境内の 1 つのコンポーネントを特定するまで問題を切り分けます。
* どのような段階を踏んだのか遡れるようにメモします。
* ソフトウェアのバージョンを確認し、文書で記録します。
* サブネットと IP アドレスの使用状況 (VIP アドレスや NAT アドレスを含む) を文書で記録します。
* ネットワーク図を用意します。 物理 (アンダーレイ) 層と論理 (オーバーレイ) 層を示す複数の図が必要です。
* 最近の環境変更を確認します。
* 解決策の影響を調査します。管理インターフェースからロックアウトされないようにしてください。
* 再ロードまたはリセットが必要になった場合に備えて、重要なコンポーネントをすべて確実にバックアップしておきます。
* 一度に複数の変更を加えないでください。
* 各変更とその結果を文書に記録します。
* サポート・リクエストを作成する場合は、細かく記入して、適切な情報を提供してください。目に見える症状を明確にし、障害のあると思われるコンポーネントを特定します。必ず正しい用語を使用してください。 できる限り勘違いしない単語、あいまいでない単語を選択してください。
* vSphere ESXi と vCenter Server の構成ファイルによってシステムの動作は制御されるので、各構成ファイルの場所を確認します。 構成ファイルのほとんどの設定はインストール時に設定しますが、インストール後も変更できます。
* ログ・ファイルには、カーネルやさまざまなサブシステムとサービスによって生成されたメッセージが記録されます。 vSphere ESXi サービスと vCenter サービスは別々にログ・ファイルを保持します。 各ログ・ファイルの場所と取得方法を確認します。
* 診断に役立つ一般的なシステム管理ツールの使用法について理解します。

詳しくは、[Troubleshooting Guidelines KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window} を参照してください。

## ログ・ファイルを使用したトラブルシューティング
{: #opsprocs-trouble-logs}

ログ・ファイルは問題のトラブルシューティングの役に立つ優れた情報源です。 ただし、多数のログ・ファイルが存在するうえに、各ログに膨大な記録があるので、診断は困難です。VMware 環境の各ログ・ファイルの場所について詳しくは、[Troubleshooting with Log Files KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window} を参照してください。 多数のログ・ファイルが存在するうえに、各ログに膨大な記録があるので、Operations Management on {{site.data.keyword.cloud_notm}} のツールを利用してイベント・ログの収集と分析を行うことを検討する必要があります。

## 一般的なシナリオのトラブルシューティング
{: #opsprocs-trouble-common}

影響を受けているコンポーネントを切り分けられるように、ここでは、一般的なシナリオのトラブルシューティングについて、以下のように分類して説明します。

* 仮想マシン - このトラブルシューティングのトピックでは、VM の問題である可能性がある場合の手順を説明します。
* ホスト - このトラブルシューティングのトピックでは、vSphere ESXi ホストの問題である場合の手順を説明します。
* クラスター - このトラブルシューティングのトピックでは、可用性とリソース管理の問題である場合の手順を説明します。
* ストレージ - このトラブルシューティングのトピックでは、vSAN と NFS のストレージの問題を解決する手順を説明します。
* ネットワーク - このトラブルシューティングのトピックでは、ネットワークの問題を解決する手順を説明します。
* vCenter - このトラブルシューティングのトピックでは、vCenter の問題を解決する手順を説明します。
* ライセンス - このトラブルシューティングのトピックでは、ライセンスの問題を解決する手順を説明します。 通常、これらは、{{site.data.keyword.cloud_notm}} にライセンスを持ち込んだお客様に関係する問題です。

### 仮想マシン
{: #opsprocs-trouble-common-vm}

表 1. 仮想マシンのトラブルシューティング

| タイトル | 説明 |
|---|---|
| 一般的な VM のトラブルシューティング | 詳しくは、[Troubleshooting Virtual Machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window} を参照してください。 |
| VM のパフォーマンスの問題 | ゲスト OS のブートが遅い、アプリケーションのパフォーマンスが低い、アプリケーションの起動に時間がかかる、アプリケーションが応答しなくなるなど、VM のパフォーマンスの問題の症状に対するトラブルシューティングについては、[Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003){:new_window} を参照してください。 |
| 孤立した VM のリカバリー | vCenter データベース内に存在するのに vSphere ESXi ホストで認識されない孤立した VM のリカバリーについては、[Knowledge - KB0012862 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:new_window} を参照してください。 |
| VM がパワーオンにならない | 詳しくは、[Troubleshooting a virtual machine that is unable to power on (2001005)](https://kb.vmware.com/s/article/2001005){:new_window} を参照してください。 |
| 複製した VM またはテンプレートからデプロイした VM がパワーオンにならない | [VMware の記事](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:new_window}に、複製した VM またはテンプレートからデプロイした VM に影響する問題について記載されています。 |
| VMware Tools が古いまたはインストールされていない - VMware Tools を VM にインストールして最新の状態に保つ必要がある。 | [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:new_window} に、これらの作業の手順が記載されています。 |
| VM ネットワーク・デバイスが古い | VM ネットワーク・デバイスが最新に保たれていない場合、ネットワークのパフォーマンスとアプリケーションのパフォーマンスに影響する可能性があります。新しい仮想ネットワーク・デバイスとドライバーのデプロイ方法について詳しくは、[Choosing a network adapter for your virtual machine (1001805)](https://kb.vmware.com/s/article/1001805){:new_window} を参照してください。 |
| 仮想マシンのメモリー制限 |メモリー制限は一般的に使用されます。しかし、必要なメモリーをゲスト OS が利用できなかった場合、ゲスト OS 内のアプリケーションのパフォーマンスが低くなる可能性があります。この問題の解決方法について詳しくは、[Configuring Resource Allocation Settings](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:new_window} を参照してください。 |
| VM のスナップショット | スナップショットは便利ですが、VM のスナップショットの数量と存続期間は VM のパフォーマンスに直接影響します。 この問題の解決方法については、[Consolidate Snapshots](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:new_window} を参照してください。 |
| VM のロギング | ロギングが正しく構成されていないと、データ・ストアの容量に悪影響が及ぶ可能性があります。 この問題の解決方法については、[Configuring Logging Levels for the Guest Operating System](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:new_window} を参照してください。 |
| ネットワーク接続の問題のトラブルシューティング | 症状としては、VM がネットワークに接続できない、単一の VM とのネットワーク接続がないなどがあります。 この問題の解決方法については、[Troubleshooting virtual machine network connection issues (1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} を参照してください。  |
| 複数の仮想 CPU がパフォーマンスの問題の原因かどうかを調べる  | 複数の CPU を構成した VM にパフォーマンスの問題が発生している場合のトラブルシューティング方法については、[Determining if multiple virtual CPUs are causing performance issues (1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} を参照してください。 これらの問題には、VM との間でデータをコピーする際の転送速度が遅い、バックアップ・ジョブがタイムアウトになる、あるいは非常に遅い、VM のパフォーマンスが低いなどの問題があります。  |
| VM がパワーオフまたは再起動された  | この問題の解決方法については、[Determining why a virtual machine was powered off or restarted (1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} を参照してください。 |
| 1 つ以上の VM の応答時間が遅い |  vSphere ESXi ホストのパフォーマンスの問題の切り分けについては、[Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window} を参照してください。 パフォーマンスの問題は、 CPU の制約、メモリーのオーバー・コミットメント、ストレージ待ち時間、またはネットワーク待ち時間が原因で発生する可能性があります。 |

### vSphere ESXi ホスト
{: #opsprocs-trouble-common-host}

表 2. 標準的な vSphere ESXi ホストのトラブルシューティング

| タイトル | 説明 |
|---|---|
| ESXI コマンド | vSphere のコマンド・ライン・インターフェース、ESXi Shell コマンド、vCLI (VMware® vSphere Command‐Line Interface) コマンドの概要については、[Getting Started with vSphere Command-Line Interfaces](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:new_window} を参照してください。|
| vSphere HA ホストの状態 | vSphere HA ホストのエラー状態を示すホスト状態が vCenter から報告された場合は、解決する必要があります。この問題を解決しないと、vSphere HA で障害が発生した場合に VM を再起動することができないからです。 詳しくは、[Troubleshooting vSphere HA Host States](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window} を参照してください。 |
| vSphere ESXi ホストが無応答状態 | vCenter でホストの VM が「応答なし」、「切断」、または使用不可として表示される場合に vSphere ESXi ホストをトラブルシューティングする方法については、[ESX/ESXi hosts do not respond and is grayed out (1019082)](https://kb.vmware.com/s/article/1019082){:new_window} を参照してください。|
| VM のパワーオン時に`ファイルが見つからない`というエラーが表示される | 失われた仮想ディスク記述子ファイル (VMDK) の再作成方法については、[Recreating a missing virtual machine disk descriptor file (1002511)](https://kb.vmware.com/s/article/1002511){:new_window} を参照してください。 |
| VM のパフォーマンスの問題 | vSphere ESXi ホストのパフォーマンスの問題の切り分けについては、[Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window} を参照してください。 パフォーマンスの問題は、 CPU の制約、メモリーのオーバー・コミットメント、ストレージ待ち時間、またはネットワーク待ち時間が原因で発生する可能性があります。 |
| ベア・メタル・サーバーがダウンする | vSphere ESXi を実行しているベア・メタル・サーバーが応答しないまたはダウンしている場合は、{{site.data.keyword.cloud_notm}} 管理 UI またはコンソールにログオンし、状況を確認します。 必要に応じて、Case をオープンしてベア・メタル・サーバーに関する支援を求めます。 詳しくは、[サポート Case の処理](/docs/get-support?topic=get-support-open-case#open-case){:new_window}を参照してください。 |
| vSphere ESXi ホストが切断状態または無応答状態である  | 詳しくは、[Troubleshooting an ESXi/ESX host in non responding state (1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:new_window} を参照してください。 |
| PSOD  | PSOD (Purple Screen of Death) はカーネル・パニックの 1 つです。リカバリー不能で、実行し続けるとサービスや VM に高いリスクが及ぶことを意味するイベントまたはエラーへの応答として、vSphere ESXi カーネル (vmkernel) がこの安全対策をトリガーします。このパニックが発生して vSphere ESXi ホストがクラッシュすると、そのホスト上で実行中のすべてのサービスが終了し、ホストされているすべての VM も一緒に終了します。 VM は正常にシャットダウンされないどころか、突然パワーオフされます。 ホストがクラスターの一部であり、HA を構成している場合は、それらの VM はクラスター内の他のホスト上で再起動します。詳しくは、[Knowledge - KB0012864 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:new_window} を参照してください。 |

### ストレージ
{: #opsprocs-trouble-common-storage}

表 3. 標準的なストレージのトラブルシューティング

| タイトル | 説明 |
|---|---|
| ストレージのトラブルシューティング | 低いパフォーマンス、予測不能な障害、ディスクの破損、または VM の破損について詳しくは、[Troubleshooting storage issues when using VMware products (2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:new_window} を参照してください。 |
| vSAN のトラブルシューティング | 詳しくは、[Failure Handling in vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:new_window} を参照してください。  |
| vSAN のディスク障害 | 障害が発生したディスクの識別と交換の要求を行う方法について詳しくは、[A hard disk/magnetic disk in a VMware vSAN disk group fails (2077185)](https://kb.vmware.com/s/article/2077185){:new_window} を参照してください。|
| vSAN 健全性の問題の除去 | VMware vSphere Web Client の「監視」ページに、SAN の健全性の問題に関するアラートや警告が表示されることがあります。 これらの問題を除去する方法については、[仮想 SAN 正常性のアラートと警告](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_vsan_alerts#trbl_vsan_alerts){:new_window}を参照してください。|
| vSAN のリバランス | ディスクの健全性チェックで、クラスターのバランスに偏りがあり、スペース使用量が多いディスクと低いディスクがあるというエラーが報告された場合は、プロアクティブ・リバランスを実行する必要があります。 これにより、vSAN クラスター内のオブジェクトのリバランスを手動で開始します。 vSAN のプロアクティブ・リバランスおよびこれを適用できる状況について詳しくは、 [vSAN proactive rebalance (2149809)](https://kb.vmware.com/s/article/2149809){:new_window} を参照してください。 |
| vSAN 健全性テストの開始 | vSAN に問題があると疑われる場合は、健全性テストを開始して、クラスター・コンポーネントが想定どおりに機能しているか検証できます。 VM 作成テストを実行すると、クラスター内の各ホスト上で VM が作成され、その後、削除されます。 これらのタスクに成功した場合は、クラスター・コンポーネントが想定どおりに機能しており、クラスターは正常です。 次は、ネットワーク・パフォーマンス・テストを使用して、接続の問題を検出して診断し、ホスト間のネットワーク帯域幅が適切か確認します。 詳しくは、[Proactive Tests](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:new_window} を参照してください。 |
| vSAN のパフォーマンスの監視 | 詳しくは、[Monitoring vSAN Performance](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:new_window} を参照してください。 クラスター、ホスト、物理ディスク、VM、仮想ディスクのパフォーマンス・グラフを利用できます。 |
| vSAN のトラブルシューティング | 詳しくは、[Handling Failures and Troubleshooting vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:new_window} を参照してください。 |


### ネットワーク
{: #opsprocs-trouble-common-network}

表 4. 標準的なネットワークのトラブルシューティング

| タイトル | 説明 |
|---|---|
|  アクティブな NSX Edge 上で Edge の /var/log がいっぱいになっている | Edge ディスクが満杯というアラートが出され、/var/log パーティションがいっぱいになっていることを検出した場合の回避策については、[NSX Edge /var/log is getting full on active Edge (50108355)](https://kb.vmware.com/s/article/50108355){:new_window} を参照してください。  |
| HCX 帯域幅のテスト  | HCX にネットワーク帯域幅の問題があると思われる場合に、`perftest` を使用して HCX トンネル内の使用可能な帯域幅を調べる方法については、[Steps to Run Perftest in HCX (56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:new_window} を参照してください。 `perftest` ごとに双方向のテストが実行されます。 ゲートウェイのペアの場合、一方は「オンプレミス」と呼ぶソース・データ・センター内にあり、もう一方は {{site.data.keyword.cloud_notm}} 内にあります。 `perftest` のスループットでは、リンクが耐えられる最大速度で送信側が送信しようとします。 したがって、どのテストでも、「送信側」の速度が「受信側」の速度より高くなります。そのため、「受信側」の速度は片方向のスループットの結果の数値と見なすことができます。|
| HCX のトラブルシューティング | 詳しくは、[HCX のトラブルシューティング](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting) を参照してください。 |
| HCX の同期状態の進行状況が 0%、0 バイトでエラー・ステータスが返される | 詳しくは、[HCX replication are in Syncing state with 0% progress and 0 bytes with status Error (56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:new_window} を参照してください。 |
| VM ネットワークのパフォーマンスが低い | VM の仮想 NIC の設定を確認してください。 VMware では、VM 用に VMXNET 3 仮想 NIC が推奨されています。パフォーマンスを目的として設計されている準仮想化 NIC の最新世代であるからです。 VMware 互換性リストを使用して VMXNET 3 の互換性を確認し、サポートされている場合は、ネットワーク・パフォーマンスの向上のために仮想 NIC を変更してください。 詳しくは、[Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} を参照してください。 |

### vCenter
{: #opsprocs-trouble-common-vcenter}

表 5. 標準的な vCenter のトラブルシューティング

| タイトル | 説明 |
|---|---|
| 仮想マシンのコンソール・アクセス | 詳しくは、[Knowledge - KB0012863 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:new_window} を参照してください。 |
| 新しい vCenter Server 証明書がロードされていないように見える | デフォルトの vCenter Server 証明書を置き換えた後に、新しい証明書がロードされていないように見える場合があります。 詳しくは、[New vCenter Server Certificate Does Not Appear to Load](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:new_window} を参照してください。 |
| vCenter Server が管理対象ホストに接続できない | デフォルトの vCenter Server 証明書を置き換えてシステムを再起動した後に、vCenter Server が管理対象ホストに接続できません。 詳しくは、[vCenter Server Cannot Connect to Managed Hosts](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:new_window} を参照してください。 |
| カスタム SSL 証明書の使用時に vSphere HA を構成できない | カスタム SSL 証明書のインストール後に、vSphere High Availability (HA) を有効にしようとすると失敗します。 詳しくは、[Cannot Configure vSphere HA When Using Custom SSL Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:new_window} を参照してください。 |

### ライセンス
{: #opsprocs-trouble-common-licenses}

表 6. 標準的なライセンスのトラブルシューティング

| タイトル | 説明 |
|---|---|
|  ライセンス構成に互換性がないまたは正しくない | 詳しくは、[Troubleshooting Host Licensing](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window} を参照してください。 |
|  VM がパワーオンにならない | vSphere ESXi ホストの VM をパワーオンできず、「``ホストの 60 日の評価期間が満了しているか、ホストのライセンスの有効期限が切れています (The 60-day evaluation period of the host is expired or the license of the host is expired)``」というメッセージが表示される場合は、ライセンスの問題の可能性があります。 詳しくは、[Unable to Power On a Virtual Machine](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:new_window} を参照してください。 |
| 機能を使用できない、または構成を変更できない  | 詳しくは、[Unable to Configure or Use a Feature](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:new_window} を参照してください。  |


## 関連リンク
{: #opsprocs-trouble-links}

* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-trbl_support#trbl_support)
* [vSphere トラブルシューティングの概要](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-C70D5A5E-7D84-446C-B8CE-0766AA7351A4.html){:new_window}
* [ログを使用した vSphere のトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:new_window}
* [Operations management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
* [サポート・ログの収集](https://kb.vmware.com/s/article/1010705){:new_window}
* [イベント、アラーム、および自動化アクションの監視](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}
* [vSphere システム・ログ・ファイル](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:new_window}
* [vCenter Server 成果物の変更に関する考慮事項](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
