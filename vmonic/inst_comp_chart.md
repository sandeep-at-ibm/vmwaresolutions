---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: vmware offering, vmware solutions functions, function support

subcollection: vmware-solutions


---

# Offering comparison chart
{: #inst_comp_chart}

Review the following chart to understand the differences in functions support for VMware vCenter Server instances and VMware vSphere clusters.

| Function | vCenter Server | VMware vSphere |
|:--- |:--- |:--- |:--- |
| Powered by {{site.data.keyword.IBM}} advanced automation <sup>1</sup> | Yes | No. Self-built and configured |
| Storage options | vSAN or NFS (Shared File-level Storage) | vSAN or NFS |
| Number of ESXi servers in initial cluster | 4 for vSAN and a minimum of 2 (3 recommended) for NFS | 1 to scale an existing cluster, 4 for new vSAN cluster, and a minimum of 3 for new cluster with NFS |
| Maximum number of ESXi servers <sup>2</sup> | 59 per cluster | 60 per cluster |
| Cloud automated multi-site deployment |Supported for new instances that are deployed in V2.0 or later | Supported. Automated configuration not included |
| Add ESXi servers | Supported | Supported. Automated configuration not included |
| Remove ESXi servers | Supported | Supported. Automated configuration not included |
| Multi-cluster support | Maximum number depends on VMware sizing guidelines | Supported. Automated configuration not included |
| Client-managed updating and patching of VMware stack | Client-managed updates:<br/>Native VMware tools (VMware Update Manager) | Client-managed updates:<br/>Native VMware tools (VMware Update Manager) |
| Backup and restore | Manually using IBM Spectrum Protect Plus or Veeam | Backup and restore solution not included |
| Software-defined networking | NSX Base, Advanced, or Enterprise | NSX Standard, Base, or Enterprise. Automated configuration not included |
| BYOL for vSphere and vSAN | Fully supported per cluster | Supported |
| BYOL for vCenter and NSX | Fully supported per instance | Supported |
| NSX license upgrade options | Upgrade available from NSX Base to Advanced or Enterprise, and from NSX Advanced to Enterprise. | None |
| vSAN license editions | vSAN Advanced or Enterprise | vSAN Advanced or Enterprise  |
| Add-on services | Supported | Not supported by the automation of this solution, but you can bring and install your own software. |
{: caption="Table 1. Supported functions for vCenter Server and vSphere clusters" caption-side="top"}

## Notes
{: #inst_comp_chart-notes}

<sup>1</sup> According to a validated design and with verification during deployment.

<sup>2</sup> You can increase the number of ESXi servers in a vSAN cluster to a maximum of 64. For more information, see _How many ESXi servers can I add to a cluster?_ in [FAQ about ESXi servers](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi).

## Related links
{: #inst_comp_chart-related}

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [VMware vSphere overview](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)
* [vCenter Server BOM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [VMware vSphere BOM](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
