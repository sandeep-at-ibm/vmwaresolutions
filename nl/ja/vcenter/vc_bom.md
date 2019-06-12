---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server の部品構成表
{: #vc_bom}

ここには、VMware vCenter Server インスタンスの部品構成表 (BOM) 情報を記載します。

## vCenter Server インスタンスの VLAN の BOM
{: #vc_bom-vlans}

次の表に、vCenter Server の VLAN の BOM 情報の詳細を示します。

表 1. vCenter Server インスタンス内の VLAN の BOM

| VLAN       | タイプ       | 詳細       |
|:---------- |:---------- |:------------- |
| VLAN1     | パブリック、プライマリー | パブリック・ネットワーク・アクセス用に物理 ESXi サーバーに割り当てられます。 初期デプロイメントの後は使用されません。 インターネット・アクセスに使用できます。 |
| VLAN2     | プライベート A、プライマリー | {{site.data.keyword.cloud}} によって物理 ESXi サーバーに割り当てられます。 管理インターフェースで VMware vSphere 管理トラフィック用に使用されます。<br><br>管理コンポーネントとして機能する VM (仮想マシン) に割り当てられます。<br><br>VMware NSX VTEP (VXLAN トンネル・エンドポイント) に割り当てられます。 |
| VLAN3     | プライベート B、ポータブル | 使用する場合は、VMware vSAN に割り当てられます。<br><br>使用する場合は、VMware NFS に割り当てられます。<br><br>VMware vSphere vMotion に割り当てられます。<br><br>NSX-T の場合は、VMware NSX VTEP (VXLAN トンネル・エンドポイント) に割り当てられます。|

## vCenter Server インスタンスのソフトウェアの BOM
{: #vc_bom-software}

次の表に、vCenter Server のソフトウェア・コンポーネントの BOM 情報の詳細を示します。

表 2. vCenter Server インスタンス内のソフトウェア・コンポーネントの BOM

| 製造元  | コンポーネント                      | バージョン    |
|:------------- |:------------------------------ |:------------- |
| VMware       | vSphere ESXi                    | 6.7 Update 1 (ビルド 6.7.0-13004448) または <br/>6.5 Update 2 (ビルド 6.5.0-13004031) |
| VMware       | vSphere 6.7                     | Distributed vSwitch 6.6.0 |
| VMware       | vSphere 6.5                     | Distributed vSwitch 6.5.0 |
| VMware       | vCenter Server Appliance        | 6.7 Update 1b (ビルド 6.7.0-11727113) または <br/>6.5 Update 2d (ビルド 6.5.0-10964411) |
| VMware       | Platform Services Controller    | 6.7 Update 1b (ビルド 6.7.0-11727113) または <br/>6.5 Update 2d (ビルド 6.5.0-10964411) |
| VMware       | vSAN                            | 6.7 Update 1 または <br/>6.6.1       |
| VMware       | NSX for vSphere                 | 6.4.4 (ビルド 11197766)    |
| VMware       | NSX-T for vSphere               | 2.4                       |
| Microsoft    | Windows Server Standard Edition | 2016       |

VMware vSAN はオプションのコンポーネントです。
{:note}

## ESXi サーバーの拡張構成の設定
{: #vc_bom-esxi-server-advance-config}

次の表で、ESXi サーバーに適用される拡張構成設定の概要を確認してください。 これらの設定は、vCenter Server インスタンスが V2.2 以降にデプロイされているか、または V2.1 以前から V2.2 以降にアップグレードされたかによって異なります。

これらの設定は、V2.2 以降の新しいインスタンスと新しいインスタンス内の新しいクラスターに適用されます。 これらの設定は、V2.1 以前の既存インスタンス内または V2.2 以降にアップグレードされた既存インスタンス内の新しいクラスターには適用されません。

表 3. vCenter Server インスタンスおよびクラスター用の ESXi サーバー拡張構成設定

| 構成設定 | V2.2 以降に新しくデプロイする場合  | V2.1 以前からアップグレードする場合 |
|:------------- |:------------- |:------------- |
| ボリュームの最大値 | **MaxVolumes** = 256 | **/NFS/MaxVolumes** = 256、**/NFS41/MaxVolumes** = 256 |
| ハートビートの最大失敗回数 | **HeartbeatMaxFailures** = 10 | 未設定 |
| ハートビートの頻度 | **HeartbeatFrequency** = 12 | 未設定 |
| ハートビートのタイムアウト | **HeartbeatTimeout** = 5 | 未設定 |
| キューの最大長 | **MaxQueueDepth** = 64 | 未設定 |
| キュー・フルのサンプル・サイズ | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| キュー・フルのしきい値 | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |
| TCP/IP ヒープ・サイズ | **TcpipHeapSize** = 32 | 未設定 |
| TCP/IP ヒープの最大値 | **TcpipHeapMax** = 1536 | 未設定 |

**注:**
* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスには **MaxVolumes** 設定が必要です。このサービスは、ESXi サーバーのデフォルトの NFS マウント数を超える NFS マウントを使用する可能性があるからです。
* **「未設定」**という構成設定の値は、ESXi サーバーを再起動しないと新しい設定が自動では適用されないことを示していますが、混乱を招く可能性があります。

  ストレージ拡張が適切にサポートされるように、**未設定**の構成設定を新しい値に変更してすべてのインスタンスで統一することをお勧めします。 IBM は、{{site.data.keyword.vmwaresolutions_short}} V2.2 以降のすべてのリリースで、これらの新しい設定だけを使用してテストする予定です。

  詳しくは、[Increasing the default value that defines the maximum number of NFS mounts on an ESXi host](https://kb.vmware.com/s/article/2239) を参照してください。

## NSX とポート・グループの構成設定
{: #vc_bom-nsx-port-group-config}

次の表で、vCenter Server インスタンス用の VMware NSX とポート・グループの構成設定の概要、リリース間の相違点を確認してください。

これらの設定は、V2.2 以降の新しいインスタンスと新しいインスタンス内の新しいクラスターに適用されます。 これらの設定は、V2.1 以前の既存インスタンス内または V2.2 以降にアップグレードされた既存インスタンス内の新しいクラスターには適用されません。

表 4. vCenter Server インスタンス用の NSX とポート・グループの構成設定

| 構成設定 | V2.1 以前  | V2.2 以降 |   
|:------------- |:------------- |:------------- |
| NSX VXLAN クラスターのチーミング・ポリシー | フェイルオーバー | ロード・バランシング - SRCID |
| NSX VXLAN クラスターの VTEP | 1 | 2 |
| プライマリー・インスタンスのセグメント ID プール | 6000-8000 | 6000-7999 |  
| 後続のセカンダリー・インスタンスのセグメント ID プール | 6000-8000 | マルチサイト構成の前の終了範囲 + 1 からマルチサイト構成の前の終了範囲 + 2000 |  
| ポート・グループ SDDC-DPortGroup-VSAN (該当する場合) | **「アクティブ・アップリンク」**を **uplink1**、**「スタンバイ・アップリンク」**を **uplink2** に設定 | **「アクティブ・アップリンク」**を **uplink2**、**「スタンバイ・アップリンク」**を **uplink1** に設定 |  
| ポート・グループ SDDC-DPortGroup-Mgmt | **「ポート・バインディング」**を**「一時的 - バインディングなし」**、**「ロード・バランシング」**を**「発信仮想ポートに基づいてルーティング」**に設定 | **「ポート・バインディング」**を**「静的バインディング」**、**「ロード・バランシング」**を**「物理 NIC の負荷に基づいてルーティング」**に設定 |  
| ポート・グループ SDDC-DPortGroup-External | **「ポート・バインディング」**を **「一時的 - バインディングなし」**に設定 | **「ポート・バインディング」**を**「静的バインディング」** に設定 |

## ネットワーク MTU の構成設定
{: #vc_bom-network-mtu-config}

vSphere クラスターは 2 つの vSphere 分散スイッチ (vDS) を使用します。1 つはパブリック・ネットワーク接続用で、もう 1 つはプライベート・ネットワーク接続用です。

プライベート・ネットワーク接続は、サイズが 9000 のジャンボ・フレーム MTU (最大伝送単位) を使用するように構成されるので、ストレージや VMware vMotion などの大量のデータ転送のパフォーマンスが向上します。 この値は、VMware 内で、および {{site.data.keyword.cloud_notm}} によって許可される最大の MTU です。

V2.1 以降では、パブリック・ネットワーク接続には標準的なイーサネット MTU の 1500 が使用されます。 この 1500 の設定は維持する必要があります。変更すると、インターネット上でパケットのフラグメント化が発生する可能性があります。

次の表で、パブリックとプライベートの分散仮想スイッチ (DVS) に適用されるネットワーク MTU 構成設定の概要を説明します。これらの構成設定は、V2.1 以降で vCenter Server インスタンスがデプロイされたかどうかによって異なります。

表 5. vCenter Server インスタンスとクラスターの MTU 構成設定 (インスタンスのバージョンによって異なる)

| vDS | V2.1 以降  | V2.0 以前 (または V2.0 以前からアップグレードされたもの) |
|:-------------- |:-------------- |:------------- |
| パブリック・スイッチ  | 1500 (デフォルト) | 9000 (ジャンボ・フレーム) |
| プライベート・スイッチ | 9000 (ジャンボ・フレーム) | 9000 (ジャンボ・フレーム) |

これらの設定は、V2.1 以降でデプロイされた新しいインスタンスおよびインスタンスの新しいクラスターに適用されます。 これらの設定は、V2.1 以降にアップグレードされたインスタンスの {{site.data.keyword.CloudDataCents_notm}}をまたぐ新しいクラスターにも適用されます。

V2.0 以前の既存インスタンスまたは V2.1 以降にアップグレードされた既存インスタンスの場合、同じ {{site.data.keyword.CloudDataCent_notm}}内の新しいクラスターにはこれらの設定は適用されません。

V2.0 以前でデプロイされたインスタンスの場合は、パブリック・スイッチ MTU 設定を 1500 に更新することをお勧めします。

### パブリック・スイッチ MTU 設定の更新
{: #vc_bom-procedure-update-public-switch-mtu-setting}

パブリック・スイッチの MTU 設定を更新するには、VMware vSphere Web Client で以下の手順を実行します。
1. vDS を右クリックし、**「設定の編集」**をクリックします。
2. **「プロパティー」**タブで、**「詳細」**オプションを選択します。
3. **「最大 MTU」**値を 1500 に設定します。

   vDS の MTU サイズを変更すると、接続アップリンク (物理 NIC) が停止した後で再開されます。 結果として、アップリンクを使用している VM に短時間の停止が発生します。 そのため、スケジュールされたダウン時間中に MTU 設定更新を計画することをお勧めします。
   {:note}

## 関連リンク
{: #vc_bom-related}

* [Build numbers and versions of VMware ESXi and ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Enabling Jumbo Frames on virtual distributed switches](https://kb.vmware.com/s/article/1038827)
* [{{site.data.keyword.vmwaresolutions_short}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040){:new_window}
* [vCenter Server の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [vCenter Server インスタンスの計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
