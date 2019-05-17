---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmware-solutions


---

# 供應項目比較圖表
{: #inst_comp_chart}

請檢閱下列圖表，來瞭解 VMware vCenter Server 實例、VMware vCenter Server with Hybridity Bundle 實例，以及 VMware vSphere 叢集的功能支援的差異。

表 1. vCenter Server、vCenter Server with Hybridity Bundle，以及 vSphere 叢集支援的功能

|功能                          |vCenter Server | vCenter Server with Hybridity |VMware vSphere |
|:--- |:--- |:--- |:--- |
|採用 {{site.data.keyword.IBM}} 進階自動化技術 <sup>1</sup> |是|是|否。自行建置及配置|
|儲存空間選項| vSAN 或 NFS（共用檔案層次儲存空間）| vSAN 或 NFS <sup>2</sup> | vSAN 或 NFS |
|起始叢集裡的 ESXi 伺服器數目| 4 部用於 vSAN，且至少 2 部（建議使用 3 部）用於 NFS |4 |1 部以便擴充現有叢集，4 部用於新的 vSAN 叢集，且至少 3 部用於具有 NFS 的新叢集|
| ESXi 伺服器數目上限 <sup>3</sup> |每個叢集 59 部|每個叢集 59 部|每個叢集 60 部|
|雲端自動化多站台部署| 支援在 2.0 版或更新版本中部署的新實例 |支援           |支援。未包括自動化配置|
|新增 ESXi 伺服器              |支援           |支援           |支援。未包括自動化配置|
|移除 ESXi 伺服器           |支援           |支援           |支援。未包括自動化配置|
|多叢集支援         |數目上限取決於 VMware 大小準則|數目上限取決於 VMware 大小準則|支援。未包括自動化配置|
|用戶端管理 VMware 堆疊的更新及修補 | 用戶端管理的更新：<br/>原生 VMware Tools (VMware Update Manager) | 用戶端管理的更新：<br/>原生 VMware Tools (VMware Update Manager) | 用戶端管理的更新：<br/>原生 VMware Tools (VMware Update Manager) |
|備份及還原            | 手動使用 IBM Spectrum Protect Plus 或 Veeam | 手動使用 IBM Spectrum Protect Plus 或 Veeam | 未包括備份及還原解決方案 |
|軟體定義網路   |NSX Base、Advanced 或 Enterprise |NSX Advanced 或 Enterprise |NSX Standard、Base 或 Enterprise。未包括自動化配置|
|對於 vSphere 及 vSAN 的 BYOL |對每個叢集充分支援   |不支援|支援           |
|對於 vCenter 及 NSX 的 BYOL |對每個實例充分支援|不支援|支援           |
|NSX 授權升級選項           |可從 NSX Base 升級至 Advanced 或 Enterprise，以及從 NSX Advanced 升級至 Enterprise。可以升級至 vCenter Server with Hybridity Bundle。|可從 NSX Advanced 升級至 Enterprise  |無   |
|vSAN 授權版本         |vSAN Advanced 或 Enterprise  |vSAN Advanced 或 Enterprise  |vSAN Advanced 或 Enterprise  |
|附加服務               |支援，不包括 HCX on {{site.data.keyword.cloud_notm}}。可以升級至 vCenter Server with Hybridity Bundle。|支援，包括 HCX on {{site.data.keyword.cloud_notm}}。| 此解決方案的自動化不支援，但您可以啟動及安裝自己的軟體。|

##  附註 
{: #inst_comp_chart-notes}

<sup>1</sup> 根據已驗證的設計並在部署期間驗證。

<sup>2</sup> vSAN 僅適用於新的 vCenter Server with Hybridity 實例和叢集。部署之後，您可以新增 NFS 儲存空間。

<sup>3</sup> 您可以將 vSAN 叢集中的 ESXi 伺服器數目增加到最多 64 個。如需相關資訊，請參閱[關於 ESXi 伺服器的常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi)中的_我可以新增多少部 ESXi 伺服器至叢集？_。

## 相關鏈結
{: #inst_comp_chart-related}

* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [vCenter Server Hybridity 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [VMware vSphere 概觀](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)
* [vCenter Server BOM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [VMware vSphere BOM](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
