---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-02"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 警示
{: #opsprocs-alarms}

## 簡介
{: #opsprocs-alarms-intro}

vSphere 包括事件及警示子系統，可追蹤 vSphere 環境中發生的事件，並讓此資訊可用於 vCenter。在此子系統中，使用下列術語：

### 事件
{: #opsprocs-alarms-events}

事件是指在 vCenter 物件（例如主機及虛擬機器 (VM)）上所發生的系統或使用者動作的記錄。事件資料包括事件的詳細資料，例如收集者、發生時間及事件類型。在 vSphere Web Client 中，事件資料會顯示在「監視」標籤中。

事件分類為：
* 錯誤 (Error) - 指出系統中發生無法復原的問題，並終止處理程序或作業。
* 警告 (Warning) - 指出系統存在潛在風險，需要予以修正。此事件不會終止處理程序或作業。
* 資訊 (Information) - 說明已順利完成使用者或系統作業。
* 審核 (Audit) - 審核日誌資料包括關於動作為何、執行者、發生時間及使用者 IP 位址的資訊。

### 警示
{: #opsprocs-alarms-alarms}

警示是為了回應一個事件、一組條件或庫存物件狀態而啟動的通知。

警示定義由 vSphere Client 中的下列元素組成：
* 名稱和說明 (Name and description) - 提供識別標籤和說明。
* 目標 (Target) - 定義受監視物件的類型。
* 警示規則 (Alarm Rule) - 定義觸發警示的事件、條件或狀況，並且定義通知嚴重性。它也定義為了回應所觸發警示而發生的作業。
* 前次修改時間 (Last modified) - 已定義警示的前次修改日期和時間。

警示具有下列嚴重性層次：
* 正常 (Normal) - 綠色。
* 警告 (Warning) - 黃色。
* 警示 (Alert) - 紅色。

### 警示定義
{: #opsprocs-alarms-def}

警示定義與庫存中選取的物件相關聯，並監視其定義中指定的庫存物件類型。

警示定義由下列元素組成：
* 名稱和說明 (Name and description) - 提供識別標籤和說明。
* 警示類型 (Alarm type) - 定義受監視物件的類型。
* 觸發程式 (Trigger) - 定義觸發警示的事件、條件或狀況，並且定義通知嚴重性。
* 容錯臨界值（報告）(Tolerance threshold (Reporting)) - 提供在觸發警示之前必須超出的條件及狀態觸發臨界值的其他限制。
* 動作 (Action) - 定義為了回應所觸發警示而發生的作業。VMware 提供庫存物件類型特定的預先定義動作集。
* 警示動作 (Alarm Action) - 警示動作是為了回應觸發程式而發生的作業。例如，您可以在觸發警示時將電子郵件通知傳送給一位以上的管理者。
* 確認已觸發警示 (Acknowledge triggered alarm) - 在您確認警示之後，會停止警示動作。不會清除警示，或在確認時重設警示。確認警示可讓其他使用者知道您擁有這個問題的所有權。
* 重設已觸發警示 (Reset triggered alarm) - 如果 vCenter 未擷取識別正常狀況的事件，則事件所觸發的警示可能不會重設為正常狀態。在這類情況下，請手動重設警示。
* 預先配置的 vSphere 警示 (Preconfigured vSphere alarm) - vSphere 事件及警示子系統具有若干預設警示，可監視 vSphere 庫存物件的作業。您只能設定這些警示的動作。

## 警示設定工作流程
{: #opsprocs-alarms-setup-workflow}

VMware 提供下列各表格所述的預先配置 vCenter 警示，然而它們已設定只能在 vCenter Web 用戶端內顯示的動作。我們的指引是配置 SMTP 伺服器詳細資料，然後設定警示動作，一開始僅針對下列警示將電子郵件傳送給系統管理者，而不造成系統管理者團隊的困擾。如需相關資訊，請參閱[傳送電子郵件作為警示動作](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-1F940DAF-933B-44B7-A200-7A11B5D3E3D5.html){:new_window}。

設定警示工作流程如下：
* 配置 SMTP 伺服器詳細資料。
* 配置叢集、主機、資料儲存庫及重要虛擬應用裝置（如 VCSA、PSC、NSX Manager 和「控制器」）的警示動作：
  * 叢集 -「VMware 高可用性」錯誤。
  * 主機 - CPU 狀態、記憶體狀態、儲存空間狀態和硬體狀態（即電壓、溫度或電源狀態變更）。
  * 資料儲存庫 - 可用磁碟空間偏低。
  * 重要虛擬應用裝置 - CPU 使用率、記憶體用量、磁碟延遲。
* 使用主動每日作業：
  * 檢閱已傳送的警示 - 是否真的需要這些警示？
  * 檢閱未傳送的警示 - 是否需要瞭解有關這些警示的資訊？
  * 檢閱度量 - 度量是否正確；例如，既然您已瞭解基準線，則是否 CPU 使用率應該設定為 75%，而不是 90%？
  * 是否需要配置自己的警示？
  * 是否需要包括虛擬機器？

##  一般警示工作流程
{: #opsprocs-alarms-alarm-workflow}

設定之後，以下是系統管理者在觸發警示時通常會採用的警示工作流範例：

1. 主機具有警示集可監視 CPU 使用率，而且警示具有警示動作可在觸發警示時將電子郵件傳送給管理者（如前一節所述）。
3. 主機 CPU 使用率驟增，這會觸發警示而將電子郵件傳送給管理者。
4. 其中一位管理者會登入 vCenter 並確認已觸發的警示，讓另一位管理者知道正在處理問題，並防止警示傳送更多電子郵件訊息。不過，系統中仍然可看見警示。
5. 管理者會尋找 CPU 尖波和更正的原因。
6. 自動重設警示。

## 預先配置的警示 - 標準
{: #opsprocs-alarms-preconfigured-std}

下表格說明了下列各項目：

* 警示名稱 - vCenter 中可見的警示名稱。
* 指引 - 使用此警示時的 IC4V 指引。
* 相關資訊 - 可從 IBM 或 VMware 取得其他資訊，以協助解決這些已觸發的警示。

表 1. 預先配置的警示

| 警示名稱 | 指引 | 相關資訊 |
|---|---|---|
| 主機連線及電源狀態 | 配置為在設為「未回應」或「待命」時傳送電子郵件一次。| [Alarms about the host connection state changing from green to red frequently occur (1020210)](https://kb.vmware.com/s/article/1020210){:new_window} |
| 主機 CPU 使用率 | 配置為在主機 CPU 使用率 > 90% 持續達 5 分鐘時傳送電子郵件一次。| [Knowledge - KB0012707 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=342e3d6adbc5730030c93a1b7c961976){:new_window} |
| 主機記憶體用量 | 配置為在主機記憶體用量 > 95% 持續達 5 分鐘時傳送電子郵件一次。| [Knowledge - KB0012712 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=30110ee2db49730030c93a1b7c96194f){:new_window} |
| 虛擬機器 CPU 使用率 | 配置為在重要應用裝置的 VM CPU 使用率 > 90% 持續達 5 分鐘時傳送電子郵件一次。| [Virtual machine CPU usage alarm (2057830)](https://kb.vmware.com/s/article/2057830){:new_window} |
| 虛擬機器記憶體用量 | 配置為在重要應用裝置的 VM 記憶體用量 > 95% 持續達 5 分鐘時傳送電子郵件一次。| [Virtual machine memory usage alarm (2057846)](https://kb.vmware.com/s/article/2057846){:new_window} |
| 磁碟上的資料儲存庫用量 | 對於 vSAN，配置為在資料儲存庫用量 > 70% 時傳送電子郵件一次。對於非 vSAN，配置為在資料儲存庫用量 > 85% 時傳送電子郵件一次。| [Knowledge - KB0012713 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=ddb3422edb89730030c93a1b7c9619f6){:new_window} |
| 虛擬機器 CPU 就緒 |配置為在 5 分鐘內重要應用裝置的 VM CPU 就緒時間大於 2000 毫秒時傳送電子郵件一次。| [Knowledge - KB0012718 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=7056426adb0d730030c93a1b7c9619e6){:new_window} |
| 虛擬機器磁碟延遲總計 |配置為在 5 分鐘內重要應用裝置的 VM 磁碟總等待時間大於 30 毫秒時傳送電子郵件一次。| [Knowledge - KB0012729 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=15dddea2db857300d5a971198c961995){:new_window} |
| 虛擬機器磁碟指令已取消 | 一開始不要設定。請考慮針對第二階段的重要應用裝置設定。| 沒有其他資訊 |
| 虛擬機器磁碟重設 | 一開始不要設定。請考慮針對第二階段的重要應用裝置設定。| 沒有其他資訊 |
| 授權庫存監視 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Troubleshooting licensing ](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} and [Licensing ESXi 6.x and vCenter Server 6.x](https://kb.vmware.com/s/article/2107538){:new_window} |
| 授權使用者臨界值監視 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [授權疑難排解](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| 授權容量監視 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [授權疑難排解](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| 主機授權版本與 vCenter Server 授權版本不相容 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Troubleshooting host licensing](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window} |
| 啟動次要 VM 時逾時 * | 未配置，因為它會監視「VMware 容錯」，這不建議用於 vCenter Server 實例。| [Timeout starting Secondary VM alarm (2064169)](https://kb.vmware.com/s/article/2064169){:new_window} |
| 次要 VM 沒有相容的主機 | 未配置，因為它會監視「VMware 容錯」，這不建議用於 vCenter Server 實例。| 沒有其他資訊 |
| 虛擬機器容錯狀態已變更 | 未配置，因為它會監視「VMware 容錯」，這不建議用於 vCenter Server 實例。| 沒有其他資訊 |
| 虛擬機器容錯 vLockStep 間隔狀態已變更 | 未配置，因為它會監視「VMware 容錯」，這不建議用於 vCenter Server 實例。| 沒有其他資訊 |
| 主機處理器狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機記憶體狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機硬體風扇狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機硬體電壓 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機硬體溫度狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機硬體電源狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機硬體系統主機板狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機電池狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 其他主機硬體物件的狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機儲存空間狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機 IPMI 系統事件日誌狀態 | 未配置，因為它不影響服務。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機基板管理控制器狀態 | 配置為在監視器從綠色變更為紅色時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 主機錯誤 * | 配置為在監視器變更為錯誤時傳送電子郵件一次。| [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support) |
| 虛擬機器錯誤 * | 配置為在重要應用裝置為嚴重時傳送電子郵件一次。| [Troubleshooting virtual machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window} |
| 主機連線失敗 * | 配置為當事件為「無法連接主機 - 網路錯誤」、「無法連接主機 - 逾時」或「主機連線遺失」時傳送電子郵件一次。| [Alarms about the host connection state changing from green to red frequently occur (1020210)](https://kb.vmware.com/s/article/1020210){:new_window} |
| 在已啟用 SIOC 的資料儲存庫上偵測到未受管理的工作負載 | 未配置，因為它不影響服務。| [Unmanaged workload is detected on datastore running SIOC (1020651)](https://kb.vmware.com/s/article/1020651){:new_window} |
| 已超出精簡佈建磁區容量臨界值 | 未在 vCenter Server 實例中配置，因為它們不支援 VASA 儲存空間。| 沒有其他資訊 |
| 資料儲存庫功能警示 | 未在 vCenter Server 實例中配置，因為它們不支援 VASA 儲存空間。| 沒有其他資訊 |
| VASA 提供者已斷線 | 未在 vCenter Server 實例中配置，因為它們不支援 VASA 儲存空間。| 沒有其他資訊 |
| VASA 提供者憑證有效期限警示 | 未在 vCenter Server 實例中配置，因為它們不支援 VASA 儲存空間。| 沒有其他資訊 |
| VM 儲存空間規範警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [VM storage compliance alarm (2061940)](https://kb.vmware.com/s/article/2061940){:new_window} |
| 資料儲存庫規範警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Working with datastores](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.storage.doc/GUID-3CC7078E-9C30-402C-B2E1-2542BEE67E8F.html){:new_window} |
| 重新整理 VASA 提供者的 CA 憑證和 CRL 失敗 | 未在 vCenter Server 實例中配置，因為它們不支援 VASA 儲存空間。| 沒有其他資訊 |
| vSphere HA 失效接手資源不足 | 配置為在嚴重時傳送電子郵件一次。| [Knowledge - KB0012739 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=fe1f0beedb8db300d5a971198c96191a){:new_window} |
| vSphere HA 失效接手正在進行 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| 找不到 vSphere HA 主代理程式 | 配置為在找不到 HA 主代理程式或無法與 HA 主代理程式通訊時傳送電子郵件一次。| [About vSphere availability](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.avail.doc/GUID-63F459B7-8884-4818-8872-C9753B2E0215.html){:new_window} |
| vSphere HA 主機狀態 | 配置為在下列情況時傳送電子郵件一次：主機上的 vSphere HA 代理程式發生錯誤、vSphere HA 偵測到網路隔離主機、vSphere HA 偵測到網路分割主機或 vSphere HA 偵測到主機故障。| [Troubleshooting vSphere HA host states](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window} |
| vSphere HA 虛擬機器失效接手失敗 | 配置為在重要應用裝置為嚴重時傳送電子郵件一次。| [Creating and using vSphere HA Clusters](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| vSphere HA 虛擬機器監視動作 | 配置為在重要應用裝置為嚴重時傳送電子郵件一次。| [Creating and using vSphere HA clusters](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| vSphere HA 虛擬機器監視錯誤 | 配置為在重要應用裝置為嚴重時傳送電子郵件一次。| [Creating and using vSphere HA clusters](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| vSphere HA VM 元件保護無法關閉虛擬機器的電源 | 配置為在重要應用裝置為嚴重時傳送電子郵件一次。| [Creating and Using vSphere HA Clusters](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window} |
| 授權錯誤 * | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [授權疑難排解](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| 性能狀態已變更 * | 配置為在狀態變更為嚴重而為嚴重時傳送電子郵件一次。| [Troubleshooting hosts](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-6F6CE545-58FA-490B-8C8A-3CB8196CAEA8.html){:new_window} |
| 儲存空間 DRS 建議 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [DRS troubleshooting information](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-5E7F6DEC-02A2-4221-AABA-EDFB9AE9EC70.html){:new_window} |
| 主機上不支援儲存空間 DRS | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [DRS troubleshooting information](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-5E7F6DEC-02A2-4221-AABA-EDFB9AE9EC70.html){:new_window} |
| 資料儲存庫叢集空間不足 | 配置為在磁碟用量超出 85% 而為嚴重時傳送電子郵件一次。| [Adding NFS storage to vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances) |
| 資料儲存庫位於多個資料中心內 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Storage DRS cannot operate on a datastore](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.troubleshooting.doc/GUID-976F5B21-8C64-4C85-BE75-0D86655E32DD.html){:new_window} |
| vSphere Distributed Switch VLAN 已設為主幹狀態 | 配置為在下列情況時傳送電子郵件一次：實體交換器未將 vSphere Distributed Switch 中的所有已配置 VLAN 都設為主幹而為嚴重時。| [Enabling vSphere Distributed Switch health check in the vSphere Web Client (2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| vSphere Distributed Switch MTU 相符狀態 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Enabling vSphere Distributed Switch health check in the vSphere Web Client (2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| vSphere Distributed Switch MTU 已支援狀態 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Enabling vSphere Distributed Switch health check in the vSphere Web Client (2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
| vSphere Distributed Switch 團隊相符狀態 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Enabling vSphere Distributed Switch health check in the vSphere Web Client (2032878)](https://kb.vmware.com/s/article/2032878){:new_window} |
|虛擬機器網路配接卡保留狀態| 僅配置為在您已啟用網路配接卡保留時傳送電子郵件一次。| [Configure bandwidth allocation for a virtual machine](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-FECAC41A-2C7A-4AD6-B740-7D8D44BADB52.html){:new_window} |
| 需要虛擬機器合併狀態 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Using Snapshots To Manage Virtual Machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-CA948C69-7F58-4519-AEB1-739545EA94E5.html){:new_window} |
| 主機虛擬快閃記憶體資源狀態 | 在 vCenter Server 實例中，不支援主機虛擬快閃記憶體。| 沒有其他資訊 |
| 主機虛擬快閃記憶體資源用量 | 未在 vCenter Server 實例中配置，因為它們不支援主機虛擬快閃記憶體。| [About Virtual Flash Resource](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.storage.doc/GUID-E69F0809-3B19-483A-B906-4CE397CE56D6.html){:new_window} |
| 登錄/取消登錄 vSAN 主機上的 VASA 供應商提供者失敗 | 未在 vCenter Server 實例中配置，因為它們不支援 VASA 儲存空間。| [VMware compatibility guide](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=vasa){:new_window} |
| 在主機上登錄/取消登錄協力廠商 IO 過濾器儲存空間提供者失敗 | 未在 vCenter Server 實例中配置，因為它們不支援 VASA 儲存空間。| [VMware compatibility guide](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=vasa){:new_window} |
| 服務控制代理程式性能警示 | 配置為在元件 ID 等於 sca 且 New 狀態等於 red 時傳送電子郵件一次。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 身分性能警示 | 配置為在元件 ID 等於 identity 且 New 狀態等於 red 時傳送電子郵件一次。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| vSphere Web Client 性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Enabling debug logging on the VMware vSphere 5.x/6.x Web Client service (2011485)](https://kb.vmware.com/s/article/2011485){:new_window} |
| ESX 代理管理程式性能警示 |配置為在元件 ID 等於 `eam` 且新狀態等於 `red` 時傳送電子郵件一次。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 訊息匯流排配置性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| CIS 授權性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 庫存性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| vCenter Server 性能警示 | 配置為在元件 ID 等於 vpxd 且新狀態等於 red 時傳送電子郵件一次。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 資料庫性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 資料服務性能警示 | 配置為在元件 ID 等於 vmware-dataservices-sca 且新狀態等於 red 時傳送電子郵件一次。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| RBD 性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| vService Manager 性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 效能圖表服務性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 內容程式庫服務性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| 傳送服務性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| VMware vSphere ESXi 傾出收集器性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [VMware ESXi Dump Collector Support](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-F8773E25-BD6A-4A6C-A999-D58CB853BA8A.html){:new_window} |
| VMware vAPI 端點服務性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| VMware 系統及硬體性能管理程式服務性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [日誌疑難排解](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.troubleshooting.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:new_window} |
| VMware vSphere 設定檔驅動儲存空間服務性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| VMware vFabric Postgres 服務性能警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [How to stop, start, or restart vCenter Server 6.x services (2109881)](https://kb.vmware.com/s/article/2109881){:new_window} |
| ESXi 主機憑證更新失敗狀態 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| ESXi 主機憑證狀態 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| ESXi 主機憑證驗證失敗狀態 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| vSphere vCenter 主機憑證管理模式 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| 主要憑證狀態 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [Troubleshooting vCenter Server and ESXi Host Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window} |
| GPU ECC 未更正的記憶體警示 | 未在 vCenter Server 實例中配置，因為它們不支援 GPU。| 沒有其他資訊 |
| GPU ECC 更正的記憶體警示 | 未在 vCenter Server 實例中配置，因為它們不支援 GPU。| 沒有其他資訊 |
| GPU 熱狀況警示 | 未在 vCenter Server 實例中配置，因為它們不支援 GPU。| 沒有其他資訊 |
| 網路連線中斷 |配置為在發生下列嚴重事件時傳送電子郵件一次：網路連線功能遺失或與 DVPort 的網路連線功能遺失。| [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| 網路上行鏈路備援中斷 |配置為在發生下列嚴重事件時傳送電子郵件一次：網路備援遺失或 DVPort 上的網路備援遺失。| [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| 網路上行鏈路備援欠佳 * |配置為在發生下列嚴重事件時傳送電子郵件一次：網路備援已降級或 DVPort 上的網路備援已降級。| [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| 未正確地配置 VMKernel NIC * |配置為在發生下列嚴重事件時傳送電子郵件一次：在 `/Migrate/VMknic` 中指定的 `vmknic` 無效。| [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window} |
| 無法連接至儲存空間 * |配置為在發生下列嚴重事件時傳送電子郵件一次：儲存空間連線中斷、儲存空間路徑備援遺失、儲存空間路徑備援欠佳，或 NFS 伺服器連線中斷。| [Identifying Fibre Channel, iSCSI, and NFS storage issues on ESX/ESXi hosts (1003659)g](https://kb.vmware.com/s/article/1003659){:new_window} |
| 移轉錯誤 * | 配置為在發生下列嚴重事件時傳送電子郵件一次：無法移轉 VM，移轉錯誤，移轉主機錯誤，無法重新定位 VM 或 VM 孤立。| [vMotion or Storage vMotion of a VM fails with the error: The migration has exceeded the maximum switchover time of 100 seconds (2141355)](https://kb.vmware.com/s/article/2141355){:new_window} |
| 結束待命錯誤 |在 vCenter Server 實例中未配置，因為不建議使用 DPM。| vSphere Distributed Power Management (DPM) 提供內部部署的省電功能，方法是在將 VM 移轉至較少的主機並且關閉不需要的 ESX 主機電源時，於較低資源使用率期間動態合併工作負載。關閉 IBM Cloud Bare Metal Server 的電源，無法節省耗電量。|

\* 表示無狀態警示。vCenter 不會保留無狀態警示的資料、不會計算或顯示其狀態。無法確認或重設無狀態警示。
{:note}

## 預先配置的警示 - vSAN
{: #opsprocs-alarms-preconfigured-vsan}

如果您具有 vSAN 叢集，則下表中的其他預先配置警示會適用：

* 警示名稱 - vCenter 中可見的警示名稱。
* 指引 - 使用此警示時的 IC4V 指引。
* 相關資訊 - 可從 IBM 或 VMware 取得其他資訊，以協助解決這些已觸發的警示。

表 2. 預先配置的警示 - vSAN

| 警示名稱 | 指引 | 相關資訊 |
|---|---|---|
| 主機快閃記憶體容量超出授權的 VSAN 限制 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| 過期的 vSAN 授權 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [授權疑難排解](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
| vSAN 主機的磁碟發生錯誤 | 配置為在 vSAN 磁碟上具有永久錯誤時傳送電子郵件一次。| [vSAN 裝置在無法讀取或寫入裝置時發生永久錯誤 (2071075)](https://kb.vmware.com/s/article/2071075){:new_window}  |
| vSAN 主機的磁碟發生錯誤 | 配置為在發生下列緊急事件時傳送電子郵件一次：虛擬 SAN 裝置發生永久故障。| [vSAN 裝置在無法讀取或寫入裝置時發生永久錯誤 (2071075)](https://kb.vmware.com/s/article/2071075){:new_window}  |
| 過期的 vSAN 授權 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。|[vSAN 授權的考量](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-planning.doc/GUID-20731F2A-B001-4A05-AB4D-30C5B0044EC5.html){:new_window}|
| 過期的 vSAN 限時授權 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 授權的考量](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-planning.doc/GUID-20731F2A-B001-4A05-AB4D-30C5B0044EC5.html){:new_window} |
| vSAN 硬體相容性問題 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能檢查資訊 (2114803)](https://kb.vmware.com/s/article/2114803?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} |
| vSAN 性能警示 `Active multicast connectivity check` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 網路性能 - 作用中多重播送連線功能檢查 (2116296)](https://kb.vmware.com/s/article/2116296){:new_window} |
| vSAN 性能警示 `Advanced vSAN configuration in sync` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 叢集性能 - 進階 vSAN 配置同步 (2107713)](https://kb.vmware.com/s/article/2107713){:new_window} |
| vSAN 性能警示 `After one additional host failure` | 配置為針對緊急事件傳送電子郵件一次。| [在兩個節點 ROBO/延伸叢集上，不正確地報告vSAN 性能警告 `after one additional host failure` (2150568)](https://kb.vmware.com/s/article/2150568?lang=en_US){:new_window} |
| vSAN 性能警示 `All hosts contributing stats` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 效能服務 - 所有提出統計資料的主機檢查 (2144400)](https://kb.vmware.com/s/article/2144400){:new_window} |
| vSAN 性能警示 `All hosts have a vSAN vmknic configured` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 網路性能 - 所有主機都已配置 vSAN vmknic (2108062)](https://kb.vmware.com/s/article/2108062){:new_window} |
| vSAN 性能警示 `All hosts have matching multicast settings` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 網路性能 - 所有主機都具有相符的多重播送設定 (2108092)](https://kb.vmware.com/s/article/2108092){:new_window} |
| vSAN 性能警示 `All hosts have matching subnets` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 網路性能 - 所有主機都具有相符的子網路 (2108066)](https://kb.vmware.com/s/article/2108066){:new_window} |
| vSAN 性能警示 `Basic (unicast) connectivity check (normal ping)` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 網路性能 - 主機小型連線測試（連線功能檢查）及主機大型連線測試（MTU 檢查）(2108285)](https://kb.vmware.com/s/article/2108285){:new_window} |
| vSAN 性能警示 `Cluster health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 叢集性能 - vSAN 性能服務安裝 (2109874)](https://kb.vmware.com/s/article/2109874){:new_window} |
| vSAN 性能警示 `Component metadata health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [元件 meta 資料性能檢查失敗，並發生無效狀態錯誤 (2145347)](https://kb.vmware.com/s/article/2145347){:new_window} |
| vSAN 性能警示 `Congestion` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 實體磁碟性能 – 壅塞 (2109255)](https://kb.vmware.com/s/article/2109255){:new_window} |
| vSAN 性能警示 `Controller disk group mode is VMware certified` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSAN HCL 性能 - vSAN HCL 上的 SCSI 控制器 (2109871)](https://kb.vmware.com/s/article/2109871){:new_window} |
| vSAN 性能警示 `Controller driver is VMware certified` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSAN HCL 性能 - 控制器驅動程式 (2109263)](https://kb.vmware.com/s/article/2109263){:new_window} |
| vSAN 性能警示 `Controller firmware is VMware certified` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [支援多個韌體版本時的控制器韌體性能檢查警告 (2150398)](https://kb.vmware.com/s/article/2150398){:new_window} |
| vSAN 性能警示 `Controller is VMware certified for ESXi release` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSAN HCL 性能 - 控制器版本支援 (2109262)](https://kb.vmware.com/s/article/2109262){:new_window} |
| vSAN 性能警示 `CPU AES-NI is disabled on hosts` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 加密 - CPU AES-NI 主機啟用檢查 (2149499)](https://kb.vmware.com/s/article/2149499){:new_window} |
| vSAN 性能警示 `Current cluster situation` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 限制性能 – 現行叢集狀況 (2108740)](https://kb.vmware.com/s/article/2108740){:new_window} |
| vSAN 性能警示 `Customer Experience Improvement Program (CEIP)` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 線上性能 - CEIP 檢查 (2148866)](https://kb.vmware.com/s/article/2148866){:new_window} |
| vSAN 性能警示 `Data health` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 資料性能 – vSAN 物件性能 (2108319)](https://kb.vmware.com/s/article/2108319){:new_window} |
| vSAN 性能警示 `Disk capacity` | 配置為針對警告事件傳送電子郵件一次。| [vSAN 性能服務 - 實體磁碟性能 - 磁碟容量 (2108907)](https://kb.vmware.com/s/article/2108907){:new_window} |
| vSAN 性能警示 `Disk format version` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 叢集 - 磁碟格式版本 (2146135)](https://kb.vmware.com/s/article/2146135){:new_window} |
| vSAN 性能警示 `ESXi vSAN Health service installation` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 叢集性能 - vSAN 性能服務保持最新 (2107705)](https://kb.vmware.com/s/article/2107705){:new_window} |
| vSAN 性能警示 `Home object` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSAN iSCSI 目標服務 - 首頁物件 (2147601)](https://kb.vmware.com/s/article/2147601){:new_window} |
| vSAN 性能警示 `Host component limit` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 限制 - 主機元件 (2146130)](https://kb.vmware.com/s/article/2146130){:new_window} |
| vSAN 性能警示 `Host issues retrieving hardware info` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN Health Service - HCL Health - Host issues retrieving hardware information (2149290)](https://kb.vmware.com/s/article/2149290){:new_window} |
| vSAN 性能警示 `Host Maintenance Mode and Decommission State` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 主機維護模式與 vSAN 節點解除任務狀態同步 (51464)](https://kb.vmware.com/s/article/51464){:new_window}|
| vSAN 性能警示 `Hosts disconnected from VC` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 網路性能 - 主機與 vCenter Server 中斷連線 (2108004)](https://kb.vmware.com/s/article/2108004){:new_window} |
| vSAN 性能警示 `Hosts with connectivity issues` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 網路性能 - 有連線功能問題的主機 (2108317)](https://kb.vmware.com/s/article/2108317){:new_window} |
| vSAN 性能警示 `Invalid preferred fault domain on witness host` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - 見證主機上偏好的錯誤網域無效 (2130589)](https://kb.vmware.com/s/article/2130589){:new_window} |
| vSAN 性能警示 `Invalid unicast agent` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 單點播送代理程式測試無效 (2144398)](https://kb.vmware.com/s/article/2144398){:new_window} |
| vSAN 性能警示 `iSCSI target service` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSAN iSCSI 目標服務 - 網路配置 (2147602)](https://kb.vmware.com/s/article/2147602){:new_window} |
| vSAN 性能警示 `Limits health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `Memory pools (heaps)` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 實體磁碟性能 - 記憶體儲存區 (2109256)](https://kb.vmware.com/s/article/2109256){:new_window} |
| vSAN 性能警示 `Memory pools (slabs)` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 實體磁碟性能 - 記憶體儲存區 (2109256)](https://kb.vmware.com/s/article/2109256){:new_window} |
| vSAN 性能警示 `MTU check (ping with large packet size)` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 網路性能 - 主機小型連線測試（連線功能檢查）及主機大型連線測試（MTU 檢查）(2108285)](https://kb.vmware.com/s/article/2108285){:new_window} |
| vSAN 性能警示 `Multicast assessment based on other checks` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 網路性能 - 根據其他檢查的多重播送評量 (2108318)](https://kb.vmware.com/s/article/2108318){:new_window} |
| vSAN 性能警示 `Network configuration` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `Network health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `Network latency check` | 配置為針對警告事件傳送電子郵件一次。| [vSAN 性能服務 - 網路性能 - 網路延遲檢查 (2149511)](https://kb.vmware.com/s/article/2149511){:new_window} |
| vSAN 性能警示 `No disk claimed on witness host` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - 見證主機上未宣告磁碟 (2130584)](https://kb.vmware.com/s/article/2130584){:new_window} |
| vSAN 性能警示 `Online health connectivity` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 線上性能 - 網際網路連線功能檢查 (2149196)](https://kb.vmware.com/s/article/2149196){:new_window} |
| vSAN 性能警示 `Operation health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `Performance Data Collection` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [效能服務上的 vSAN 性能測試失敗 (2150589)](https://kb.vmware.com/s/article/2150589){:new_window} |
| vSAN 性能警示 `Performance service status` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [效能服務上的 vSAN 性能測試失敗 (2150589)](https://kb.vmware.com/s/article/2150589){:new_window} |
| vSAN 性能警示 `Physical disk component limit health` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 實體磁碟 - 元件限制 (2146086)](https://kb.vmware.com/s/article/2146086){:new_window} |
| vSAN 性能警示 `Physical disk health retrieval issues` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 實體磁碟性能 - 實體磁碟性能擷取問題 (2149291)](https://kb.vmware.com/s/article/2149291){:new_window} |
| vSAN 性能警示 `Physical disk health - Metadata Health` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 實體磁碟性能 - meta 資料性能 (2108690)](https://kb.vmware.com/s/article/2108690){:new_window} |
| vSAN 性能警示 `Preferred fault domain unset` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - 偏好的錯誤網域取消設定 (2130590)](https://kb.vmware.com/s/article/2130590){:new_window} |
| vSAN 性能警示 `Resync operations throttling` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 叢集性能 - 重新同步作業節流控制檢查 (2149504)](https://kb.vmware.com/s/article/2149504){:new_window} |
| vSAN 性能警示 `SCSI controller is VMware certified` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSAN HCL 性能 - 控制器驅動程式 (2109263)](https://kb.vmware.com/s/article/2109263){:new_window} |
| vSAN 性能警示 `Service runtime status` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `Site Latency Health` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - 已延展的叢集 - 網站延遲 (2146133)](https://kb.vmware.com/s/article/2146133){:new_window} |
| vSAN 性能警示 `Software version compatibility` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 叢集 - 軟體版本相容性 (2146134)](https://kb.vmware.com/s/article/2146134){:new_window} |
| vSAN 性能警示 `Space efficiency configuration consistency` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `Space efficiency usage health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `Stats DB object conflicts` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 效能服務 - 統計資料 DB 物件衝突檢查 (2144405)](https://kb.vmware.com/s/article/2144405){:new_window} |
| vSAN 性能警示 `Stats DB object` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 效能服務 - 統計資料 DB 物件檢查 (2144403)](https://kb.vmware.com/s/article/2144403){:new_window} |
| vSAN 性能警示 `Stats master election` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 效能服務 - 統計資料主節點選取檢查 (2144408)](https://kb.vmware.com/s/article/2144408){:new_window} |
| vSAN 性能警示 `Stretched cluster health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `Time is not synchronized across hosts and VC` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 叢集性能 - 主機與 VC 之間的時間同步化 (2149505)](https://kb.vmware.com/s/article/2149505){:new_window} |
| vSAN 性能警示 `Unexpected number of fault domains` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - 非預期的錯誤網域數目 (2130581)](https://kb.vmware.com/s/article/2130581){:new_window} |
| vSAN 性能警示 `Unicast agent configuration inconsistent` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - 單點播送代理程式配置不一致 (2130580)](https://kb.vmware.com/s/article/2130580){:new_window} |
| vSAN 性能警示 `Unicast agent not configured` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - 未配置單點播送代理程式 (2130582)](https://kb.vmware.com/s/article/2130582){:new_window} |
| vSAN 性能警示 `Unsupported host version` | 只有在已延展 vSAN 時，才考量使用警示。| [VMware KB 文章](https://kb.vmware.com/s/article/2130583){:new_window} |
| vSAN 性能警示 `vCenter or hosts are not connected to Key Management Servers` | 只有在已啟用 vSAN 加密時，才考量使用警示。| [vSAN 性能服務 - 不受支援的主機版本 (2130583)](https://kb.vmware.com/s/article/2149497){:new_window} |
| vSAN 性能警示 `vCenter state is authoritative` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 叢集性能 - vCenter 狀態為具有授權性 (2150916)](https://kb.vmware.com/s/article/2150916){:new_window} |
| vSAN 性能警示 `Verbose mode` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [效能服務 - vSAN 性能服務中的詳細模式 (51527)](https://kb.vmware.com/s/article/51527){:new_window} |
| vSAN 性能警示 `vSAN Build Recommendation Engine build recommendation` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSphere Update Manager - vSAN 建置建議引擎性能 (2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
| vSAN 性能警示 `vSAN Build Recommendation Engine Health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSphere Update Manager - vSAN 建置建議引擎性能 (2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
| vSAN 性能警示 `vSAN Build Recommendation Engine Health` configuration issues | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSphere Update Manager - vSAN 建置建議引擎性能 (2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
| vSAN 性能警示 `vSAN CLOMD liveness` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 叢集性能 - CLOMD 存活性檢查 (2109873)](https://kb.vmware.com/s/article/2109873){:new_window} |
| vSAN 性能警示 `vSAN cluster configuration consistency` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 叢集配置一致性 (2149506)](https://kb.vmware.com/s/article/2149506){:new_window} |
| vSAN 性能警示 `vSAN cluster partition` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 網路性能 - vSAN 叢集分割區 (2108011)](https://kb.vmware.com/s/article/2108011){:new_window} |
| vSAN 性能警示 `vSAN disk balance` | 配置為針對警告事件傳送電子郵件一次。| [vSAN 性能服務 - 叢集性能 - vSAN 磁碟平衡 (2144278)](https://kb.vmware.com/s/article/2144278){:new_window} |
| vSAN 性能警示 `vSAN HCL DB Auto Update` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 硬體相容性 - vSAN HCL DB 自動更新 (2146132)](https://kb.vmware.com/s/article/2146132){:new_window} |
| vSAN 性能警示 `vSAN HCL DB up-to-date` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSAN HCL 性能 - vSAN HCL DB 保持最新 (2109870)](https://kb.vmware.com/s/article/2109870){:new_window} |
| vSAN 性能警示 `vSAN HCL health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `vSAN Health Service up-to-date` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - vSAN 建置建議 - vSAN 版本型錄保持最新 (58891)](https://kb.vmware.com/s/article/58891){:new_window} |
| vSAN 性能警示 `vSAN object health` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 資料性能 – vSAN 物件性能 (2108319)](https://kb.vmware.com/s/article/2108319){:new_window} |
| vSAN 性能警示 `vSAN Performance Service health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 效能服務 - 狀態檢查 (2149406)](https://kb.vmware.com/s/article/2149406){:new_window} |
| vSAN 性能警示 `vSAN VM health` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| vSAN 性能警示 `vSphere cluster members do not match vSAN cluster members` | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| [vSAN 性能服務 - 叢集性能 - vSphere 及 vSAN 叢集成員符合 vSAN (2149507)](https://kb.vmware.com/s/article/2149507){:new_window} |
| vSAN 性能警示 `Witness host fault domain misconfigured` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - 見證主機錯誤網域配置錯誤 (2130586)](https://kb.vmware.com/s/article/2130586){:new_window} |
| vSAN 性能警示 `Witness host not found` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - 找不到見證主機 (2130585)](https://kb.vmware.com/s/article/2130585){:new_window} |
| vSAN 性能警示 `Witness host within vCenter cluster` | 只有在已延展 vSAN 時，才考量使用警示。| [vSAN 性能服務 - vCenter 叢集內的見證主機 (2130587)](https://kb.vmware.com/s/article/2130587){:new_window} |
| vSAN 性能警示 for vMotion `Basic (unicast) connectivity check (normal ping)` | 配置為針對緊急事件傳送電子郵件一次。| [VSAN 性能顯示連線功能錯誤](https://developer.ibm.com/answers/questions/452172/vsan-health-shows-connectivity-errors/){:new_window} |
| vSAN 性能警示 for vMotion `MTU check (ping with large packet size)` | 配置為針對緊急事件傳送電子郵件一次。| [vSAN 性能服務 - 網路性能 - 主機小型連線測試（連線功能檢查）及主機大型連線測試（MTU 檢查）(2108285)](https://kb.vmware.com/s/article/2108285){:new_window} |
| VSAN 性能服務警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |
| 整體性能摘要的 vSAN 性能服務警示 | 不視為通知的必要項目。在主動每日檢查時檢閱的警示。| 沒有其他資訊 |


## 預先配置的警示 - Hybridity Bundle
{: #opsprocs-alarms-preconfigured-hcx}

Hybridity Bundle 會安裝 HCX，這會建立下列其他預先配置的警示：

表 3. 預先配置的警示 - HCX

| 警示名稱 | 指引 | 相關資訊 |
|---|---|---|
| 大量移轉失敗 | 不視為通知的必要項目，因為將對移轉進行管理。|請參閱 [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)及 [VMware HCX 疑難排解](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}。|
| 冷移轉失敗 | 不視為通知的必要項目，因為將對移轉進行管理。|請參閱 [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)及 [VMware HCX 疑難排解](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}。|
| HCX 雲端資料庫升級失敗 | 不視為通知的必要項目，因為將對升級進行管理。|請參閱 [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)及 [VMware HCX 疑難排解](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}。|
| HCX 企業資料庫升級失敗 | 不視為通知的必要項目，因為將對升級進行管理。|請參閱 [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)及 [VMware HCX 疑難排解](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}。|
| HCX 交互連接通道狀態 | 配置為針對重要通道狀態為關閉事件傳送電子郵件一次。|請參閱[網路 (WAN) 連線功能](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting#hcxclient-troubleshooting-wan-connect)。|

## 事件及警示程序
{: #opsprocs-alarms-procedures}

下表說明一些用於事件及警示的程序。

表 4. 事件及警示程序

| 標題 |說明       |
|---|---|
| 檢視事件 | 若要檢視事件，請導覽至 vCenter，然後選取庫存物件。按一下**監視**標籤、**作業及事件**與**事件**。選取事件，以查看詳細資料。您可以使用過濾器，並選取直欄標題來排序清單。|
| 匯出事件 | 您可能需要匯出事件，才能使用 MS Excel 中的工具來進行協助。選取所需的庫存物件。按一下**監視**標籤、**事件**及**匯出**圖示。在**匯出事件**視窗中，指定您要匯出的事件資訊類型。選取**產生 CSV 報告**，然後按一下**儲存**。指定檔名及位置，並儲存檔案。|
| 事件保留 | 依預設，事件保留設為 30 天。您需要在 VMware vSphere Web Client 中變更此設定。按一下**配置**標籤、**設定**及**一般**。按一下**編輯**，將「事件保留」變更為所需天數，然後按一下**確定**。|
| 檢視已觸發的警示 | 若要檢視已觸發的警示，請導覽至 vCenter，然後在**警示**窗格中選取**全部**或**新建**。此清單每 120 秒重新整理一次。若要檢視在所選取庫存物件上已觸發的警示，請選取物件。按一下**監視**標籤、**問題**，然後選取**已觸發的警示**。|

## 相關鏈結
{: #opsprocs-alarms-links}

* [vSphere 監視及效能](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-monitoring-performance-guide.pdf){:new_window}
