---

copyright:

  years:  2019

lastupdated: "2019-07-09"

keywords: about vmware solutions, product overview, benefits

subcollection: vmware-solutions

---
{:external: target="_blank" .external}

# IBM Cloud for VMware Solutions：深入查看
{: #under_the_hood}

## 部署及管理 VMware 虛擬化環境
{: #under_the_hood-deploy}

深入查看 {{site.data.keyword.vmwaresolutions_full}} 架構，而它提供部署和管理 VMware 虛擬化環境的 {{site.data.keyword.cloud_notm}} 供應項目。本指導教學顯示供應項目的元件，讓您可以瞭解它們如何搭配運作以佈建和維護公用雲端中的環境。

## 兩家公司，一個簡化的解決方案
{: #under_the_hood-two-companies}

現在，使用者已經正在將 VMware 虛擬化環境部署至 IBM Public Cloud，不論是他們自己還是利用專業服務的協助。在 2016 年 2 月，[IBM 與 VMware 已發表夥伴關係](https://www-03.ibm.com/press/us/en/pressrelease/49154.wss){:external}，以自動化在 {{site.data.keyword.cloud_notm}} 中部署 VMware 軟體和 VMware 環境的處理程序。此夥伴關係的其中一個初期優勢是可以從 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購各種 VMware 產品部署和授權，稍後再提供 {{site.data.keyword.cloud_notm}} 中的 [VMware Horizon Air](https://www-03.ibm.com/press/us/en/pressrelease/49932.wss){:external}。此外，IBM 也與 VMware 合作，共同產生 IBM Public Cloud 中 [VMware 的標準參照架構及部署命令](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture){:external}。

在 2016 年秋季，IBM 與 VMware 聯合發行 {{site.data.keyword.vmwaresolutions_short}}。這組供應項目以 VMware 虛擬化技術為基礎，包括虛擬化運算 (VMware vSphere)、網路 (VMware NSX)，以及選擇性地包括虛擬化儲存空間 (VMware vSAN)。這些環境通稱為軟體定義資料中心。

{{site.data.keyword.vmwaresolutions_short}} 以 VMware 技術為建置基礎，大幅簡化 IBM Public Cloud 中這些軟體定義資料中心的部署與管理。現在，使用 {{site.data.keyword.vmwaresolutions_short}} 可以自動將部分的標準參照架構部署至 {{site.data.keyword.cloud_notm}}，而不是手動部署。現在，在幾個小時內，可以佈建先前需要數週才能部署及配置的環境。

這項輕鬆的部署可讓您著重於在 VMware 上實作解決方案，而不是建置環境。透過快速處置的環境，您可以建置跨專用雲端及 IBM Public Cloud 的混合式雲端解決方案，以及 IBM Public Cloud 中的雲端原生解決方案。透過結合多個部署，您可以輕鬆將災難回復或高可用性功能新增至解決方案。

現在，讓我們深入查看 {{site.data.keyword.vmwaresolutions_short}} 架構。您可以深入瞭解屬於解決方案的不同元件，並瞭解它們如何一起佈建及管理 {{site.data.keyword.cloud_notm}} 中的軟體定義資料中心。您也將瞭解用於連接至環境的網路拓蹼及數個選項。

## IBM Cloud for VMware Solutions 基本知識

軟體定義資料中心是使用 [{{site.data.keyword.vmwaresolutions_short}} 主控台](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}進行佈建和管理。您可以使用 IBM ID 帳戶登入主控台。

從「VMware 解決方案」型錄中，您可以佈建其中一種虛擬化環境。精選虛擬化解決方案是 *VMware vCenter Server on {{site.data.keyword.cloud_notm}}*，其提供 VMware 的 vSphere Hypervisor、VMware vCenter Server、VMware NSX，以及 VMware vSAN（選用）。您也可以使用更多附加服務來佈建此環境，這些服務提供備份、災難回復、移轉、安全、法規遵循及網路服務。

訂購 vCenter Server 實例之前，您必須在「VMware 解決方案」型錄中配置 {{site.data.keyword.cloud_notm}} 基礎架構 API 金鑰。若要這麼做，請按一下主控台左邊功能表中的[設定](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings){:external}鏈結，然後在系統提示您輸入 {{site.data.keyword.cloud_notm}} 基礎架構認證時輸入您的使用者名稱和 API 金鑰。系統會驗證 API 金鑰及帳戶是否具有適當的許可權及設定可以部署實例。

訂購 vCenter Server 實例時，請先選擇其名稱及 VMware vSphere 版本。所有 VMware 實例都已與 Microsoft Active Directory 網域控制站一起部署，而且用於單一登入，您必須將實例指定為主要或次要站台。主要實例是您單一登入網域中的第一個或唯一的實例。您可以部署更多的次要實例，並將它們關聯至現有主要實例的相同單一登入網域。接下來，您選擇要攜帶您自己的 VMware 授權，還是要從 {{site.data.keyword.cloud_notm}} 租借的授權版本。最後，您選擇實例的 {{site.data.keyword.cloud_notm}} 地區和資料中心，以及叢集中主機的 CPU 和記憶體特徵。

在訂單頁面的下一個部分中，輸入實例的儲存空間及網路特徵。您可以為叢集選擇 SAN 或 NFS 儲存空間，以及可以選擇 vSAN 快閃記憶體磁碟及 vSAN 授權版本的大小和數目，或是 NFS 儲存空間磁區的大小與計數和效能。對於網路，您可以選擇主機的主機名稱字首，以及叢集的子網域和網域。您可以選擇將 Active Directory 控制器部署為單一 {{site.data.keyword.cloud_notm}} 虛擬伺服器實例 (VSI)。或者，您可以將這些控制器部署為叢集內的兩部虛擬機器 (VM)（針對這些 VM，您需要提供授權及啟動）。

在 vCenter Server 訂單頁面底端，您可以選取可針對 VMware 實例所部署的各種附加服務，並向您的 {{site.data.keyword.cloud_notm}} 帳戶收費。部分服務需要您指定為訂單表單一部分的額外配置。

訂單表單會根據您的選擇來計算和顯示價格預估值。在下訂單之前，您有機會可以檢閱此預估值以及各種條款。

### 部署選項
{: #under_the_hood-deploy-options}

vCenter Server 訂單表格會呈現實例的各種 CPU、記憶體及儲存空間選項。新的選項會定期提供，因此如需最新的可用性資訊，請檢查 {{site.data.keyword.cloud_notm}} 型錄。

{{site.data.keyword.cloud_notm}} 使用三個 VLAN 來部署 vCenter 伺服器實例：一個公用及兩個專用。公用 VLAN 連接至雙 10 GbE 介面，並大部分保留供您自行決定用於您自己工作負載部署的公用連線功能或通道作業。不過，在部署時，會在公用 VLAN 上部署 NSX Edge Services Gateway 配對，以容許部分附加服務連接至公用網路以進行授權及計費。專用 VLAN 連接至個別的雙 10 GbE 介面：第一個專用 VLAN 用於管理通訊及 NSX VTEP，第二個則用於 vMotion 及 NFS 儲存空間資料流量。

VMware 實例可以佈建於 35 個不同的 {{site.data.keyword.CloudDataCents_notm}} 中。{{site.data.keyword.cloud_notm}} 有時會佈建新的資料中心。如需可用位置的最新清單，請檢查 {{site.data.keyword.cloud_notm}} 型錄。

### 實例部署
{: #under_the_hood-inst-deploy}

當您訂購新的 VMware vCenter 實例時，可以選擇實例位置及規格。{{site.data.keyword.vmwaresolutions_short}} 接著會使用您先前選取的 {{site.data.keyword.cloud_notm}} 使用者名稱及 API 金鑰，來編排整個訂購、安裝及配置虛擬化環境的處理程序。包括：

1. 訂購 VLAN 及子網路來連接網路。
2. 訂購已安裝 vSphere Hypervisor 的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}。
3. 部署與配置具有內嵌 Platform Services Controller 的 VMware vCenter Server、VMware NSX Manager、Controller 及 Edge Services Gateway。
4. 訂購及配置叢集儲存空間，包括 VMware vSAN 或「{{site.data.keyword.cloud_notm}} 耐久性」儲存空間。
5. 部署稱為 IBM CloudDriver 的 IBM 管理元件。
6. 部署及配置您為實例選取的任何附加服務。
7. 驗證環境的安裝及配置。

您可以選取要佈建實例的 {{site.data.keyword.CloudDataCent_notm}}。如果硬體可在您選取的 {{site.data.keyword.CloudDataCent_notm}} 中使用，則實例佈建處理程序通常會少於 24 小時。

佈建實例之後，如果您是透過 VPN 連接至 {{site.data.keyword.cloud_notm}} 帳戶，則可以直接從工作站 Web 瀏覽器連接至 vCenter 伺服器。

實例元件一般是透過主機名稱進行存取，而非 IP 位址。若要連接至 vCenter 並向 vCenter 進行鑑別，您應該將 vCenter 及 Platform Services Controller (PSC) 主機名稱新增至工作站的 hosts 檔，確定工作站可以解析它，如清單 1 中所示。您可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台中於您實例的**摘要**標籤上找到主機名稱及 IP 位址。您可能也想要將 vSphere 主機的主機名稱及 IP 位址新增至 hosts 檔。

*清單 1. Hosts 檔*

<pre># Dallas site vCenter and Platform Services Controller (PSC)
10.208.85.196  vcenter-dallas.dallas.example.com
# 達拉斯站台主機
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com</pre>

部署實例之後，即可從主控台進行管理。管理功能包括執行下列每項作業的能力：

* 從叢集中部署及移除節點
* 在相同的資料中心和 Pod 或在替代資料中心和 Pod 中，部署及移除其他叢集
* 部署及移除實例的附加服務
* 升級實例的特定授權版本

{{site.data.keyword.vmwaresolutions_short}} 主控台提供每個 vCenter Server 實例的詳細視圖。對於每個實例，**摘要**標籤都會包括 vCenter 主控台的鏈結，以及實例和管理元件的其他詳細資料。**基礎架構**標籤顯示實例之叢集、主機、儲存空間及網路的詳細資料，並可讓您新增或移除叢集、主機及儲存空間。在**更新及修補程式**標籤上，您可以升級特定授權版本。在**服務**標籤上，您可以檢視及管理針對實例所部署的附加服務。**部署歷程**標籤顯示您實例上所執行之所有動作的歷程。

## IBM Cloud for VMware Solutions 元件
{: #under_the_hood-comp}

有許多不同的元件會搭配運作，以佈建及管理環境。這些元件大部分都會部署至 {{site.data.keyword.cloud_notm}} 帳戶。因為解決方案取決於所有這些搭配運作的元件，所以您不應該從 {{site.data.keyword.cloud_notm}} 帳戶修改或取消任何這些元件。移除執行中實例的正確方式是使用主控台，而不是取消個別元件。

雖然這是整合式虛擬化環境，但各種虛擬化元件（例如 VMware 授權）、基礎架構元件（裸機伺服器、VLAN、子網路和儲存空間）及管理元件的成本，都會在您從 {{site.data.keyword.cloud_notm}} 收到的帳單中逐項說明。

### IBM Cloud for VMware Solutions 主控台
{: #under_the_hood-console}

您可以登入 [{{site.data.keyword.vmwaresolutions_short}} 主控台](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}來建立和管理實例。解決方案的這個部分負責起始訂購及佈建環境，也負責環境的進行中管理。您部署的實例會使用 {{site.data.keyword.cloud_notm}} Private 網路，與主控台進行通訊。

### IBM CloudBuilder 元件
{: #under_the_hood-ibm-cb}

當您佈建新的實例時，主控台會將暫時虛擬伺服器實例 (VSI) 部署至您的 {{site.data.keyword.cloud_notm}} 帳戶。此虛擬伺服器稱為 IBM CloudBuilder。它會執行實例的所有元件的安裝與配置，以及環境的驗證。佈建完成之後，即會刪除 CloudBuilder。

### IBM CloudDriver 元件
{: #under_the_hood-ibm-cd}

與 CloudBuilder 類似，IBM CloudDriver 是部署至 {{site.data.keyword.cloud_notm}} 帳戶的暫時虛擬伺服器實例 (VSI)，可對您的實例執行後續的作業。請視需要部署它，以配置或移除實例中的主機、叢集、儲存空間或服務。

### VMware 元件
{: #under_the_hood-vmware-comp}

對於所有實例，vSphere Hypervisor 都是安裝在裸機伺服器上。{{site.data.keyword.cloud_notm}} 接著會將一個具有整合式 Platform Services Controller (PSC) 的 vCenter Server Appliance、一個 NSX Manager、三個 NSX Controller，以及兩個 NSX Edge Services Gateway 配對部署至 VMware 管理叢集。

### 其他元件
{: #under_the_hood-add-comp}

根據您的選擇，會部署一個 Microsoft Windows VSI 或同時部署兩個 Microsoft Windows VM，或者將其部署至叢集，以作為管理元件的 Active Directory 伺服器。您可以選擇性地新增自己的 Active Directory 伺服器，作為管理存取權的其他身分來源。

不論您選擇如何為您自己的工作負載提供企業永續，{{site.data.keyword.cloud_notm}} 都強烈建議您備份實例的管理元件。{{site.data.keyword.vmwaresolutions_short}} 主控台可讓您將整合式 IBM Spectrum Protect Plus 備份伺服器或 Veeam Backup & Replication 備份伺服器與實例一起部署。您可以使用這些備份服務作為實例的[完整備份解決方案](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup)一部分。

### 授權
{: #under_the_hood-licenses}

{{site.data.keyword.cloud_notm}} 提供數個 VMware 授權（例如 vCenter Server 及 NSX），以安裝至實例，並向 {{site.data.keyword.cloud_notm}} 帳戶收費。

## IBM Cloud for VMware Solutions 網路架構
{: #under_the_hood-network}

vCenter Server 實例會連接至公用 VLAN，以與已部署的工作負載搭配使用。公用 VLAN 大部分保留供您自行決定，但 NSX Edge Services Gateway 配對會連接至公用 VLAN，容許特定附加服務進行出埠通訊來進行授權及計費。您可以在不使用公用網路的情況下部署實例，在此情況下，並不支援所有附加服務，而且您可能需要提供 Web Proxy 才能啟用特定附加服務。

vCenter Server 實例具有兩個專用 VLAN，它們會一起成為 Hypervisor 專用網路介面的主幹。第一個專用 VLAN 用於管理連線功能（例如與 Hypervisor 的 vCenter 通訊），以及透過 NSX 來通道處理已部署工作負載的所有 VXLAN 資料流量。第二個專用 VLAN 用於 vMotion，並用於儲存空間資料流量。儲存空間資料流量可以是 NFS 或 vSAN 通訊協定。

{{site.data.keyword.cloud_notm}} 在這些專用 VLAN 上提供特定其他服務。Active Directory 伺服器會透過專用管理 VLAN 以與 {{site.data.keyword.cloud_notm}} DNS 伺服器進行通訊。主機及其他元件會透過專用管理 VLAN 以與 {{site.data.keyword.cloud_notm}} NTP 伺服器進行通訊。IBM CloudBuilder 及 CloudDriver 也透過此 VLAN 以與 {{site.data.keyword.vmwaresolutions_short}} 主控台進行通訊。主機會透過專用儲存空間 VLAN 連接至「{{site.data.keyword.cloud_notm}} 耐久性」儲存空間。

### 連接至實例
{: #under_the_hood-connect-inst}

有許多選項可以用來連接至實例。您可以使用 [{{site.data.keyword.cloud_notm}} VPN](https://www.softlayer.com/VPN-Access){:external}，直接連接至實例中的專用 IP 位址（例如，vCenter)。您也可以訂購帳戶的 [{{site.data.keyword.cloud_notm}} 網路應用裝置](https://www.ibm.com/cloud/network-appliances){:external}及 [{{site.data.keyword.cloud_notm}} 硬體或虛擬防火牆](https://www.ibm.com/cloud/network-security)（例如 FortiGate 及 vSRX）。{{site.data.keyword.cloud_notm}} 也提供 {{site.data.keyword.cloud_notm}} 帳戶中網路與 VLAN 之間的[直接鏈結](https://www.ibm.com/cloud/direct-link){:external}。

若要存取已部署的 VM，您可以將公用 IP 位址直接套用至 VM。不過，您也可以使用 {{site.data.keyword.cloud_notm}} 網路應用裝置和防火牆功能，以利用 NAT 和防火牆，為 VM 設定更安全的公用存取權。您也可以部署 NSX Edge 伺服器，並使用這些伺服器來設定 VM 的 VPN 或 NAT 連線功能。

## 總結
{: #under_the_hood-conclusion}

在本指導教學中，您已瞭解 {{site.data.keyword.vmwaresolutions_short}} 的基本功能，用於部署及管理公用雲端中的標準化 VMware 虛擬化環境。因為您可以使用比以前更快的方式來佈建這些環境，所以可以專注於在其上部署應用程式和解決方案，以及將這些雲端連接在一起，以解決災難回復或高可用性。

我們已探索部署至 {{site.data.keyword.cloud_notm}} 帳戶的各種元件，而這些元件出現在您的 {{site.data.keyword.cloud_notm}} 計費對帳單上，並搭配運作以保持環境的執行。最後，我們考量使用解決方案的網路架構，以及一些選項來建立環境的連線功能，方法是使用各種安全連線選項來保持通訊專用，或使用各種選項來進行公用網際網路連線。

既然，您已準備好需要知道的一切可開始使用，請立即接著在 {{site.data.keyword.cloud_notm}} 上部署 VMware 虛擬化環境！

## 相關鏈結
{: #under_the_hood-related}

* [開始使用](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [VMware Solutions 架構](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
