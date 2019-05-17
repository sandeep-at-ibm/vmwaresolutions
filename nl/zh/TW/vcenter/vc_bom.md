---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 資料清單
{: #vc_bom}

檢閱 VMware vCenter Server 實例的資料清單 (BOM) 資訊。

## vCenter Server 實例的 VLAN BOM
{: #vc_bom-vlans}

下表詳述 vCenter Server VLAN 的 BOM 資訊。

表 1. vCenter Server 實例中的 VLAN BOM

|VLAN      |類型      |詳細資料     |
|:---------- |:---------- |:------------- |
|VLAN1     |公用、主要|指派給實體 ESXi 伺服器，以進行公用網路存取。在起始部署之後不會使用。可用於網際網路存取。|
|VLAN2     |專用 A、主要|由 {{site.data.keyword.cloud}} 指派給實體 ESXi 伺服器。由管理介面用於 VMware vSphere 管理資料流量。<br><br>指派給充當管理元件的 VM（虛擬機器）。<br><br>指派給 VMware NSX VTEP（VXLAN 通道端點）。|
|VLAN3     |專用 B、可攜式|指派給 VMware vSAN（如果使用的話）。<br><br>指派給 VMware NFS（如果使用的話）。<br><br>指派給 VMware vSphere vMotion。<br><br>若為 NSX-T，指派給 VMware NSX VTEP（VXLAN 通道端點）。|

## vCenter Server 實例的軟體 BOM
{: #vc_bom-software}

下表詳述 vCenter Server 軟體元件的 BOM 資訊。

表 2. vCenter Server 實例中的軟體元件的 BOM

|製造商       |元件                            |版本|
|:------------- |:------------------------------ |:------------- |
|VMware       |vSphere ESXi                    | 6.7 Update 1（建置 6.7.0-13004448）或 <br/>6.5 Update 2（建置 6.5.0-13004031）|
|VMware       | vSphere 6.7                     | Distributed vSwitch 6.6.0 |
|VMware       | vSphere 6.5                     | Distributed vSwitch 6.5.0 |
|VMware       |vCenter Server Appliance        | 6.7 Update 1b（建置 6.7.0-11727113）或 <br/>6.5 Update 2d（建置 6.5.0-10964411）|
|VMware       |Platform Services Controller    | 6.7 Update 1b（建置 6.7.0-11727113）或 <br/>6.5 Update 2d（建置 6.5.0-10964411）|
|VMware       |vSAN                            | 6.7 Update 1 或 <br/>6.6.1        |
|VMware       |NSX for vSphere                 | 6.4.4（建置 11197766）   |
|VMware       | NSX-T for vSphere               |2.4          |
|Microsoft    |Windows Server Standard Edition | 2016       |

VMware vSAN 是選用元件。
{:note}

## ESXi 伺服器的進階配置設定
{: #vc_bom-esxi-server-advance-config}

請檢閱下表，以取得套用至 ESXi 伺服器之進階配置設定的概觀。這些設定取決於 vCenter Server 實例是部署在 2.2 版或更新版本，還是從 2.1 版或更早版本升級至 2.2 版或更新版本。

這些設定會套用至新實例及新實例 2.2 版或更新版本中的新叢集。這些設定不適用於 2.1 版或更早版本現有實例中的新叢集，或升級至 2.2 版或更新版本之現有實例中的新叢集。

表 3. vCenter Server 實例及叢集的 ESXi 伺服器進階配置設定

|配置設定|如果新部署至 2.2 版或更新版本       |如果從 2.1 版或更早版本升級      |
|:------------- |:------------- |:------------- |
|磁區數目上限|**MaxVolumes** = 256 |**/NFS/MaxVolumes** 且 **/NFS41/MaxVolumes** = 256 |
|活動訊號失敗次數上限|**HeartbeatMaxFailures** = 10 |未設定 |
|活動訊號頻率|**HeartbeatFrequency** = 12 |未設定 |
|活動訊號逾時|**HeartbeatTimeout** = 5 |未設定 |
|佇列深度上限|**MaxQueueDepth** = 64 |未設定 |
|佇列已滿樣本大小|**QFullSampleSize** = 32 |**/Disk/QFullSampleSize** = 32 |
|佇列已滿臨界值|**QFullThreshold** = 8 |**/Disk/QFullThreshold** = 8 |
|TCP/IP 資料堆大小|**TcpipHeapSize** = 32 |未設定 |
|TCP/IP 資料堆上限|**TcpipHeapMax** = 1536 |未設定 |

**附註：**
* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服務需要 **MaxVolumes** 設定，因為服務可能會在 ESXi 伺服器上使用超過預設的 NFS 裝載數目。
* 配置設定的**未設定**值指出未自動套用新設定，因為它需要重新啟動 ESXi 伺服器，這可能會造成干擾。

  建議您將**未設定**配置設定變更為新值，以維持所有實例的一致性，並容許提供儲存空間擴充足夠的支援。IBM 只打算對所有 {{site.data.keyword.vmwaresolutions_short}} 2.2 版以及更新版本測試這些新設定。

  如需相關資訊，請參閱 [Increasing the default value that defines the maximum number of NFS mounts on an ESXi host](https://kb.vmware.com/s/article/2239)。

## NSX 和埠群組配置設定
{: #vc_bom-nsx-port-group-config}

請檢閱下表，以取得 vCenter Server 實例的 VMware NSX 及埠群組配置設定的概觀，以及版本之間的差異。

這些設定會套用至新實例及新實例 2.2 版或更新版本中的新叢集。這些設定不適用於 2.1 版或更早版本的現有實例中的新叢集，或升級至 2.2 版或更新版本的現有實例中的新叢集。

表 4. vCenter Server 實例的 NSX 及埠群組配置設定

|配置設定|2.1 版或更舊版本|2.2 版或更新版本|   
|:------------- |:------------- |:------------- |
|NSX VXLAN 叢集小組原則|失效接手|負載平衡 - SRCID |
|NSX VXLAN 叢集 VTEP |1 |2 |
|主要實例的區段 ID 儲存區|6000-8000 |6000-7999 |  
|後續次要實例的區段 ID 儲存區|6000-8000 |多站台配置中的前一個結束範圍 + 1，到多站台配置中的前一個結束範圍 + 2000|  
|埠群組 SDDC-DPortGroup-VSAN（如果適用）|**作用中的上行鏈路**設為 **uplink1**，**待命上行鏈路**設為 **uplink2** |**作用中的上行鏈路**設為 **uplink2**，**待命上行鏈路**設為 **uplink1** |  
|埠群組 SDDC-DPortGroup-Mgmt |**埠連結**設為**暫時 - 無連結**，**負載平衡**設為**根據來源虛擬埠遞送**|**埠連結**設為**靜態連結**，**負載平衡**設為**根據實體 NIC 負載遞送** |  
|埠群組 SDDC-DPortGroup-External |**埠連結**設為**暫時 - 無連結** |**埠連結**設為**靜態連結** |

## 網路 MTU 配置設定
{: #vc_bom-network-mtu-config}

vSphere 叢集使用兩個 vSphere Distributed Switch (vDS)：一個用於公用網路連線功能，另一個用於專用網路連線功能。

專用網路連線配置成使用大小為 9000 的「巨大訊框 MTU（最大傳輸單位）」，以改善大型資料傳送（例如儲存空間及 VMware vMotion）的效能。此值是 VMware 內及 {{site.data.keyword.cloud_notm}} 容許的最大 MTU。

在 2.1 版或更新版本中，公用網路連線使用標準乙太網路 MTU 1500。必須維護此設定 1500；任何變更都可能會導致透過網際網路進行封包片段化。

請檢閱下表，以取得「網路 MTU」配置設定的概觀，這些設定會根據 vCenter Server 實例是否部署在 2.1 版或更新版本上，而套用至公用及專用「分散式虛擬交換器 (DVS)」。

表 5. vCenter Server 實例及叢集的 MTU 配置設定（取決於實例版本）

| vDS |2.1 版或更新版本 |2.0 版或更早版本（或從 2.0 版或更早版本升級）|
|:-------------- |:-------------- |:------------- |
|公用交換器|1500（預設值）|9000（巨大訊框）|
|專用交換器|9000（巨大訊框）|9000（巨大訊框）|

這些設定適用於新實例以及部署在 2.1 版或更新版本中的實例的新叢集。這些設定也適用於跨 {{site.data.keyword.CloudDataCents_notm}} 中已升級至 2.1 版或更新版本的實例內的新叢集。

這些設定不適用於相同 {{site.data.keyword.CloudDataCent_notm}} 中的新叢集，而新叢集位於 2.0 版或更早版本中的現有實例，或升級至 2.1 版或更新版本的現有實例。

對於已部署在 2.0 版或更早版本中的實例，建議您將公用交換器 MTU 設定更新為 1500。

### 更新公用交換器 MTU 設定
{: #vc_bom-procedure-update-public-switch-mtu-setting}

若要更新公用交換器的 MTU 設定，請在 VMware vSphere Web Client 中完成下列步驟：
1. 在 vDS 上按一下滑鼠右鍵，然後按一下**編輯設定**。
2. 在**內容**標籤上，選取**進階**選項。
3. 確定**最大 MTU** 值已設為 1500。

   當 vDS 中的 MTU 大小變更時，會將連接的上行鏈路（實體 NIC）卸下再重新連接。因此，使用此上行鏈路的 VM 會短暫的中斷。所以，建議您在排定的關閉時間計劃 MTU 設定更新。
   {:note}

## 相關鏈結
{: #vc_bom-related}

* [Build numbers and versions of VMware ESXi and ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [VMware vCenter Server 的建置號碼和版本 (2143838)](https://kb.vmware.com/s/article/2143838)
* [在虛擬分散式交換器上啟用巨大訊框](https://kb.vmware.com/s/article/1038827)
* [{{site.data.keyword.vmwaresolutions_short}} 保護資料表](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040){:new_window}
* [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [規劃 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
