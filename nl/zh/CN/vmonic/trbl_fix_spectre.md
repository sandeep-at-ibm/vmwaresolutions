---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# 解决 Spectre 和 Meldown 漏洞

要解决 Spectre 和 Meldown 漏洞，必须按特定顺序应用多个补丁。

## 更新固件

有关更新固件的最新信息，请参阅[防御最近的安全漏洞](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)。

## 更新 V2.0 或更高版本中部署的实例

V2.0 或更高版本中的实例是随 VMware vSphere 6.5 和 VMware vCenter Server 6.5 一起部署的。这两种软件组件都需要修补。

### V2.0 或更高版本中部署的 vCenter Server 实例

对于 VMware vSphere 6.5：
* 对于所有新的 V2.3 实例，部署 vSphere 时将应用以下补丁：ESXi650-201712101-SG、ESXi650-201803401-BG 和 ESXi650-201803402-BG。  
* 对于 V2.3 之前的版本中部署的所有现有实例，将使用以下补丁更新所有新集群和 ESXi 服务器：ESXi650-201712101-SG、ESXi650-201803401-BG 和 ESXi650-201803402-BG。
* 对于所有现有 ESXi 服务器以及在升级到 V2.3 之前继续部署的任何集群或 ESXi 服务器，必须应用 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的以下补丁：ESXi650-201712101-SG、ESXi650-201803401-BG 和 ESXi650-201803402-BG。

对于 VMware vCenter Server 6.5：
* 对于所有新的 V2.3 实例，部署 vCenter Server 时将应用 vCenter 6.5 U1g 补丁。
* 对于 V2.3 之前的版本中部署的所有现有实例，必须应用 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的 vCenter 6.5 U1g 补丁。

### V2.0 或更高版本中部署的 Cloud Foundation 实例

要应用 VMware vSphere 6.5 和 VMware vCenter Server 6.5 的必需补丁，必须将 Cloud Foundation 实例升级到最新的 V2.3 版本。

对于所有现有实例和 ESXi 服务器，系统将提示您在 {{site.data.keyword.vmwaresolutions_full}} 控制台的**更新和补丁**页面上应用补丁（对于 vSphere，应用 ESXi650-201712101-SG、ESXi650-201803401-BG 和 ESXi650-201803402-BG；对于 vCenter Server，应用 vCenter 6.5 U1g）。有关更多信息，请参阅[对 Cloud Foundation 实例应用更新](../sddc/sd_applyingupdates.html)。

### V2.0 或更高版本中部署的 VMware vSphere 集群

对于 VMware vSphere 6.5，必须将 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中以下补丁应用于所有 vSphere 集群和 ESXi 服务器（包括新部署的和现有的 vSphere 集群和 ESXi 服务器）：ESXi650-201712101-SG、ESXi650-201803401-BG 和 ESXi650-201803402-BG。

对于 VMware vCenter Server 6.5，必须将 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的 vCenter 6.5 U1g 补丁应用于所有 vCenter Server（包括新部署的和现有的 vCenter Server）。

## V1.9 或更低版本中部署的实例

Cloud Foundation 和 vCenter Server 实例以及 V1.9 或更低版本中的 VMware vSphere 集群是随 VMware vSphere 6.0 和 VMware vCenter Server 6.0 一起部署的。

### V1.9 或更低版本中部署的 vCenter Server 实例

对于 VMware vSphere 6.0 和 VMware vCenter Server 6.0，必须将 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的补丁（对于 vSphere，应用 ESXi600-201711101-SG、ESXi600-201803401-BG 和 ESXi600-201803402-BG；对于 vCenter Server，应用 vCenter 6.0 U3e）应用于所有实例和 ESXi 服务器（包括新部署的和现有的实例和 ESXi 服务器）。

### V1.9 或更低版本中部署的 Cloud Foundation 实例

这些实例的更新将在发布这些实例所依赖的必要供应商更新时可用。

### V1.9 或更低版本中部署的 VMware vSphere 集群

对于 VMware vSphere 6.0 和 VMware vCenter Server 6.0，必须将 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的补丁（对于 vSphere，应用 ESXi600-201711101-SG、ESXi600-201803401-BG 和 ESXi600-201803402-BG；对于 vCenter Server，应用 vCenter 6.0 U3e）应用于所有 vSphere 集群和 ESXi 服务器（包括新部署的和现有的 vSphere 集群和 ESXi 服务器）。

### 相关链接

* [对 Cloud Foundation 实例应用更新](../sddc/sd_applyingupdates.html)
* [防御最近的安全漏洞](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)
