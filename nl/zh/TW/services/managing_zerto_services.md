---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: Zerto, request Zerto Orchestrated, Zerto managed service

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# Managed Services for Zerto on IBM Cloud
{: #managing_zerto_services}

Zerto on {{site.data.keyword.cloud}} 服務提供抄寫及災難回復功能。這些功能可以整合到部署供應項目，以保護及回復 {{site.data.keyword.cloud_notm}} 上 VMware 虛擬環境中的資料。

當您要求 Managed Services for Zerto on {{site.data.keyword.cloud_notm}} 時，可以使用 Zerto DR 軟體及 IBM Resiliency Services 部署完整受管理災難回復 (DR) 環境。

Managed Services for Zerto on {{site.data.keyword.cloud_notm}} 的下列模型可供使用。

## IBM Orchestrated Managed Services for Zerto
{: #managing_zerto_services-orchestrated}

如果您要使用 Zerto on {{site.data.keyword.cloud_notm}} 供應項目，則適合此模型。

在此模型中，會針對 Zerto on {{site.data.keyword.cloud_notm}} 佈建 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 服務。此模型可以持續保護 {{site.data.keyword.cloud_notm}} 上的虛擬機器、作業系統及資料，且具有不中斷 DR 測試、RTO/RPO（回復時間目標/回復點目標）可見性、失效接手及失效回復功能。

「IBM Resiliency Services 廣域指令中心」從 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 儀表板管理所有功能。

如需相關資訊，請參閱 [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration){:external}。

## IBM-Managed Services for Zerto（無 Orchestration）
{: #managing_zerto_services-without-orchestrated}

在此模型中，會針對 Zerto on {{site.data.keyword.cloud_notm}} 佈建完全受管理的 DR 解決方案。如果您只要 Zerto Virtual Replication 的受管理服務（{{site.data.keyword.cloud_notm}} 上沒有 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 服務），則適合此模型。

如需相關資訊，請參閱 [IBM Resiliency Disaster Recovery 即服務](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top){:external}。

## 要求 Managed Services for Zerto on IBM Cloud 的程序
{: #managing_zerto_services-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**開始使用**。
2. 向下捲動頁面，然後按一下 **VMware 受管理服務**下的 **Managed Services for Zerto on IBM Cloud** 卡。
3. 在 **Zerto on IBM Cloud** 頁面上，檢閱 Zerto on {{site.data.keyword.cloud_notm}} 即受管理服務的說明及技術規格，然後按一下**建立**。
4. 根據您的需求指定配置設定，或接受預設值。
5. 按一下 **vCenter Server**，將服務新增至其中一個實例。
6. 若要在訂購新實例時新增服務，請按一下**新增至新實例**，然後繼續訂購新的 [vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance) 實例。
7. 若要將服務新增至現有實例，請按一下**新增至現有實例**，從清單中選取您要的實例，然後按一下**佈建**確認您要繼續訂購。

## 相關鏈結
{: #managing_zerto_services-related}

* [訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
