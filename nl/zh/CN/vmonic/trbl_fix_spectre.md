---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# 解决 Spectre 和 Meldown 漏洞
{: #trbl_fix_spectre}

要解决 Spectre 和 Meldown 漏洞，必须按特定顺序应用多个补丁。

## 更新固件
{: #trbl_fix_spectre-firmware-update}

有关更新固件的最新信息，请参阅[防御最近的安全漏洞](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)。

## 更新 V2.0 或更高版本中部署的实例
{: #trbl_fix_spectre-instance2.0-update}

V2.0 或更高版本中的实例是随 VMware vSphere 6.5 和 VMware vCenter Server 6.5 一起部署的。这两种软件组件都需要修补。

### 在 V2.0 或更高版本中部署的 vCenter Server 实例
{: #trbl_fix_spectre-vcs2.0}

#### 对于 VMware vSphere 6.5
{: #trbl_fix_spectre-vcs2.0-vsphere}

* 对于所有新的 V2.6 实例，部署 vSphere 时将应用以下补丁：ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG 和 ESXi650-201808403-BG。
* 对于在 V2.5 之前部署但升级到 V2.5 的所有现有实例，将使用以下补丁更新所有新集群和 ESXi 服务器：ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG 和 ESXi650-201808403-BG。
* 对于所有现有 ESXi 服务器以及在升级到 V2.5 之前继续部署的任何集群或 ESXi 服务器，必须应用 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的以下补丁：ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG 和 ESXi650-201808403-BG。

#### 对于 VMware vCenter Server 6.5
{: #trbl_fix_spectre-vcs2.0-vcenter}

* 对于所有新的 V2.6 实例，部署 vCenter Server 时将应用 vCenter 6.5 U2c 累积补丁。
* 对于 V2.6 之前的版本中部署的所有现有实例，必须应用 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的 vCenter 6.5 U2c 补丁。

### 在 V2.0 或更高版本中部署的 Cloud Foundation 实例
{: #trbl_fix_spectre-cf2.0}

要应用 VMware vSphere 6.5 和 VMware vCenter Server 6.5 的必需补丁，必须将 Cloud Foundation 实例升级到最新的 VMware 补丁捆绑软件。对于所有现有实例和 ESXi 服务器，系统将提示您应用 {{site.data.keyword.vmwaresolutions_full}} 控制台中**更新和补丁**页面上的补丁。有关更多信息，请参阅[对 Cloud Foundation 实例应用更新](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_applyingupdates)。

### 在 V2.0 或更高版本中部署的 VMware vSphere 集群
{: #trbl_fix_spectre-vss2.0}

对于所有新的 VMware vSphere 6.5 集群和 ESXi 服务器，必须应用 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的以下补丁：ESXi650-201808401-BG、ESXi650-201808402-BG 和 ESXi650-201808403-BG。

对于所有现有 VMware vSphere 6.5 集群，必须应用 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的以下补丁：ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG 和 ESXi650-201808403-BG。

对于 VMware vCenter Server 6.5，必须将 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的 vCenter 6.5 U2c 补丁应用于所有 vCenter Server（包括新部署的和现有的 vCenter Server）。

## V1.9 或更低版本中部署的实例
{: #trbl_fix_spectre-instance1.9-update}

V1.9 或更低版本中的 Cloud Foundation 实例、vCenter Server 实例和 VMware vSphere 集群是随 VMware vSphere 6.0 和 VMware vCenter Server 6.0 一起部署的。

### 在 V1.9 或更低版本中部署的 vCenter Server 实例
{: #trbl_fix_spectre-vcs1.9}

对于 VMware vSphere 6.0 和 VMware vCenter Server 6.0，必须将 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的补丁（对于 vSphere，应用 ESXi600-201711101-SG、ESXi600-201803401-BG、ESXi600-201803402-BG、ESXi600-201808401-BG、ESXi600-201808402-BG 和 ESXi600-201808403-BG；对于 vCenter Server，应用 vCenter 6.0 U3h）应用于所有实例和 ESXi 服务器（包括新部署的和现有的实例和 ESXi 服务器）。

### 在 V1.9 或更低版本中部署的 Cloud Foundation 实例
{: #trbl_fix_spectre-cf1.9}

这些实例的更新将在发布这些实例所依赖的必要供应商更新时可用。

### 在 V1.9 或更低版本中部署的 VMware vSphere 集群
{: #trbl_fix_spectre-vss1.9}

对于 VMware vSphere 6.0 和 VMware vCenter Server 6.0，必须将 [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)中的补丁（对于 vSphere，应用 ESXi600-201711101-SG、ESXi600-201803401-BG、ESXi600-201803402-BG、ESXi600-201808401-BG、ESXi600-201808402-BG 和 ESXi600-201808403-BG；对于 vCenter Server，应用 vCenter 6.0 U3h）应用于所有 vSphere 集群和 ESXi 服务器（包括新部署的和现有的 vSphere 集群和 ESXi 服务器）。

## 相关链接
{: #trbl_fix_spectre-related}

* [对 Cloud Foundation 实例应用更新](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_applyingupdates)
* [防御最近的安全漏洞](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [VMware 产品补丁站点](https://my.vmware.com/group/vmware/patch)
