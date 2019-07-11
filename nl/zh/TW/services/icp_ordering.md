---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: IBM Cloud Private Hosted, ICP configuration, order Cloud Private

subcollection: vmware-solutions


---

# 訂購 IBM Cloud Private Hosted
{: #icp_ordering}

您可以在訂購包含服務的新實例時，同時訂購 {{site.data.keyword.cloud}} Private Hosted 服務，或將服務新增至現有實例。

## 為新實例訂購 IBM Cloud Private Hosted
{: #icp_ordering-new}

您可以使用下列其中一種方法，訂購包含 {{site.data.keyword.cloud_notm}} Private Hosted 服務的新實例：
* 當您從 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購新實例時，請選取**選用服務**區段中的 **IBM Cloud Private Hosted**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，選取 **IBM Cloud Private Hosted**，指定服務設定，然後選取**新增至新實例**。

## 為現有的實例訂購 IBM Cloud Private Hosted
{: #icp_ordering-existing}

您可以使用下列其中一種方法，將 {{site.data.keyword.cloud_notm}} Private Hosted 服務新增至現有實例：
* 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，檢視您要為其新增服務的實例，按一下左導覽窗格上的**服務**，然後按一下**新增**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，選取 **IBM Cloud Private Hosted**，指定服務設定，然後選取**新增至現有實例**。

## IBM Cloud Private Hosted 服務配置
{: #icp_ordering-config}

當您訂購此服務時，請提供下列設定：
* 根據您的需求，選取**正式作業就緒**或**開發/測試**。
* 請選取必要的勾選框，以認證您已取得部署 {{site.data.keyword.cloud_notm}} Private Hosted 服務所需的授權。

## 部署更多節點
{: #icp_ordering-deploy-nodes}

如果要部署更多節點，請檢閱下列資訊：
* 使用隨初始 {{site.data.keyword.cloud_notm}} Private Hosted 安裝一起部署的 {{site.data.keyword.cloud_notm}} Private Ubuntu 範本 (Ubuntu 1604)。
* 若要尋找 Ubuntu 範本，請在 VMware vSphere Web Client 中，移至 `cam` 資料夾下的 **VM 和範本**標籤。
* Ubuntu 範本的預設密碼為 `icponcloud`。建議您在使用該範本之前變更此密碼。
* {{site.data.keyword.vmwaresolutions_short}} 不支援套用 Ubuntu 範本的更新和修補程式。您必須自行監視並套用這些更新。


## 相關鏈結
{: #icp_ordering-related}

* [IBM Cloud Private Hosted 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [訂購、檢視及移除 vCenter Server with Hybridity Bundle 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
