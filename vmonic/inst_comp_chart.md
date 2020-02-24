---

copyright:

  years:  2016, 2020

lastupdated: "2020-02-10"

keywords: vmware offering, vmware solutions functions, function support

subcollection: vmware-solutions


---

# Offering comparison chart
{: #inst_comp_chart}

Review the following chart to understand the differences in functions support for VMware vCenter Server instances and VMware vSphere clusters.

| Function | vCenter Server | VMware vSphere |
|:--- |:--- |:--- |:--- |
| Powered by {{site.data.keyword.IBM}} advanced automation[^automation] | Yes | No. Self-built and configured |
| Storage options | vSAN or NFS (Shared File-level Storage) | vSAN or NFS |
| Number of ESXi servers in initial cluster | Four for vSAN</br>(NSX-V) Minimum two (three recommended) for NFS</br>(NSX-T) Minimum three (four recommended) for NFS | One to scale an existing cluster, four for new vSAN cluster, and a minimum of three for new NFS cluster |
| Maximum number of ESXi servers[^servers] | 59 per cluster | 60 per cluster |
| Cloud automated multi-site deployment |Supported for new instances | Supported. Automated configuration not included |
| Add ESXi servers | Supported | Supported. Automated configuration not included |
| Remove ESXi servers | Supported | Supported. Automated configuration not included |
| Multi-cluster support | Maximum number depends on VMware sizing guidelines | Supported. Automated configuration not included |
| Client-managed updating and patching of VMware stack | Client-managed updates: Native VMware tools (VMware Update Manager)[^nsxv1] | Client-managed updates:<br/>Native VMware tools (VMware Update Manager) |
| Backup and restore | Manually using IBM Spectrum Protect Plus or Veeam[^nsxv2] | Backup and restore solution not included |
| Software-defined networking | NSX Base, Advanced, or Enterprise | NSX Standard, Base, or Enterprise. Automated configuration not included |
| BYOL for vSphere and vSAN | Fully supported per cluster | Supported |
| BYOL for vCenter and NSX | Fully supported per instance | Supported |
| NSX license upgrade options | Upgrade available from NSX Base to Advanced or Enterprise, and from NSX Advanced to Enterprise. | None |
| vSAN license editions | vSAN Advanced or Enterprise | vSAN Advanced or Enterprise  |
| Add-on services | Supported[^nsxv3] | Not supported by the automation of this solution, but you can bring and install your own software. |
{: caption="Table 1. Supported functions for vCenter Server and vSphere clusters" caption-side="top"}
{: row-headers}
{: class="comparison-table"}
{: summary="This table has row and column headers. The row headers identify different functions. The column headers identify the product offerings. To check whether a function is supported in a certain offering, navigate to the row, and then find the description in the corresponding offering column."}

[^automation]: According to a validated design and with verification during deployment.

[^servers]: To increase beyond 32 ESXi servers in a vSAN cluster, see [How many ESXi servers can I add to a cluster?](/docs/services/vmwaresolutions?topic=vmware-solutions-faq_esxi#faq_esxi-cluster).

[^nsxv1]: NSX-V only

[^nsxv2]: NSX-V only

[^nsxv3]: NSX-V only

## Related links
{: #inst_comp_chart-related}

* [FAQ](/docs/services/vmwaresolutions?topic=vmware-solutions-faq)
* [vCenter Server overview](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_vcenterserveroverview)
* [VMware vSphere overview](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_vsphereclusteroverview)
* [vCenter Server BOM](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_bom)
* [VMware vSphere BOM](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_bom)
