---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-16"

---

# Instance comparison chart

Review the following chart to understand the differences in functions support for VMware Cloud Foundation instances, VMware vCenter Server instances, and VMware vSphere instances.

Table 1. Supported functions for Cloud Foundation, vCenter Server, and VMware vSphere instances

| Function                          | Cloud Foundation    | vCenter Server | VMware vSphere |
|:----------------------------------|:--------------------|:----------------------|:----------------------|
| Powered by IBM advanced automation | Yes | Yes | No. Self-built and configured |
| Storage options        | vSAN                | vSAN or Shared File-level Storage (NFS) | vSAN or Shared File-level Storage (NFS) |
| Number of ESXi servers in initial cluster | 4 | 4 for vSAN and a minimum of 2 (with 3 strongly recommended) for NFS | 1 to scale an existing cluster, 4 for new vSAN cluster, and a minimum of 3 for new cluster with NFS |
| Maximum number of ESXi servers * | 32 per cluster      | 59 per cluster     |60 per cluster     |
| Cloud automated multi-site deployment | Supported for new instances deployed in V2.0 or later | Supported for new instances deployed in V2.0 or later | Supported. Automated configuration not included |
| Add ESXi servers              | Supported           | Supported | Supported. Automated configuration not included |
| Remove ESXi servers           | Supported           | Supported | Supported. Automated configuration not included |
| Multi-cluster support         | 5 clusters | 10 clusters | Supported. Automated configuration not included |
| Client-managed updating and patching of VMware stack | IBM CloudDriver and VMware updates | IBM CloudDriver | Automated patching not included |
| Backup and restore            | Supported | Supported | Automated backup solution configuration not included |
| Software-defined networking   | NSX Enterprise   | NSX Base, Advanced, or Enterprise | NSX Standard, Base, or Enterprise. Automated configuration not included |
| BYOL for vSphere and vSAN | Fully supported per cluster   | Fully supported per cluster     | Supported |
| BYOL for vCenter and NSX | Fully supported per instance   | Fully supported per instance     | Supported |
| NSX license upgrade options           | None   | Upgrade available from NSX Base to Advanced or Enterprise, and from NSX Advanced to Enterprise  | None |
| vSAN license editions         | vSAN Advanced or Enterprise  | vSAN Advanced or Enterprise  | vSAN Advanced or Enterprise  |
| Add-on services               | Supported  | Supported | Supported. Automated configuration not included |

**Note**: You can increase the number of ESXi servers in a vSAN cluster to a maximum of 64. For more information, see _How many ESXi servers can I add to a cluster?_ in [FAQ about ESXi servers](faq_esxi.html).

## Related links

* [FAQ](faq.html)
* [Cloud Foundation overview](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server overview](../vcenter/vc_vcenterserveroverview.html)
* [Vmware vSphere overview](../vsphere/vs_vsphereclusteroverview.html)
* [Cloud Foundation BOM](../sddc/sd_bom.html)
* [vCenter Server BOM](../vcenter/vc_bom.html)
* [Vmware vSphere BOM](../vsphere/vs_bom.html)
