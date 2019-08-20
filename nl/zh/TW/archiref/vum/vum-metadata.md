---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	收集 meta 資料
{: #vum-metadata}

VUM 會透過您可以修改的預先定義自動處理程序，下載有關升級、修補程式或延伸規格的 meta 資料。VUM 會依一般可配置的間隔聯絡 VMware 或協力廠商來源，以收集有關可用升級、修補程式或延伸規格的最新 meta 資料。不過，VMware 中的預設值可使用於 VMware vCenter Server on {{site.data.keyword.cloud}} 實例，您可以視企業需求加以變更。

VUM 會顯示 vSAN 所產生的系統管理基準線。系統管理的基準線會定期自動更新其內容，這需要 VUM 可以持續存取網際網路。vSAN 系統基準線通常每 24 小時會重新整理一次。

您可以使用系統管理的基準線，將您的 vSAN 叢集升級為建議的重要修補程式、驅動程式、更新或適用於 vSAN 的最新支援 ESXi 主機版本。

對於大部分企業，VUM 的 VMware 預設值視為適合。如果您的企業要使用不同的設定，則下列資訊提供如何變更這些設定的說明。

##	下載排程
{: #vum-metadata-download-schedule}

更新是虛擬應用裝置升級、主機修補程式及延伸規格，而且依預設 VUM 會每天下載更新。下載排程的變更方式是存取 vSphere Web Client，導覽至**首頁** > **Update Manager** > **管理** > **設定**，然後選取**下載排程**，再按一下**編輯**。

##	通知檢查排程
{: #vum-metadata-notif-check-schedule}

通知是修補程式取消、新修正程式及警示的相關資訊，而且依預設 VUM 會每小時下載通知。此作業的變更方式是存取 vSphere Web Client，導覽至**首頁** > **Update Manager** > **管理** > **設定**，然後選取**通知檢查排程**，再按一下**編輯**。

##	虛擬機器設定
{: #vum-metadata-vm-settings}

若要變更虛擬機器 (VM) 設定，請存取 vSphere Web Client，導覽至**首頁** > **Update Manager** > **管理** > **設定**及 **VM 設定**，然後按一下**編輯**。

##	主機/叢集設定
{: #vum-metadata-host-settings}

若要變更「主機/叢集設定」，請存取 vSphere Web Client，導覽至**首頁** > **Update Manager** > **管理** > **設定**及**主機/叢集設定**，然後按一下**編輯**。

## 相關鏈結
{: #vum-metadata-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/)（示範）
