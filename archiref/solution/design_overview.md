---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-15"

subcollection: vmwaresolutions


---
# IBM Cloud for VMware Solutions components
{: #design_overview}

{{site.data.keyword.vmwaresolutions_full}} provides automation to deploy VMware technology components into {{site.data.keyword.CloudDataCents_notm}} across the globe.

The offerings in this solution portfolio include VMware vSphere products within an automatically deployed and configured cluster: VMware vSphere ESXi, VMware vCenter Server Appliance with an embedded Platform Services Controller (PSC), VMware NSX-V or NSX-T, and optionally, VMware vSAN.

The architecture consists of a single cloud region and supports the ability to extend into more cloud regions that are located in another geography and into another {{site.data.keyword.cloud_notm}} pod within the same data center. A region is defined as a unique vCenter Server instance. This design also allows for automated expansion and contraction of virtual capacity within a vCenter Server instance.

Figure 1. Solution components of {{site.data.keyword.vmwaresolutions_short}}
![Solution components of {{site.data.keyword.vmwaresolutions_short}}](vcsv4radiagrams-ra-full.svg "The solution comprises physical infrastructure, virtual infrastructure, infrastructure management, and common services.")

## Related links
{: #design_overview-related}

* [Physical infrastructure design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_physicalinfrastructure)
* [Virtual infrastructure design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure)
* [Common services design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice)
* [Infrastructure management design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_infrastructuremgmt)
