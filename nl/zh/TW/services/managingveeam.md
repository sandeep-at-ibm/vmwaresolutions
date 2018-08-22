---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# 管理 Veeam on IBM Cloud

將服務部署至實例之後，您可以使用 RDP 來存取 Veeam 主控台，以管理環境中所有虛擬機器的備份及還原（包括管理元件的備份及還原）。您也可以從 Veeam 網站下載並安裝 Veeam 更新，以升級服務。

針對 1.8 版之前版本中所部署的實例，如果您要使用 Veeam on {{site.data.keyword.cloud}} 服務，則必須取代實例中的現有 Veeam VSI。如需相關資訊，請參閱本主題中的_將 1.8 版之前的實例的 Veeam VSI 取代為 Veeam on IBM Cloud_ 小節。

## 使用 RDP 來存取 Veeam 主控台

若要管理 Veeam on {{site.data.keyword.cloud_notm}} 服務，請完成下列步驟來存取 Veeam 主控台：
1. 使用「遠端桌面通訊協定 (RDP)」，可以連接至 Windows IP 位址。
2. 使用「管理者」認證來登入 Windows 主控台。
3. 使用「管理者」認證來存取 Windows 主控台中的 Veeam 主控台。

您可以在 Veeam on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到 Windows IP 位址及「管理者」認證。

如需相關資訊，請參閱下列主題：
* [訂購、檢視及移除 Cloud Foundation 實例的服務](../sddc/sd_addingremovingservices.html)
* [訂購、檢視及移除 vCenter Server 實例的服務](../vcenter/vc_addingremovingservices.html)

## 備份及還原已安裝 Veeam on IBM Cloud 之實例的管理元件

Veeam on {{site.data.keyword.cloud_notm}} 服務可以配置成使用 Veeam 主控台來備份管理元件。如需相關資訊，請參閱[備份元件](../archiref/solution/solution_backingup.html)。

對於部署在（或升級至）1.8 版或更新版本的實例，不會自動備份環境的配置變更。因此，在變更環境的配置之前，建議您在 Veeam 主控台中執行管理備份工作，以手動備份管理元件。如需手動備份的相關資訊，請參閱 [Veeam 技術指示](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}。

管理元件失敗時，您可以使用 Veeam 主控台將管理元件還原至先前備份。如需手動還原的相關資訊，請參閱 [Veeam 技術指示]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}。

## 將更新套用至 Veeam on IBM Cloud

您負責維護 Veem，以保持更新至最新版本。若要將 Veeam 升級至最新版本，請從 Veeam 網站下載 Veeam 更新，並將更新複製到 Veeam VSI，然後進行安裝。

## 將 1.8 版之前的實例的 Veeam VSI 取代為 Veeam on IBM Cloud

Veeam on {{site.data.keyword.cloud_notm}} 服務可以備份管理元件及工作負載，並取代舊版 Veeam VSI，而其已整合至 1.8 版之前版本中的 VMware Cloud Foundation 及 VMware vCenter Server，並且僅用於備份管理元件。

基於這項變更，已移除實例詳細資料頁面上的先前**備份及還原**標籤，而且 {{site.data.keyword.vmwaresolutions_short}} 主控台中不再有實例的備份點，雖然 1.8 版前之實例中的 Veeam VSI 仍然保持運作。

您必須建立 {{site.data.keyword.cloud_notm}} 支援問題單，才能取得還原協助。此外，1.8 版之前的實例中的 Veeam VSI 授權已於 2017 年 10 月 14 日過期。因此，您必須將舊版 Veeam VSI 取代為新的 Veeam on {{site.data.keyword.cloud_notm}} 服務。

請完成下列步驟：
1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，從左導覽窗格中按一下**已部署的實例**，然後按一下目標實例。
2. 在實例詳細資料頁面上，按一下**更新及修補程式**標籤。請確定您已將實例升級至 1.8 版。
3. 按一下**服務**標籤。
4. 在**新增服務**標籤上，安裝 Veeam on {{site.data.keyword.cloud_notm}} 服務。

部署新的 Veeam on {{site.data.keyword.cloud_notm}} 服務並完成您管理元件的成功備份之後，即可建立 {{site.data.keyword.cloud_notm}} 支援問題單，以從您的帳戶移除現有 Veeam VSI。「IBM 支援中心」接著會識別並刪除現有 Veeam VSI 及儲存空間。

### 相關鏈結

* [Veeam on {{site.data.keyword.cloud_notm}} 概觀](veeam_considerations.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [常見問題](../vmonic/faq.html)
* [Veeam.com 網站](https://www.veeam.com/)
* [Veeam 技術文件](https://www.veeam.com/documentation-guides-datasheets.html)
