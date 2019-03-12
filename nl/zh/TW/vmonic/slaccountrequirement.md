---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud 基礎架構帳戶的需求
{: #slaccountrequirement}

若要使用 {{site.data.keyword.vmwaresolutions_full}} 來訂購實例，您必須具有 {{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶。實例中訂購的元件費用會向該 {{site.data.keyword.cloud_notm}}帳戶收費。

{{site.data.keyword.cloud_notm}} 基礎架構 (SoftLayer) 帳戶先前稱為 IBM SoftLayer 帳戶。{:note}

## IBM Cloud 基礎架構帳戶的許可權
{: #slaccountrequirement-permissions}

您使用的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶必須具有特定許可權，才能訂購實例中的元件，並代表您執行作業。許可權需求適用於您從 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購的所有類型之實例和服務。

獲授權的使用者可以在 {{site.data.keyword.slportal}} 中驗證及更新 {{site.data.keyword.cloud_notm}} 基礎架構帳戶的許可權。如需相關資訊，請參閱[編輯使用者的客戶入口網站許可權](/docs/customer-portal?topic=customer-portal-customerportal_accuserprof#cp_editusercpperm){:new_window}。

表 1. {{site.data.keyword.cloud_notm}} 基礎架構帳戶的必要許可權

|許可權|詳細資料     |
|:------------------ |:--------------------------------------- |
|新增伺服器|下列作業需要此許可權：要訂購執行 VMware ESXi 的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}，以及佈建用於實例配置、維護及支援作業的每小時虛擬伺服器。|
|取消伺服器|需要此許可權，才能釋放及收回執行 VMware ESXi 的 {{site.data.keyword.baremetal_short}}。如果您刪除實例，則會依正確的相依關係順序自動釋放所訂購的元件。|
|檢視虛擬伺服器詳細資料|需要此許可權才能擷取伺服器佈建詳細資料，這些是訂單驗證和自動化配置所需要的。|
|新增儲存空間|需要此許可權才能訂購實例的備份儲存空間及共用儲存空間。|
|管理儲存空間|需要此許可權才能管理實例的備份儲存空間及共用儲存空間。|
|硬體防火牆|如果已在實例上安裝 Fortinet on {{site.data.keyword.cloud_notm}} 服務，則需要此許可權才能編輯或檢視此服務的防火牆日誌檔及設定。|
|新增運算與公用網路埠|需要此許可權，才能使用公用網路埠來訂購硬體和 VSI（虛擬伺服器實例）。|
|新增 IP 位址|需要此許可權才能代表您訂購可攜式專用子網路範圍，這是要管理在 vSphere 叢集裡執行的虛擬機器所需要的。如果要在實例中新增更多服務，會將可攜式專用 IP 位址指派給 VMware ESXi 伺服器以隔離及配置頻寬。|
|新增問題單|需要此許可權才能代表您開立服務問題單。可能會針對下列作業建立問題單：要起始還原作業，以及在發現問題時自動起始問題解決程序。|
|編輯問題單|需要此許可權，才能代表您編輯所建立的服務問題單。|
|檢視問題單|需要此許可權，才能監視與實例中的元件相關的服務問題單，以處理 {{site.data.keyword.cloud_notm}} 基礎架構佈建延遲及問題。|
|檢視硬體詳細資料|需要此許可權才能擷取硬體詳細資料，這些是訂單驗證和自動化配置所需要的。|
|檢視授權|需要此許可權，才能擷取及驗證實例所使用的授權。|
|檢視密碼|需要此許可權，才能管理已訂購的 VSI。|
|管理伺服器監視|下訂單不需要此許可權，但需要它才能擷取及驗證在實例中執行 VMware ESXi 伺服器的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 的監視狀態。|

## 虛擬遞送及轉遞 (VRF) 需求
{: #slaccountrequirement-vrf}

{{site.data.keyword.cloud_notm}} 基礎架構帳戶必須是 VRF 帳戶，或者，如果是非 VRF 帳戶，則必須已啟用 VLAN Spanning。如需將帳戶從非 VRF 轉換成 VRF 的相關資訊，請參閱 [VRF on IBM Cloud 概觀](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)。

## 非 VRF 帳戶的 VLAN Spanning
{: #slaccountrequirement-vlan-spanning}

如果您使用非 VRF {{site.data.keyword.cloud_notm}} 基礎架構帳戶，則必須啟用 VLAN Spanning。如果未對非 VRF 帳戶啟用 VLAN Spanning，則 VMware 虛擬化環境的各種元件可能無法彼此通訊。

若要在帳戶中啟用 VLAN Spanning，請參閱 [VLAN Spanning](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}。

## 相關鏈結
{: #slaccountrequirement-related}

* [Cloud Foundation 實例的需求](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_planning)
* [vCenter Server 實例的需求](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [VRF on IBM Cloud 概觀](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
