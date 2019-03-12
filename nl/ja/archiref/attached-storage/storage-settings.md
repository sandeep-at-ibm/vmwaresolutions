---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 接続ストレージの構成と設定
{: #storage-settings}

この設計は、NFS v3 による共有ストレージの接続のみをサポートしています。 NFS v4 および v4.1 はサポートされていません。

この設計の接続ストレージは、vCenter Server ソリューションと同じ {{site.data.keyword.CloudDataCent_notm}}で提供されている {{site.data.keyword.cloud_notm}} ストレージに制限されます。 また、データ・ストアに格納されるすべての仮想ディスクは、デフォルトでシン・プロビジョニングされます。
{:note}

このアーキテクチャーでは、共有に接続できるように、{{site.data.keyword.cloud_notm}} ストレージの DNS 名を使用して NFS v3 データ・ストアが接続されるように指定しています。 NFS 共有は、vCenter Server クラスター内のすべてのホストに接続され、Storage DRS が有効にされたデータ・ストア・クラスターに組み込まれます。

## vSphere Storage Distributed Resource Scheduler (Storage DRS)
{: #storage-settings-vsphere-storage-drs}

Storage DRS を使用して、データ・ストア・クラスターの集約リソースを管理できます。 Storage DRS が有効な場合、データ・ストア・クラスター内のデータ・ストア間でスペースと入出力リソースのバランスを取るために、仮想マシン (VM) のディスクの配置と移行に関する推奨情報が生成されます。

Storage DRS がオンの場合は、以下の機能を使用できます。
* データ・ストア・クラスター内のデータ・ストア間でのスペースのロード・バランシング
* データ・ストア・クラスター内のデータ・ストア間での入出力のロード・バランシング
* スペースと入出力ワークロードに基づく、仮想ディスクの最初の配置。

この設計では、Storage DRS が有効で、自動化レベルは**「完全自動化」**に設定されています。 その結果、データ・クラスター上のリソース使用率を最適化するために、ファイルが自動的に移行されます。 クラスターは完全に自動化されるため、その他の Storage DRS オプションはすべて**「クラスタ設定の使用」**に設定されます。

## NFS v3 を使用する場合の Storage DRS のランタイム設定
{: #storage-settings-drs-nfs3}

Storage DRS の積極性は、領域使用率と入出力待ち時間のしきい値を指定することで決まります。 Storage DRS は、データ・ストア・クラスター内のデータ・ストアに関するリソース使用率の情報を収集します。 vCenter Server は、この情報を使用して、データ・ストア上の仮想ディスクの配置に関する推奨情報を生成します。

データ・ストア・クラスターに対して低い積極性レベルを設定すると、Storage DRS は、必要な場合にのみ Storage vMotion の移行を推奨します。 例えば、入出力負荷や領域使用率が高くなったり、バランスが大きく偏ったりした場合に、Storage DRS は移行を推奨します。 データ・ストア・クラスターに対して高い積極性レベルを設定すると、Storage DRS は、領域や入出力のロード・バランシングがデータ・ストア・クラスターにとって有効である場合には常に移行を推奨します。

データ・ストア・クラスターには、次のしきい値カテゴリーがあります。

* 使用領域: データ・ストア上の領域使用率が、vSphere Web Client で設定したしきい値を超えると、Storage DRS は、推奨を生成するか移行を実行します。
* I/O 待ち時間: 1 日の間に測定されたデータ・ストアの 90 パーセンタイルの入出力待ち時間がしきい値を超えると、 Storage DRS は、推奨を生成するか移行を実行します。

この設計では、「ストレージ DRS ランタイム設定」が有効で、しきい値はデフォルト値のままになっています。 ワークロード入出力の要件や待ち時間の重要度に基づいて、これらの値を変更してください。

次の表に、VMware vSphere Web Client の設定を示しています。

表 1. Storage DRS のランタイム設定

| 設定       | 値  |
|:--------------- |:------ |
| SDRS 推奨に対する I/O メトリックの有効化 | 選択済み |
| 使用領域 | 選択済み、80% に設定 |
| I/O 待ち時間のしきい値 | 15 ms |

vSphere Web Client 内のこれらの設定の詳細と構成方法については、[Set Storage DRS Runtime Rules in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html) を参照してください。

## NFS v3 を使用する場合の Storage I/O Control
{: #storage-settings-io-control-nfs-v3}

SIOC (Storage I/O Control) を有効にした環境では、単一 VM のデバイス・キューの長さが変更されます。 このデバイス・キューの長さの変更により、すべての VM のストレージ・アレイ・キューが、同じシェアに縮小され、ストレージ・キューがスロットルされます。 SIOC は、リソースが制約されていて、定義したしきい値をストレージ入出力の待ち時間が超える場合にのみ有効です。

ストレージ・デバイスが輻輳または制約されていることを SIOC が検知できるようにするために、定義されたしきい値が必要です。 輻輳しきい値待ち時間は、ストレージ・タイプによって異なります。 この設計では、10 ミリ秒のしきい値の待ち時間を推奨し、実装しています。

SIOC を使用して、個々の VM の個々の仮想ディスクを制限したり、異なるシェアを付与したりすることができます。 ディスクを制限し、異なるシェアを付与することで、取得したファイル・ストレージ・ボリュームのIOPS 数のワークロードに環境を合わせることができます。 この制限は IOPS の単位で設定します。異なるウェイトまたはシェアを設定できます。

シェアを**「高」**(2,000 シェア) に設定した仮想ディスクは、**「標準」**(シェア 1,000) に設定したディスクの 2 倍、**「低」**(シェア 500) に設定したディスクの 4 倍の入出力を受け取ります。 **「標準」**がすべての VM のデフォルト値であるため、入出力を必要とする VM に合わせて**「標準」**の設定を調整する必要があります。

## NFS v3 を使用する場合の追加ストレージ
{: #storage-settings-additional-storage-nfs-v3}

スペースの不足や待ち時間が長いためにストレージを環境に追加する必要が生じた場合は、コンソールから別の NFS 共有を注文できます。 共有の注文後に、エクスポートをクラスター内の vSphere ESXi ホストに接続し、ストレージ・クラスター内に配置します。 新しい NFS 共有はストレージ・クラスター内に配置されるので、環境に関連付けられているストレージを効率的かつシームレスに拡張できます。自分でストレージ・レベルの移行を行う必要はありません。

## 拡張構成パラメーター
{: #storage-settings-adv-config-param}

この設計では、{{site.data.keyword.cloud_notm}} 推奨の拡張構成パラメーターが追加されます。 その結果、{{site.data.keyword.cloud_notm}} NFS 共有に接続されるすべての vSphere ESXi ホストに以下のパラメーターが設定されます。

表 2. NFS 拡張構成パラメーター

| パラメーター       | 値  |
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MaxQueueDepth | 64 |

## 関連リンク
{: #storage-settings-related}

* [ソリューションの概要](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
