---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: view NetApp, view instance, view instance details

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 檢視 NetApp ONTAP Select 實例
{: #np_viewinginstances}

檢視針對不同使用者帳戶佈建之 NetApp ONTAP Select 實例的摘要及詳細資訊。

## 檢視 NetApp ONTAP Select 實例摘要的程序
{: #np_viewinginstances-procedure-view-inst-summary}

若要檢視針對使用者帳戶佈建之所有 NetApp ONTAP Select 實例的摘要，請完成下列步驟：

1. 從 {{site.data.keyword.vmwaresolutions_full}} 主控台中，按一下左導覽窗格中的**資源**。
2. 從主控台橫幅，按一下您的使用者帳戶圖示，然後按一下**帳戶**欄位，以選取您要檢查其實例的使用者帳戶。
3. 在 **NetApp ONTAP Select 實例**表格中，檢視所選取使用者帳戶中佈建的實例清單。

表 1. NetApp ONTAP Select 實例項目

|項目        |說明       |  
|:------------- |:--------------- |
|名稱 |實例的名稱。|
|版本|實例的版本。|  
|位置|管理實例所在的資料中心。|
|建立時間|建立實例的日期和時間。|   
|狀態|實例的狀態。狀態可以具有下列其中一個值：
     <ul><li>正在建立：正在建立實例。</li><li>正在建置：正在配置實例。</li><li>備妥使用：實例已備妥可供使用。</li><li>正在修改：正在修改實例。</li><li>失敗：建立、配置或修改程序失敗。</li><li>正在刪除：正在刪除實例。</li><li>刪除錯誤：刪除實例時發生錯誤。</li><li>已刪除：已刪除實例。</li></ul>|

## 檢視 NetApp ONTAP Select 實例內容詳細資料的程序
{: #np_viewinginstances-procedure-view-inst-property}

若要檢視實例的內容詳細資料，請執行下列動作：

1. 在 **NetApp ONTAP Select 實例**表格中，按一下實例名稱。
2. 在**內容**下，檢視實例的詳細資料。

表 2. NetApp ONTAP Select 實例內容

|內容        |說明       |
|:--------------- |:----------------- |
|名稱 |實例的名稱。|
|ID |實例的 ID。|
|位置|管理實例所在的資料中心。|
|已部署的版本|已部署的 {{site.data.keyword.vmwaresolutions_short}} 版本。|
|vCenter 版本|VMware vCenter Server 的版本。<br><br>**附註**：{{site.data.keyword.vmwaresolutions_short}} 主控台及 VMware vSphere Web Client 上所顯示的 vCenter Server 版本之間有輕微變化。兩者皆正確。|
|NSX for vSphere |VMware NSX for vSphere 產品版本。|
|NSX 授權版本|VMware NSX 授權的版本。|
|NetApp 版本|NetApp ONTAP Select 的版本。|
|NetApp 授權類型|NetApp ONTAP Select 授權的類型。|
|DNS、根網域|根網域名稱是實例的 DNS（網域名稱系統）網域名稱及 Microsoft Active Directory (AD) 樹系根名稱。|
|DNS、SSO 網域|SSO 網域是 vSphere Single Sign-On 網域。針對值為 `vsphere.local` 的所有已部署 NetApp ONTAP Select 實例，設定 SSO 網域名稱。|
|DNS、子網域|子網域是本端 NetApp ONTAP Select 實例主機名稱所在根網域名稱的 DNS 子網域名稱。子網域名稱的格式為 `<subdomain_label>.<root_domain>`。|
|狀態|實例的狀態。|

## 檢視 NetApp ONTAP Select 實例存取資訊的程序
{: #np_viewinginstances-procedure-view-inst-access-info}

在**存取資訊**下，檢視實例相關元件的存取資訊。這些密碼是系統所產生的起始密碼。如果您在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更它們，則不會在實例摘要頁面上更新它們。

表 3. NetApp ONTAP Select 實例相關元件的存取資訊

|元件        |說明       |
|:---------------- |:----------------- |
|AD/DNS IP |兩部 AD 伺服器的 IP 位址。|
|AD/DNS FQDN |AD/DNS 伺服器的完整網域名稱。|
|AD/DNS ADMIN（遠端桌面）|您可以用來透過遠端桌面連線存取 AD 伺服器的使用者名稱及密碼。|
|NSX Manager IP  |NSX Manager 的 IP 位址。|
|NSX Manager FQDN  |NSX Manager 的完整網域名稱。|
|NSX Manager HTTP  |您可以用來存取 NSX Manager Web 主控台的使用者名稱及密碼。|
|NetApp 叢集 IP |NetApp ONTAP Select 叢集的 IP 位址。|
|NetApp 叢集 FQDN |NetApp ONTAP 叢集的完整網域名稱。|
|NetApp 叢集 HTTPS |您可以用來存取 NetApp ONTAP Select 叢集的使用者名稱及密碼。|
|NetApp 部署工具 IP |「NetApp ONTAP Select 部署」虛擬機器的 IP 位址。|
|NetApp 部署工具 FQDN |「NetApp ONTAP Select 部署」的完整網域名稱。|
|NetApp 部署工具 HTTPS |您可以用來存取「NetApp ONTAP Select 部署」虛擬機器的使用者名稱及密碼。|
|vCenter IP  |vCenter Server 的 IP 位址。|
|vCenter FQDN  |vCenter Server 的完整網域名稱。|
|vCenter ADMIN  |您可以用來使用 vSphere Web Client 登入 vCenter Server 的 VMware vCenter Single Sign-On 使用者名稱及密碼。|
|vCenter SSH  |您可用來透過 SSH 連線存取 vCenter Server VM 的使用者名稱及密碼。|

## 檢視 NetApp ONTAP Select 實例部署歷程的程序
{: #np_viewinginstances-procedure-view-inst-deploy-history}

按一下左導覽窗格中的**部署歷程**，以檢視該實例的部署歷程。

表 4. NetApp ONTAP Select 實例部署歷程

|項目        |說明       |  
|:------------|:------------- |
|日期 |變更實例狀態的日期和時間|
|摘要 |變更的詳細資料|

如果在部署實例或刪除實例期間發生錯誤，則會自動通知「{{site.data.keyword.cloud_notm}} 支援中心」團隊。若要查詢問題單的狀態，您可以[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。

## 檢視 NetApp ONTAP Select 叢集的程序
{: #np_viewinginstances-procedure-view-cluster}

1. 從左導覽窗格中，按一下**基礎架構**。
2. 在**叢集**下，檢視 NetApp ONTAP Select 叢集的相關摘要。

	表 5. NetApp ONTAP Select 叢集項目

	 <table>
	   <tr>
	     <th>項目        </th>
	     <th>說明       </th>
	   </tr>
	   <tr>
	     <td>名稱 </td>
	     <td>叢集的名稱。</td>
	   </tr>
	   <tr>
	     <td>ESXi 伺服器</td>
	     <td>叢集裡的 ESXi 伺服器數目。</td>
	   </tr>
	   <tr>
	      <td>CPU </td>
	      <td>叢集裡的 ESXi 伺服器的 CPU 規格。</td>
	   </tr>
	   <tr>
	      <td>有效儲存空間</td>
	      <td>叢集中的 ESXi 伺服器的磁碟容量總計。</td>
	   </tr>
	   <tr>
	      <td>記憶體</td>
	      <td>叢集裡的 ESXi 伺服器的記憶體大小總計。</td>
	   </tr>
	   <tr>
	      <td>資料中心位置</td>
	      <td>管理叢集所在的資料中心。它是與實例的資料中心位置相同。</td>
	   </tr>
		 <tr>
		   <td>Pod </td>
			 <td>在其中建立叢集的 Pod。</td>
		 </tr>
		 <tr>
		  <td>狀態</td>
			<td>叢集的狀態。狀態可以具有下列其中一個值：
     <ul><li>正在起始設定：正在建立及配置叢集。</li><li>正在修改：正在修改叢集。</li><li>備妥使用：叢集已備妥可供使用。</li></ul></td>
		 </tr>
		 <tr>
		  <td>動作</td>
			<td>按一下**刪除**圖示，以刪除叢集。</td>
		 </tr>
	 </table>

3. 按一下叢集名稱以檢視其 ESXi 伺服器詳細資料。

表 6. NetApp ONTAP Select 叢集的 ESXi 伺服器詳細資料

|項目        |說明       |  
|:------------|:----------------- |
|名稱 |ESXi 伺服器的名稱格式為 `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中：<br><br>`host_prefix` 是主機名稱字首、`n` 是伺服器的序列、`subdomain_label` 是子網域標籤，而 `root_domain` 是根網域名稱。|
|版本|ESXi 伺服器的版本。|
|認證|用來存取 ESXi 伺服器的使用者名稱和密碼。|
|專用 IP |ESXi 伺服器的專用 IP 位址。|
|狀態|ESXi 伺服器的狀態，可以是下列其中一個值：<ul><li>作用中：ESXi 伺服器已備妥可供使用。</li><li>正在刪除：正在刪除 ESXi 伺服器。</li></ul> |

## 下一步
{: #np_viewinginstances-next}

從 {{site.data.keyword.vmwaresolutions_short}} 主控台、VMware vSphere Web Client 或 NetApp 主控台管理實例。

您必須先登入 {{site.data.keyword.CloudDataCent_notm}} 的 VPN 入口網站，才能在實例摘要頁面上按一下 **vCenter 主控台**，以移至 vSphere Web Client 並開始管理 ESXi 伺服器。將游標移至 **vCenter 主控台**按鈕上方，並遵循指示以確保您符合所有需求，並在存取 vSphere Web Client 之前完成必要的步驟。
{:important}

如需協助您完成登入指示的相關資訊，請檢閱下列主題：

*  如需存取 vSphere Web Client 之前的需求及必要步驟，請參閱[連接至 vSphere Web Client 時發生逾時](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console)。
*  如需使用 VPN 登入 {{site.data.keyword.cloud_notm}} 基礎架構「專用網路」的存取點清單，請參閱 [VPN 存取](http://www.softlayer.com/vpn-access){:new_window}。
*  如果您在使用 vSphere Web Client 部署 OVF（開放式虛擬化格式）檔案時發生問題，請參閱[使用 vSphere Web Client 部署 OVF 檔案](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_deploy_ovf)。

## 相關鏈結
{: #np_viewinginstances-related}

* [訂購 NetApp ONTAP Select 實例](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)
* [刪除 NetApp ONTAP Select 實例](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_deletinginstance)
* [Attach dedicated storage to NetApp ONTAP Select deployments](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
