---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Cloud Foundation 資料清單

檢閱 VMware Cloud Foundation 實例的「資料清單 (BOM)」資訊。

## Cloud Foundation 實例的 VLAN BOM

下表詳述 Cloud Foundation VLAN 的 BOM 資訊。

表 1. Cloud Foundation 實例中 VLAN 的 BOM

|VLAN      |類型      |詳細資料     |
|:----------|:----------|:-------------|
|VLAN1     |公用、主要|指派給實體 ESXi 伺服器，以進行公用網路存取。在起始部署之後不會使用。可用於網際網路存取。|
|VLAN2     |專用 A、主要|由 {{site.data.keyword.cloud}} 指派給實體 ESXi 伺服器。由管理介面用於 VMware vSphere 管理資料流量。<br><br>指派給充當管理元件的 VM（虛擬機器）。<br><br>指派給 VMware NSX VTEP（VXLAN 通道端點）。|
|VLAN3     |專用 B、可攜式|指派給 VMware vSAN（如果使用的話）。<br><br>指派給 VMware NFS（如果使用的話）。<br><br>指派給 VMware vSphere vMotion。|

## Cloud Foundation 實例的軟體 BOM

下表詳述 Cloud Foundation 軟體元件的 BOM 資訊。

表 2. Cloud Foundation 實例中軟體元件的 BOM

|製造商       |元件                                     |版本         |
|:-------------|:-----------------------------------------|:-------------|
|VMware       |vSphere ESXi                             |6.5 Update EP11（建置 6.5.0-10719125）|
|VMware       |vCenter Server Appliance                 |6.5 U2c（建置 6.5.0-9451637）|
|VMware       |Platform Services Controller             |6.5 U2c（建置 6.5.0-9451637）|
|VMware       |vSAN                                     |6.6.1        |
|VMware       |NSX for vSphere                          |6.4.1        |
|VMware       |SDDC Manager                             |2.4          |
|Microsoft    |Windows Server 標準版（64 位元）         |2012R2       |

## ESXi 伺服器的進階配置設定

請檢閱下表，以取得套用至 ESXi 伺服器之進階配置設定的概觀。這些設定根據 Cloud Foundation 實例是部署在（或升級至）2.2 版或更新版本中，還是從舊版（2.1 版或更早版本）升級至 2.2 版或更新版本中，而有所不同。

表 3. Cloud Foundation 實例及叢集的 ESXi 伺服器進階配置設定

|配置設定              |如果新部署在 2.2 版或更新版本       |如果從 2.1 版或更早版本升級      |   
|:------------- |:------------- |:------------- |
|TCP/IP 資料堆大小 |**TcpipHeapSize** = 32 |未設定  |
|TCP/IP 資料堆上限 |**TcpipHeapMax** = 1536 |未設定  |  
|磁區數目上限|**MaxVolumes** = 256 |**/NFS/MaxVolumes** 且 **/NFS41/MaxVolumes** = 256 |  
|活動訊號失敗次數上限|**HeartbeatMaxFailures** = 10 |未設定  |  
|活動訊號頻率      |**HeartbeatFrequency** = 12 |未設定  |  
|活動訊號逾時      |**HeartbeatTimeout** = 5 |未設定  |
|佇列深度上限      |**MaxQueueDepth** = 64 |未設定  |
|佇列已滿樣本大小|**QFullSampleSize** = 32 |**/Disk/QFullSampleSize** = 32 |
|佇列已滿臨界值    |**QFullThreshold** = 8 |**/Disk/QFullThreshold** = 8 |

###  附註 

* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服務需要 **MaxVolumes** 設定，因為服務可能會在 ESXi 伺服器上使用超過預設的 NFS 裝載數目。
* 配置設定的**未設定**值指出未自動套用新設定，因為它需要重新啟動 ESXi 伺服器，這可能會造成干擾。

  建議您將**未設定**配置設定變更為新值，以維持所有實例的一致性，並容許提供儲存空間擴充的足夠支援。IBM 只打算對所有 {{site.data.keyword.vmwaresolutions_short}} 2.2 版以及更新版本測試這些新設定。

  如需相關資訊，請參閱 [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239)。

### 相關鏈結

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=C87A0EC07E7311E6BA51E79BE9476040)
* [Cloud Foundation 概觀](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)
* [規劃 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc/sd_planning.html)
