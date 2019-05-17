---

copyright:

  years:  2016, 2017

lastupdated: "2017-05-22"

subcollection: vmware-solutions


---

# 1.6 版的版本注意事項
{: #relnotes_v16}

此版本包括新增特性、元件更新、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VMware Cloud Foundation 實例的更新
{: #relnotes_v16-vcf}

以下是新元件或更新的元件：

*  SDDC Manager 2.2.1
*  IBM 管理元件 1.6 版
*  視您的需求而定，新硬體規格為：**小型**或**標準**。
*  可用於部署的新資料中心：**HKG02 - 香港**、**OSL01 - 奧斯陸**、**SEO01 - 首爾**、**SNG01 - 新加坡**及 **SYD04 - 雪梨**。

## VMware vCenter Server 實例的更新
{: #relnotes_v16-vcs}

### vCenter Server 實例的硬體加強功能
{: #relnotes_v16-hw-vcs}

從 1.6 版開始，vCenter Server 實例有多項可用的加強功能。

*  vCenter Server 供應項目 2.0 版規格的完整實作。
*  視您的需求而定，新的硬體規格為：**小型**、**中型**或**大型**。
*  可用於部署的新資料中心：**HKG02 - 香港**、**OSL01 - 奧斯陸**、**SEO01 - 首爾**、**SNG01 - 新加坡**及 **SYD04 - 雪梨**。
*  您的實例訂單中至少有兩部 ESXi 伺服器，依預設，會啟用 VMware vSphere DRS（分散式資源排程器）和 VMware HA（高可用性）。
*  當您訂購實例時，最多可以新增七個 NFS 檔案共用。管理元件（vCenter、PSC、NSX Manager 及 Controller、CloudDriver）現在是在 NFS 檔案共用上執行，以獲得高可用性。
*  能自動部署及配置客戶管理的 VMware NSX Edge Services Gateway。

由於這些變更，您無法在現行版本中依現狀使用（或升級）現有的 vCenter Server 實例。在僅限檢視模式的 {{site.data.keyword.vmwaresolutions_short}} 主控台上，仍然可以看到來自 1.6 版之前的 vCenter Server 實例。在使用者介面中這些實例將標示為**已淘汰**，且具有警告符號圖示。

下列動作可用於 1.6 版之前的 vCenter Server 實例：

*  檢視實例詳細資料頁面上的資訊。實例內容中顯示的資訊反映從 1.6 版發行日期開始的資料，且不再重新整理。
*  開啟 VMware vSphere Web Client，並在 vCenter 中使用該實例。
*  刪除實例。

1.6 版之前的實例上的所有其他動作皆不再可用。

### vCenter Server 實例的網路加強功能
{: #relnotes_v16-network-vcs}

*  代表您訂購公用 VLAN 上具有 16 個 IP 位址的公用子網路，以容許 VM（虛擬機器）存取網際網路。
*  代表您訂購專用 VLAN 上具有 64 個 IP 位址的專用子網路，以容許 VM 存取 SoftLayer® 內部網路。
*  NSX Controller 使用反親緣性規則部署，並在 3 節點部署配置的個別 ESXi 伺服器上執行。
*  新的 VMware NSX Edge Services Gateway 供客戶使用。

   現在，在您訂購的新 vCenter Server 實例中會部署另一個 NSX Edge Services Gateway (ESG)。

   所提供的這個 ESG 是要與您自己的 VM 一起使用，以進行代表您訂購的專用與公用子網路之間的通訊，它包括兩個介面：一個介面連接至與您的 VM 相關聯的虛擬化 VXLAN，另一個介面連接至公用 VLAN。此外，還配置了下列設定：
   *  防火牆規則，其容許專用子網路 IP 位址範圍內所有送出的資料流量。
   *  SNAT（來源網址轉換）規則（依預設會停用），能將專用子網路中的所有 IP 位址轉換為公用子網路上的單一 IP 位址。
   * VMware HA（高可用性）已配置為使用在管理 ESG 與客戶管理的 ESG 之間共用的新埠群組。

   這個 ESG 是針對所有實例硬體類型而部署的，客戶可以修改配置。如需相關資訊，請參閱下列主題：
   *  [配置網路以使用客戶管理的 NSX Edge Services Gateway 來搭配您的 VM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config)
   *  [VMware NSX 文件](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## 可用性加強功能
{: #relnotes_v16-ui}

在整個使用者介面中進行了改善：

*  透過建立左導覽窗格來存取使用者介面的所有區域，使主控台的主要導覽大幅改進。您可以快速訂購新實例、檢視已部署的實例、檢閱系統通知、變更設定，以及存取線上文件。
*  可從左導覽窗格中存取的新**開始使用**頁面，在主控台上直接提供足夠的詳細資料，以協助您對所要訂購的實例的元件做出明智的決策。在**開始使用**頁面上，也會逐步引導您完成實例的訂購處理程序，從滿足訂購實例的所有必要條件（例如所需的使用者帳戶）開始，一直到下訂單為止。
*  Cloud Foundation 實例和 vCenter Server 實例的摘要詳細資料已合併至單一頁面，可從左導覽窗格的**資源**功能表存取該頁面。您可以從該頁面選取適當的標籤，以過濾 Cloud Foundation 實例或 vCenter Server 實例。
* 如果您的實例上已安裝 Zerto 災難回復，您只要按一下就可以直接從服務詳細資料頁面存取 Zerto 主控台。如需相關資訊，請參閱[訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)。
