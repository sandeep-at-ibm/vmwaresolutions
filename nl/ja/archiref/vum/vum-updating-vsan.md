---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# vSAN クラスターの更新
{: #vum-updating-vsan}

vSAN では、VUM で使用するシステム・ベースラインおよびベースライン・グループを生成します。これらの推奨されるベースラインを使用して、vSAN を使用する VMware vCenter Server on {{site.data.keyword.cloud_notm}} インスタンス内の vSphere ESXi ホストのソフトウェア、パッチ、および拡張機能を更新できます。 vSAN 6.6.1 以降では、vSAN クラスター用の自動化されたビルド推奨が生成されます。 vSAN では、「VMware Compatibility Guide」と vSAN リリース・カタログの情報を、インストールされている vSphere ESXi リリースに関する情報と組み合わせます。

これらの推奨される更新により、ハードウェアをサポートされている状態に保つために使用可能な最良のリリースが提供されます。
* **vSAN システム・ベースライン** - vSAN ビルド推奨は VUM 用の vSAN システム・ベースラインを介して提供されます。 vSAN では、vSAN クラスターごとに 1 つのベースライン・グループが生成され、これらは「Baselines and Groups」タブの「Baselines」ペインにリストされます。 VUM では、各 vSAN クラスターを自動的にスキャンして、ベースライン・グループに対するコンプライアンスを検査します。 ただし、vSAN クラスターをアップグレードするには、VUM を使用してシステム・ベースラインを手動で修復する必要があり、この場合、単一ホストまたはクラスター全体で vSAN システム・ベースラインを修復できます。
* **vSAN リリース・カタログ** - vSAN リリース・カタログには、使用可能なリリースに関する情報、リリースの優先順序、および各リリースに必要な重要なパッチが保守されます。 vSAN では、リリース・カタログにアクセスするためにインターネット接続が必要です。 vSAN がリリース・カタログにアクセスするために、ユーザーがカスタマー・エクスペリエンス向上プログラム (CEIP) に登録する必要はありません。
* **vSAN ビルド推奨**の使用 - VUM では、インストールされている vSphere ESXi リリースを「VMware Compatibility Guide」のハードウェア互換性リスト (HCL) に照らして検査します。 これにより、現在の vSAN リリース・カタログに基づいて、各 vSAN クラスターに適切なアップグレード・パスを判別します。 vSAN のシステム・ベースラインには、推奨リリースに必要なドライバーおよびパッチ更新も含まれています。 vSAN ビルド推奨により、各 vSAN クラスターが現在のハードウェア互換性状況以上の状態を保持することが保証されます。 vSAN クラスター内のハードウェアが HCL に含まれていない場合、vSAN により、最新リリースへのアップグレードが推奨されます。

vSAN クラスターのアップグレードは、以下の一連のタスクで進行します。
* **vSAN オンライン・ヘルス・ワークフローの有効化** - このワークフローを使用すると、VUM 内の vSAN ベースラインが有効になり、更新を確認および修復できます。 このワークフローは、VUM で vSAN を有効にするためにのみ、最初に実行する必要があります。
* **前提条件** - 前提条件、プロセス、および制約事項を理解します。
* **vCenter Server Appliance をアップグレードします**。 詳しくは、[VCSA 更新および SSO がリンクされた vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa) を参照してください。
* **vSphere ESXi ホストのアップグレード** - 詳しくは、[ベースラインの作成とインベントリー・オブジェクトへの接続](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines)を参照してください。
* **vSAN ディスク・フォーマットのアップグレード** - 『vSAN ディスク・フォーマットのアップグレード』を参照してください。 ディスク・フォーマットのアップグレードはオプションですが、最良の結果を得るために、最新バージョンを使用するようオブジェクトをアップグレードします。 オンディスク・フォーマットでは、vSAN の機能セット全体に環境が公開されます。

## vSAN オンライン・ヘルス・ワークフローの有効化
{: #vum-updating-vsan-enable-vsan-workflow}

VUM で vSAN ベースラインを使用可能にするには、以下のセクションのタスクを使用します。 vSAN 6.6.1 以降では、VMware vCenter Server on {{site.data.keyword.cloud_notm}} インスタンスをサポートされている状態に保つために、使用可能な最良のリリースを使用して vSAN クラスターが最新の状態となるよう、シームレスな自動更新プロセスを提供します。
* **vSAN バージョン推奨** - 「VMware Compatibility Guide」、vSAN リリース・カタログ、および基礎となるハードウェア構成の認識からの情報を使用して、自動的に生成されます。 このシステム・ベースラインには、推奨リリースに必要なドライバーおよびパッチ更新も含まれています。
* **vSAN ビルド推奨** - クラスターが現在のハードウェア互換性状況以上の状態を保持することが保証されます。

続行する前に、VCSA が vCenter 6.5 パッチ 2 以降のバージョンであることを確認してください。これにより、プロキシーの使用に関する問題が修正されます。 詳しくは、[VCSA 更新および SSO がリンクされた vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa) を参照してください。

VUM で vSAN が更新されたことを確認するには、vSAN オンライン・ヘルス・ワークフローに従います。 したがって、vSAN オンライン・ヘルス・ワークフローを有効にするために、vSAN オンライン・ヘルスで `vcsa.vmware.com` および `vmware.com` の各サイトに接続し、以下のオンライン・ヘルス・チェックを実行する必要があります。
* プロキシーを使用するための VCSA の構成
* プロキシーを使用するための vSAN の構成
* カスタマー・エクスペリエンス向上プログラム (CEIP) の有効化
* テスト・アップロードの実行およびアップロードが機能したことの確認

最初のステップでは、vSAN ビルド推奨エンジンに my.vmware.com 資格情報を追加します。 正常にログインすると、vSAN では、vSAN クラスターごとに推奨される更新のベースライン・グループが生成されます。 vSAN システム・ベースラインは、「Baselines and Groups」タブの「Baselines」ペインにリストされます。

### プロキシーを使用するための VCSA の構成
{: #vum-updating-vsan-config-vcsa-proxy}

1.	ジャンプ・サーバーの Web ブラウザーから、VCSA 管理インターフェース (`https://<vCenter ip>:5480`) に接続します。
2.	IC4VS コンソールから資格情報を使用して、VCSA 管理インターフェースに root としてログインします。
3.	vCenter Server Appliance 管理インターフェースで、**「Networking」**をクリックして**「Manage」**をクリックします。
4.	プロキシー・サーバーを構成するには、「Proxy Settings」ペインで**「Edit」**をクリックします。
5.	**「Use a Proxy Server」**を選択してプロキシー・サーバー設定を入力し、**「OK」**をクリックします。

プロキシー情報に HTTPS ではなく HTTP のみが設定されるということが報告されています。 HTTPS トラフィックもプロキシー情報に構成するためには、先に HTTPS トラフィックを有効にしておく必要があります。 SSH 経由で VCSA にログインした後、proxy.get コマンドを使用して構成を表示し、HTTPS パラメーターが設定されていないことを確認します。

HTTPS パラメーターが設定されていない場合は、次のコマンドを使用します。
  `proxy.set --protocol https --server ``<proxy ip>`` --port 3128`

### プロキシーを使用するための vSAN の構成
{: #vum-updating-vsan-config-vsan-proxy}

1. **「Home」** > **「Hosts and Clusters」**にナビゲートし、ナビゲーション・ペインで**「vSAN cluster」**を選択してから、**「Configure」タブ**を選択して**「vSAN」**、**「General」**の順にナビゲートします。 **「Internet Connectivity」**セクションまでスクロールして、**「Edit」**をクリックします。
2. プロキシーの IP アドレスとポート番号を入力し、**「OK」**をクリックします。

### カスタマー・エクスペリエンス向上プログラム (CEIP) の有効化
{: #vum-updating-vsan-enable-ceip}

これはオプション・ステップです。 vSphere Web Client を使用して、**「Home」** > **「Administration」** > **「Customer Experience Improvement Program」**にナビゲートしてから、**「Join」**をクリックします。

### テスト・アップロードを実行し、アップロードが成功したことを確認する
{: #vum-updating-vsan-complete-upload}

1. vSphere Web Client を使用して、**「Home」** > **「Hosts and Clusters」**にナビゲートします。 必要なクラスターを選択して、**「Monitor」タブ**および**「vSAN」**ページを選択してから、**「Health」**をクリックします。 **「Enable Online Health」**をクリックします。
2. **「Retest」**をクリックし、プロセスが完了するまで待機します。
3. _「Online health connectivity」_という新しいチェックが「Health」に表示され、**「Enable Online Health」**が**「Retest with Online Health」**に変わります。
4. **「Retest with Online Health」**をクリックして最初のアップロードを開始し、「Recent Tasks」ペインで状況を確認してプロセスが完了するまで待ちます。 「Test Name」が「Online health」に変わります (「Last check」は「just now」になります)。
5. 完了したら、「Health」ウィンドウで、「vSAN Build Recommendation」までスクロールして展開し、**「vSAN Build Recommendation Engine Health」**をクリックします。
6. **「Login to my.vmware.com」**をクリックして、資格情報を入力します。 プロセスが完了すると、**「Test Result」**が**「Passed」**状態に変わります。
7. **「Update Manager」タブ**を押すと、vSAN クラスターがベースラインに追加されます。

## 前提条件
{: #vum-updating-vsan-prereq}

vSAN アップグレード・プロセスを開始する前に、以下の要件が満たされていることを確認してください。
* VMware 知識ベースの記事を確認し、現在の vSAN バージョンと必要なターゲット vSAN バージョンとの間の既知の互換性に関するすべての問題を確認します。
* **vSphere 環境が最新であることを確認します**。
  - VCSA は、vSphere ESXi ホストと同等以上のパッチ・レベルである必要があります。 必要に応じて、VCSA を更新します。
  - すべてのホストが同じビルドの ESXi を実行している必要があります。 vSphere ESXi ホストのバージョンが一致しない場合は、更新します。
* **すべての vSAN ディスクは正常である必要があります**:
  - 故障または欠落したディスクはありません。 これは、vSphere Web Client の**「vSAN Disk Management」**ビューを使用して判別できます。 **「Home」** > **「Hosts and Clusters」**を選択してから、**「vSAN Cluster」**を選択して、**「vSAN」タブ**、**「Physical Disks」**の順にクリックします。 すべてのディスクをスクロールして、vSAN のヘルス状況を確認します。
  - アクセス不能な vSAN オブジェクトはありません。 これは、**「Home」** > **「Hosts and Clusters」**をクリックしてから**「vSAN Cluster」**を選択し、**「vSAN Health Service」**で確認できます。 **「Monitor」タブ**、**「vSAN」**をクリックしてから**「Health」**をクリックします。 テスト結果を確認します。
  - アップグレード・プロセスの開始時、**「Home」** > **「Hosts and Clusters」**をクリックしてから、**「vSAN Cluster」**を選択して**「vSAN」タブ**、**「Resync Components」**の順にクリックしたときに、アクティブな再同期はありません。 _再同期コンポーネント数は 0 である必要があります_。 ホストの再始動後にデータを同期する必要があるため、アップグレード・プロセス中はいくつかの再同期アクティビティーがあることが予期されます。
* **vSphere ESXi ホストの準備** - vSAN クラスターでホストを保守モードに移行する場合、以下の 3 つのオプションがあります。
  - **No data migration** - このオプションを選択する場合、vSAN では、データをこのホストからは退避しません。 ホストの電源をオフにするか、クラスターからホストを削除すると、一部の仮想マシン (VM) がアクセス不能になる場合があります。
  - **Ensure availability** - このオプションを選択すると、vSAN では、全データ・マイグレーションよりも高速にホストを保守モードに移行でき、環境内の VM にアクセスできます。
  - **Full data migration**
* **保守モードおよび再同期の終了** - vSphere ESXi ホストがアップグレードされ、保守モードが終了すると、再同期が行われます。 これは、Web クライアントを使用して確認できます。 次のホストに移動する前に、これが完了していることを確認してください。 更新されたホストを再度 vSAN データ・ストアに使用できるようになったため、再同期が行われます。 データ損失を防ぐには、この再同期が完了するまで待機することが重要です。
* **vSAN クラスターのアップグレードの開始後**:
  - クラスターに新しいバージョンを導入したり、ワークロードをマイグレーションしたりして、クラスターのアップグレードを試行しないでください。
  - 新規ホストを導入する場合は、これらのホストが同じ初期バージョンであることを確認し、残りのクラスターとともにアップグレードします。
  - アップグレード中にディスクを追加または置換する場合は、適切なレガシー・オンディスク・フォーマット・バージョンでフォーマットされていることを確認してください (該当する場合)。
  - したがって、特定の vSAN 動作変更はオンディスク・フォーマットによって制御されるため、より新しいオンディスク・フォーマット・バージョンを混合バージョン・クラスターに導入しないようにすることが重要です。

## vCenter Server Appliance のアップグレード
{: #vum-updating-vsan-upgrade-vcsa}

詳しくは、[VCSA 更新および SSO がリンクされた vCenter](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa) を参照してください。

##	vSphere ESXi ホストのアップグレード
{: #vum-updating-vsan-upgrade-hosts}

詳しくは、[ベースラインの作成とインベントリー・オブジェクトへの接続](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines)を参照してください。

##	vSAN ディスク・フォーマットのアップグレード
{: #vum-updating-vsan-upgrade-vsan}

Ruby vSphere Console (RVC) は、vSphere 用の Ruby ベースのコマンド・ライン・インターフェースであり、VMware vSphere ESXi および vCenter の管理に使用できます。 vSphere インベントリーはツリー構造で表示されるため、vCenter オブジェクトにナビゲートしてコマンドを実行できます。

vSphere Client でクリックするよりも、より効率的に多くの基本的な管理用タスクを実行できます。 RVC は VCSA に完全に実装されており、VCSA にはアプライアンスへの SSH 接続によってアクセスします。
1. VCSA に SSH で接続し、root および ICVS コンソールで指定したパスワードを使用してログインします。
2. プロンプトで、
  `rvc Administrator@vsphere.local@localhost` と入力し、**Enter** キーを押します。
3. ICVS コンソールで指定した管理者パスワードを入力します。 次は、仮想ファイル・システムのルートに移動します。ls と入力してから **Enter** キーを押すと、次のように表示されます。
  `0 /
  1 localhost/``

5. `cd 1` と入力してから、`ls` と入力し、**Enter** キーを押します。 次のように表示されます。
  `0 / datacenter1 (datacenter)`

6. `cd 0` と入力してから、`ls` と入力し、**Enter** キーを押します。 以下が表示されます。

  `0 storage/
  1 computers [host]/
  2 networks [network]/
  3 datastores [datastore]/
  4 vms [vm]/`

7. `cd 1` と入力して **Enter** キーを押してから、`ls` と入力して **Enter** キーを押します。 次のようにクラスターが表示されます。
  `0 cluster1 (cluster)``

8. このクラスターに対して VSAN コマンドを使用します。 ディスク状況を確認するには、`vsan.disks_stats 0` と入力して **Enter** キーを押します。

9. すべてのディスクのヘルス状況が「OK」であることを確認します。 次に、`vsan.ondisk_upgrade 0` と入力して **Enter** キーを押し、アップグレードを開始します。

10. vSAN のサイズによっては、このタスクに時間がかかる場合があります。 完了したら、`vsan.objstatusreport 0` と入力してから **Enter** キーを押して、オブジェクト・バージョンが新しいオンディスク・フォーマットにアップグレードされていることを確認します。

11. これで VSAN クラスターのアップグレードが完了しました。 `exit` と入力して **Enter** キーを押し、RVC を終了します。

## 関連リンク
{: #vum-updating-vsan-related}

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (デモンストレーション)
