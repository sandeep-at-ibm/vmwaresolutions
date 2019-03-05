---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 刪除多站台配置中的 Cloud Foundation 實例

在您打算刪除多站台配置中的 Cloud Foundation 實例之前，請檢閱下列考量。

刪除 Cloud Foundation 實例時，會循序釋放下列元件：
1. 所有已部署的服務
2. 支援與服務費用
3. VMware 產品授權
4. ESXi 伺服器
5. 子網路
6. VLAN

由於資源相依關係，當您刪除實例時，不會立即釋放實例中的元件。例如，在 {{site.data.keyword.cloud}} 基礎架構完整收回 ESXi 伺服器（發生於 {{site.data.keyword.cloud_notm}} 計費週期結束時）之前，無法刪除子網路及 VLAN。在 {{site.data.keyword.cloud_notm}} 計費週期（通常為 30 天）結束時，會刪除子網路及 VLAN，並完成實例刪除。

將針對已刪除的實例，向您收取到 {{site.data.keyword.cloud_notm}} 計費週期結束為止的費用。
{:note}

## 刪除多站台配置中的 Cloud Foundation 實例的程序

1. 移除次要 Cloud Foundation 實例中的所有服務。
2. 確定您未將任何 NSX 物件擴充至要刪除的次要實例。
3. 從主要 SSO（單一登入）網域刪除次要 vCenter 及 PSC (Platform Services Controller)。如需相關資訊，請參閱 [Unregister vCenter Server from Single Sign-On](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}。
4. 將本端網域控制站 VSI（虛擬服務實例）降級。如需相關資訊，請參閱 [Demoting domain controllers and domains](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}。
5. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台刪除次要 Cloud Foundation 實例。
6. 針對多站台配置中的所有次要 Cloud Foundation 實例，重複步驟 1 - 5。
7. 刪除所有次要實例之後，您也可以從 {{site.data.keyword.vmwaresolutions_short}} 主控台刪除主要實例。

### 相關鏈結

* [刪除 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc/sd_deletinginstance.html)
* [訂購、檢視及移除 Cloud Foundation 實例的服務](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
