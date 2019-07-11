---

copyright:

  years: 2016, 2019

lastupdated: "2019-05-31"

keywords: IBM Cloud for VMware Solutions, getting started, vmware solutions offerings, add-on services for vmwaresolutions, vmwaresolutions use cases

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# 入門指導教學
{: #getting-started}

在此入門指導教學中，我們將逐步引導您完成訂購實例和其一些附加程式服務的處理程序。
{:shortdesc}

## 開始之前
{: #getting-started-prereqs}

在您開始使用 {{site.data.keyword.vmwaresolutions_full}} 之前，請檢閱瀏覽器需求、使用者帳戶、部署選項及附加程式服務的下列重要資訊。

### 瀏覽器需求
{: #getting-started-browser-req}

以下是支援的瀏覽器：
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

不支援 Microsoft Internet Explorer。
{:note}

為了在 {{site.data.keyword.vmwaresolutions_short}} 主控台上獲得最佳檢視及運作，請將螢幕解析度設為至少 1024 px（寬）x 500 px（高）。

### 使用者帳戶
{: #getting-started-user-accts}

您需要 {{site.data.keyword.cloud_notm}} 帳戶及 {{site.data.keyword.cloud_notm}} 基礎架構帳戶。這些帳戶必須符合特定需求。

   表 1. 必要使用者帳戶
   <table>
   <tr>
      <th>帳戶</th>
      <th>說明       </th>
   </tr>
   <tr>
      <td>IBM ID</td>
      <td>使用 **IBM ID**，您可以有所使用之所有 IBM 產品及服務的單一登入使用者名稱（包括 {{site.data.keyword.cloud_notm}}）。在 {{site.data.keyword.cloud_notm}} 型錄中，{{site.data.keyword.vmwaresolutions_short}} 提供作為基礎架構解決方案。若要存取 {{site.data.keyword.vmwaresolutions_short}} 主控台，您必須有 **IBM ID**。<br><br>若要使用 **IBM ID** 來登入 {{site.data.keyword.vmwaresolutions_short}} 主控台，您必須將 **IBM ID** 與 {{site.data.keyword.cloud_notm}} 帳戶相關聯。當您第一次登入主控台時，引導您將現有 **IBM ID** 與 {{site.data.keyword.cloud_notm}} 帳戶相關聯，或註冊新的 {{site.data.keyword.cloud_notm}} 帳戶。新的 {{site.data.keyword.cloud_notm}} 帳戶會自動與 **IBM ID** 相關聯。您只需要執行此處理程序一次。<br><br>如果您在使 **IBMid** 與 {{site.data.keyword.cloud_notm}} 帳戶相關聯時發生問題，請參閱[存取 {{site.data.keyword.cloud_notm}} 的疑難排解](/docs/account?topic=account-accessing#accessing)。</td>
   </tr>
   <tr>
      <td>IBM Cloud 帳戶</td>
      <td>若要訂購及使用 {{site.data.keyword.cloud_notm}} 服務，需要 {{site.data.keyword.cloud_notm}} 帳戶。計費資訊與 {{site.data.keyword.cloud_notm}} 帳戶相關聯。實體及虛擬基礎架構以及所產生授權的成本會記入您的 {{site.data.keyword.cloud_notm}} 帳戶。</td>
   </tr>
   <tr>
      <td>IBM Cloud 基礎架構帳戶</td>
      <td>如需 {{site.data.keyword.cloud_notm}} 基礎架構帳戶之需求的相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 基礎架構帳戶的需求](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)。<br><br>您可以鏈結 {{site.data.keyword.cloud_notm}} 基礎架構帳戶與 {{site.data.keyword.cloud_notm}} 帳戶，以使用結合的基礎架構即服務 (IaaS) 及平台即服務 (PaaS) 資源。然後，您就可以從單一登入存取 IaaS 資源及 PaaS 資源。鏈結您的帳戶也會提供您使用之所有 PaaS 及 IaaS 資源的單一發票。<ul><li>如果您沒有 {{site.data.keyword.cloud_notm}} 基礎架構帳戶，請遵循[註冊 IBM Cloud 基礎架構帳戶](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts#signing_required_accounts-infra)中的程序來要求帳戶，然後遵循[切換至 IBM ID 並鏈結帳戶](/docs/account?topic=account-unifyingaccounts#unifyingaccounts)中的程序，將 {{site.data.keyword.cloud_notm}} 基礎架構帳戶鏈結至 {{site.data.keyword.cloud_notm}} 帳戶。</li><li>如果您有 {{site.data.keyword.cloud_notm}} 基礎架構帳戶，則可以遵循[切換至 IBM ID 並鏈結帳戶](/docs/account?topic=account-unifyingaccounts#unifyingaccounts)中的程序，將它鏈結至 {{site.data.keyword.cloud_notm}} 帳戶。</li></ul></td>
   </tr>
   </table>

### 部署供應項目
{: #getting-started-depl-offerings}

請檢閱及選擇部署供應項目。

  表 2. 部署供應項目
  <table>
    <tr>
       <th>部署供應項目</th>
       <th>說明       </th>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)</td>
       <td>使用 vCenter Server 供應項目，您可以使用自訂運算、儲存空間及網路資源來部署 VMware 虛擬環境，以充分配合您的商業需要。</td>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)</td>
       <td>vCenter Server with Hybridity 供應項目是一種受管理的專用雲端，有助於快速且輕鬆地將內部部署基礎架構延伸到雲端。VMware 環境根據 IBM 提供的「VMware 軟體定義資料中心」授權，並包括 VMware Hybrid Cloud Extension (HCX)。使用 HCX，您可以透過內部部署方式安全地連接 vSphere 5.0+ 環境與 {{site.data.keyword.cloud_notm}} 站台，來獲得無縫的基礎架構混合及實際應用程式行動性。</td>
    </tr>
    <tr>
       <td>[VMware vSphere on IBM Cloud](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)</td>
       <td>vSphere on {{site.data.keyword.cloud_notm}} 供應項目提供可自訂的虛擬化服務，結合 VMware 相容的 {{site.data.keyword.baremetal_short}}、硬體元件及授權，來建置您自己的 IBM 代管 VMware 環境。</td>
    </tr>
    <tr>
       <td>[NetApp  ONTAP  Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)</td>
       <td>NetApp ONTAP Select 供應項目容許您部署軟體定義的儲存空間叢集，以根據 NetApp ONTAP Select 來處理您對於專用及高可用性儲存空間應用裝置的需要。</td>
    </tr>
  </table>

### 附加服務               
{: #getting-started-add-on-services}

請檢閱及選擇部署供應項目的附加程式服務。

  表 3. 部署供應項目的可用附加程式服務
  <table>
    <tr>
       <th> 服務名稱                                                                               </th>
       <th>說明       </th>
    </tr>
    <tr>
       <td>[F5 on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)</td>
       <td>F5 on {{site.data.keyword.cloud_notm}} 服務 (F5 BIG-IP® Virtual Edition) 提供區域和廣域範圍的智慧型 L4-L7 負載平衡及資料流量管理服務、健全網路及 Web 應用程式防火牆保護，以及安全和聯合應用程式存取。</td>
    </tr>
    <tr>
       <td>[FortiGate Security Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)</td>
       <td>FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務會以高可用性模式部署一組 FortiGate Security Appliance (FSA) 300 系列裝置，以提供防火牆、遞送、NAT 及 VPN 服務，來保護實例之公用 VLAN 上的所有伺服器及虛擬機器。</td>
    </tr>
    <tr>
       <td>[FortiGate Virtual Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)</td>
       <td>FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務會將一組 FortiGate Virtual Appliance 部署到您的環境，以協助您在虛擬基礎架構內實作重要安全控制來降低風險。</td>
    </tr>
    <tr>
       <td>[HyTrust CloudControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)</td>
       <td>HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務會施行並控制是否符合安全標準，並提供詳細角色型存取控制 (RBAC)、核准及審核功能。與 HyTrust DataControl 結合時，此服務可確保虛擬機器及工作負載資料不會離開 {{site.data.keyword.CloudDataCent_notm}} 內的特定地區、叢集或 ESXi 伺服器。</td>
    </tr>
    <tr>
       <td>[HyTrust DataControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)</td>
       <td>HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務提供具有整合式金鑰管理的高度加密，在工作負載的整個生命週期內保護其安全。此服務可以提供作業系統層次及資料層次的加密，表示可以加密及解密工作負載內的任何目錄、資料夾或檔案。</td>
    </tr>
    <tr>
       <td>[HyTrust KeyControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)</td>
       <td>HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服務藉由自動化及簡化加密金鑰的生命週期，來簡化加密工作負載的管理。服務可以使用符合 FIPS 140-2 標準的加密，輕鬆地大規模管理加密金鑰。</td>
    </tr>
    <tr>
       <td>[IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)</td>
       <td>{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} 服務為您在 {{site.data.keyword.cloud_notm}} 上的 VMware 環境帶來微服務及容器的功能。使用此服務，您可以將熟悉的相同 VMware 與 {{site.data.keyword.cloud_notm}} Private 作業模型和工具，從內部部署延伸到 {{site.data.keyword.cloud_notm}}。</td>
    </tr>
    <tr>
       <td>[IBM Spectrum Protect Plus on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)</td>
       <td>IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服務提供有效且可調式解決方案，以進行虛擬環境的資料保護、資料重複使用及資料回復。您可以將服務當成獨立式解決方案來實作，或與 IBM Spectrum Protect 環境整合以卸載副本，進行長期儲存及資料控管。</td>
    </tr>
    <tr>
       <td>[KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)</td>
       <td>KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務提供高可性服務，以管理 {{site.data.keyword.cloud_notm}} 中 VMware 所使用的加密金鑰。此服務提供運行環境功能，以容許客戶建立、擷取、啟動、撤銷及毀損加密金鑰。同時提供管理功能來維護用戶端認證與加密金鑰之間的關聯。</td>
    </tr>
    <tr>
       <td>[Veeam on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)</td>
       <td>Veeam on {{site.data.keyword.cloud_notm}} 服務與 VMware Hypervisor 無縫整合，以協助您的企業達到高可用性。此服務可以提供您應用程式及資料的回復點及時間目標。完成配置之後，可以在 15 分鐘以內提供回復點及時間目標。使用此服務，即可從 Veeam 主控台直接控制基礎架構之所有虛擬機器的備份及還原。</td>
    </tr>
    <tr>
       <td>[VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)</td>
       <td>HCX on {{site.data.keyword.cloud_notm}} 服務可以將內部部署資料中心的網路無縫地擴充至 {{site.data.keyword.cloud_notm}}，這容許將虛擬機器 (VM) 移轉至 {{site.data.keyword.cloud_notm}} 或從其移轉，而不需要進行任何轉換或變更。</td>
    </tr>
    <tr>
       <td>[Zerto on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)</td>
       <td>Zerto on {{site.data.keyword.cloud_notm}} 服務提供抄寫及災難回復功能，可整合至部署供應項目以保護及回復 {{site.data.keyword.cloud_notm}} 上 VMware 虛擬環境中的資料。</td>
    </tr>
   </table>

## 步驟 1：存取 IBM Cloud for VMware Solutions 主控台
{: #getting-started-step1}

{{site.data.keyword.vmwaresolutions_short}} 主控台是您訂購及管理部署的介面。在主控台中，每一個部署都會當成實例進行管理。主控台是與 {{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站分開的獨立式使用者介面。

若要存取 {{site.data.keyword.vmwaresolutions_short}} 主控台，請執行下列動作：
1. 移至 https://cloud.ibm.com/infrastructure/vmware-solutions/console。
2. 使用您的 **IBM ID** 登入主控台。

## 步驟 2：配置使用者帳戶及設定
{: #getting-started-step2}

在您訂購實例之前，必須在主控台的**設定**頁面上輸入 {{site.data.keyword.cloud_notm}} 基礎架構帳戶的使用者名稱及 API 金鑰。

如需如何配置使用者帳戶及設定的相關資訊，請參閱[管理使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。

## 步驟 3：訂購實例
{: #getting-started-step3}

在您決定部署供應項目（這當成主控台中的實例來管理）之後，請開始訂購處理程序。

如需如何訂購實例的相關資訊，請根據您選取的部署供應項目來參閱下列主題：
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [訂購 vCenter Server with Hybridity Bundle 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [訂購新的 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [訂購 NetApp ONTAP Select 實例](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## 步驟 4：檢視實例
{: #getting-started-step4}

在您於**步驟 3** 下實例訂單之後，會自動啟動實例的部署。您可以檢視實例詳細資料，以追蹤部署的狀態。完成實例部署時，您也可以在實例詳細資料頁面上檢視實例及其附加程式服務的摘要和詳細資訊。

如需如何檢視所訂購實例的相關資訊，請參閱下列主題：
* [檢視 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [檢視 vCenter Server with Hybridity Bundle 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [檢視 NetApp ONTAP Select 實例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-np_viewinginstances#np_viewinginstances)
