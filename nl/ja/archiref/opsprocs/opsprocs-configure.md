---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# 構成タスク
{: #opsprocs-configure}

vCenter Server インスタンスがプロビジョンされたら、初期環境を企業のニーズに合わせて調整し、将来のサービス要求に対応するために、システム管理者が実行する必要がある構成タスクがいくつかあります。使いやすくするために、それらを以下のように分類しました。

* インスタンスとクラスターのガイダンス
* 仮想マシン (VM) の手順
* vCenter の手順
* vSphere ESXi ホストの手順
* ストレージの手順
* ネットワークの手順

## インスタンスとクラスターのガイダンス
{: #opsprocs-configure-instance}

表 1. vCenter Server のインスタンスおよびクラスター

| タイトル | 説明 |
|---|---|
| 命名規則  |  最初のタスクの 1 つは、vCenter Server インスタンスの命名規則を導入することです。組織で使用されている既存の命名規則を拡張することも、新たに作成することもできます。詳しくは、[Naming Convention in VMware Validated Design 4.1](https://docs.vmware.com/en/VMware-Validated-Design/4.1/com.vmware.vvd.sddc-upgrade.doc/GUID-FCA126F1-E429-454E-B3BA-226525742DC1.html){:new_window} を参照してください。命名規則を導入して vCenter Server インスタンス内のいずれかの名前を変更する前に、[vCenter Server 成果物の変更に関する考慮事項](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact){:new_window}を参照してください。|
| vCenter Server インスタンスへの接続  | プロビジョンが完了したら、vCenter に接続します。最初にこれを行うには 2 つの方法があります。「ジャンプボックス」サーバーをデプロイし、インターネットを使用してジャンプボックスに接続して、ジャンプボックスからプライベート・ネットワークを使用して vCenter に接続できます。2 つ目の方法は、ユーザーのロケーションから {{site.data.keyword.cloud_notm}} プライベート・ネットワークへの VPN 接続である {{site.data.keyword.cloud_notm}} VPN を使用する方法です。これにより、アウト・オブ・バンドの管理および vCenter アクセスが可能になります。詳しくは、[仮想プライベート・ネットワーキング (VPN) の概要](/docs/infrastructure/iaas-vpn?topic=VPN-gettingstarted-with-virtual-private-networking){:new_window}を参照してください。|
| 名前解決の構成 |  vCenter の機能を使用するには、接続方式に応じてワークステーションまたはジャンプボックスに vCenter Server コンポーネントの名前解決を追加します。/etc/hosts ファイルまたは c:&#xa5;Windows&#xa5;System32&#xa5;Drivers&#xa5;etc&#xa5;hosts ファイルに、Platform Services Controller (PSC)、vCenter、および vSphere ESXi ホストを登録する必要があります。詳しくは、[VMware vSphere Web Client を使用した OVF ファイルのデプロイ](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_deploy_ovf#trbl_deploy_ovf){:new_window}を参照してください。|
| RBAC | vSphere 環境の一般的なタスクに必要な特権については、[Required Privileges for Common Tasks](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-4D0F8E63-2961-4B71-B365-BBFA24673FDB.html){:new_window} を参照してください。|
| 認証局の署名付きのカスタム証明書の使用 |  vSphere 6.x マシンの SSL 証明書を認証局 (CA) の署名付きのカスタム証明書に置き換える方法については、[Replacing a vSphere 6.x Machine SSL certificate with a Custom Certificate Authority Signed Certificate (2112277)](https://kb.vmware.com/s/article/2112277){:new_window} を参照してください。|
| vSphere モニターの構成  | vSphere にはユーザーが構成できるイベントとアラームのサブシステムが含まれており、このサブシステムは vSphere コンポーネントのイベントを追跡してログ・ファイルと vCenter データベースにデータを保管します。イベントは、vSphere オブジェクトで発生したユーザーまたはシステムのアクションのレコードです。イベントには、情報、警告、およびエラーという 3 つのタイプがあります。アラームは、イベント、一連の条件、または vSphere オブジェクトの状態への応答として起動される通知です。アラームの重大度レベルは、正常 (緑)、警告 (黄色)、およびアラート (赤) です。アラーム・アクションは、アラームへの応答として実行される操作です (E メール通知を送信するなど)。vSphere モニターを構成および使用する方法については、[Monitoring Events, Alarms, and Automated Actions](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window} を参照してください。|
| クラスターの追加、表示、削除 | vCenter Server インスタンスは vSphere ESXi ホストのクラスターとともにデプロイされています。クラスターをインスタンスにさらに追加して、コンピュートやストレージの容量を拡張できます。詳しくは、[vCenter Server インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters){:new_window}を参照してください。|
| vCenter Server の容量 |VMware vCenter Server インスタンスの容量は、vSphere ESXi サーバーまたはネットワーク・ファイル・システム (NFS) ストレージを追加/削除することで、ビジネス・ニーズに応じて拡張/縮小できます。詳しくは、[vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers){:new_window}を参照してください。|
| vCenter Server インスタンスのサービス | vCenter Server インスタンスがデプロイされた後に、災害復旧、重大度、バックアップのソリューションなどの追加サービスをポートフォリオから追加できます。これらのサービスが不要になった場合は、インスタンスから削除できます。詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices){:new_window}を参照してください。|
| vCenter Server インスタンスの更新 | vCenter Server インスタンスに更新を適用する方法については、[vCenter Server インスタンスへの IBM 管理コンポーネントの更新の適用](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_applyingupdates#vc_applyingupdates)を参照してください。vCenter Server インスタンスにパッチと更新を適用するこのプロセスが自動化されているのは、管理コンポーネントだけです。システム管理者が VMware 製品の更新を手動で適用する方法については、[vCenter Server on IBM Cloud with Hybridity Bundle の概要](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-hybridity-intro#vcs-hybridity-intro){:new_window}を参照してください。|
| マルチサイト構成 |マルチサイト構成機能では、1 つのプライマリー・サイトと最大 7 つのセカンダリー・サイトで構成されるハブ・アンド・スポークのトポロジーを使用します。vCenter Server on {{site.data.keyword.cloud_notm}} インスタンスのマルチサイト構成を行う方法については、[vCenter Server on IBM Cloud インスタンスのマルチサイト構成](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_multisite#vc_multisite){:new_window}を参照してください。マルチサイト構成の vCenter Server インスタンスを削除する手順については、[マルチサイト構成での vCenter Server インスタンスの削除](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_deletinginstance_multi#vc_deletinginstance_multi){:new_window}を参照してください。|
| VMware Update Manager の使用 | デプロイ後の VMware 製品はシステム管理者が更新します。システム管理者が vCenter Server インスタンスで VUM を使用する方法については、[VMware Update Manager の概要](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro){:new_window}を参照してください。|
| Key vCenter Server インスタンスのコンポーネントのバックアップ | vCenter Server インスタンスのすべてのソフトウェア・コンポーネントの構成、管理、およびモニター (管理用のインフラストラクチャーやワークロードのバックアップと可用性を含む) を行うのは、お客様のシステム管理者です。そのソリューションの一部として、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} アドオン・サービスや Veeam on {{site.data.keyword.cloud_notm}} アドオン・サービスをデプロイすることもできます。Veeam や IBM Spectrum Protect Plus を使用して、管理コンポーネントのバックアップ要件を満たすことができます。バックアップのメカニズム、および、バックアップすべき重要なコンポーネントについては、[コンポーネントのバックアップ](/docs/services/vmwaresolutions/archiref/solution/solution_backingup.html#vcenter-file-based-backup){:new_window}を参照してください。|
| VMware 製品の診断情報の収集 | VMware テクニカル・サポートは、サポート要求への対応時に決まって診断情報を要求します。この診断情報には、製品固有のログ、構成ファイル、状況に応じたデータが含まれます。この情報の収集に関する VMware Knowledgebase の記事の URL、および、収集作業の詳しい説明については、[Collecting diagnostic information for VMware products (1008524)](https://kb.vmware.com/s/article/1008524?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} を参照してください。VMware NSX Edge デバイスに関する必要な診断情報を収集するプロセスについては、[Collecting diagnostic information for VMware NSX Edge (2079380)](https://kb.vmware.com/s/article/2079380?lang=en_US#q=Collecting%20diagnostic%20information%20for%20VMware%20NSX%20Edge%20){:new_window} を参照してください。|

## VM の手順
{: #opsprocs-configure-vm}

表 2. VM の手順

| タイトル	| 説明 |
|---|---|
| VM の作成 | 新しい VM を作成する方法については、[Create a Virtual Machine with the New Virtual Machine Wizard](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-AE8AFBF1-75D1-4172-988C-378C35C9FAF2.html?hWord=N4IghgNiBcIMICcCmYAuSAEYMDUCWCqArpBgLJgDGAFngHaYDueq1GrmAcko7gcaQo16mAOp4AXmAQATEAF8gA) を参照してください。|
| VM の構成 | VM ハードウェアを構成する方法については、[Configuring Virtual Machine Hardware](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-4AB8C63C-61EA-4202-8158-D9903E04A0ED.html){:new_window} を参照してください。|
| VM へのゲスト OS のインストール | ゲスト OS を VM にインストールするプロセスについては、[Installing a Guest Operating System](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-90E7F734-D699-4603-B222-AF4DE84459C7.html){:new_window} を参照してください。|
| スナップショットの作成 | スナップショットは、そのスナップショットを取得した時点の VM 全体の状態をキャプチャーします。スナップショットは、VM の電源がオン、オフ、一時停止のどの状態でも取得できます。詳しくは、[Take a Snapshot in the VMware Host Client](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.html.hostclient.doc/GUID-A0D8E8E7-629B-466D-A50C-38705ACA7613.html){:new_window} を参照してください。|
| スナップショットの復元 | スナップショットを開始した時点の過去の状態に VM の状態を復元する方法については、[Restoring Snapshots](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E0080795-C2F0-4F05-907C-2F976433AC0D.html){:new_window} を参照してください。|
| VM およびテンプレートの削除と追加 | VM および VM テンプレートを vCenter インベントリーから削除する方法、または、ディスクから削除する方法については、[Removing and Reregistering VMs and VM Templates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-376174FE-F936-4BE4-B8C2-48EED42F110B.html){:new_window} を参照してください。|
| VM / ツールのアップグレード | 高い互換性レベルおよび高いバージョンの VMware ツールに VM をアップグレードする方法については、[Upgrading Virtual Machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE77B0A9-F8FF-4785-BEAD-B6F04EE04492.html){:new_window} を参照してください。|
| ディスクの追加	| 既存の VM にディスクを追加する方法については、[Add a Hard Disk to a Virtual Machine](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-79116E5D-22B3-4E84-86DF-49A8D16E7AF2.html){:new_window} を参照してください。|
| ディスクの圧縮 | 既存の VM のディスクを圧縮する方法については、[Growing, thinning, and shrinking virtual disks for VMware ESX and ESXi (1002019)](https://kb.vmware.com/s/article/1002019){:new_window} を参照してください。|
| ディスクの拡張	| 既存の VM のディスクのサイズを拡張する方法については、[Change the Virtual Disk Configuration](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E1D541D1-DF96-467A-89B7-E84F83B2563D.html){:new_window} を参照してください。|
| ホット移行 | 同じクラスター内の vSphere ホスト間で VM の vMotion を行う方法については、[Managing Virtual Machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-B7023DD7-F790-4DF8-89B4-FF09DA3DBFB1.html?hWord=N4IghgNiBcIBYHsAuACAtgSwOYCcxIFMUA3NEAXyA){:new_window} を参照してください。|
| コールド移行 | vCenter Server のインスタンス間で VM を移行する方法については、[Migrate a Powered Off or Suspended Virtual Machine](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E8DE930E-8079-4AC0-AEC2-B6EA1604F4E3.html){:new_window} を参照してください。|
| VM の削除 | VM を削除する方法については、[Remove VMs or VM Templates from vCenter Server or from the Datastore](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-27E53D26-F13F-4F94-8866-9C6CFA40471C.html){:new_window} を参照してください。|
| ディスクの削除 | VM からディスクを削除する方法については、[Remove a Hard Disk from a Virtual Machine](https://pubs.vmware.com/vsphere-4-esx-vcenter/index.jsp?topic=/com.vmware.vsphere.webaccess.doc_41/configuring_virtual_machine_options_and_resources/t_remove_an_existing_hard_disk.html){:new_window} を参照してください。|
| VM ツール | VM ツールを更新するプロセスについては、[ベースラインの作成とインベントリー・オブジェクトへの接続](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-baselines#vum-baselines)を参照してください。|
| 仮想ディスクの形式を確認し、シン・プロビジョン形式の仮想ディスクをシック・プロビジョン形式に変換する| シン・プロビジョン形式の仮想ディスクとして作成された VM ディスクをシック・プロビジョン形式に変換するプロセスについては、[Determine the Virtual Disk Format and Convert a Virtual Disk from the Thin Provision Format to a Thick Provision Format](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E8F50BEC-F575-4AB1-BC77-D9A13CDBDCF7.html){:new_window} を参照してください。|
| AD/DNS サーバーの OS の更新  | Microsoft Active Directory (AD) / ドメイン・ネーム・サーバー (DNS) には、更新プログラムのダウンロードだけが自動的にセットアップされます。詳しくは、[Windows 更新プログラムの自動インストール](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_limitations#trbl_limitations-windows-update)を参照してください。|

## vCenter の手順
{: #opsprocs-configure-vcenter}

表 3. vCenter の手順

| タイトル | 説明 |
|---|---|
| VCSA のバックアップ	| 詳しくは、[vCenter Server Appliance 6.7 File-Based Backup and Restore Walkthroughs](https://blogs.vmware.com/vsphere/2018/05/vcenter-server-appliance-6-7-file-based-backup-and-restore-walkthroughs.html){:new_window} を参照してください。|
| VSCA/PSC のパッチ適用	| 詳しくは、[Patching the vCenter Server Appliance and Platform Services Controller Appliance](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-043EF6BD-78F7-412F-837F-CBDF844F850C.html){:new_window} を参照してください。|
| VCSA サービスの停止、開始、または再始動 | トラブルシューティングや保守のために、VMware vCenter Server Appliance (VCSA) サービスの状況を変更する必要がある場合があります。詳しくは、[Stopping, starting, or restarting VMware vCenter Server Appliance 6.x services (2109887)](https://kb.vmware.com/s/article/2109887?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} を参照してください。|
| VCSA のバックアップとリストアのオプションの概要 |	詳しくは、[Overview of Backup and Restore options in vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window} を参照してください。|
| vCenter の E メール通知の構成 | 定義済みのアラームとカスタム作成アラームで特定の条件がトリガーされた場合に E メール・アドレスに E メール通知を送信するように構成する方法については、[Configuring an email alert for the vCenter Server alarm (2123925)](https://kb.vmware.com/s/article/2123925?lang=en_US){:new_window} を参照してください。|

## vSphere ESXi ホストの手順
{: #opsprocs-configure-host}

表 4. vSphere ESXi ホストの手順

| タイトル | 説明 |
|---|---|
| vSphere ホストの保守	| アップグレードや物理デバイスの交換などの保守タスクを実行する必要があるときには、ホストを保守モードにします。ホストの保守モードの開始/終了は、システム管理者が要求した場合にのみ実行されます。保守モードにするホストで稼働中の VM は、別のホストに (手動または DRS を介して自動で) 移行するかシャットダウンする必要があります。詳しくは、[Place a Host in Maintenance Mode](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html?hWord=N4IghgNiBcIG4GUAOALApgJzQAgBIHsBnAF2wFkwBLAO2LWrGoGM0QBfIA){:new_window} を参照してください。|
| vSphere ESXi ホストの追加 | 詳しくは、[vCenter Server インスタンスへの ESXi サーバーの追加](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-adding){:new_window}を参照してください。
| vSphere ESXi ホストの削除 |	詳しくは、[ESXi サーバーを削除する手順](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing-procedure){:new_window}を参照してください。|
| ベア・メタル・サーバーのファームウェアのパッチ適用 | 詳しくは、[ベア・メタル・サーバーのファームウェアが古い場合、どうすればよいでしょうか?](/docs/bare-metal/faq.html#what-if-my-bare-metal-server-has-out-of-date-firmware-){:new_window} を参照してください。|
| vSphere ESXi ホストのパッチ適用 | VMware Update Manager (VUM) を使用して vSphere ESXi ホストだけでなく他のいくつかの vCenter Serer インスタンス・コンポーネントも更新する方法については、[VMware Update Manager の概要](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro){:new_window}を参照してください。|
| ホスト・ネットワーク接続のテスト	| vSphere ESXi ホストと物理スイッチの物理ネットワーク・アダプター間のネットワーク・リンクが稼働中で使用可能であることを確認する方法については、[Verifying network links (1003724)](https://kb.vmware.com/s/article/1003724?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} を参照してください。|
| ESXi でのネットワーク/ストレージのファームウェアとドライバーのバージョンの判別 | 詳しくは、[Determining Network/Storage firmware and driver version in ESXi 4.x and later (1027206)](https://kb.vmware.com/s/article/1027206?lang=en_US#q=network%20interface%20card%20error){:new_window} を参照してください。|
| ESXi でのネットワークおよび TCP/UDP ポート接続の問題のトラブルシューティング | 詳しくは、[Troubleshooting network and TCP/UDP port connectivity issues on ESX/ESXi (2020669)](https://kb.vmware.com/s/article/2020669?lang=en_US#q=network%20interface%20card%20error){:new_window} を参照してください。|

## ストレージの手順
{: #opsprocs-configure-storage}

表 5. ストレージの手順

| タイトル | 説明 |
|---|---|
| {{site.data.keyword.cloud_notm}} エンデュランス NFS ストレージの追加 | 既存のクラスターに {{site.data.keyword.cloud_notm}} エンデュランス NFS 共有を追加する方法については、[vCenter Server インスタンスへの NFS ストレージの追加](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances){:new_window}を参照してください。|
| {{site.data.keyword.cloud_notm}} エンデュランス NFS ストレージの削除	| 既存のクラスターから {{site.data.keyword.cloud_notm}} エンデュランス NFS 共有を削除する方法については、[vCenter Server インスタンスからの NFS ストレージの削除](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing-nfs-storage){:new_window}を参照してください。
| {{site.data.keyword.cloud_notm}} エンデュランス NFS ストレージの拡張	| {{site.data.keyword.cloud_notm}} エンデュランス NFS 共有に容量を追加する方法については、[ブロック・ストレージ容量の拡張](/docs/infrastructure/BlockStorage?topic=BlockStorage-expandingcapacity#expandingcapacity){:new_window}を参照してください。|
| {{site.data.keyword.cloud_notm}} エンデュランス NFS ストレージの圧縮 | {{site.data.keyword.cloud_notm}} エンデュランス NFS 共有の容量を圧縮する方法については、[ブロック・ストレージ容量の拡張](/docs/infrastructure/BlockStorage?topic=BlockStorage-expandingcapacity#expandingcapacity){:new_window}を参照してください。|
| vSAN ポリシーのベスト・プラクティスのアドバイス | 詳しくは、[vSAN ポリシー設計](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure#design_virtualinfrastructure-storage-policy){:new_window}を参照してください。|
| vSAN 健全性チェックの有効化	| 詳しくは、[vSAN オンライン・ヘルス・ワークフローの有効化](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vsan#vum-updating-vsan-enable-vsan-workflow){:new_window}および [vSAN Health Check Information (2114803)](https://kb.vmware.com/s/article/2114803){:new_window} を参照してください。|
| 暗号化の有効化 |	KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスを使用して暗号化を有効にする方法については、[KMIP for VMware on IBM Cloud の概要](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations)を参照してください。VM の暗号化を有効にする方法については、[Virtual Machine Encryption](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.security.doc/GUID-E6C5CE29-CD1D-4555-859C-A0492E7CB45D.html){:new_window} を参照してください。保存データの暗号化を使用して vSAN クラスター内のデータを保護する方法については、[Using Encryption on a vSAN Cluster](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-F3B2714F-3406-48E7-AC2D-3677355C94D3.html){:new_window} を参照してください。|
| vSAN ストレージの追加	| 既存の vSAN クラスターに vSphere ESXi ホストを追加する方法については、[vCenter Server インスタンスへの ESXi サーバーの追加](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-adding){:new_window}を参照してください。ホストを追加して、クラスターの CPU、RAM、およびストレージを増やすことができます。vSAN テクノロジーについて詳しくは、[Expanding a vSAN Cluster](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-666D9839-2726-4936-8C0F-94476ECE0606.html){:new_window} を参照してください。|
| vSAN ストレージの削除	| vSAN クラスターからストレージを削除する方法については、[vCenter Server インスタンスからの ESXi サーバーの削除](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing){:new_window}を参照してください。ホストを削除して、クラスターの CPU、RAM、およびストレージを減らすことができます。|
| デフォルトの vSAN アラームの使用  | デフォルトの vSAN アラームを使用して、クラスター、ホスト、および既存の vSAN ライセンスをモニターできます。アラームに対応するイベントが起動されるか、アラームに指定した条件のいずれかまたはすべてが満たされると、アラームが自動的にトリガーされます。デフォルトのアラームは、条件を編集することも、アラームを削除することもできません。ユーザーの要件に固有のアラームを構成するには、vSAN のカスタム・アラームを作成してください。『Creating a vCenter Server Alarm for a vSAN Event』を参照してください。アラームとイベントのモニター、既存のアラーム設定の編集、デフォルトの vSAN アラームを使用したクラスターとホストのモニター、新規イベントの分析、およびクラスター全体の健全性の評価については、[Using the vSAN Default Alarms](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-E7885CDE-654D-4732-A5FE-31D0AB2B2F57.html){:new_window} を参照してください。|
| SIOC の有効化 | デフォルトでは、Storage IO Control (SIOC) は無効です。データ・ストア内の VM のパフォーマンスが低い場合は、ストレージ・リソースの優先順位付けを行うために SIOC を有効にすることができます。SIOC は、ストレージの競合が発生した場合にのみ活動化されて、すべての VM にストレージ・リソースが公平に割り当てられるようにします。そのためには、VM ストレージ・ポリシーを使用し、そのポリシーを VM または VMDK に割り当てます。詳しくは、[Managing Storage I/O Resources](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-7686FEC3-1FAC-4DA7-B698-B808C44E5E96.html){:new_window} を参照してください。|
| データ・ストア・クラスターの構成 | データ・ストア・クラスターは、リソースと管理インターフェースを共有するデータ・ストアの集合です。データ・ストア・クラスターとデータ・ストアの関係は、クラスターとホストの関係と同じです。データ・ストア・クラスターを作成すると、vSphere Storage DRS を使用してストレージ・リソースを管理できます。データ・ストアをデータ・ストア・クラスターに追加すると、そのデータ・ストアのリソースはデータ・ストア・クラスターのリソースの一部になります。データ・ストア・クラスターを使用してストレージ・リソースを集約すると、データ・ストア・クラスター・レベルでリソース割り振りポリシーを利用できます。詳しくは、[Creating a Datastore Cluster](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-598DF695-107E-406B-9C95-0AF961FC227A.html){:new_window} を参照してください。|


## ネットワークの手順
{: #opsprocs-configure-networks}

表 6. ネットワークの手順

| タイトル	| 説明 |
|---|---|
| ネットワークに関する考慮事項 | 詳しくは、[vCenter Server インスタンスのネットワーキングに関する考慮事項](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_networkingonvcenterserver){:new_window}を参照してください。|
| HCX の計画 | VMware Hybrid Cloud Services (HCX) を使用すると、各種ネットワーク・タイプをまたいで vSphere ソフトウェア定義データ・センター (SDDC) の別々のインスタンスを相互運用できます。HCX は、オンプレミスやクラウド・プロバイダーの境界をまたいで拡張したマルチインスタンス、マルチサイトの vSphere をデプロイする場合に遭遇するセキュリティー、互換性、複雑さ、パフォーマンスの問題を解決するために設計されたものです。詳しくは、[デプロイメント前の計画](/docs/services/vmwaresolutions?topic=vmware-solutions-vcshcx-planning#vcshcx-planning){:new_window}を参照してください。|
| NSX の初期構成 | vCenter Server インスタンスのデプロイメントの一部として、プライベート・サブネット、パブリック・サブネット、NSX 論理スイッチ、分散論理ルーターで構成されたサンプルの顧客ネットワークが提供されます。また、NSX エッジ・アプライアンスがデプロイされ、ネットワーク・アドレス変換を実行するように構成されます。このサンプルの顧客ネットワークを VM 用に構成する手順については、[ユーザー管理の NSX ESG を VM で使用するためのネットワークの構成](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_esg_config#vc_esg_config){:new_window}を参照してください。|
| 論理スイッチの追加 | VM を接続できるネットワーク接続を提供するという点では、論理スイッチは VLAN に似ています。同じ論理スイッチに接続した VM 同士は、VXLAN を介して相互に通信できます。論理スイッチを追加する場合は、作成する具体的なトポロジーを念頭に置くことが重要です。詳しくは、[Add a Logical Switch](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-DD31D6BC-2E56-4E91-B45F-FCA3E80FF786.html){:new_window} を参照してください。|
| DLR の追加 | 分散論理ルーター (DLR) は、接続された論理スイッチの間のルーティング (East-West トラフィック) を行う仮想アプライアンスです。詳しくは、[Add a Distributed Logical Router](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-E825C0C7-F4CC-4B26-90AF-A2167AC519DB.html){:new_window} を参照してください。|
| ESG の追加 | 外部サービス・ゲートウェイ (ESG) は、物理ネットワークと論理ネットワークの間のルーティング (North-South トラフィック) を行う仮想アプライアンスです。詳しくは、[Add an Edge Services Gateway](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-B9A97F20-4996-4E16-822C-0B98DDE70571.html){:new_window} を参照してください。|
| NSX エッジ・ファイアウォール・ルールの構成 | エッジ・ファイアウォールは、North-South トラフィックをモニターして、ファイアウォール、ネットワーク・アドレス変換 (NAT)、サイト間 IPSec、SSL VPN 機能などの境界セキュリティー機能を提供します。管理インターフェース、アップリンク・インターフェース、またはその両方に対するファイアウォール・ルールのみが適用されます。詳しくは、[Working with NSX Edge Firewall Rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-178B11B8-FEB1-49B8-B6FF-D069C41EEB32.html){:new_window} を参照してください。|
| 分散ファイアウォール | 分散ファイアウォールは、ハイパーバイザー・カーネルに埋め込まれたファイアウォールであり、VM のためのネットワーク・アクセス制御を提供します。データ・センター、クラスター、VM 名、IP、VLAN (DVS ポート・グループ)、VXLAN (論理スイッチ)、セキュリティー・グループなどの VMware vCenter オブジェクトと Active Directory のユーザー・グループ ID に基づいて、アクセス制御ポリシーを作成します。ファイアウォール・ルールは各 VM の vNIC レベルで適用されるため、VM を vMotion した場合でも一貫したアクセス制御が適用されます。詳しくは、[Distributed Firewall](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-95600C1C-FE9A-4652-821B-5BCFE2FD8AFB.html){:new_window} を参照してください。|
| NAT ルールの構成  | NSX Edge は、VM または VM グループに異なる送信元 IP アドレスまたは宛先 IP アドレスを割り当てるためのネットワーク・アドレス変換 (NAT) サービスを備えています。NAT サービスの構成は、送信元 NAT (SNAT) ルールと宛先 NAT (DNAT) ルールに分けられます。詳しくは、[Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window} を参照してください。|
| NSX ロード・バランサーの構成 | NSX Edge ロード・バランサーは、高可用性サービスを有効にし、ネットワーク・トラフィックの負荷を複数の VM に分散させます。着信サービス要求を、ユーザーからは透過的に、複数の VM 間で均等に負荷分散します。ロード・バランシングは、リソース使用効率の最適化、スループットの最大化、応答時間の最小化、および過負荷の回避に役立ちます。NSX Edge は、レイヤー 7 までのロード・バランシングを提供します。ロード・バランシングのために、外部またはパブリック IP アドレスを一連の内部 VM にマップしてください。ロード・バランサーは、外部 IP アドレスで TCP、UDP、HTTP、または HTTPS 要求を受け入れ、使用する内部サーバーを決定します。ポート 80 が HTTP のデフォルト・ポートで、ポート 443 が HTTPS のデフォルト・ポートです。NSX で使用可能なロード・バランシング・サービスには、ワンアーム・モード (プロキシー・モード) とインライン・モード (透過モード) という 2 つのタイプがあります。詳しくは、[Logical Load Balancer](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-152982CF-108F-47A6-B86A-0F0F6A56D628.html){:new_window} を参照してください。|
| NSX パスワードの変更 | 詳しくは、[ファイアウォールに関する考慮事項](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_networkingonvcenterserver#vc_networkingonvcenterserver-firewall-considerations)を参照してください。|
| Juniper vSRX アプライアンスのデプロイ | [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービス](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)では、ご使用の環境に FortiGate Virtual Appliances のペアがデプロイされます。これによって、仮想インフラストラクチャー内に重要なセキュリティー管理を実装してリスクを軽減できます。ただし、このサービスが要件に合わない場合には、必要に応じて独自のサード・パーティー・ソリューションを実装し、vCenter Server インスタンスに vSRX ゲートウェイを追加することができます。詳しくは、[Installing vSRX with VMware vSphere Web Client](https://www.juniper.net/documentation/en_US/vsrx/topics/task/installation/security-vsrx-vsphere-client-installing.html){:new_window} を参照してください。|
| Palo Alto VM-Series ファイアウォールのデプロイ | [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービス](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)では、ご使用の環境に FortiGate Virtual Appliances のペアがデプロイされます。これによって、仮想インフラストラクチャー内に重要なセキュリティー管理を実装してリスクを軽減できます。ただし、このサービスが要件に合わない場合には、必要に応じて独自のサード・パーティー・ソリューションを実装できます。Palo Alto VM-Series ファイアウォールを vCenter Server インスタンスに追加する方法については、[Set Up a VM-Series Firewall on an ESXi Server](https://docs.paloaltonetworks.com/vm-series/8-0/vm-series-deployment/set-up-a-vm-series-firewall-on-an-esxi-server.html#){:new_window} を参照してください。|
| Cisco Firepower アプライアンスのデプロイ | [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービス](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)では、ご使用の環境に FortiGate Virtual Appliances のペアがデプロイされます。これによって、仮想インフラストラクチャー内に重要なセキュリティー管理を実装してリスクを軽減できます。ただし、このサービスが要件に合わない場合には、必要に応じて独自のサード・パーティー・ソリューションを実装できます。vCenter Server インスタンスに Cisco Firepower アプライアンスを追加する方法については、[Deploy the Firepower Threat Defense Virtual Using the VMware vSphere Web Client or vSphere Hypervisor](https://www.cisco.com/c/en/us/td/docs/security/firepower/quick_start/vmware/ftdv/ftdv-vmware-qsg.html#17970){:new_window} を参照してください。|
| Direct Link | vCenter Server インスタンスのデプロイメント後に、システム管理者は {{site.data.keyword.cloud_notm}} 管理 VPN を介してユーザーのインスタンスに接続できます。その後、システム管理者は、ワークロードのインターネット・アクセスを構成できます。ただし、インターネットではなく直接接続を使用することもできます。{{site.data.keyword.cloud_notm}} Direct Link は、{{site.data.keyword.cloud_notm}} Network の 4 つのオファリングから成るスイートで、世界中のあらゆる場所で使用可能です。各オファリングは、公衆インターネットを使用せずに、お客様のリモートのネットワーク環境と {{site.data.keyword.cloud_notm}} デプロイメントをつなぐ直接のプライベート接続を作成することを可能にします。通常、これらのオファリングを実装する目的は、ハイブリッド・ワークロード、プロバイダー間ネットワーク、大量または頻繁なデータ転送、プライベート・ワークロードをサポートするため、あるいは、{{site.data.keyword.cloud_notm}} 環境の管理を簡単にするためです。詳しくは、[IBM Cloud Direct Link の概要](/docs/infrastructure/direct-link?topic=direct-link-get-started-with-ibm-cloud-direct-link#get-started-with-ibm-cloud-direct-link){:new_window}を参照してください。プライベート・ネットワークでのみアクセス可能な vCenter Server インスタンスについては、[パブリックまたはプライベート・ネットワーク](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-public-private-network){:new_window}を参照してください。|
| Web プロキシーのデプロイ |	VMware サーバー・インスタンスがデプロイされたときに、vCenter Server Appliance (VCSA) に、vSAN 健全性チェックの更新を可能にする VMware リポジトリーへの直接接続はありません。Squid Web プロキシー VM をデプロイして、これらのリポジトリーにアクセスできるようにする方法については、[初期構成](/docs/services/vmwaresolutions/archiref/vum/vum-init-config.html#install-and-configure-squid){:new_window}を参照してください。この手順は、他者ベンダーの他のプロキシー・アプリケーションにも該当します。|
| ファイアウォール・ロギング | NSX エッジと分散ファイアウォールは、監査ログ、ルール・メッセージ・ログ、システム・イベント・ログなどのログ・ファイルを生成して保管します。ファイアウォールを有効にしたクラスターごとに syslog サーバーを構成する必要があります。詳しくは、[Firewall Logs](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-6F9DC53E-222D-464B-8613-AB2D517CE5E3.html){:new_window} を参照してください。{{site.data.keyword.cloud_notm}} の運用管理には、syslog サーバーとして機能する vRealize Log Insights が含まれています。|
| NSX ロギングおよびシステム・イベント | syslog サーバーに NSX コンポーネントを構成する方法、システム・イベント、アラーム、監査ログの情報、および、テクニカル・サポート・ログの収集方法については、[NSX Logging and System Events](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.logging.doc/GUID-3F08DC2E-2D82-4C89-8829-EF1EA0160B13.html){:new_window} を参照してください。|
| オンプレミスでの HCX のデプロイ | 詳しくは、[オンプレミスの VMware HCX on IBM Cloud インスタンスに関する考慮事項](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_considerations#standalone_considerations){:new_window}を参照してください。|
| HCX チェック | HCX on {{site.data.keyword.cloud_notm}} サービスは、オンプレミス・データ・センターのネットワークを {{site.data.keyword.cloud_notm}} にシームレスに拡張できます。これにより、変換や変更を行わずに VM を {{site.data.keyword.cloud_notm}} との間で移行できるようになります。HCX Cloud Management コンソールにアクセスする方法、および HCX on {{site.data.keyword.cloud_notm}} に更新を適用する方法については、[VMware HCX on IBM Cloud の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx#managing-vmware-hcx-on-ibm-cloud)を参照してください。|


## 関連リンク
{: #opsprocs-configure-links}

* [VMware vSphere Documentation](https://docs.vmware.com/en/VMware-vSphere/index.html){:new_window}
* [NSX Installation Guide](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-DD31D6BC-2E56-4E91-B45F-FCA3E80FF786.html){:new_window}
* [NSX Administration Guide ](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-B5C70003-8194-4EC3-AB36-54C848508818.html){:new_window}
* [VMware vSAN Administration Guide](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-AEF15062-1ED9-4E2B-BA12-A5CE0932B976.html){:new_window}
* [vCenter Server 成果物の変更に関する考慮事項](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
