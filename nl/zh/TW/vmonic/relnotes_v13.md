---

copyright:

  years:  2016, 2018

lastupdated: "2017-01-23"

---

# 1.3 版的版本注意事項

此版本包括新增特性、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## vCenter Server 實例的共用檔案層次儲存空間

您現在可以將共用 NAS（網路連接儲存空間）新增至 vCenter Server 實例。新增此特性可讓您在 vCenter Server 上執行正式作業工作負載，並防止在發生節點失敗時遺失資料。在 vCenter Server 實例的訂購處理程序中，會提供 NFS（網路檔案系統）檔案儲存空間作為選項。如需相關資訊，請參閱[訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)。

## Zerto 災難回復移除

不論您是訂購 Zerto 災難回復作為實例的一部分，或是將它新增至現有的實例中，當您不再需要它時，您現在可以移除此服務。在您要求從主控台移除此服務之後，「IBM 支援中心」會引導您完成移除處理程序。

如需相關資訊，請參閱下列主題：

* [災難回復移除](../services/removingzertodr.html)
* [檢視 Cloud Foundation 實例](../sddc/sd_viewinginstances.html)
* [檢視 vCenter Server 實例](../vcenter/vc_viewinginstances.html)

## VMware NSX Edge for Cloud Foundation 實例

現在，NSX Edge 已包含成為您訂購的新 Cloud Foundation 實例的一部分。NSX Edge 提供網路 Edge 安全及閘道服務，以隔離虛擬化網路。

在實例部署期間，由 IBM 部署 Management NSX Edge Services Gateway (ESG)。IBM 管理虛擬機器會利用此 ESG，來和與自動化相關的特定外部 IBM 管理元件進行通訊。所部署的這個 ESG 包括兩個介面：一個介面連接至 {{site.data.keyword.cloud_notm}} 專用 VLAN，另一個介面連接至 {{site.data.keyword.cloud_notm}} 公用 VLAN。

為了確保安全，已設置防火牆規則，僅容許管理虛擬機器所起始的出埠 HTTPS 通訊。這個 ESG 部署在「大型」配置中，只有「IBM 支援中心」才能修改此配置。

如需相關資訊，請參閱下列主題：

* [Cloud Foundation 實例的技術規格](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)
* [管理服務 NSX Edge 是否造成安全風險？](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX 文件](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## 實例訂購處理程序

已改進 Cloud Foundation 實例及 vCenter Server 實例的實例訂購處理程序：

* 摘要頁面會顯示所有訂購的元件及服務的所有適用條款，讓您在下訂單之前能夠輕易存取來檢閱及同意這些條款。
* 在下訂單之前，您可以先儲存及列印實例的訂單摘要。利用這個新功能，您可以檢閱實例設定和成本，必要的話可以修改訂購的元件，取得核准，然後回到您的訂單。

如需相關資訊，請參閱下列主題：

* [訂購 Cloud Foundation 實例](../sddc/sd_orderinginstance.html)
* [訂購 vCenter Server 實例](../vcenter/vc_orderinginstance.html)

## 實例管理

實例管理程序的新增特性及改善：

* 對於 Cloud Foundation 實例和 vCenter Server 實例，您可以查看並檢閱 ESXi 伺服器的預估成本，然後再決定是否將它們新增至實例。指定您要新增多少部伺服器之後，主控台上會顯示每部伺服器每月的預估成本。如需相關資訊，請參閱[擴充及縮減 Cloud Foundation 實例的容量](../sddc/sd_addingremovingservers.html)和[擴充及縮減 vCenter Server 實例的容量](../vcenter/vc_addingremovingservers.html)。
* 對於 Cloud Foundation 實例和 vCenter Server 實例，實例總數會顯示在摘要頁面頂端。您也可以按一下實例摘要頁面來訂購實例。此外，在摘要頁面上，您可以檢視佈建期間的詳細訂單狀態。將滑鼠移至顯示的狀態時，您可以查看現行步驟或錯誤的更多詳細資料（如果有的話）。
* 對於 Cloud Foundation 實例，實例詳細資料頁面會顯示實例的部署歷程，以及逐步顯示部署狀態的相關資訊。如需相關資訊，請參閱[檢視 Cloud Foundation 實例](../sddc/sd_viewinginstances.html)。
* 對於 Cloud Foundation 實例，透過在**更新及修補程式**頁面上提供關於更新的更多詳細資料，改進了更新與修補程序的可用性，例如：修補程式所需的關閉時間、排定更新的時間，以及在現行修補程式之前需要套用必要的修補程式時的視覺化指示。如需相關資訊，請參閱[將更新及修補程式套用至 Cloud Foundation 實例](../sddc/sd_applyingupdates.html)。

## 電子郵件通知

現在，當建立實例部署的新訂單，以及在實例中新增、部署或移除服務時，您現在會收到電子郵件通知。依預設，會啟用通知設定。根據您的喜好設定，您可以在**設定**頁面上設定您要接收何種通知。如需相關資訊，請參閱[使用者帳戶及設定](useraccount.html)。
