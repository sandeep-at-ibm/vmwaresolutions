---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

# 利用 IAM 管理使用者存取
{: #iam}

您帳戶中使用者的 {{site.data.keyword.vmwaresolutions_full}} 服務實例存取權，是透過 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 所控制。每位存取您帳戶中 {{site.data.keyword.vmwaresolutions_short}} 服務的使用者，都必須獲指派已定義 IAM 使用者角色的存取原則。

存取原則決定使用者可在您選取之服務或實例的環境定義內執行的動作。{{site.data.keyword.cloud_notm}} 服務會將可容許的動作自訂及定義為容許對服務執行的作業。然後，這些動作會對映至 IAM 使用者角色。

原則允許在不同層次授與存取權。部分選項包括下列存取權：

* 您帳戶中所有服務實例的存取權
* 您帳戶中個別服務實例的存取權
* 實例內特定資源的存取權
* 您帳戶中所有已啟用 IAM 功能之服務的存取權

定義存取原則的範圍之後，即可指派角色。

請檢閱下列資訊，以概述 {{site.data.keyword.vmwaresolutions_short}} 服務內每個角色所容許的動作。

## 平台管理角色及許可權
{: #iam-roles}

平台管理角色可讓使用者在平台層次對服務資源執行作業。例如，指派使用者對服務的存取權、建立或刪除服務 ID、建立實例，以及將實例連結至應用程式。

下表提供對映至平台管理角色之動作的相關資訊。

表 1. 平台管理角色及容許的動作

| 平台管理角色 |動作| 範例動作 |
|:----------------- |:----------------- |:----------------- |
| 檢視者 | 唯讀動作 | <ul><li>檢視實例的摘要</li><li>檢視實例的詳細資料</li></ul>|
| 編輯者 | 更新特定實例 |<ul><li>新增或移除 ESXi 伺服器</li><li>新增或移除叢集</li><li>新增或移除服務</li><li>將實例升級至更高版本</li></ul> |
| 操作員 | 唯讀動作 | <ul><li>列出實例</li><li>檢視實例的詳細資料</li></ul> |
| 管理者 | 完整管理存取權 |<ul><li>建立新實例</li><li>刪除實例</li><li>將平台存取權授與其他使用者</li></ul>|

對於 {{site.data.keyword.vmwaresolutions_short}}，存在下列動作：

表 2. 動作說明及必要角色

| 動作 | 服務上的作業 | 角色 |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | 建立新實例 | 管理者 |
| vmware-solutions.instances.delete | 刪除實例 | 管理者 |
| vmware-solutions.instances.view | <ul><li>列出實例</li><li>檢視實例的詳細資料</li></ul> | 檢視者、操作員、編輯者及管理者 |
| vmware-solutions.instances.update | <ul><li>新增或移除 ESXi 伺服器</li><li>新增或移除叢集</li><li>新增或移除服務</li><li>將實例升級至更高版本</li></ul> | 編輯者及管理者 |
| vmware-solutions.account.update | 更新帳戶設定 | 管理者 |

## 管理使用者的存取權
{: #iam-users}

您可以將新使用者新增至 {{site.data.keyword.cloud_notm}} 帳戶，讓這些使用者可以共用針對該帳戶所佈建的服務及資源。如需相關資訊，請參閱[邀請使用者存取服務及資源](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)。

您也可以管理現有使用者的存取權，包括修改現有存取權、指派新存取權，以及檢閱指派的存取權。若要管理使用者的存取權，您必須是帳戶擁有者，或者必須具有**管理者**平台管理角色。如需相關資訊，請參閱[管理資源的存取](/docs/iam?topic=iam-iammanidaccser)。

## 將現有實例移轉至 IBM Cloud 帳戶
{: #iam-migrate}

因為 {{site.data.keyword.vmwaresolutions_short}} 與 IAM 整合，所以 {{site.data.keyword.cloud_notm}} 帳戶中部署於 2.5 版及更新版本的實例會自動新增至您的帳戶，並由 IAM 管理。

對於已部署在 2.4 版及更早版本中的現有實例，您可以將它們移轉至指定的 {{site.data.keyword.cloud_notm}} 帳戶，以進行啟用 IAM 功能的管理。如需相關資訊，請參閱下列主題：
* [將 2.5 版之前的 vCenter Server 實例移轉至 IBM Cloud 帳戶](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [將 2.5 版之前的 vCenter Server with Hybridity Bundle 實例移轉至 IBM Cloud 帳戶](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [將 2.5 版之前的 NetApp ONTAP Select 實例移轉至 IBM Cloud 帳戶](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

## 相關鏈結
{: #iam-related}

* [管理身分及存取](/docs/iam?topic=iam-getstarted)
* [邀請使用者](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [何謂 IAM](/docs/iam?topic=iam-iamoverview)
