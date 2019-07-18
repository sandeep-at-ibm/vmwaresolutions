---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購 Zerto on IBM Cloud
{: #zerto_ordering}

您可以在訂購包含服務的新實例時，同時訂購 Zerto on {{site.data.keyword.cloud}} 服務，或將服務新增至現有實例。

## 針對 Zerto 抄寫的計費
{: #zerto_ordering-billing}

使用 Zerto 抄寫的 VM 會由 Zerto 和 {{site.data.keyword.cloud_notm}} 計量。此用量的帳單將透過 {{site.data.keyword.cloud_notm}} 計費帳戶（而不是 {{site.data.keyword.cloud_notm}} 基礎架構帳戶）收費。

在訂購 Zerto on {{site.data.keyword.cloud_notm}} 之前，請確保您的 {{site.data.keyword.cloud_notm}} 帳戶是計費帳戶，並且該帳戶已鏈結到部署實例的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶。 

如果您有來自 3.0 版或更低版本的 Zerto on {{site.data.keyword.cloud_notm}} 安裝，則您的 VM 抄寫成本仍將使用 {{site.data.keyword.cloud_notm}} 基礎架構計費來進行計算。如果您的帳戶和計費設定符合先前列出的需求，則可以將 Zerto 計費方法轉換為可計費。

在 {{site.data.keyword.vmwaresolutions_short}} 主控台上，系統會提示您將 {{site.data.keyword.cloud_notm}} 基礎架構方案轉換為計費方案，並根據需要將 {{site.data.keyword.cloud_notm}} 帳戶升級到計費帳戶。

* 如需免費和計費帳戶的資訊，請參閱[帳戶類型](/docs/account?topic=account-accounts)。
* 如需升級到計費帳戶的資訊，請參閱[升級帳戶](/docs/account?topic=account-upgrading-account)。
* 如需鏈結 {{site.data.keyword.cloud_notm}} 和 {{site.data.keyword.cloud_notm}} 基礎架構帳戶的資訊，請參閱[切換至 IBM ID 並鏈結帳戶](/docs/account?topic=account-unifyingaccounts)。

## 為新實例訂購 Zerto on IBM Cloud
{: #zerto_ordering-new}

您可以使用下列其中一種方法，訂購包含 Zerto on {{site.data.keyword.cloud_notm}} 的新實例：
* 當您從 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購新實例時，請選取**服務**區段中的 **Zerto on IBM Cloud**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格上的 **VMware** 圖示，然後按一下 **VMware Services** 區段中的 **Zerto on IBM Cloud** 卡。指定服務設定，然後選取**新增至新實例**。

## 為現有實例訂購 Zerto on IBM Cloud
{: #zerto_ordering-existing}

您可以使用下列其中一種方法，將 Zerto on {{site.data.keyword.cloud_notm}} 服務新增至現有實例：
* 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，檢視要為其新增服務的實例，按一下左側導覽窗格上的**服務**，然後按一下**新增**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，按一下左導覽窗格上的 **VMware** 圖示，然後按一下 **VMware Services** 區段中的 **Zerto on IBM Cloud** 卡。指定服務設定，然後選取**新增至現有實例**。

如果將 Zerto on {{site.data.keyword.cloud_notm}} 新增到具有處於維護模式的 ESXi 伺服器的 vCenter Server 實例中，則您必須使用 Zerto Virtual Manager (ZVM) 主控台和預先移入的 Zerto Virtual Replication Appliance (VRA) IP 位址來手動部署 VRA 虛擬機器 (VM)。
{:note}

## 為僅限專用實例訂購 Zerto on IBM Cloud
{: #zerto_ordering-private-only}

如果您要將 Zerto on {{site.data.keyword.cloud_notm}} 新增至僅限專用實例，請確保符合下列需求：
* 您負責設定您自己的 Proxy 伺服器來連接至網際網路。如需相關資訊，請參閱[公用網路連線功能](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity)。
* 您還必須配置 Zerto 的 Call Home 特性。如需 Zats Call Home 的相關資訊，請參閱 [Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:external}。

## 相關鏈結
{: #zerto_ordering-related}

* [Zerto on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [管理 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Managed Services for Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com 網站](https://www.zerto.com){:external}
* [Zerto 技術文件](https://www.zerto.com/myzerto/technical-documentation/){:external}
