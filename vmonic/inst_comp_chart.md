---

copyright:

  years:  2016, 2021

lastupdated: "2021-04-05"

keywords: vmware offering, vmware solutions functions, function support

subcollection: vmwaresolutions

---

# Offering comparison chart
{: #inst_comp_chart}

Review the following information to understand the differences in feature support between the various VMware Solutions offerings.

## vCenter Server vs VMware vSphere
{: #inst_comp_chart-vcs-vss}

Review the following table to understand the differences in feature support for VMware® vCenter Server® instances and VMware vSphere® clusters.

| Feature | vCenter Server | VMware vSphere |
|:-------- |:-------------- |:-------------- |
| Powered by {{site.data.keyword.IBM}} advanced automation[^automation] | Yes | No. Self-built and configured. |
| Storage options | - NFS (Shared File-level Storage) or vSAN™ available with automation </br>- iSCSI available with manual configuration | NFS, vSAN, or iSCSI available with manual configuration |
| Number of ESXi™ servers in the initial cluster | For vSAN - four servers </br>For NFS </br> - three servers for production use </br> - two servers for non-production use | Because VMware vSphere is self-managed, there is no limitation. A customer can add as many ESXi servers as the portal allows. For example, you can deploy a 3 node vSAN cluster with FTT=1. |
| Maximum number of ESXi servers[^servers] | 59 per cluster | 64 per cluster |
| Cloud automated multi-site deployment | Supported for new instances | Supported. Automated configuration not included. |
| Add ESXi servers | Supported | Supported. Automated configuration not included. |
| Remove ESXi servers | Supported | Supported. Automated configuration not included. |
| Multi-cluster support | Maximum number depends on VMware® sizing guidelines | Supported. Automated configuration not included. |
| Client-managed updating and patching of VMware stack | Client-managed updates - Native VMware tools (VMware Update Manager™)[^nsxv1] | Client-managed updates - Native VMware tools (VMware Update Manager) |
| Backup and restore | Manually using IBM Spectrum® Protect Plus or Veeam®[^nsxv2] | Backup and restore solution not included |
| Software-defined networking | NSX Advanced or Enterprise | NSX Advanced or Enterprise. Automated configuration not included. |
| BYOL for vSphere and vSAN | Fully supported per cluster | Supported |
| BYOL for vCenter Server and NSX | Fully supported per instance | Supported |
| NSX license upgrade options | Upgrade available from NSX Advanced to Enterprise. | None |
| vSAN license editions | vSAN Advanced or Enterprise | vSAN Advanced or Enterprise  |
| Add-on services | Supported[^nsxv3] | Not supported by the automation of this solution. You can bring and install your own software. |
{: caption="Table 1. Supported functions for vCenter Server instances and for vSphere clusters" caption-side="top"}

[^automation]: According to a validated design and with verification during deployment

[^servers]: For V2.1 or earlier instances, to increase beyond 32 ESXi servers in a vSAN cluster, see [How many ESXi servers can I add to a cluster?](/docs/vmwaresolutions?topic=vmwaresolutions-faq_esxi#faq_esxi-cluster)

[^nsxv1]: NSX-V only

[^nsxv2]: NSX-V only

[^nsxv3]: Not all add-on services are supported for NSX-T instances

## vCenter Server, Security and Compliance Readiness Bundle, and VMware Regulated Workloads
{: #inst_comp_chart-vcs-scb-vrw}

Review the following table to understand the differences in feature support for vCenter Server instances, Security and Compliance Readiness Bundle instances, and VMware Regulated Workloads.

| Feature | vCenter Server | Security and Compliance Readiness Bundle | VMware Regulated Workloads |
|:-------- |:-------------- |:-------------- |:-------------- |
| vSphere version | 6.7 Update 3 or 7.0 Update 1c | 7.0 Update 1c | 7.0 Update 1c |
| NSX edition | Advanced or Enterprise | Advanced or Enterprise | Enterprise |
| NSX networking solution | NSX-V or NSX-T™ | NSX-T | NSX-T |
| NFS | Optional | Optional | Not allowed |
| vSAN | Optional | Optional | Required |
| Consolidated cluster | Optional | Optional | Not allowed |
| Separate management cluster | Supported | Not supported | Supported |
| Minimum number of ESXi servers | For vSAN, four servers. </br>For NFS, three servers for production use and two servers for non-production use. | For vSAN, six servers. </br>For NFS, five servers. | 10 |
| Edge services cluster | Optional | Required. Juniper vSRX or Bring your own gateway. | Required. Juniper vSRX, Bring your own gateway, or FortiGate Security Appliance. |
| Logging and monitoring with VMware vRealize Operations and Log Insight | Optional | Required | Required |
| Role-based access with HyTrust CloudControl | Optional | Required | Required |
| Compliance with Caveonix | Optional | Required | Required |
| Caveonix pricing | Per VM | Per host | Per host |
| Key encryption | Key Protect or Hyper Protect Crypto Services | Hyper Protect Crypto Services required | Hyper Protect Crypto Services required |
| Direct Link | Optional | Optional | Required for private only instances |
| Backup | Veeam (opt out) or VMware Software Purchasing Program | Veeam 11 (opt out) | Veeam 11 required with option to remove on day 2 |
| Veeam backup server | Optional (opt out) | Optional (opt out) | Required with option to remove on day 2 |
| Disaster recovery | Veeam or Zerto | Veeam 11 | Veeam 11|
| Migration | HCX, Zerto, or PrimaryIO | HCX (optional) | HCX (optional) |
| Stretched cluster - High Availability | Optional | Optional | Optional |
| Financial Services Cloud with policy framework | No | No. Stepping stone to Financial Services, but no in-place upgrade. | Yes |
{: caption="Table 2. Supported features for vCenter Server instances, Security and Compliance Readiness Bundle instances, and VMware Regulated Workloads" caption-side="top"}

## Related links
{: #inst_comp_chart-related}

* [vCenter Server overview](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview)
* [VMware vSphere overview](/docs/vmwaresolutions?topic=vmwaresolutions-vs_vsphereclusteroverview)
* [vCenter Server BOM](/docs/vmwaresolutions?topic=vmwaresolutions-vc_bom)
* [VMware vSphere BOM](/docs/vmwaresolutions?topic=vmwaresolutions-vs_bom)
* [VMware Regulated Workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-overview)
* [Security and Compliance Readiness Bundle overview](/docs/vmwaresolutions?topic=vmwaresolutions-scb-overview)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
