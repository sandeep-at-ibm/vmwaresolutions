---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-20"

---

# Ordering VMware HCX on IBM Cloud

You can order the VMware HCX on {{site.data.keyword.cloud_notm}} service while ordering a new VMware vCenter Server with Hybridity Bundle instance with the service included or by adding the service to your existing instance.

## Ordering VMware HCX on IBM Cloud for a new instance

To order a new VMware vCenter Server on IBM Cloud with Hybridity Bundle instance with VMware HCX on {{site.data.keyword.cloud_notm}}, select **VMware HCX on IBM Cloud** in the **Services** section when you order the instance from the {{site.data.keyword.vmwaresolutions_full}} console.


## Ordering VMware HCX on IBM Cloud for an existing instance

To add the VMware HCX on {{site.data.keyword.cloud_notm}} service into an existing VMware vCenter Server on IBM Cloud with Hybridity Bundle instance, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add Service**.

## VMware HCX on IBM Cloud configuration

To install HCX on {{site.data.keyword.cloud_notm}}, complete the following settings:
1. Specify the **HCX interconnect type** by selecting one of the following options:
  * **Public network**: HCX creates an encrypted connection between sites over the public network.
  * **Private network**: HCX creates an encrypted connection between sites over the private network.
2. Specify the **Public endpoint certificate type**. If you select **CA Certificate**, configure the following settings:
  * **Certificate Contents**: Enter the contents of the CA certificate.
  * **Private Key**: Enter the private key of the CA certificate.
  * (Optional) **Password**: Enter the password for the private key if it is encrypted.
  * (Optional) **Reenter Password**: Enter the password for the private key again.
  * (Optional) **Hostname**: The host name to be mapped to the common name (CN) of the CA certificate. HCX on {{site.data.keyword.cloud_notm}} requires that the format of the CA certificate must be accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Deployment process for HCX on IBM Cloud

The deployment of HCX on {{site.data.keyword.cloud_notm}} is automated. Whether you order a vCenter Server with Hybridity Bundle instance with the service included or you deploy the service later into your instance, the following steps are completed by the {{site.data.keyword.vmwaresolutions_short}} automation process:
1. Three subnets are ordered for HCX from the {{site.data.keyword.cloud_notm}} infrastructure:
   * One private portable subnet for HCX management.
   * One private portable subnet for HCX interconnects if **Private network** is selected for **HCX interconnect type**.
   * One public portable subnet for HCX interconnects if **Public network** is selected for **HCX interconnect type**. This subnet is also used for activation and maintenance with VMware.

   **Important:** The IP addresses in the subnets ordered for HCX are intended to be managed by the VMware on {{site.data.keyword.cloud_notm}} automation. These IP addresses cannot be assigned to VMware resources, such as VMs and NSX Edges, that are created by you. If you need additional IP addresses for your VMware artifacts, you must order your own subnets from {{site.data.keyword.cloud_notm}}.
2. If **Private network** was selected for **HCX interconnect type**, a port group named **SDDC-DPortGroup-HCX-Private** is created on the private Distributed Virtual Switch (DVS).
3. An HCX activation key is ordered from VMware.
4. Three resource pools and VM folders for HCX are created, which are needed for the HCX interconnects, local HCX components, and remote HCX components.
5. A pair of VMware NSX Edge Services Gateways (ESGs) for the HCX management traffic is deployed and configured:
   * Public and private uplink interfaces are configured by using the ordered subnets.
   * The ESGs are configured as a pair of extra large edge appliances with High Availability (HA) enabled.
   * The firewall rules and network address translation (NAT) rules are configured to allow inbound and outbound HTTPS traffic to and from the HCX Manager.
   * The load balancer rules and resource pools are configured. These rules are resource pools are used to forward HCX-related inbound traffic to the appropriate virtual appliances of HCX Manager, vCenter Server, and Platform Services Controller (PSC).
   * An SSL certificate to encrypt the HCX related inbound HTTPS traffic coming through the ESGs is applied.

   **Important**: The HCX management edge is dedicated to the HCX management traffic between the on-premises HCX components and the cloud-side HCX components. Do not modify the HCX management edge or use it for HCX network extensions. Instead, create separate edges for network extensions. In addition, note that using a firewall or disabling the HCX management edge communications to the private IBM management components or public Internet might adversely impact the HCX functionality.

6. The HCX Manager on {{site.data.keyword.cloud_notm}} is deployed, activated, and configured:
   * The HCX Manager is registered with vCenter Server.
   * The HCX Manager, vCenter Server, PSC, and NSX Manager are configured.
   * The HCX fleet is configured.
   * Local and remote HCX deployment containers are configured.
7. The host name and IP address of the HCX Manager is registered with the DNS server of VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## Related links

* [HCX on {{site.data.keyword.cloud_notm}} overview](hcx_considerations.html)
* [Managing HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Ordering, viewing, and removing services for vCenter Server with Hybridity Bundle instances](../vcenter/vc_hybrid_addingremovingservices.html)
* [Glossary of HCX terms](hcx_glossary.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#vm-documentation)
