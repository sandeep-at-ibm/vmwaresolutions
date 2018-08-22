---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# vCenter Server の部品構成表

ここには、VMware vCenter Server インスタンスの部品構成表 (BOM) 情報を記載します。

## vCenter Server インスタンスの VLAN の BOM

次の表に、vCenter Server の VLAN の BOM 情報の詳細を示します。

表 1. vCenter Server インスタンス内の VLAN の BOM

| VLAN       | タイプ       | 詳細       |
|:---------- |:---------- |:------------- |
| VLAN1     | パブリック、プライマリー | パブリック・ネットワーク・アクセス用に物理 ESXi サーバーに割り当てられます。 初期デプロイメントの後は使用されません。 インターネット・アクセスに使用できます。 |
| VLAN2     | プライベート A、プライマリー | {{site.data.keyword.cloud}} によって物理 ESXi サーバーに割り当てられます。 管理インターフェースで VMware vSphere 管理トラフィック用に使用されます。<br><br>管理コンポーネントとして機能する VM (仮想マシン) に割り当てられます。<br><br>VMware NSX VTEP (VXLAN トンネル・エンドポイント) に割り当てられます。 |
| VLAN3     | プライベート B、ポータブル | 使用する場合は、VMware vSAN に割り当てられます。<br><br>使用する場合は、VMware NFS に割り当てられます。<br><br>VMware vSphere vMotion に割り当てられます。 |

## vCenter Server インスタンスのソフトウェアの BOM

次の表に、vCenter Server のソフトウェア・コンポーネントの BOM 情報の詳細を示します。

表 2. vCenter Server インスタンス内のソフトウェア・コンポーネントの BOM

| 製造元  | コンポーネント                      | バージョン       |
|:------------- |:------------------------------ |:------------- |
| VMware       | vSphere ESXi                    | 6.5 U1g (パッチ・レベル ESXi650-201803001 を適用済みの ESXi 6.5u1) |
| VMware       | vCenter Server Appliance        | 6.5 Update 1g |
| VMware       | Platform Services Controller    | 6.5 Update 1g |
| VMware       | vSAN                            | 6.6.1        |
| VMware       | NSX for vSphere                 | 6.4.1        |
| IBM          | CloudDriver                     | 2.4          |
| Microsoft    | Windows Server Standard Edition | 2012R2       |

**注**: VMware vSAN はオプションのコンポーネントです。

## ESXi サーバーの拡張構成の設定

次の表で、ESXi サーバーに適用される拡張構成設定の概要を確認してください。拡張構成設定は、vCenter Server インスタンスが、V2.2 以降でデプロイされたか、V2.1 以前のリリースから V2.2 以降にアップグレードされたかによって異なります。

これらの設定は、V2.2 以降の新しいインスタンスと新しいインスタンス内の新しいクラスターに適用されます。 V2.1 以前の既存インスタンス内または V2.2 以降にアップグレードされた既存インスタンス内の新しいクラスターには適用されません。

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

**注**:
* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスには **MaxVolumes** 設定が必要です。このサービスは、ESXi サーバーのデフォルトの NFS マウント数を超える NFS マウントを使用する可能性があるからです。
* **「未設定」**という構成設定の値は、ESXi サーバーを再起動しないと新しい設定が自動では適用されないことを示していますが、混乱を招く可能性があります。

  ストレージ拡張が適切にサポートされるように、**未設定**の構成設定を新しい値に変更してすべてのインスタンスで統一することをお勧めします。 IBM は、{{site.data.keyword.vmwaresolutions_short}} V2.2 以降のすべてのリリースで、これらの新しい設定だけを使用してテストする予定です。

  詳しくは、[Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239) を参照してください。

## NSX とポート・グループの構成設定

次の表で、vCenter Server インスタンス用の VMware NSX とポート・グループの構成設定の概要、リリース間の相違点を確認してください。

これらの設定は、V2.2 以降の新しいインスタンスと新しいインスタンス内の新しいクラスターに適用されます。 V2.1 以前の既存インスタンス内または V2.2 以降にアップグレードされた既存インスタンス内の新しいクラスターには適用されません。

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

vSphere クラスターは 2 つの vSphere 仮想分散スイッチ (VDS) を使用します。1 つはパブリック・ネットワーク接続用で、もう 1 つはプライベート・ネットワーク接続用です。

プライベート・ネットワーク接続は、サイズが 9000 のジャンボ・フレーム MTU (最大伝送単位) を使用するように構成されるので、ストレージや VMware vMotion などの大量のデータ転送のパフォーマンスが向上します。 この値は、VMware 内で、および {{site.data.keyword.cloud_notm}} によって許可される最大の MTU です。

V2.1 以降では、パブリック・ネットワーク接続には標準的なイーサネット MTU の 1500 が使用されます。 この 1500 の設定は維持する必要があります。変更すると、インターネット上でパケットのフラグメント化が発生する可能性があります。

次の表で、パブリックとプライベートの分散仮想スイッチ (DVS) に適用されるネットワーク MTU 構成設定の概要を説明します。これらの構成設定は、V2.1 以降で vCenter Server インスタンスがデプロイされたかどうかによって異なります。

表 5. vCenter Server インスタンスとクラスターの MTU 構成設定 (インスタンスのバージョンによって異なる)

| VDS | V2.1 以降  | V2.0 以前 (または V2.0 以前からアップグレードされたもの) |
|:-------------- |:-------------- |:------------- |
| パブリック・スイッチ  | 1500 (デフォルト) | 9000 (ジャンボ・フレーム) |
| プライベート・スイッチ | 9000 (ジャンボ・フレーム) | 9000 (ジャンボ・フレーム) |

これらの設定は、V2.1 以降でデプロイされた新しいインスタンスおよびインスタンスの新しいクラスターに適用されます。 これらの設定は、V2.1 以降にアップグレードされたインスタンスの {{site.data.keyword.CloudDataCents_notm}}をまたぐ新しいクラスターにも適用されます。

V2.0 以前の既存インスタンスまたは V2.1 以降にアップグレードされた既存インスタンスの場合、同じ {{site.data.keyword.CloudDataCent_notm}}内の新しいクラスターにはこれらの設定は適用されません。

V2.0 以前でデプロイされたインスタンスの場合は、パブリック・スイッチ MTU 設定を 1500 に更新することをお勧めします。

### パブリック・スイッチ MTU 設定の更新

パブリック・スイッチの MTU 設定を更新するには、VMware vSphere Web Client で以下の手順を実行します。
1. VDS を右クリックし、**「設定の編集」**をクリックします。
2. **「プロパティ」**タブで、**「詳細」**オプションを選択します。
3. **「最大 MTU」**値を 1500 に設定します。

   **注**: vDS の MTU サイズを変更すると、接続アップリンク (物理 NIC) が停止した後再開されます。 結果として、アップリンクを使用している VM に短時間の停止が発生します。 そのため、スケジュールされたダウン時間中に MTU 設定更新を計画することをお勧めします。

### 関連リンク

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Enabling Jumbo Frames on virtual distributed switches](https://kb.vmware.com/s/article/1038827)
* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040)
* [vCenter Server の概要](vc_vcenterserveroverview.html)
* [vCenter Server インスタンスの計画](vc_planning.html)
