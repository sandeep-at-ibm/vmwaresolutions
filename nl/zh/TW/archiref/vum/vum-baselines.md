---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# 建立基準線並連接至庫存物件
{: #vum-baselines}

基準線具有一個以上修補程式、延伸規格、服務套件、錯誤修正程式或升級的集合，而且可以分類為修補程式、延伸規格或升級基準線。基準線群組是從現有基準線組合而成。主機基準線群組可以具有單一升級基準線，以及各種修補程式和延伸規格基準線。虛擬機器及虛擬應用裝置基準線群組最多可以具有三個升級基準線：一個 VMware Tools 升級基準線、一個虛擬機器硬體升級基準線，以及一個虛擬應用裝置升級基準線。

VUM 包括您無法編輯或刪除的預先定義基準線。您可以使用預先定義的基準線，或建立符合您準則的修補程式、延伸規格及升級基準線。您建立的自訂基準線以及預先定義的基準線可以結合至基準線群組。

VUM 包括的預設基準線可以用來掃描下列任何裝置，以判斷是否將環境中的主機更新為最新的修補程式，或是否將虛擬應用裝置及虛擬機器升級至最新版本：
* 任何虛擬機器
* 任何虛擬應用裝置
* 任何主機

這些預先定義的基準線如下：
* **重要主機修補程式（預先定義）** - 檢查 ESXi 主機符合所有重要修補程式的標準。
* **非重要主機修補程式（預先定義）** - 檢查 ESXi 主機符合所有選用修補程式的標準。
* **VMware Tools 升級以符合主機（預先定義）** - 檢查虛擬機器符合主機上最新 VMware Tools 版本的標準。在執行 ESXi 5.5.x 及更新版本的主機上，Update Manager 支援升級虛擬機器的 VMware Tools。
* **VM Hardware 升級以符合主機（預先定義）** - 檢查虛擬機器的虛擬硬體符合主機所支援之最新版本的標準。在執行 ESXi 6.5 的主機上，Update Manager 支援升級至虛擬硬體版本 vmx-13。
* **VA 升級至最新（預先定義）** - 檢查虛擬應用裝置符合最新發行之虛擬應用裝置版本的標準。

若要使用基準線及基準線群組，您必須將它們連接至選取的庫存物件（例如容器物件、虛擬機器、虛擬應用裝置或主機）。雖然您可以將基準線及基準線群組連接至個別物件，但更有效率的方法是將它們連接至容器物件（例如資料夾、vApp、叢集或資料中心）。在此步驟中，我們會根據叢集中的主機來使用預先定義的基準線。

1. 使用 vSphere Web Client，移至**首頁** > **主機及叢集**。
2. 按一下您要掃描的叢集物件。
3. 按一下**連接基準線**，選取兩個預先定義的「修補程式基準線」，然後按一下**確定**。

## 相關鏈結
{: #vum-baselines-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware)（示範）
