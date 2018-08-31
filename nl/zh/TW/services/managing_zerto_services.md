---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# 要求 Zerto on IBM Cloud 的受管理服務

Zerto on {{site.data.keyword.cloud}} 服務提供抄寫及災難回復功能。這些功能可以整合到部署供應項目，以保護及回復 {{site.data.keyword.cloud_notm}} 上 VMware 虛擬環境中的資料。

當您要求 Zerto on {{site.data.keyword.cloud_notm}} 的受管理服務時，可以使用 Zerto DR 軟體及 IBM Resiliency Services 部署完整受管理災難回復 (DR) 環境。

Zerto on {{site.data.keyword.cloud_notm}} 之受管理服務的下列模型可供使用。

## IBM Orchestrated Managed Services for Zerto

如果您要使用 Zerto on {{site.data.keyword.cloud_notm}} 供應項目，則適合此模型。

在此模型中，會針對 Zerto on {{site.data.keyword.cloud_notm}} 佈建 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 服務。此模型可以持續保護 {{site.data.keyword.cloud_notm}} 上的虛擬機器、作業系統及資料，且具有不中斷 DR 測試、RTO/RPO（回復時間目標/回復點目標）可見性、失效接手及失效回復功能。

「IBM Resiliency Services 廣域指令中心」透過 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 儀表板管理所有功能。

如需相關資訊，請參閱 [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration)。

## IBM Managed Services for Zerto（無 Orchestration）

在此模型中，會針對 Zerto on {{site.data.keyword.cloud_notm}} 佈建完整受管理的 DR 解決方案。如果您只要 Zerto Virtual Replication 的受管理服務（{{site.data.keyword.cloud_notm}} 上沒有 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 服務），則適合此模型。

如需相關資訊，請參閱 [IBM Resiliency Disaster Recovery 即服務](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top)。

## 程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**開始使用**。
2. 向下捲動頁面，然後按一下**訂購其他受管理服務**下的 **Zerto on IBM Cloud 的受管理服務**卡片。
3. 在 **Zerto on IBM Cloud** 頁面上，檢閱 Zerto on {{site.data.keyword.cloud_notm}} 即受管理服務的說明及技術規格，然後按一下**建立**。
4. 根據您的需求指定配置設定，或接受預設值。
5. 按一下 **vCenter Server** 或 **Cloud Foundation**，將服務新增至其中一個實例。
6. 若要在訂購新實例時新增服務，請按一下**新增至新實例**，然後繼續訂購新的 [vCenter Server](../vcenter/vc_orderinginstance.html)、[vCenter Server with Hybridity](../vcenter/vc_hybrid_orderinginstance.html) 或 [Cloud Foundation](../sddc/sd_orderinginstance.html) 實例。
7. 若要將服務新增至現有實例，請按一下**新增至現有實例**，從清單中選取您要的實例，然後按一下**佈建**確認您要繼續訂購。

### 相關鏈結

* [訂購、檢視及移除 vCenter Server 實例的服務](../vcenter/vc_addingremovingservices.html)
* [訂購、檢視及移除 Cloud Foundation 實例的服務](../sddc/sd_addingremovingservices.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
