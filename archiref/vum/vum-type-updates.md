---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmware-solutions


---

# Types of VMware software updates
{: #vum-type-updates}

VMware uses the following terms to describe software updates.

Table 1. VMware software update terms and definitions

| Term | Definition |
|:------- |:----------- |
| Bulletin |	A grouping of one or more VIBs. Bulletins are defined within metadata. |
| Depot |	A logical grouping of VIBs and associated metadata that is published online |
| Host upgrade image |	An ESXi image that you can import in the Update Manager repository and use for upgrading ESXi 5.5 or ESXi 6.0 hosts to ESXi 6.5. |
| Extension | 	A bulletin that defines a group of VIBs for adding an optional component to an ESXi host. An extension is usually provided by a third party that is also responsible for patches or updates to the extension. |
| Metadata |	Extra data that defines dependency information, textual descriptions, system requirements, and bulletins. |
| Offline bundle compressed file |	An archive that encapsulates VIBs and corresponding metadata in a self-contained package that is useful for offline patching. You can't use third-party offline bundles or offline bundles that you generated from custom VIB sets for host upgrade from ESXi 5.5 or ESXi 6.0 to ESXi 6.5. |
| Patch |	A bulletin that groups one or more VIBs together to address a particular issue or enhancement. |
| Roll-up |	A collection of patches that is grouped for ease of download and deployment. |
| VA upgrade |	Updates for a virtual appliance, which the vendor considers an upgrade. |
| VIB |	A VIB is a single software package. |

## Related links
{: #vum-type-updates-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrations)
