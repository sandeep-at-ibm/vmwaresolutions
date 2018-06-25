---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# VMware HCX on IBM Cloud overview

The HCX on {{site.data.keyword.cloud}} service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

**Availability**: This service is available only to VMware vCenter Server on IBM Cloud with Hybridity Bundle instances that are deployed in V2.3 and later releases.

You can upgrade your existing vCenter Server instance to a vCenter Server with Hybridity Bundle instance. For more information on upgrading your instance and deploying the HCX on {{site.data.keyword.cloud_notm}} service, see [Upgrading to the vCenter Server with Hybridity Bundle instance](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html#upgrading-to-the-vcenter-server-with-hybridity-bundle-instance).

**Note:** A vCenter Server instance with HCX on {{site.data.keyword.cloud_notm}} is limited to three simultaneous connections from on-premises sites.

## Considerations when installing HCX on IBM Cloud

Review the following considerations before attempting to install HCX on {{site.data.keyword.cloud_notm}}.

### Requirements on the number of ESXi servers

The HCX on {{site.data.keyword.cloud_notm}} service cannot be installed into an instance for which the default cluster has more than 51 ESXi servers. Because HCX on {{site.data.keyword.cloud_notm}} requires eight IP addresses in the vMotion subnet from the default cluster, if the number of ESXi servers exceeds 51, no IP addresses in the vMotion subnet are available for HCX on {{site.data.keyword.cloud_notm}}.

### Requirements on firewall rules

Before installing the HCX on {{site.data.keyword.cloud_notm}} service, you must add a firewall rule to any existing firewalls to allow all outbound HTTPS traffic so that the HCX Manager virtual appliance (HCX Manager) can register itself. After the HCX Manager installation is completed, you can remove the firewall rule. In addition, you must configure firewall rules to allow HCX to function properly. For more information, see *Appendix A - Port Access Requirements* in [HCX on {{site.data.keyword.cloud_notm}} Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

## Considerations when removing HCX on IBM Cloud

Review the following considerations before you remove the HCX on {{site.data.keyword.cloud_notm}} service:
* Ensure that the interconnects and extended networks between the on-premises source site and the {{site.data.keyword.cloud_notm}} target sites are removed. To remove the interconnects and extended networks, use the HCX user interface in the on-premises VMware vSphere Web Client.
* Ensure that the site pairings between the on-premises source site and the {{site.data.keyword.cloud_notm}} target sites are removed. To remove the site pairings, use the HCX user interface in the on-premises VMware vSphere Web Client.
* The removal of HCX on {{site.data.keyword.cloud_notm}} is automated. The following procedures are completed for the successful removal of this service:
   * The HCX license ordered for the cloud-side HCX Manager is deactivated.
   * HCX Manager is deleted.
   * The vMotion IP addresses that were reserved for HCX are released.
   * If empty, the HCX-related resource pools are removed.
   * If empty, the HCX-related folders are removed.
   * The HCX management edge appliances are deleted.

## Related links

* [Ordering HCX on {{site.data.keyword.cloud_notm}}](hcx_ordering.html)
* [Managing HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Glossary of HCX terms](hcx_glossary.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#vm-documentation)
