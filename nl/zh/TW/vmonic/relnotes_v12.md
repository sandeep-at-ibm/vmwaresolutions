---

copyright:

  years:  2016, 2019

lastupdated: "2016-12-12"

---

# 1.2 版的版本注意事項

此版本包括新增特性、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## 元件更新

VMware ESXi 的新版本是 vSphere 6.0 u2 p03，這是從舊版的 ESXi 6.0 u2 更新。

## IBM ID 與 Bluemix 帳戶的關聯

在 IBM Bluemix® 型錄中，{{site.data.keyword.vmwaresolutions_full}} 是提供作為基礎架構解決方案。您必須將 **IBM ID** 帳戶與 Bluemix 帳戶相關聯，以使用 **IBM ID** 帳戶來登入 {{site.data.keyword.vmwaresolutions_short}} 主控台。

如需相關資訊，請參閱下列主題：
* [開始使用](/docs/services/vmwaresolutions/index.html)
* [存取 Bluemix 的疑難排解](/docs/account/ts_accessing.html){:new_window}

## Zerto 災難回復

您可以在訂購實例時，同時訂購 VMware Cloud Foundation 實例及 VMware vCenter Server 實例，並內含 Zerto 災難回復。您也可以在實例詳細資料頁面中，將 Zerto 災難回復新增至現有的 Cloud Foundation 實例及 vCenter Server 實例。

如需相關資訊，請參閱下列主題：
* [訂購 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [檢視 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc/sd_viewinginstances.html)
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [檢視 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter/vc_viewinginstances.html)
* [Zerto 災難回復](/docs/services/vmwaresolutions/services/addingzertodr.html)

## 計價資訊

您現在可以查看並檢閱已訂購實例的預估成本，然後再決定下訂單。在您選取元件之後，當您訂購實例時，**摘要**頁面上會顯示所有元件的總成本和詳細計價。

如需相關資訊，請參閱下列主題：
* [訂購 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)

## 實例訂購處理程序的加強功能

透過下列加強功能，可大幅改善實例訂購處理程序：
* 對於 Cloud Foundation 實例及 vCenter Server 實例，已設置新的驗證檢查，以確保您使用的 SoftLayer® 使用者帳戶具有必要的使用者許可權、已啟用 VLAN 跨越，而且已提供正確的 API 金鑰。如果有任何需求不符合，使用者介面上會立即出現指示來解決問題。
*  對於 vCenter Server 實例，您選取實例元件的順序已最佳化，因此只會顯示具有您需要的硬體及 ESXi 伺服器的資料中心。這項變更可使後來發生錯誤的可能性降至最低。

如需相關資訊，請參閱下列主題：
* [訂購 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)

## 其他電子郵件通知

現在，當您在實例中新增 ESXi 伺服器時，以及移除現有的 ESXi 伺服器時，您會收到電子郵件通知。此外，當刪除實例時，您會收到電子郵件通知。依預設，會啟用通知設定。根據您的喜好設定，您可以在**設定**頁面上設定您要接收何種通知。

如需相關資訊，請參閱[使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic/useraccount.html)。
