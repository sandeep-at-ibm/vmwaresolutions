---

copyright:

  years:  2016, 2021

lastupdated: "2021-02-03"

keywords: vmware offering, vmware solutions functions, function support

subcollection: vmwaresolutions


---

# Offering comparison chart
{: #inst_comp_chart}

Review the following chart to understand the differences in functions support for VMware® vCenter Server® instances and VMware vSphere® clusters.

| Function | vCenter Server | VMware vSphere |
|:-------- |:-------------- |:-------------- |
| Powered by {{site.data.keyword.IBM}} advanced automation[^automation] | Yes | No. Self-built and configured. |
| Storage options | vSAN™ or NFS (Shared File-level Storage) | vSAN or NFS |
| Number of ESXi™ servers in the initial cluster | For vSAN: 4 servers </br>For NFS: </br> - 3 servers for production use </br> - 2 servers for non-production use | - For a new vSAN cluster: 4 servers </br> - For a new NFS cluster: 1 server </br> - To scale an existing cluster: 1 server |
| Maximum number of ESXi servers[^servers] | 59 per cluster | 60 per cluster |
| Cloud automated multi-site deployment |Supported for new instances | Supported. Automated configuration not included. |
| Add ESXi servers | Supported | Supported. Automated configuration not included. |
| Remove ESXi servers | Supported | Supported. Automated configuration not included. |
| Multi-cluster support | Maximum number depends on VMware® sizing guidelines | Supported. Automated configuration not included. |
| Client-managed updating and patching of VMware stack | Client-managed updates: Native VMware tools (VMware Update Manager™)[^nsxv1] | Client-managed updates: Native VMware tools (VMware Update Manager) |
| Backup and restore | Manually using IBM Spectrum® Protect Plus or Veeam®[^nsxv2] | Backup and restore solution is not included |
| Software-defined networking | NSX Advanced or Enterprise | NSX Advanced or Enterprise. Automated configuration not included. |
| BYOL for vSphere and vSAN | Fully supported per cluster | Supported |
| BYOL for vCenter and NSX | Fully supported per instance | Supported |
| NSX license upgrade options | Upgrade available from NSX Advanced to Enterprise. | None |
| vSAN license editions | vSAN Advanced or Enterprise | vSAN Advanced or Enterprise  |
| Add-on services | Supported[^nsxv3] | Not supported by the automation of this solution, but you can bring and install your own software. |
{: caption="Table 1. Supported functions for vCenter Server instances and for vSphere clusters" caption-side="top"}

[^automation]: According to a validated design and with verification during deployment

[^servers]: To increase beyond 32 ESXi servers in a vSAN cluster, see [How many ESXi servers can I add to a cluster?](/docs/vmwaresolutions?topic=vmwaresolutions-faq_esxi#faq_esxi-cluster)

[^nsxv1]: NSX-V only

[^nsxv2]: NSX-V only

[^nsxv3]: Not all add-on services are supported for NSX-T instances

## Related links
{: #inst_comp_chart-related}

* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [vCenter Server overview](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview)
* [VMware vSphere overview](/docs/vmwaresolutions?topic=vmwaresolutions-vs_vsphereclusteroverview)
* [vCenter Server BOM](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom)
* [VMware vSphere BOM](/docs/vmwaresolutions?topic=vmwaresolutions-vs_bom)
