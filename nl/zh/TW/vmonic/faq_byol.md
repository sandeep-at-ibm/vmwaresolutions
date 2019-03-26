---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# 授權及 BYOL 的常見問題
{: #faq_byol}

尋找授權相關常見問題的回答，其中包括 {{site.data.keyword.vmwaresolutions_full}} 的自帶授權 (BYOL) 特性。

## 何謂 BYOL？
{: #faq_byol-def}
{: faq}

「自帶授權」或 BYOL 是 1.8 版及更新版本中的 VMware Cloud Foundation 實例以及 2.0 版及更新版本中的 VMware vCenter Server 和 VMware vSphere 叢集可用的特性。使用 BYOL，您可以對下列一個以上的 VMware 軟體元件使用您自己的 VMware 授權：
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

如果您選擇要對 VMware 元件使用您自己的授權，並為它提供有效的授權碼，則不會向 IBM 訂購此元件的授權，且不會向您的 {{site.data.keyword.cloud_notm}} 基礎架構帳戶收取此元件的每月授權費用。

BYOL 特性不適用於「事業夥伴」使用者。
{:note}

## 哪裡可以管理透過 VMware vSphere on IBM Cloud 訂購的授權和元件？
{: #faq_byol-license-mgmt}
{: faq}

在送出為 VMware vSphere on {{site.data.keyword.cloud_notm}} 建立新叢集的訂單之後，會遞送 VMware 授權、ESXi 伺服器及其他網路元件，並可從 {{site.data.keyword.slportal}} 進行管理。

部署之後，請移至 {{site.data.keyword.vmwaresolutions_short}} 主控台，以使用已儲存的配置來擴充新叢集。如需相關資訊，請參閱[擴充現有 vSphere 叢集](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)。

## BYOL 需要哪些授權版本及 CPU？
{: #faq_byol-license-cpu-reqs}
{: faq}

下列需求適用於 BYOL 的授權版本。

### vCenter Server 實例的 BYOL 需求
{: #faq_byol-vcs-reqs}

表 1. vCenter Server 實例的授權版本及 CPU 最低需求

  |VMware 元件|需要的授權版本|需要的最低 CPU
  |:-------------  |:-------------  |:-------|
  |vCenter Server |Standard                |N/A |
  |vSphere        |Enterprise Plus |8 CPU |
  |vSAN           |Advanced 或 Enterprise |8 CPU |
  |NSX            |Standard、Advanced 或 Enterprise |8 CPU |

### Cloud Foundation 實例的 BYOL 需求
{: #faq_byol-cf-reqs}

表 2. Cloud Foundation 實例的授權版本及 CPU 最低需求

  |VMware 元件|需要的授權版本|需要的最低 CPU
  |:-------------  |:-------------  |:-------|
  |vCenter Server |Standard |N/A |
  |vSphere        |Enterprise Plus |8 CPU |
  |vSAN           |Advanced 或 Enterprise |8 CPU |
  |NSX            |Enterprise |8 CPU |

## 如果我提供的授權碼不正確會發生生什麼情況？
{: #faq_byol-incorrect-license}
{: faq}

您提供的所有授權碼都會經過驗證，以確保它們對於對應的 VMware 元件是正確的，而且符合 VMware 元件的最低版本和 CPU 需求。如果任何授權碼驗證失敗，您會得到通知，且無法繼續進行實例訂購。

## 我可以提供超過 8 個 CPU 的授權碼嗎？
{: #faq_byol-license-key}
{: faq}

是的。對於每一個 VMware 元件，需要每個 CPU 一份授權。目前，所有 vCenter Server 和 Cloud Foundation 伺服器都有兩個 CPU。因此，每部伺服器都需要兩份授權。建議您提供的授權碼能支援基礎實例，以及您未來要新增至該實例的任何擴充節點。

## 如果使用 BYOL 特性，是否可以提供 SDDC Manager 授權？
{: #faq_byol-sddc}
{: faq}

否。我們與 VMware 的合約規定我們必須接受客戶的實際授權碼。雖然 Cloud Foundation 部署包括 SDDC Manager 授權，但我們無法接受 SDDC Manager 授權碼檔案並驗證其 BYOL。因此，IBM 會針對所有實例的 SDDC Manager 授權收費。SDDC Manager 授權代表 Cloud Foundation 實例整體授權費用中的一小部分。

## 我可以對某些 VMware 元件使用 BYOL 特性，並對某些元件購買每月授權嗎？
{: #faq_byol-mthly-license}
{: faq}

是的。您可以針對四個 VMware 元件的任何組合使用 BYOL 特性或購買授權。當您訂購實例時，{{site.data.keyword.vmwaresolutions_short}} 主控台會直接讓您選取授權選項。您在起始實例訂單時的授權選項在該實例的生命期限內皆適用。

## 針對特定 VMware 元件，我可以對部分授權使用 BYOL，並向 IBM 購買其餘授權嗎？
{: #faq_byol-purchase}
{: faq}

是的。如果您已在建立叢集時選取特定 VMware 元件的 BYOL，則會有下列選項：
* 輸入新的 BYOL 金鑰
* 繼續使用現有 BYOL 金鑰
* 購買 IBM 針對該叢集所提供的授權。

目前，每個叢集只能授權 VMware vSphere Enterprise 及 VMware vSAN。

## 建立叢集時，我可以使用 BYOL 嗎？
{: #faq_byol-cluster}
{: faq}

是的。您可以從現有的 BYOL 授權使用 BYOL，或在建立叢集時輸入新的 BYOL。此外，當您建立叢集時，可以購買 IBM 提供的訂閱授權。

目前，每個叢集只能授權 VMware vSphere Enterprise 及 VMware vSAN。

## 如何管理 BYOL 授權？
{: #faq_byol-mgmt}
{: faq}

您可以在完成實例部署之後使用 VMware vSphere Web Client 來管理 BYOL 授權。

## 當我稍後將其他 ESXi 伺服器新增至實例時，該實例會驗證我的 BYOL 授權是否具有足夠的容量？
{: #faq_byol-add-esxi}
{: faq}

是的。當您將其他 ESXi 伺服器新增至已部署的實例時，會針對指定數目的 ESCi 伺服器自動檢查您的 BYOL 授權容量。如果容量不足，則不會新增 ESXi 伺服器，且您會收到主控台通知。

## 我如何得知具有 BYOL 的叢集上有多少可用的授權容量？
{: #faq_byol-capacity}
{: faq}

若要尋找授權碼中可用的 CPU 數目，請完成下列步驟：
1. 移至**資源**頁面。
2. 找到並按一下實例。
3. 在**基礎架構**標籤上，按一下您要檢查授權容量的叢集。可用的 CPU 數目會列在**使用者提供的授權**表格中。

## 如果我選取 BYOL 授權選項，IBM 是否提供支援？
{: #faq_byol-support}
{: faq}

「IBM 支援中心」會繼續作為您任何實例配置問題的聯絡窗口。不過，如果所報告的問題被判定是關於 BYOL VMware 元件，則會引導您到「VMware 支援中心」。

## 如果我使用 BYOL，為何價格預估清單上會顯示 vSphere 授權費用？有向我收取此費用嗎？
{: #faq_byol-vsphere}
{: faq}

{{site.data.keyword.baremetal_short}} 佈建時已安裝 VMware vSphere，並已包括 vSphere 授權。如果您為 vSphere 選取 BYOL，則在實例部署時會自動起始程序來移除已包括的 vSphere 授權。然後，授權費用將會記入您的 {{site.data.keyword.cloud_notm}} 帳戶。您不需要在此程序中執行任何動作。

## 我是否仍然可以對 BYOL 使用現有的手動程序？
{: #faq_byol-manual-process}
{: faq}

在引進 BYOL 特性時，不建議繼續使用手動程序。如果您要使用 BYOL，請在訂購實例時提供您自己的授權。

## 有針對其他 VMware 產品支援 BYOL 嗎？例如，VMware vRealize Automation、VMware vRealize Operations 或 VMware vRealize Log Insight？
{: #faq_byol-other-support}
{: faq}

不，因為這些 VMware 產品不是實例部署的一部分。除了起始部署之外，可能還會安裝這些 VMware 產品，這需要客戶或其代理人安裝及授權這些產品。

## 我可以訂購 vCenter Server with Hybridity Bundle 的 NFS 儲存空間嗎？
{: #faq_byol-nfs}
{: faq}

對於新部署的實例，僅支援 vSAN 全快閃記憶體儲存空間。vCenter Server with Hybridity Bundle 供應項目包括 vSAN Advanced 或 Enterprise 授權。

如果您的 vCenter Server 實例具有 NFS 儲存空間，則可以將現有實例升級至 vCenter Server with Hybridity Bundle。在升級期間訂購 vSAN Advanced 授權時，您不需要佈建全快閃記憶體 vSAN 叢集。

## 我可以使用 BYOL 與 vCenter Server with Hybridity Bundle 搭配嗎？
{: #faq_byol-hybridity}
{: faq}

您無法將自己的 VMware 授權 (BYOL) 帶到 {{site.data.keyword.cloud_notm}}。vCenter Server with Hybridity Bundle 需要 IBM 提供所有 VMware 授權。

## vCenter Server with Hybridity Bundle 授權與 vCenter Server 授權之間的差異為何？
{: #faq_byol-hybridity-vcs}
{: faq}

vCenter Server 中可用的個別 VMware 授權是根據 CPU 計價。與 IBM 所提供的所有個別 CPU VMware 授權相同，個別 CPU 有 16 個以上核心的所有伺服器在價格方面會有 1.3x 的額外費用（例如，針對「雙重 Intel Xeon Gold 6140」）。

vCenter Server with Hybridity Bundle 是根據核心授權的一組預定 VMware 授權及版本，而不是根據 CPU。因此，這些實例的授權價格不會變更。

## 哪些 IBM 提供的 VMware 授權元件及版本適用於 vCenter Server with Hybridity Bundle？
{: #faq_byol-hybridity-avail}
{: faq}

新的 vCenter Server with Hybridity Bundle 實例，包括 VMware vSphere Enterprise Plus、VMware vCenter Standard、VMware NSX Advanced 或 Enterprise、VMware vSAN Advanced 或 Enterprise，以及 VMware Hybrid Cloud Extension (HCX)。

如果您的 vCenter Server 實例具有 NSX Base 版本，則會在您訂購 vCenter Server with Hybridity Bundle 時自動將您升級至 NSX Advanced。

## 我可以將 vCenter Server with Hybridity Bundle 所含的 NSX Advanced 版本升級至 NSX Enterprise 版本嗎？
{: #faq_byol-nsx-upgrade}
{: faq}

vCenter Server with Hybridity Bundle 包括 NSX Advanced 時，您可以在訂購 vCenter Server with Hybridity Bundle 之後升級至 NSX Enterprise 版本。若要這樣做，請使用 {{site.data.keyword.vmwaresolutions_short}} 主控台之實例詳細資料頁面上的**更新及修補程式**標籤。

## 相關鏈結
{: #faq_byol-related}

* [存取主控台](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
