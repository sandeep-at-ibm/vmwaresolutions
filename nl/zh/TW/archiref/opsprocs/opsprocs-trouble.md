---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# 疑難排解
{: #opsprocs-trouble}

若要疑難排解 vCenter Server 實例問題，系統管理者必須識別問題的症狀、判斷哪些解決方案元件受到影響、研究並提出修正程式或暫行解決方法，以及測試修正程式。

* 識別症狀 - 有多個潛在原因可能會導致實例的效能不佳或無效能。有效疑難排解的第一個步驟是確切識別將發生錯誤的項目。這些症狀可能是從下列項目報告而來：vSphere 事件及警示、{{site.data.keyword.cloud}} 中的 Operations Management，或透過其中一位使用者的「服務台」進行報告。
* 隔離受影響的元件 - 識別問題的症狀之後，您必須識別受影響且可能造成問題的軟體或硬體元件，以及未涉及的元件。{{site.data.keyword.cloud_notm}} 中的 vCenter Operations Management 這類工具會協助您執行此步驟。
* 提出修正程式或暫行解決方法 - 瞭解症狀並隔離元件之後，就可以研究可能的修正程式及暫行解決方法。系統管理者也可以使用「{{site.data.keyword.cloud_notm}} 入口網站」，其中包括本文件中的疑難排解情境，以及 IBM ServiceNow 和 VMware 知識庫。此外，還有許多 Wiki 及部落格可協助您完成。為了更快速地解決，{{site.data.keyword.cloud_notm}} 中的 Operations Management 包括所找到問題的許多補救方式。
* 測試可能的解決方案 - 如果您知道問題的症狀涉及元件，並已提出修正程式/暫行解決方法，則系統管理者會系統性地測試解決方案，直到解決問題為止。

vSphere 包括使用者可配置的事件及警示子系統，它會追蹤在整個 vSphere 環境中發生的事件，並將資料儲存在日誌檔及 vCenter 資料庫中。此子系統也可讓系統管理者指定觸發警示的條件。系統條件變更時，警示會將狀態從警告變更為更嚴重的警示，而且可以觸發自動化警示動作，例如，將電子郵件寄送給系統管理者團隊。當您想要在特定庫存物件或物件群組的特定事件或條件發生時收到通知或採取立即動作時，此功能十分有用。

其他工具（例如納入 Operations Management on {{site.data.keyword.cloud_notm}} 架構的工具）可提供更高的協助：識別症狀、隔離受影響的元件，並提出修正程式/暫行解決方法。

## 準則
{: #opsprocs-trouble-guidelines}

下列準則是針對 {{site.data.keyword.vmwaresolutions_short}} 問題進行疑難排解時的最佳作法：
* 系統性地進行疑難排解和問題解決。
* 下列項目的相關症狀：可用性、使用率或配置：
 *  可用性 - 這些症狀與軟硬體元件可用性相關，並以「沒有回應」表示。高可用性設計經常會遮蔽這些問題，讓它們不會直接影響您的工作負載及使用者。
 * 使用率 - 這些症狀與容量及效能相關，並以「執行緩慢」或「無法載入」表示。主動管理容量會大幅降低這些問題。
 * 配置 - 通常是在佈建新服務或套用變更時探索到這些問題。不正確的設定可能會顯現為可用性或使用率症狀。例如，不正確的 IP 位址顯示為可用性問題，而虛擬機器 (VM) RAM 設定太低會導致使用率症狀。
* 嘗試將問題隔離到環境中的元件。
* 記下注意事項，以追蹤您的步驟。
* 瞭解及記載軟體版本。
* 記載子網路及 IP 位址使用情形，包括 VIP 及 NAT 位址。
* 具有網路的圖表。您需要許多圖表來顯示實體（基礎）及邏輯（重疊）層。
* 瞭解環境的任何最新變更。
* 研究修正程式的影響，請不要將您自己鎖定到任何管理介面。
* 確定您有所有重要元件的備份；以防需要重新載入或重設它們時。
* 一次不要變更多個事項。
* 記載每項變更及其結果。
* 提出支援要求時，請確定您已仔細記載並提供相關資訊。十分清楚您看到的症狀，並識別您相信的元件發生錯誤。確定您使用正確的術語。在您選擇的字組中，盡可能減少任何混淆或語義不明確。
* vSphere ESXi 及 vCenter Server 配置檔會控制系統的行為，並瞭解其位置。大部分配置檔設定都是在安裝期間設定，但在安裝之後可以進行修改。
* 日誌檔會擷取核心及不同子系統和服務所產生的訊息。vSphere ESXi 及 vCenter 服務會維護個別的日誌檔、瞭解其位置及其存取方式。
* 瞭解如何使用熱門系統管理工具，以協助進行診斷。

如需相關資訊，請參閱[疑難排解準則 KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}。

## 日誌檔疑難排解
{: #opsprocs-trouble-logs}

日誌檔是疑難排解問題的絕佳資訊來源，不過，實際上，日誌檔數目和每個日誌中的大量項目都會導致困難。[日誌檔疑難排解 KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window} 詳述這些日誌檔在 VMware 環境中的位置。由於日誌檔數目和每個日誌中的大量項目，您應該考量使用 Operations Management on {{site.data.keyword.cloud_notm}} 中的工具，以協助擷取及分析事件日誌。

## 一般情境疑難排解
{: #opsprocs-trouble-common}

為了協助隔離受影響的元件，已將這份有關一般情境疑難排解的文件分類如下：

* 虛擬機器 - 這些疑難排解主題提供有關 VM 潛在問題的指引。
* 主機 - 這些疑難排解主題提供有關 vSphere ESXi 主機問題的指引。
* 叢集 - 這些疑難排解主題提供有關可用性及資源管理的指引。
* 儲存空間 - 這些疑難排解主題提供有關解決 vSAN 及 NFS 儲存空間問題的指引。
* 網路 - 這些疑難排解主題提供有關解決網路問題的指引。
* vCenter - 這些疑難排解主題提供有關解決 vCenter 問題的指引。
* 授權 - 這些疑難排解主題提供有關解決授權問題的指引。這些通常與已將自己的授權帶到 {{site.data.keyword.cloud_notm}} 的用戶端相關。

### 虛擬機器
{: #opsprocs-trouble-common-vm}

表 1. 虛擬機器疑難排解

| 標題 |說明       |
|---|---|
| 一般 VM 疑難排解 | 如需相關資訊，請參閱[虛擬機器疑難排解](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window}。|
| VM 效能問題 | 如需 VM 效能問題症狀疑難排解的相關資訊，包括來賓 OS 開機速度較慢、應用程式執行效能不佳、應用程式的啟動時間較長或應用程式變得無回應，請參閱 [ESX/ESXi 虛擬機器效能問題疑難排解 (2001003)](https://kb.vmware.com/s/article/2001003){:new_window}。|
| 回復孤立的 VM | 如需回復孤立的 VM（即 vCenter 資料庫中的 VM，但 vSphere ESXi 主機無法辨識）的相關資訊，請參閱[知識 - KB0012862 0.01 版](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:new_window}。|
| 未開啟 VM 電源 | 如需相關資訊，請參閱[無法開啟電源的虛擬機器疑難排解 (2001005)](https://kb.vmware.com/s/article/2001005){:new_window}。|
| 從範本複製或部署之後，未開啟 VM 電源 | [VMware 文章](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:new_window}會查看從範本複製或部署 VM 之後對 VM 產生的問題。|
| VMware Tools 過期或未安裝 - VMware Tools 應該安裝在 VM 上，且保持最新。| [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:new_window} 提供這些作業的指引。|
| 舊 VM 網路裝置 | 如果 VM 網路裝置未保持最新的網路效能，因此，不會影響應用程式效能。如需部署新虛擬網路裝置及驅動程式的相關資訊，請參閱[選擇虛擬機器的網路配接卡 (1001805)](https://kb.vmware.com/s/article/1001805){:new_window}。|
| 虛擬機器記憶體限制 | 通常會使用記憶體限制，不過，如果來賓 OS 無法存取所需的記憶體，則來賓 OS 內的應用程式可能會執行效果較差。如需解決問題的相關資訊，請參閱[配置資源配置設定](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:new_window}。|
| VM Snapshot | 雖然 Snapshot 十分有用，但是 VM Snapshot 的數量和經歷時間會直接影響 VM 的效能。如需解決問題的相關資訊，請參閱[合併 Snapshot](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:new_window}。|
| VM 記載 | 如果尚未正確地配置記載，則資料儲存庫的容量會受到負面影響。如需解決問題的相關資訊，請參閱[配置來賓作業系統的記載層次](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:new_window}。|
| 網路連線問題疑難排解 | 症狀可能包括 VM 無法連接至網路，或沒有與單一 VM 之間的網路連線。如需解決問題的相關資訊，請參閱[虛擬機器網路連線問題疑難排解 (1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。|
| 判定多個虛擬 CPU 是否導致效能問題 | 如需在 VM 配置多個 CPU 時對遭遇效能問題的 VM 進行疑難排解的相關資訊，請參閱[判定多個虛擬 CPU 是否導致效能問題 (1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。如果將資料複製到 VM 或從中複製資料、備份工作逾時或速度非常慢，或者 VM 效能不佳，則這些問題可能包括不佳的傳送速度。|
| 已關閉 VM 的電源或將其重新啟動 | 如需解決問題的相關資訊，請參閱[判斷為何關閉 VM 的電源或將其重新啟動 (1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。|
| 一或多個 VM 回應時間不佳 | 如需在 vSphere ESXi 主機上隔離效能問題的相關資訊，請參閱 [ESX/ESXi 虛擬機器效能問題疑難排解 (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}。效能問題可能是 CPU 限制、記憶體過度確定、儲存空間延遲或網路延遲所造成。|

### vSphere ESXi 主機
{: #opsprocs-trouble-common-host}

表 2. 一般 vSphere ESXi 主機疑難排解

| 標題 |說明       |
|---|---|
| EXI 指令 | 如需 vSphere、ESXi Shell 指令及 VMware vSphere 指令行介面 (vCLI) 指令中指令行介面的概觀，請參閱[開始使用 vSphere 指令行介面](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:new_window}。|
| vSphere HA 主機狀態 | 如果 vCenter 報告在主機上指出錯誤狀況的 vSphere HA 主機狀態，則需要重新修補這些錯誤狀況，因為此問題可以防止 vSphere HA 在失敗之後重新啟動 VM。如需相關資訊，請參閱 [vSphere HA 主機狀態疑難排解](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window}。|
| vSphere ESXi 主機處於非回應狀態 | 如需疑難排解顯示為「未回應」或「已中斷連線」的 vSphere ESXi 主機的相關資訊，或疑難排解主機上的 VM 在 vCenter 中顯示為灰色的相關資訊，請參閱 [ESX/ESXi 主機未回應且變成灰色 (1019082)](https://kb.vmware.com/s/article/1019082){:new_window}。|
| 開啟 VM 的電源時，您會看到「找不到檔案」錯誤 | 如需重建遺失虛擬磁碟描述子檔案 (VMDK) 的相關資訊，請參閱[重建遺漏的虛擬機器磁碟描述子檔案 (1002511)](https://kb.vmware.com/s/article/1002511){:new_window}。|
| VM 效能問題 | 如需在 vSphere ESXi 主機上隔離效能問題的相關資訊，請參閱 [ESX/ESXi 虛擬機器效能問題疑難排解 (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}。效能問題可能是 CPU 限制、記憶體過度確定、儲存空間延遲或網路延遲所造成。|
| Bare Metal Server 已關閉 | 如果執行 vSphere ESXi 的 Bare Metal Server 未回應或已關閉，則請登入 {{site.data.keyword.cloud_notm}} 管理使用者介面或主控台，並檢查狀態。必要時，請開啟案例，以取得 Bare Metal Server 的協助。如需相關資訊，請參閱[使用支援案例](/docs/get-support?topic=get-support-open-case#open-case){:new_window}。|
| vSphere ESXi 主機處於已中斷連線或未回應狀態 | 如需相關資訊，請參閱[處於非回應狀態的 ESXi/ESX 主機疑難排解 (1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:new_window}。|
| 紫色死亡畫面 |「紫色死亡畫面 (PSOD)」是核心危急，而 vSphere ESXi 核心 (vmkernel) 會觸發此安全措施以回應無法復原的事件/錯誤，且表示繼續執行會造成服務及 VM 的高風險。如果發生危急，且 vSphere ESXi 主機當機，則會同時終止所有在其上執行的服務，並管理所有 VM。VM 不會循序關閉，而是突然地關閉電源。如果主機是叢集的一部分，且您已配置 HA，則會在叢集的其他主機上重新啟動這些 VM。如需相關資訊，請參閱[知識 - KB0012864 0.01 版](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:new_window}。|

### Storage
{: #opsprocs-trouble-common-storage}

表 3. 一般儲存空間疑難排解

| 標題 |說明       |
|---|---|
| 儲存空間疑難排解 | 如需效能緩慢、無法預期失敗、磁碟毀損或 VM 毀損的相關資訊，請參閱[使用 VMware 產品時的儲存空間問題疑難排解 (2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:new_window}。|
| vSAN 疑難排解 | 如需相關資訊，請參閱 [vSAN 中的失敗處理](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:new_window}。|
| vSAN 磁碟故障 | 如需識別故障磁碟及要求取代的相關資訊，請參閱[VMware vSAN 磁碟群組中的硬碟/磁碟故障 (2077185)](https://kb.vmware.com/s/article/2077185){:new_window}。|
| 清除 vSAN 性能問題 | 在 VMware vSphere Web Client「監視」頁面中，您可能會看到與「vSAN 性能」問題相關的警示及警告。如需清除這些問題的相關資訊，請參閱 [Virtual SAN 性能警示及警告](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_vsan_alerts#trbl_vsan_alerts){:new_window}。|
| vSAN 重新平衡 | 如果磁碟在性能檢查中報告錯誤以指出叢集不平衡，而且有些磁碟的空間用量很高，但有些磁碟的空間用量極低，則您應該執行主動重新平衡。這會手動起始重新平衡 vSAN 叢集中的物件。如需 vSAN 主動重新平衡及其適用時機的相關資訊，請參閱 [vSAN 主動重新平衡 (2149809)](https://kb.vmware.com/s/article/2149809){:new_window}。|
| 起始 vSAN 性能測試 | 如果您懷疑 vSAN 發生問題，則可以起始性能測試以驗證叢集元件是否如預期運作。執行 VM 建立測試會在叢集的每個主機上建立 VM，然後刪除 VM。如果這些作業順利完成，則叢集元件會如預期運作，且叢集可運作。然後，使用網路效能測試來偵測及診斷連線功能問題，以及確定主機之間的網路頻寬足夠。如需相關資訊，請參閱[主動測試](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:new_window}。|
| 監視 vSAN 效能 | 如需相關資訊，請參閱[監視 vSAN 效能](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:new_window}。效能圖表適用於叢集、主機、實體磁碟、VM 及虛擬磁碟。|
| vSAN 疑難排解 | 如需相關資訊，請參閱[處理失敗及疑難排解 vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:new_window}。|


### 網路
{: #opsprocs-trouble-common-network}

表 4. 一般網路疑難排解

| 標題 |說明       |
|---|---|
| 作用中 Edge 上的 NSX Edge /var/log 將滿 | 如需警告您 Edge 磁碟將填滿並發現 /var/log 分割區將滿時的暫行解決方法的相關資訊，請參閱[作用中 Edge 上的 NSX Edge /var/log 將滿 (50108355)](https://kb.vmware.com/s/article/50108355){:new_window}。|
| 測試 HCX 頻寬 | 如需在認為 HCX 發生網路頻寬問題時使用 'perftest' 尋找 HCX 通道內可用頻寬的相關資訊，請參閱[在 HCX 中執行 Perftest 的步驟 (56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:new_window}。針對每個 perftest 執行雙向測試。閘道配對的其中一個位在來源資料中心（稱為 OnPrem）內，另一個則位在 {{site.data.keyword.cloud_notm}} 中。perftest 傳輸量的運作方式是讓傳送端嘗試在鏈結可以承受時快速傳送。因此，針對每個測試，您會看到「傳送端」率高於「接收端」率，而且您可以採用「接收端」率作為單向傳輸量結果數目。|
|HCX 疑難排解| 如需相關資訊，請參閱 [HCX 疑難排解](/docs/services/vmwaresolutions?topic=vmware-solutions-vcshcx-troubleshooting#vcshcx-troubleshooting){:new_window}。|
| 具有 0% 進度及 0 位元組且狀態為「錯誤」的 HCX 同步狀態 | 如需相關資訊，請參閱 [HCX 抄寫處於具有 0% 進度及 0 位元組且狀態為錯誤的同步狀態 (56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:new_window}。|
| VM 網路效能不佳 | 檢閱 VM 虛擬 NIC 設定。VMware 建議將 VMXNET 3 虛擬 NIC 用於 VM，因為它是從效能往上設計的最新一代半虛擬化 NIC。使用 VMware 相容性清單檢查 VMXNET 3 相容性，若支援，請變更虛擬 NIC 以獲得額外的網路效能。如需相關資訊，請參閱[網路疑難排解](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}。|

### vCenter
{: #opsprocs-trouble-common-vcenter}

表 5. 一般 vCenter 疑難排解

| 標題 |說明       |
|---|---|
| 虛擬機器主控台存取 | 如需相關資訊，請參閱[知識 - KB0012863 0.01 版](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:new_window}。|
| 似乎未載入新 vCenter Server 憑證 | 取代預設 vCenter Server 憑證之後，似乎未載入新的憑證。如需相關資訊，請參閱[似乎未載入新 vCenter Server 憑證](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:new_window}。|
| vCenter Server 無法連接至受管理主機 | 取代預設 vCenter Server 憑證並重新啟動系統之後，vCenter Server 無法連接至受管理主機。如需相關資訊，請參閱 [vCenter Server 無法連接至受管理主機](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:new_window}。|
| 使用自訂 SSL 憑證時無法配置 vSphere HA | 安裝自訂 SSL 憑證之後，嘗試啟用「vSphere 高可用性 (HA)」失敗。如需相關資訊，請參閱[使用自訂 SSL 憑證時無法配置 vSphere HA](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:new_window}。|

### 授權
{: #opsprocs-trouble-common-licenses}

表 6. 一般授權疑難排解

| 標題 |說明       |
|---|---|
| 不相容或不正確的授權配置 | 如需相關資訊，請參閱[主機授權疑難排解](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window}。|
| 未開啟 VM 電源 | 如果您無法在 vSphere ESXi 主機上開啟 VM 電源，且收到 ``The 60-day evaluation period of the host is expired or the license of the host is expired`` 訊息，則可能發生授權問題。如需相關資訊，請參閱[無法開啟虛擬機器電源](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:new_window}。|
| 無法使用特性，或無法變更配置 | 如需相關資訊，請參閱[無法配置或使用特性](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:new_window}。|


## 相關鏈結
{: #opsprocs-trouble-links}
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-trbl_support#trbl_support)
* [疑難排解準則 - KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}
* [日誌檔疑難排解 - KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window}
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
* [支援日誌收集](https://kb.vmware.com/s/article/1010705){:new_window}
* [監視事件、警示及自動化動作](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}
* [vSphere 系統日誌檔](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:new_window}
* [變更 vCenter Server 構件的考量](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
