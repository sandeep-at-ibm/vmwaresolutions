---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# 處理 Spectre 及 Meltdown 漏洞

若要處理 Spectron 及 Meldown 漏洞，您必須依特定的順序套用許多修補程式。

## 更新韌體

如需關於更新韌體的最新資訊，請參閱[針對最新安全漏洞的安全防護](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)。

## 更新已部署在 2.0 版或更新版本中的實例

來自 2.0 版或更新版本的實例已與 VMware vSphere 6.5 及 VMware vCenter Server 6.5 一起部署。這兩個軟體元件都需要修補。

### 已部署在 2.0 版或更新版本中的 vCenter Server 實例

#### 對於 VMware vSphere 6.5

* 對於您所有新的 2.6 版實例，將部署已套用下列修補程式的 vSphere：ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG 及 ESXi650-201808403-BG。
* 對於 2.5 版之前所部署但升級至 2.5 版的所有現有實例，將使用下列修補程式來更新所有新的叢集及 ESXi 伺服器：ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG 及 ESXi650-201808403-BG。
* 對於所有現有的 ESXi 伺服器，以及對於在升級至 2.5 版之前繼續部署的任何叢集或 ESXi 伺服器，您必須從 [VMware 產品修補程式站台](https://my.vmware.com/group/vmware/patch)套用下列修補程式：ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG 及 ESXi650-201808403-BG。

#### 對於 VMware vCenter Server 6.5

* 對於您所有新的 2.6 版實例，將部署已套用 vCenter 6.5 U2c 積存修補程式的 vCenter Server。
* 對於 2.6 版之前已部署的所有現有實例，您必須從 [VMware 產品修補程式站台](https://my.vmware.com/group/vmware/patch)套用 vCenter 6.5 U2c 修補程式。

### 已部署在 2.0 版或更新版本中的 Cloud Foundation 實例

若要套用 VMware vSphere 6.5 及 VMware vCenter Server 6.5 所需的修補程式，您必須將 Cloud Foundation 實例升級至最新 VMware 修補程式軟體組。對於所有現有的實例及 ESXi 伺服器，會提示您從 {{site.data.keyword.vmwaresolutions_full}} 主控台的**更新及修補程式**頁面套用修補程式。如需相關資訊，請參閱[將更新套用至 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc/sd_applyingupdates.html)。

### 已部署在 2.0 版或更新版本中的 VMware vSphere 叢集

對於所有新的 VMware vSphere 6.5 叢集及 ESXi 伺服器，您必須從 [VMware 產品修補程式站台](https://my.vmware.com/group/vmware/patch)套用下列修補程式：ESXi650-201808401-BG、ESXi650-201808402-BG 及 ESXi650-201808403-BG。

對於所有現有的 VMware vSphere 6.5 叢集，您必須從 [VMware 產品修補程式站台](https://my.vmware.com/group/vmware/patch)套用下列修補程式：ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG 及 ESXi650-201808403-BG。

對於 VMware vCenter Server 6.5，您必須將 [VMware 產品修補程式站台](https://my.vmware.com/group/vmware/patch)中的 vCenter 6.5 U2c 修補程式套用至所有 vCenter Server，不論是新部署或現有的。

## 已部署在 1.9 版或更早版本中的實例

Cloud Foundation 實例、vCenter Server 實例以及 1.9 版或更早版本中的 VMware vSphere 叢集，與 VMware vSphere 6.0 及 VMware vCenter Server 6.0 一起部署。

### 已部署在 1.9 版或更早版本中的 vCenter Server 實例

對於 VMware vSphere 6.0 及 VMware vCenter Server 6.0，您必須將修補程式（適用於 vSphere 的 ESXi600-201711101-SG、ESXi600-201803401-BG、ESXi600-201803402-BG、ESXi600-201808401-BG、ESXi600-201808402-BG 及 ESXi600-201808403-BG，以及適用於 vCenter Server 的 vCenter 6.0 U3h）從 [VMware 產品修補程式站台](https://my.vmware.com/group/vmware/patch)套用至您所有的實例和 ESXi 伺服器，不論是新部署或現有的。

### 已部署在 1.9 版或更早版本中的 Cloud Foundation 實例

當這些實例所仰賴的必要供應商更新釋出時，這些實例的更新即可供使用。

### 已部署在 1.9 版或更早版本中的 VMware vSphere 叢集

對於 VMware vSphere 6.0 及 VMware vCenter Server 6.0，您必須將修補程式（適用於 vSphere 的 ESXi600-201711101-SG、ESXi600-201803401-BG、ESXi600-201803402-BG、ESXi600-201808401-BG、ESXi600-201808402-BG 及 ESXi600-201808403-BG，以及適用於 vCenter Server 的 vCenter 6.0 U3h）從 [VMware 產品修補程式站台](https://my.vmware.com/group/vmware/patch)套用至您所有的 vSphere 叢集和 ESXi 伺服器，不論是新部署或現有的。

### 相關鏈結

* [將更新套用至 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc/sd_applyingupdates.html)
* [針對最新安全漏洞的安全防範](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [VMware 產品修補程式站台](https://my.vmware.com/group/vmware/patch)
