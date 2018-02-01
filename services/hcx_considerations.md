---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-29"

---

# Considerations for HCX on IBM Cloud

The HCX on {{site.data.keyword.cloud}} service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

This service is available only to VMware Cloud Foundation instances and VMware vCenter Server instances that are running vSphere 6.5 and that are deployed in or have been upgraded to V2.1 or later releases.

You can order an instance with the HCX on {{site.data.keyword.cloud_notm}} service included. For more information, see:
* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)

You can also deploy the HCX on {{site.data.keyword.cloud_notm}} service into your existing instances after initial deployment. For more information, see:
* [Ordering and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)

## Considerations when installing HCX on IBM Cloud

Review the following considerations before attempting to install HCX on {{site.data.keyword.cloud_notm}}.

### Requirements on the number of ESXi servers

The HCX on {{site.data.keyword.cloud_notm}} service cannot be installed into an instance for which the default cluster has more than 51 ESXi servers. Because HCX on {{site.data.keyword.cloud_notm}} requires 8 IP addresses in the vMotion subnet from the default cluster, if the number of ESXi servers exceeds 51, no IP addresses in the vMotion subnet are available for HCX on {{site.data.keyword.cloud_notm}}.

### Requirements on firewall rules

Before installing the HCX on {{site.data.keyword.cloud_notm}} service, you must add a firewall rule to any existing firewalls to allow all outbound HTTPS traffic so that the HCX Manager virtual appliance (HCX Manager) can register itself. After the HCX Manager installation is completed, you can remove the firewall rule. In addition, you must configure firewall rules to allow HCX to function properly. For more information, see *Appendix A - Port Access Requirements* in [HCX on IBM Cloud Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

### Deployment process for HCX on IBM Cloud

The deployment of HCX on {{site.data.keyword.cloud_notm}} is automated. Whether you order an instance with this service included or you deploy the service later into your instance, the following procedures are completed for successful deployment:
1. Order two subnets for HCX from the {{site.data.keyword.cloud_notm}} infrastructure:
   * One private portable subnet for HCX management
   * One public portable subnet for HCX interconnects

   **Important:** The IP addresses in the subnets ordered for HCX are intended to be managed by the VMware on {{site.data.keyword.cloud_notm}} automation. These IP addresses cannot be assigned to VMware resources, such as VMs and NSX Edges, that are created by you. If you need additional IP addresses for your VMware artifacts, you must order your own subnets from {{site.data.keyword.cloud_notm}}.
2. Order an HCX activation key from VMware.
3. Create three resource pools and VM folders for HCX, which are needed for the HCX interconnects, local HCX components, and remote HCX components.
4. Deploy and configure a pair of VMware NSX Edge Services Gateways (ESGs) for the HCX management traffic:
   * Configure public and private uplink interfaces by using the ordered subnets.
   * Configure the ESGs as a pair of extra large edge appliances with High Availability (HA) enabled.
   * Configure the firewall rules and network address translation (NAT) rules to allow inbound and outbound HTTPS traffic to and from the HCX Manager.
   * Configure the load balancer rules and resource pools for forwarding HCX related inbound traffic to the appropriate virtual appliances of HCX Manager, vCenter Server, and Platform Services Controller (PSC).
   * Apply SSL certificate to encrypt the HCX related inbound HTTPS traffic coming through the ESGs.

   **Important**: The HCX management edge is dedicated to the HCX management traffic between the on-premises HCX components and the cloud-side HCX components. Do not modify the HCX management edge or use it for HCX network extensions. Instead, create separate edges for network extensions. In addition, note that using a firewall or disabling the HCX management edge communications to the private IBM management components or public Internet might adversely impact the HCX functionality.

5. Deploy, activate, and configure the HCX Manager on {{site.data.keyword.cloud_notm}}, including:
   * Register the HCX Manager with vCenter Server.   
   * Configure the HCX Manager, vCenter Server, PSC, and NSX Manager.
   * Configure the HCX fleet.
   * Configure local and remote HCX deployment containers.
6. Register the host name and IP address of the HCX Manager with the DNS server of VMware Cloud Foundation or VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## Considerations when removing HCX on IBM Cloud

Review the following considerations before you remove the HCX on {{site.data.keyword.cloud_notm}} service:
* Ensure that the interconnects and extended networks between the on-premises source site and the {{site.data.keyword.cloud_notm}} target sites are removed. To remove the interconnects and extended networks, use the HCX user interface in the on-premises VMware vSphere Web Client.
* Ensure that the site pairings between the on-premises source site and the {{site.data.keyword.cloud_notm}} target sites are removed. To remove the site pairings, use the HCX user interface in the on-premises VMware vSphere Web Client.
* The removal of HCX on {{site.data.keyword.cloud_notm}} is automated. The following procedures are completed for the successful removal of this service:
   * Deactivate the HCX license ordered for the cloud-side HCX Manager.
   * Delete the HCX Manager.
   * Release the vMotion IP addresses that were reserved for HCX.
   * Remove the HCX related resource pools if they are empty.
   * Remove the HCX related folders if they are empty.
   * Delete the HCX management edge appliances.

## Related links

* [Managing HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Glossary of HCX terms](hcx_glossary.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#vm-documentation)
