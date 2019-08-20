---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-02"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# アラーム
{: #opsprocs-alarms}

## 概要
{: #opsprocs-alarms-intro}

vSphere には、vSphere 環境で発生したイベントを追跡し、その情報を vCenter で利用できるようにする、イベントとアラームのサブシステムが含まれています。 このサブシステムでは、以下の用語を使用します。

### イベント
{: #opsprocs-alarms-events}

イベントは、vCenter 内のオブジェクト (ホストや仮想マシン (VM) など) で発生したシステムおよびユーザーのアクションのレコードです。 イベント・データには、イベントの詳細 (イベントの生成者、発生日時、イベントのタイプなど) が含まれます。 vSphere Web Client では、「監視」タブにイベント・データが表示されます。

イベントは以下のように分類されます。
* エラー - システムでリカバリー不能な問題が発生し、プロセスや操作が強制終了されたことを意味します。
* 警告 - 解決する必要がある潜在的なリスクがシステムに存在することを意味します。 このイベントではプロセスや操作は強制終了されていません。
* 情報 - ユーザーまたはシステムの操作が正常に完了したことを表します。
* 監査 - 監査ログ・データには、アクションの内容、アクションの実行者、実行日時、ユーザーの IP アドレスに関する情報が含まれます。

### アラーム
{: #opsprocs-alarms-alarms}

アラームは、イベント、一連の条件、またはインベントリー・オブジェクトの状態への応答として起動される通知です。

vSphere Client では、アラームの定義は、以下の要素で構成されています。
* 名前と説明 - 識別ラベルと説明を指定します。
* ターゲット - モニターするオブジェクトのタイプを定義します。
* アラーム・ルール - アラームを起動するイベント、条件、状態、および通知の重大度を定義します。 起動されたアラームへの応答として実行する操作も定義します。
* 最終変更日時 - 定義したアラームの最終変更日時です。

アラームには以下の重大度レベルがあります。
* 正常 – 緑色。
* 警告 – 黄色。
* アラート – 赤色。

### アラーム定義
{: #opsprocs-alarms-def}

アラーム定義は、インベントリーで選択したオブジェクトに関連付けられます。その定義で指定したタイプのインベントリー・オブジェクトがモニターの対象になります。

アラーム定義は以下の要素で構成されます。
* 名前と説明 - 識別ラベルと説明を指定します。
* アラーム・タイプ - モニターするオブジェクトのタイプを定義します。
* トリガー - アラームを起動するイベント、条件、状態、および通知の重大度を定義します。
* 許容度しきい値 (報告) - 条件トリガーと状態トリガーのしきい値に関する追加の制限を指定します (そのしきい値を超えるとアラームが起動します)。
* アクション - 起動されたアラームへの応答として実行する操作を定義します。 VMware には、インベントリー・オブジェクトのタイプに固有の一連の事前定義アクションが用意されています。
* アラーム・アクション - アラーム・アクションは、トリガーへの応答として実行する操作です。 例えば、アラームが起動されたときに 1 人以上の管理者に E メール通知を送信できます。
* 起動されたアラームの確認 - アラームを確認すると、アラーム・アクションが中止されます。 アラームを確認しても、アラームがクリアされたり、リセットされたりすることはありません。 アラームを確認することで、自分が問題を引き受けることを他のユーザーに知らせることができます。
* 起動されたアラームのリセット - イベントで起動されたアラームは、正常な状態を表すイベントを vCenter が取得しないと、正常な状態にリセットされません。 その場合は、アラームを手動でリセットしてください。
* 事前構成 vSphere アラーム - vSphere のイベントとアラームのサブシステムには、vSphere のインベントリー・オブジェクトの操作をモニターするための多数のデフォルト・アラームがあります。 それらのアラームについては、アクションをセットアップするだけで済みます。

## アラームのセットアップのワークフロー
{: #opsprocs-alarms-setup-workflow}

VMware には、以下の表の事前構成 vCenter アラームが用意されています。ただし、これらのアラームには、vCentre Web Client に表示するアクションしか設定されていません。 システム管理者チームに大量の E メールが送信されないように、ガイダンスでは、SMTP サーバーの詳細を構成してから、最初は以下のアラームに対してのみ、システム管理者に E メールを送信するアラート・アクションを設定するように説明しています。 詳しくは、[アラーム・アクションとしての E メールの送信](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-1F940DAF-933B-44B7-A200-7A11B5D3E3D5.html){:new_window}を参照してください。

アラーム設定のワークフローは以下のとおりです。
* SMTP サーバーの詳細を構成します。
* クラスター、ホスト、データ・ストア、重要な仮想アプライアンス (VCSA、PSC、NSX Manager、NSX Controllers) のアラート・アクションを構成します。
  * クラスター - VMware 高可用性エラー。
  * ホスト - CPU 状況、メモリー状況、ストレージ状況、ハードウェア状況 (電圧、温度、電源状況の変化など)。
  * データ・ストア - 空きディスク・スペースの減少。
  * 重要な仮想アプライアンス - CPU 使用量、メモリー使用量、ディスク待ち時間
* 毎日のプロアクティブなタスクの使用:
  * 送信されたアラートを検討します。本当に必要なアラートですか。
  * 送信されなかったアラートを検討します。知る必要があるものですか。
  * メトリックを確認します。メトリックは正しいですか。例えば、ベースラインが明らかになった今からすると、CPU 使用率は 90% ではなく 75% に設定する必要がありますか。
  * 独自のアラームを構成する必要がありますか。
  * 仮想マシンを含める必要がありますか。

##  標準的なアラーム・ワークフロー
{: #opsprocs-alarms-alarm-workflow}

セットアップ後のアラーム・ワークフローの例を以下に示します。通常は、アラームが起動された場合にシステム管理者が実施するワークフローです。

1. ホストの CPU 使用率を監視するアラームが設定されています。そのアラームには、アラーム起動時に管理者に E メールを送信するアラーム・アクションが設定されています (前のセクションを参照)。
3. ホストの CPU 使用率が急上昇し、アラームが起動され、E メールが管理者に送信されます。
4. 管理者の 1 人が vCenter にログインし、起動されたアラームの確認を実行することで、自分が問題に対応することを他の管理者に知らせ、そのアラームのE メール・メッセージがそれ以上送信されないようにします。 ただし、システムにはそのアラームが引き続き表示されます。
5. その管理者が CPU の急上昇の原因を突き止めて、問題を解決します。
6. アラームが自動的にリセットされます。

## 事前構成アラーム - 標準
{: #opsprocs-alarms-preconfigured-std}

以下の表の各項目の意味は次のとおりです。

* アラーム名 - vCenter で表示されるアラームの名前。
* ガイダンス - このアラームの使用に関する IC4V のガイダンス。
* 詳細情報 - アラームが起動された場合に解決に役立つ詳しい情報。IBM または VMware が提供しています。

表 1. 事前構成アラーム

| アラーム名 | ガイダンス | 詳細情報 |
|---|---|---|
| ホストの接続とパワー状態 | 「応答なし (Not Responding)」や「スタンバイ (Standby)」に設定された場合に E メールを 1 回送信するように構成します。 | [Alarms about the host connection state changing from green to red frequently occur (1020210)](https://kb.vmware.com/s/article/1020210){:new_window} |
| ホストの CPU 使用率 | ホストの CPU 使用率が 90 % を超えた状態が 5 分間続いたら E メールを 1 回送信するように構成します。 | [Knowledge - KB0012707 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=342e3d6adbc5730030c93a1b7c961976){:new_window} |
| ホストのメモリ使用率 | ホストのメモリー使用率が 95 % を超えた状態が 5 分間続いたら E メールを 1 回送信するように構成します。 | [Knowledge - KB0012712 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=30110ee2db49730030c93a1b7c96194f){:new_window} |
| 仮想マシンの CPU 使用率 | 重要なアプライアンスの VM の CPU 使用率が 90 % を超えた状態が 5 分間続いたら E メールを 1 回送信するように構成します。 | [Virtual machine CPU usage alarm (2057830)](https://kb.vmware.com/s/article/2057830){:new_window} |
| 仮想マシンのメモリ使用率 | 重要なアプライアンスの VM のメモリー使用率が 95 % を超えた状態が 5 分間続いたら E メールを 1 回送信するように構成します。 | [Virtual machine memory usage alarm (2057846)](https://kb.vmware.com/s/article/2057846){:new_window} |
| ディスク上のデータストア使用率 | vSAN の場合は、データ・ストア使用率が 70% を超えたときに E メールを 1 回送信するように構成します。VSAN 以外の場合は、データ・ストア使用率が 85% を超えたときに E メールを 1 回送信するように構成します。 | [Knowledge - KB0012713 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=ddb3422edb89730030c93a1b7c9619f6){:new_window} |
| 仮想マシンの CPU 準備完了 | 重要なアプライアンスの VM の CPU 準備時間が 5 分間で 2000 ms を超えたときに E メールを 1 回送信するように構成します。 | [Knowledge - KB0012718 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=7056426adb0d730030c93a1b7c9619e6){:new_window} |
| 仮想マシンのディスク待ち時間合計 | 重要なアプライアンスの VM の合計ディスク待ち時間が 5 分間で 30 ms を超えたときに E メールを 1 回送信するように構成します。 | [Knowledge - KB0012729 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=15dddea2db857300d5a971198c961995){:new_window} |
| 仮想マシンのディスクコマンドがキャンセルされました | 初期段階では設定しません。 第 2 段階で重要なアプライアンスについて検討します。 | 追加情報なし |
| 仮想マシンのディスクがリセットされました | 初期段階では設定しません。 第 2 段階で重要なアプライアンスについて検討します。 | 追加情報なし |
| ライセンス インベントリの監視 | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [ライセンス供与に関するトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window}および [Licensing ESXi 6.x and vCenter Server 6.x](https://kb.vmware.com/s/article/2107538){:new_window} を参照してください。 |
| ライセンス ユーザーしきい値監視 | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [ライセンス供与に関するトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| ライセンス キャパシティの監視 | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [ライセンス供与に関するトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| ホストのライセンスエディションが vCenter Server のライセンスエディションと互換性を持っていません | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [ホストのライセンス供与に関するトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window} |
| セカンダリ仮想マシンの起動のタイムアウト * | 構成しません。モニター対象の VMware フォールト・トレランスは、vCenter Server インスタンスでは推奨されていないからです。 | [Timeout starting Secondary VM alarm (2064169)](https://kb.vmware.com/s/article/2064169){:new_window} |
| セカンダリ仮想マシンに適合するホストがありません | 構成しません。モニター対象の VMware フォールト・トレランスは、vCenter Server インスタンスでは推奨されていないからです。 | 追加情報なし |
| 仮想マシンのフォールト トレランスの状態変化 | 構成しません。モニター対象の VMware フォールト・トレランスは、vCenter Server インスタンスでは推奨されていないからです。 | 追加情報なし |
| 仮想マシンの Fault Tolerance 対応 vLockStep 間隔の状態変化 | 構成しません。モニター対象の VMware フォールト・トレランスは、vCenter Server インスタンスでは推奨されていないからです。 | 追加情報なし |
| ホストのプロセッサ ステータス | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストのメモリ ステータス | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストのハードウェア ファン ステータス | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストのハードウェア電圧 | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストのハードウェア温度ステータス | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストのハードウェアの電源状態 | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。| [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストのハードウェア システム ボード ステータス | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストのバッテリ ステータス | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。| [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ほかのホストのハードウェア オブジェクトのステータス |  モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストのストレージ ステータス | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストの IPMI システム イベント ログの状態 | サービスへの影響がないので構成しません。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホストのベースボード管理コントローラのステータス | モニターが緑から赤に変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| ホスト エラー * | モニターがエラーに変わったときに E メールを 1 回送信するように構成します。 | [IBM サポートにお問い合わせください](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 仮想マシン エラー * | 重要なアプライアンスにとって重大な状況である場合は E メールを 1 回送信するように構成します。 | [仮想マシンのトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window} |
| ホストの接続障害 * | 「ホストに接続できません - ネットワーク・エラー (Cannot connect host - network error)」、「ホストに接続できません - タイムアウト (Cannot connect host - timeout)」、「ホスト接続が失われました (Host connection lost)」のいずれかのイベントが発生したときに E メールを 1 回送信するように構成します。 | [Alarms about the host connection state changing from green to red frequently occur (1020210)](https://kb.vmware.com/s/article/1020210){:new_window} |
| SIOC が有効なデータストアで管理されていないワークロードが検出されました | サービスへの影響がないので構成しません。 | [Unmanaged workload is detected on datastore running SIOC (1020651)](https://kb.vmware.com/s/article/1020651){:new_window} |
| シン プロビジョニング ボリュームの容量しきい値を超えています | vCenter Server インスタンスでは VASA ストレージがサポートされていないので構成しません。 | 追加情報なし |
| データストア機能アラーム | vCenter Server インスタンスでは VASA ストレージがサポートされていないので構成しません。 | 追加情報なし |
| VASA プロバイダが切断されています | vCenter Server インスタンスでは VASA ストレージがサポートされていないので構成しません。 | 追加情報なし |
| VASA プロバイダ証明書の期限切れアラーム | vCenter Server インスタンスでは VASA ストレージがサポートされていないので構成しません。 | 追加情報なし |
| 仮想マシン ストレージ コンプライアンス アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [VM storage compliance alarm (2061940)](https://kb.vmware.com/s/article/2061940){:new_window} |
| データストア コンプライアンス アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [データ・ストアでの作業](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.storage.doc/GUID-3CC7078E-9C30-402C-B2E1-2542BEE67E8F.html){:new_window} |
| VASA プロバイダで CA 証明書と CRL の更新に失敗しました | vCenter Server インスタンスでは VASA ストレージがサポートされていないので構成しません。 | 追加情報なし |
| vSphere HA フェイルオーバーのリソースが不足しています | 重大な状況である場合は E メールを 1 回送信するように構成します。 | [Knowledge - KB0012739 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=fe1f0beedb8db300d5a971198c96191a){:new_window} |
| vSphere HA フェイルオーバーが進行中です | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSphere HA Master Agent が見つかりません | HA マスター・エージェントの検出または HA マスター・エージェントとの通信ができないときに E メールを 1 回送信するように構成します。 | [vSphere の可用性について](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.avail.doc/GUID-63F459B7-8884-4818-8872-C9753B2E0215.html){:new_window} |
| vSphere HA ホストのステータス  | 次の状況が発生したときに E メールを 1 回送信するように構成します: 「ホスト上の vSphere HA エージェントでエラーが発生しました (vSphere HA detects a network isolated host)」、「vSphere HA がネットワーク隔離ホストを検出しました (vSphere HA detects a network isolated host)」、「vSphere HA がネットワーク・パーティション・ホストを検出しました (vSphere HA detects a network-partitioned host)」、「vSphere HA がホスト障害を検出しました (vSphere HA detects a host failure)」。 | [vSphere HA ホスト状態のトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window} |
| vSphere HA による仮想マシンのフェイルオーバーが失敗しました | 重要なアプライアンスにとって重大な状況である場合は E メールを 1 回送信するように構成します。 | [vSphere HA クラスターの作成と使用](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| vSphere HA の仮想マシン監視アクション | 重要なアプライアンスにとって重大な状況である場合は E メールを 1 回送信するように構成します。 | [vSphere HA クラスターの作成と使用](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| vSphere HA の仮想マシン監視エラー | 重要なアプライアンスにとって重大な状況である場合は E メールを 1 回送信するように構成します。 | [vSphere HA クラスターの作成と使用](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| vSphere HA 仮想マシンのコンポーネント保護で、仮想マシンをパワーオフできませんでした | 重要なアプライアンスにとって重大な状況である場合は E メールを 1 回送信するように構成します。 | [Creating and Using vSphere HA Clusters](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| ライセンス エラー * |  重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [ライセンス供与に関するトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| 健全性ステータスの変更 * | 重大なステータスの変更がある場合は発生時に E メールを 1 回送信するように構成します。 | [ホストのトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-6F6CE545-58FA-490B-8C8A-3CB8196CAEA8.html){:new_window} |
| ストレージ DRS 推奨 | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [DRS トラブルシューティング情報](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-5E7F6DEC-02A2-4221-AABA-EDFB9AE9EC70.html){:new_window} |
| ストレージ DRS はホストでサポートされていません | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [DRS トラブルシューティング情報](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-5E7F6DEC-02A2-4221-AABA-EDFB9AE9EC70.html){:new_window} |
| データストア クラスタに容量がありません | ディスク使用率が 85% を超えることが重大な状況である場合は E メールを 1 回送信するように構成します。 | [Adding NFS storage to vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances) |
| データストアが複数のデータセンター内にあります | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [ストレージ DRS がデータ・ストアで操作できない](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.troubleshooting.doc/GUID-976F5B21-8C64-4C85-BE75-0D86655E32DD.html){:new_window} |
| vSphere Distributed Switch VLAN のトランキング ステータス | vSphere 分散スイッチの構成済み VLAN の一部が物理スイッチにトランキングされていないことが重大な状況である場合は、E メールを 1 回送信するように構成します。 | [Enabling vSphere Distributed Switch health check in the vSphere Web Client (2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| vSphere Distributed Switch MTU の一致ステータス  | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Enabling vSphere Distributed Switch health check in the vSphere Web Client (2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| vSphere Distributed Switch MTU のサポートされるステータス | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Enabling vSphere Distributed Switch health check in the vSphere Web Client (2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| vSphere Distributed Switch チーミングの一致ステータス | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Enabling vSphere Distributed Switch health check in the vSphere Web Client (2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| 仮想マシンのネットワーク アダプタ予約のステータス | ネットワーク・アダプターの予約を有効にした場合のみ、E メールを送信するように構成します。 | [仮想マシンのバンド幅割り当ての構成](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-FECAC41A-2C7A-4AD6-B740-7D8D44BADB52.html){:new_window} |
| 仮想マシンの統合が必要なステータス | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Using Snapshots To Manage Virtual Machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-CA948C69-7F58-4519-AEB1-739545EA94E5.html){:new_window} |
| ホストの仮想フラッシュ リソース ステータス | vCenter Server インスタンスでは、ホストの仮想フラッシュはサポートされていません。 | 追加情報なし |
| ホストの仮想フラッシュ リソース使用量 | vCenter Server インスタンスではホストの仮想フラッシュがサポートされていないので構成しません。 | [About Virtual Flash Resource](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.storage.doc/GUID-E69F0809-3B19-483A-B906-4CE397CE56D6.html){:new_window} |
| vSAN ホスト上の VASA ベンダー プロバイダの登録/登録解除に失敗しました | vCenter Server インスタンスでは VASA ストレージがサポートされていないので構成しません。 | [VMware compatibility guide](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=vasa){:new_window} |
| ホスト上のサードパーティ IO フィルタ ストレージ プロバイダの登録/登録解除に失敗する | vCenter Server インスタンスでは VASA ストレージがサポートされていないので構成しません。 | [VMware compatibility guide](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=vasa){:new_window} |
| サービス コントロール エージェント健全性アラーム | コンポーネント ID が sca で新規ステータスが赤のときに E メールを 1 回送信するように構成します。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| ID 健全性アラーム | コンポーネント ID が identity で新規ステータスが赤のときに E メールを 1 回送信するように構成します。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| vSphere Web Client 健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Enabling debug logging on the VMware vSphere 5.x/6.x Web Client service (2011485)](https://kb.vmware.com/s/article/2011485){:new_window} |
| ESX Agent Manager 健全性アラーム | コンポーネント ID が `eam` で新規ステータスが`赤`のときに E メールを 1 回送信するように構成します。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| メッセージ バス構成の健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| Cis ライセンス健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| インベントリ健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| vCenter Server 健全性アラーム | コンポーネント ID が vpxd で新規ステータスが赤のときに E メールを 1 回送信するように構成します。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| データベース健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| データ サービス健全性アラーム | コンポーネント ID が vmware-dataservices-sca で新規ステータスが赤のときに E メールを 1 回送信するように構成します。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| RBD 健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| vService Manager 健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| パフォーマンス チャート サービス健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| Content Library Service の健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 転送サービス健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| VMware vSphere ESXi ダンプ・コレクター健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。| [VMware ESXi Dump Collector Support](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-F8773E25-BD6A-4A6C-A999-D58CB853BA8A.html){:new_window} |
| VMware vAPI Endpoint サービス健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| VMware システムおよびハードウェア健全性マネージャ サービス健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Troubleshooting with Logs](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.troubleshooting.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:new_window} |
| VMware vSphere Profile-Driven Storage サービス健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| VMware vFabric Postgres サービス健全性アラーム | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| ESXi ホスト証明書の更新の失敗ステータス | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| ESXi ホスト証明書ステータス | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| ESXi ホスト証明書の検証の失敗ステータス | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| vSphere vCenter ホスト証明書の管理モード | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| ルート証明書ステータス |  重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。  | [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| GPU ECC 未修正メモリ アラーム | vCenter Server インスタンスでは GPU がサポートされていないので構成しません。 | 追加情報なし |
| GPU ECC 修正済みメモリ アラーム | vCenter Server インスタンスでは GPU がサポートされていないので構成しません。 | 追加情報なし |
| GPU 温度条件アラーム | vCenter Server インスタンスでは GPU がサポートされていないので構成しません。 | 追加情報なし |
| ネットワーク接続が失われました | 次の重大なイベントが発生したときに E メールを 1 回送信するように構成します:「ネットワーク接続が失われました (Lost Network Connectivity)」または「DVPorts へのネットワーク接続が失われました (Lost Network Connectivity to DVPorts)」。 | [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| ネットワーク アップリンクの冗長性が失われました | 次の重大なイベントが発生したときに E メールを 1 回送信するように構成します:「ネットワークの冗長性が失われました (Lost Network Redundancy)」または「DVPorts のネットワークの冗長性が失われました (Lost Network Redundancy on DVPorts)」。| [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| ネットワーク アップリンクの冗長性が低下しました * | 次の重大なイベントが発生したときに E メールを 1 回送信するように構成します:「ネットワークの冗長性が低下しました (Network Redundancy Degraded)」または「DVPorts のネットワークの冗長性が低下しました (Network Redundancy Degraded on DVPorts)」。 | [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| VMKernel NIC が正しく構成されていません * | 次の重大なイベントが発生したときに E メールを 1 回送信するように構成します:「`/Migrate/VMknic` に無効な `vmknic` が指定されています (Invalid vmknic specified in /Migrate/VMknic)」。 | [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| ストレージに接続できません * | 次の重大なイベントが発生したときに E メールを 1 回送信するように構成します:「ストレージ接続が失われました (Lost Storage Connectivity)」、「ストレージ・パスの冗長性が失われました (Lost Storage Path Redundancy)」、「ストレージ・パスの冗長性が低下しました (Degraded Storage Path Redundancy)」、「NFS サーバーへの接続が失われました (Lost connection to NFS server)」。| [Identifying Fibre Channel, iSCSI, and NFS storage issues on ESX/ESXi hosts (1003659)](https://kb.vmware.com/s/article/1003659){:new_window} |
| 移行エラー * | 次の重大なイベントが発生したときに E メールを 1 回送信するように構成します:「VM を移行できません (Cannot migrate VM)」、「移行エラー」、「移行ホスト エラー (Migration host error)」、「VM を再配置できません (Cannot relocate VM)」、「VM が孤立しています (VM orphaned)」。 | [vMotion or Storage vMotion of a VM fails with the error: The migration has exceeded the maximum switchover time of 100 second(s) (2141355)](https://kb.vmware.com/s/article/2141355){:new_window} |
| スタンバイの終了エラー | vCenter Server インスタンスでは DPM の使用が推奨されていないので構成しません。 | vSphere Distributed Power Management (DPM) には、オンプレミス・デプロイメントでの節電機能が用意されています。この機能は、リソース使用率が低いときにワークロードを動的に集約し、VM を移行してホストの台数を減らし、必要ではない ESX ホストの電源をオフにします。 IBM Cloud ベア・メタル・サーバーの電源をオフにして電力消費量の節約を実現することはできません。 |

\* が付いているのは、ステートレスなアラームです。 ステートレスなアラームのデータは、vCenter で保管されません。計算もされず、ステータスも表示されません。 ステートレスなアラームは、確認もリセットも実行できません。
{:note}

## 事前構成アラーム - vSAN
{: #opsprocs-alarms-preconfigured-vsan}

vSAN クラスターを使用する場合は、以下の表の追加の事前構成アラームが適用されます。

* アラーム名 - vCenter で表示されるアラームの名前。
* ガイダンス - このアラームの使用に関する IC4V のガイダンス。
* 詳細情報 - アラームが起動された場合に解決に役立つ詳しい情報。IBM または VMware が提供しています。

表 2. 事前構成アラーム - vSAN

| アラーム名 | ガイダンス | 詳細情報 |
|---|---|---|
| ホストのフラッシュ容量が vSAN のライセンス制限を超えています | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN ライセンスの有効期限が切れました | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [ライセンス供与に関するトラブルシューティング](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| vSAN ホストのディスクでエラーが発生しました | vSAN ディスクに永続的なエラーがあるときに E メールを 1 回送信するように構成します。 | [vSAN device encounters a permanent error when devices are not readable or writeable (2071075)](https://kb.vmware.com/s/article/2071075){:new_window}  |
| vSAN ホストのディスクでエラーが発生しました | 次の重大なイベントが発生したときに E メールを 1 回送信するように構成します:「仮想 SAN デバイスに永続的な障害があります (Virtual SAN device is under permanent failure)」。 | [vSAN device encounters a permanent error when devices are not readable or writeable (2071075)](https://kb.vmware.com/s/article/2071075){:new_window} |
| vSAN ライセンスの有効期限が切れました | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN ライセンスに関する考慮事項](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-planning.doc/GUID-20731F2A-B001-4A05-AB4D-30C5B0044EC5.html){:new_window} |
| vSAN 時間制限ライセンスの有効期限が切れました (Expired vSAN time-limited license) | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Considerations about the vSAN License](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-planning.doc/GUID-20731F2A-B001-4A05-AB4D-30C5B0044EC5.html){:new_window} |
| vSAN ハードウェアの互換性の問題 (vSAN hardware compatibility issues) | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Check Information (2114803)](https://kb.vmware.com/s/article/2114803?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} |
| vSAN 健全性アラーム `アクティブ・マルチキャスト接続の検査 (Active multicast connectivity check)` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Network Health - Active Multicast connectivity check (2116296)](https://kb.vmware.com/s/article/2116296){:new_window} |
| vSAN 健全性アラーム `Virtual SAN 詳細構成の同期状態` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Cluster Health - Advanced vSAN configuration in sync (2107713)](https://kb.vmware.com/s/article/2107713){:new_window} |
| vSAN 健全性アラーム `1 件のホスト障害を追加後` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN health warning `after one additional host failure` is reported incorrectly on two node ROBO/stretched clusters (2150568)](https://kb.vmware.com/s/article/2150568?lang=en_US){:new_window} |
| vSAN 健全性アラーム `統計情報に影響するすべてのホスト` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - performance service - All hosts contributing stats check (2144400)](https://kb.vmware.com/s/article/2144400){:new_window} |
| vSAN 健全性アラーム `すべてのホストで vSAN vmknic が構成済み` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Network Health - All hosts have a vSAN vmknic configured (2108062)](https://kb.vmware.com/s/article/2108062){:new_window} |
| vSAN 健全性アラーム `すべてのホストでマルチキャスト設定が一致` |  重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Network Health - All hosts have matching multicast settings (2108092)](https://kb.vmware.com/s/article/2108092){:new_window} |
| vSAN 健全性アラーム `すべてのホストでサブネットが一致` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Network Health - All hosts have matching subnets (2108066)](https://kb.vmware.com/s/article/2108066){:new_window} |
| vSAN 健全性アラーム `基本 (ユニキャスト) 接続チェック (通常の ping)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Network Health - Hosts small ping test (connectivity check) and Hosts large ping test (MTU check) (2108285)](https://kb.vmware.com/s/article/2108285){:new_window} |
| vSAN 健全性アラーム `クラスターの健全性 (Cluster health)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Cluster Health - vSAN Health service installation (2109874)](https://kb.vmware.com/s/article/2109874){:new_window} |
| vSAN 健全性アラーム `コンポーネントのメタデータ健全性` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Component metadata health check fails with invalid state error (2145347)](https://kb.vmware.com/s/article/2145347){:new_window} |
| vSAN 健全性アラーム `輻輳` | 重大なイベントについて E メールを 1 回送信するように構成します。| [vSAN Health Service - Physical Disk Health – Congestion (2109255)](https://kb.vmware.com/s/article/2109255){:new_window} |
| vSAN 健全性アラーム `コントローラ ディスク グループのモードが VMware により認定済み` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - vSAN HCL Health – SCSI Controller on vSAN HCL (2109871)](https://kb.vmware.com/s/article/2109871){:new_window} |
| vSAN 健全性アラーム `コントローラ ドライバが VMware により認定済み` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service – vSAN HCL Health – Controller Driver (2109263)](https://kb.vmware.com/s/article/2109263){:new_window} |
| vSAN 健全性アラーム `コントローラ ファームウェアが VMware により認定済み` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Controller firmware health check warning if multiple firmware versions are supported (2150398)](https://kb.vmware.com/s/article/2150398){:new_window} |
| vSAN 健全性アラーム `コントローラが ESXi リリースに対して VMware により認定済み` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - vSAN HCL Health - Controller Release Support (2109262)](https://kb.vmware.com/s/article/2109262){:new_window} |
| vSAN 健全性アラーム `CPU AES-NI がホストで無効になっています (CPU AES-NI is disabled on hosts)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Encryption - CPU AES-NI Host Enablement Check (2149499)](https://kb.vmware.com/s/article/2149499){:new_window} |
| vSAN 健全性アラーム `現在のクラスタの状態` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Limits Health – Current Cluster Situation (2108740)](https://kb.vmware.com/s/article/2108740){:new_window} |
| vSAN 健全性アラーム `カスタマ エクスペリエンス改善プログラム (CEIP)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Online Health - CEIP Check (2148866)](https://kb.vmware.com/s/article/2148866){:new_window} |
| vSAN 健全性アラーム `データの健全性 (Data health)` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Data Health – vSAN Object Health (2108319)](https://kb.vmware.com/s/article/2108319){:new_window} |
| vSAN 健全性アラーム `ディスク容量` | 警告のイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Physical Disk Health - Disk Capacity (2108907)](https://kb.vmware.com/s/article/2108907){:new_window} |
| vSAN 健全性アラーム `ディスク フォーマットのバージョン` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Cluster - Disk format version (2146135)](https://kb.vmware.com/s/article/2146135){:new_window} |
| vSAN 健全性アラーム `ESXi vSAN Health Service のインストール (ESXi vSAN Health service installation)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Cluster Health - vSAN Health Service up-do-date (2107705)](https://kb.vmware.com/s/article/2107705){:new_window} |
| vSAN 健全性アラーム `ホーム オブジェクト (Home object)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - vSAN iSCSI target service - Home object (2147601)](https://kb.vmware.com/s/article/2147601){:new_window} |
| vSAN 健全性アラーム `ホスト コンポーネントの制限` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Limits - Host component (2146130)](https://kb.vmware.com/s/article/2146130){:new_window} |
| vSAN 健全性アラーム `ハードウェア情報の取得時にホストの問題 (Host issues retrieving hardware info)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - HCL Health - Host issues retrieving hardware information (2149290)](https://kb.vmware.com/s/article/2149290){:new_window} |
| vSAN 健全性アラーム `ホストの保守モードと廃止状態 (Host Maintenance Mode and Decommission State)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Host Maintenance Mode is in sync with vSAN Node Decommission State (51464)](https://kb.vmware.com/s/article/51464){:new_window}|
| vSAN 健全性アラーム `VC から切断されたホスト` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Network Health - Hosts disconnected from vCenter Server (2108004)](https://kb.vmware.com/s/article/2108004){:new_window} |
| vSAN 健全性アラーム `接続に問題のあるホスト` | 重大なイベントについて E メールを 1 回送信するように構成します。  | [vSAN Health Service - Network Health - Hosts with connectivity issues (2108317)](https://kb.vmware.com/s/article/2108317){:new_window} |
| vSAN 健全性アラーム `監視ホストのフォールト ドメインの構成に誤りがあります` | vSAN を拡張した場合にのみアラームを検討してください。 | [vSAN Health Service - Invalid preferred fault domain on witness host (2130589)](https://kb.vmware.com/s/article/2130589){:new_window} |
| vSAN 健全性アラーム `無効なユニキャスト エージェント` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Invalid unicast agent test (2144398)](https://kb.vmware.com/s/article/2144398){:new_window} |
| vSAN 健全性アラーム `iSCSI ターゲット・サービス (iSCSI target service)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - vSAN iSCSI target service – Network configuration (2147602)](https://kb.vmware.com/s/article/2147602){:new_window} |
| vSAN 健全性アラーム `制限の健全性 (Limits health)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `メモリ プール (ヒープ)` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Physical Disk Health – Memory pools (2109256)](https://kb.vmware.com/s/article/2109256){:new_window} |
| vSAN 健全性アラーム `メモリ プール (スラブ)` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Physical Disk Health – Memory pools (2109256)](https://kb.vmware.com/s/article/2109256){:new_window} |
| vSAN 健全性アラーム `MTU チェック (パケット サイズの大きい ping)` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Network Health - Hosts small ping test (connectivity check) and Hosts large ping test (MTU check) (2108285)](https://kb.vmware.com/s/article/2108285){:new_window} |
| vSAN 健全性アラーム `その他のチェックに基づくマルチキャスト評価` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Network Health – Multicast assessment based on other checks (2108318)](https://kb.vmware.com/s/article/2108318){:new_window} |
| vSAN 健全性アラーム `ネットワーク構成 (Network configuration)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `ネットワークの健全性 (Network health)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `ネットワーク遅延チェック` | 警告のイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Network Health - Network Latency Check (2149511)](https://kb.vmware.com/s/article/2149511){:new_window} |
| vSAN 健全性アラーム `監視ホスト上でディスクが要求されていません` | vSAN を拡張した場合にのみアラームを検討してください。 | [vSAN Health Service - No disk claimed on witness host (2130584)](https://kb.vmware.com/s/article/2130584){:new_window} |
| vSAN 健全性アラーム `オンライン健全性接続状態` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Online Health - Internet Connectivity Check (2149196)](https://kb.vmware.com/s/article/2149196){:new_window} |
| vSAN 健全性アラーム `「操作の健全性 (Operation health)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `パフォーマンス・データの収集` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN health test fails on Performance Service (2150589)](https://kb.vmware.com/s/article/2150589){:new_window} |
| vSAN 健全性アラーム `パフォーマンス サービスのステータス (Performance service status)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN health test fails on Performance Service (2150589)](https://kb.vmware.com/s/article/2150589){:new_window} |
| vSAN 健全性アラーム `物理ディスク コンポーネントの制限の健全性` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Physical disk - Component limit (2146086)](https://kb.vmware.com/s/article/2146086){:new_window} |
| vSAN 健全性アラーム `物理ディスクの健全性の取得の問題 (Physical disk health retrieval issues)` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Physical Disk Health - Physical disk health retrieval issue (2149291)](https://kb.vmware.com/s/article/2149291){:new_window} |
| vSAN 健全性アラーム `物理ディスクの健全性 - メタデータ健全性` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Physical Disk Health - Metadata Health (2108690)](https://kb.vmware.com/s/article/2108690){:new_window} |
| vSAN 健全性アラーム `優先フォールト ドメインが設定されていません` | vSAN を拡張した場合にのみアラームを検討してください。 | [vSAN Health Service - Preferred fault domain unset (2130590)](https://kb.vmware.com/s/article/2130590){:new_window} |
| vSAN 健全性アラーム `再同期操作の調整` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Cluster Health - Resynchronization Operations Throttling Check (2149504)](https://kb.vmware.com/s/article/2149504){:new_window} |
| vSAN 健全性アラーム `SCSI コントローラが VMware により認定済み` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service – vSAN HCL Health – Controller Driver (2109263)](https://kb.vmware.com/s/article/2109263){:new_window} |
| vSAN 健全性アラーム `サービス ランタイムのステータス (Service runtime status)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `サイト遅延の健全性` | vSAN を拡張した場合にのみアラームを検討してください。 | [vSAN Health Service - Stretched cluster - Site latency (2146133)](https://kb.vmware.com/s/article/2146133){:new_window} |
| vSAN 健全性アラーム `ソフトウェア バージョンの互換性` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Cluster - Software version compatibility (2146134)](https://kb.vmware.com/s/article/2146134){:new_window} |
| vSAN 健全性アラーム `スペース効率の構成の一貫性 (Space efficiency configuration consistency)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `スペース効率の使用法の健全性 (Space efficiency usage health)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `統計 DB オブジェクトの競合` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Performance Service - Stats DB object conflicts check (2144405)](https://kb.vmware.com/s/article/2144405){:new_window} |
| vSAN 健全性アラーム `統計 DB オブジェクト` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Performance Service - Stats DB object check (2144403)](https://kb.vmware.com/s/article/2144403){:new_window} |
| vSAN 健全性アラーム `統計マスターの選択` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Performance Service - Stats master election check (2144408)](https://kb.vmware.com/s/article/2144408){:new_window} |
| vSAN 健全性アラーム `拡張クラスタの健全性` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `ホストと VC 全体で時刻が同期されていません (Time is not synchronized across hosts and VC)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Cluster Health - Time Synchronization Across Hosts and VC (2149505)](https://kb.vmware.com/s/article/2149505){:new_window} |
| vSAN 健全性アラーム `フォールト ドメインの予期しない番号` | vSAN を拡張した場合にのみアラームを検討してください。| [vSAN Health Service - Unexpected number of fault domains (2130581)](https://kb.vmware.com/s/article/2130581){:new_window} |
| vSAN 健全性アラーム `ユニキャスト エージェントの構成に一貫性がありません` | vSAN を拡張した場合にのみアラームを検討してください。 | [vSAN Health Service - Unicast agent configuration inconsistent (2130580)](https://kb.vmware.com/s/article/2130580){:new_window} |
| vSAN 健全性アラーム `ユニキャスト エージェントが構成されていません` | vSAN を拡張した場合にのみアラームを検討してください。 | [vSAN Health Service - Unicast agent not configured (2130582)](https://kb.vmware.com/s/article/2130582){:new_window} |
| vSAN 健全性アラーム `サポートされていないホスト バージョンです` | vSAN を拡張した場合にのみアラームを検討してください。 | [VMware KB article](https://kb.vmware.com/s/article/2130583){:new_window} |
| vSAN 健全性アラーム `vCenter またはホストが鍵管理サーバーに接続されていません (vCenter or hosts are not connected to Key Management Servers)` | vSAN 暗号化を有効にした場合にのみアラームを検討してください。 | [vSAN Health Service - Unsupported host version (2130583)](https://kb.vmware.com/s/article/2149497){:new_window} |
| vSAN 健全性アラーム `vCenter Server の状態は信頼できます` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Cluster health – vCenter state is authoritative (2150916)](https://kb.vmware.com/s/article/2150916){:new_window} |
| vSAN 健全性アラーム `冗長モード (Verbose mode)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [Performance Service - Verbose Mode in the vSAN health service (51527)](https://kb.vmware.com/s/article/51527){:new_window} |
| vSAN 健全性アラーム `vSAN ビルドに関する推奨事項 エンジンのビルドに関する推奨事項` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - vSphere Update Manager - vSAN build recommendation engine health (2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
| vSAN 健全性アラーム `vSAN ビルドに関する推奨事項 エンジンの健全性` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - vSphere Update Manager - vSAN build recommendation engine health (2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
| vSAN 健全性アラーム `vSAN ビルドに関する推奨事項 エンジンの健全性`の構成の問題 | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - vSphere Update Manager - vSAN build recommendation engine health (2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
| vSAN 健全性アラーム `vSAN の CLOMD 稼動状態` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Cluster Health – CLOMD liveness check (2109873)](https://kb.vmware.com/s/article/2109873){:new_window} |
| vSAN 健全性アラーム `vSAN クラスタ構成の一貫性` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Cluster Configuration Consistency (2149506)](https://kb.vmware.com/s/article/2149506){:new_window} |
| vSAN 健全性アラーム `vSAN クラスタ パーティション` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Network Health - vSAN Cluster Partition (2108011)](https://kb.vmware.com/s/article/2108011){:new_window} |
| vSAN 健全性アラーム `vSAN ディスク バランス` | 警告のイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Cluster health - vSAN disk balance (2144278)](https://kb.vmware.com/s/article/2144278){:new_window} |
| vSAN 健全性アラーム `vSAN HCL DB の自動更新` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Hardware compatibility - vSAN HCL DB Auto Update (2146132)](https://kb.vmware.com/s/article/2146132){:new_window} |
| vSAN 健全性アラーム `vSAN HCL DB の更新状態` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - vSAN HCL Health – vSAN HCL DB up-to-date (2109870)](https://kb.vmware.com/s/article/2109870){:new_window} |
| vSAN 健全性アラーム `vSAN HCL の健全性 (vSAN HCL health)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `vSAN Health Service の更新状態` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - vSAN Build Recommendation - vSAN release catalog up-to-date (58891)](https://kb.vmware.com/s/article/58891){:new_window} |
| vSAN 健全性アラーム `vSAN オブジェクトの健全性` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Data Health – vSAN Object Health (2108319)](https://kb.vmware.com/s/article/2108319){:new_window} |
| vSAN 健全性アラーム `vSAN パフォーマンス サービスの健全性 (vSAN Performance Service health)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Performance Service - Status Check (2149406)](https://kb.vmware.com/s/article/2149406){:new_window} |
| vSAN 健全性アラーム `vSAN VM の健全性 (vSAN VM health)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| vSAN 健全性アラーム `vSphere クラスタ メンバと vSAN クラスタ メンバが一致しません (vSphere cluster members do not match vSAN cluster members)` | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | [vSAN Health Service - Cluster Health - vSphere and vSAN Cluster Members Match vSAN (2149507)](https://kb.vmware.com/s/article/2149507){:new_window} |
| vSAN 健全性アラーム `監視ホスト上の無効な優先フォールト ドメイン` | vSAN を拡張した場合にのみアラームを検討してください。 | [vSAN Health Service - Witness host fault domain misconfigured (2130586)](https://kb.vmware.com/s/article/2130586){:new_window} |
| vSAN 健全性アラーム `監視ホストが見つかりません` | vSAN を拡張した場合にのみアラームを検討してください。 | [vSAN Health Service - Witness host not found (2130585)](https://kb.vmware.com/s/article/2130585){:new_window} |
| vSAN 健全性アラーム `vCenter クラスタ内の監視ホスト` | vSAN を拡張した場合にのみアラームを検討してください。 | [vSAN Health Service - Witness host within vCenter cluster (2130587)](https://kb.vmware.com/s/article/2130587){:new_window} |
| vSAN 健全性アラーム (vMotion 用) `基本 (ユニキャスト) 接続チェック (通常の ping)` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [VSAN health shows connectivity errors](https://developer.ibm.com/answers/questions/452172/vsan-health-shows-connectivity-errors/){:new_window} |
| vSAN 健全性アラーム (vMotion 用)  `MTU チェック (パケット サイズの大きい ping)` | 重大なイベントについて E メールを 1 回送信するように構成します。 | [vSAN Health Service - Network Health - Hosts small ping test (connectivity check) and Hosts large ping test (MTU check) (2108285)](https://kb.vmware.com/s/article/2108285){:new_window} |
| VSAN 健全性サービスのアラーム (VSAN Health Service Alarm) | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |
| VSAN 健全性サービスのアラーム (全体の健全性の要約) (vSAN health service alarm for Overall Health Summary) | 重要な通知とは見なされません。 プロアクティブな日常検査の一部として検討するアラームです。 | 追加情報なし |


## 事前構成アラーム - Hybridity Bundle
{: #opsprocs-alarms-preconfigured-hcx}

Hybridity Bundle では HCX がインストールされるので、以下の追加の事前構成アラームが作成されます。

表 3. 事前構成アラーム - HCX

| アラーム名 | ガイダンス | 詳細情報 |
|---|---|---|
| 一括移行が失敗しました (Bulk Migration Failed) | 重要な通知とは見なされません。移行は管理されているからです。 | [HCX troubleshooting](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting) と [VMware HCX Troubleshooting](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window} を参照。 |
| コールド移行が失敗しました (Cold Migration Failed) | 重要な通知とは見なされません。移行は管理されているからです。 | [HCX troubleshooting](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting) と [VMware HCX Troubleshooting](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window} を参照。 |
| HCX クラウド データベースのアップグレードが失敗しました (HCX Cloud Database Upgrade Failed) | 重要な通知とは見なされません。アップグレードは管理されているからです。 | [HCX troubleshooting](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting) と [VMware HCX Troubleshooting](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window} を参照。 |
| HCX エンタープライズ データベースのアップグレードが失敗しました (HCX Enterprise Database Upgrade Failed) | 重要な通知とは見なされません。アップグレードは管理されているからです。 | [HCX troubleshooting](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting) と [VMware HCX Troubleshooting](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window} を参照。 |
| HCX 相互接続トンネルのステータス (HCX Interconnect tunnel status) | トンネルのステータスがダウンしたという重大なイベントについて E メールを 1 回送信するように構成します。 | [Network (WAN) connectivity](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting#hcxclient-troubleshooting-wan-connect) を参照。 |

## イベントとアラームの手順
{: #opsprocs-alarms-procedures}

イベントとアラームの手順を以下の表にまとめます。

表 4. イベントとアラームの手順

| タイトル | 説明 |
|---|---|
| イベントの表示  | イベントを表示するには、vCenter にナビゲートし、インベントリー・オブジェクトを選択します。 **「監視」**タブをクリックし、**「タスク」&「イベント」**をクリックし、**「イベント」**をクリックします。 詳細を表示するイベントを選択します。 フィルターを使用したり、列見出しを選択してリストをソートしたりできます。 |
|  イベントのエクスポート  | MS Excel のツールを利用するために、イベントをエクスポートしたい場合があります。 必要なインベントリー・オブジェクトを選択します。 **「監視」**タブをクリックし、**「イベント」**をクリックし、**「エクスポート」**アイコンをクリックします。 **「イベントのエクスポート」**ウィンドウで、エクスポートするイベント情報のタイプを指定します。 **「CSV レポートの生成 (Generate CSV Report)」**を選択し、**「保存」**をクリックします。 ファイル名と場所を指定して、ファイルを保存します。 |
| イベントの保存  |  デフォルトでは、イベントの保存期間は 30 日に設定されます。 VMware vSphere Web Client で設定を変更する必要があります。 **「構成」**タブをクリックし、**「設定」**、**「一般」**の順にクリックします。 **「編集」**をクリックし、イベントの保存期間を必要な日数に変更し、**「OK」**をクリックします。 |
| 起動されたアラームの表示  | 起動されたアラームを表示するには、vCenter にナビゲートし、**「アラーム」**ペインで**「すべて」**または**「新規」**を選択します。 このリストは 120 秒ごとに最新表示されます。 選択したインベントリー・オブジェクトについて起動されたアラームを表示するには、そのオブジェクトを選択します。 **「監視」**タブをクリックし、**「問題」**をクリックし、**「起動されたアラーム (Triggered Alarms)」**を選択します。 |

## 関連リンク
{: #opsprocs-alarms-links}

* [vSphere Monitoring and Performance](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-monitoring-performance-guide.pdf){:new_window}
