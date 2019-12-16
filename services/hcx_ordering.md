---

copyright:

  years:  2016, 2019

lastupdated: "2019-12-12"

keywords: VMware HCX deployment, HCX configuration, order HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering VMware HCX
{: #hcx_ordering}

You can order the VMware HCX service as part of your new VMware vCenter Server order or you can add the service to your existing instance.

A 12-month commitment is required when you order the VMware HCX service. Your account continues to be charged for the HCX components if you delete a host or cluster before the end of the 12-month commitment period.
{:important}

## Ordering VMware HCX for a new instance
{: #hcx_ordering-new}

To order a new VMware vCenter Server instance with VMware HCX, click **HCX 3.5** under the **Hybridity/Migration** category in the **Optional Services** section when you order the instance from the {{site.data.keyword.vmwaresolutions_full}} console.


## Ordering VMware HCX for an existing instance
{: #hcx_ordering-existing}

To add the VMware HCX service to an existing vCenter Server instance, view the instance, click **Services** on the left navigation pane, and click **Add**.

## VMware HCX configuration
{: #hcx_ordering-config}

To install HCX, complete the following settings:

Steps 1 and 2 do not apply to HCX installations on vCenter Server with Hybridity Bundle instances.
{:note}

1. Select the checkbox to confirm that you agree with the 12-month agreement for ordering the HCX service.
2. If you want to use your own NSX license (BYOL), select the checkbox to confirm that your NSX license is either Advanced or Enterprise edition.
3. Specify the **HCX Network Connection** by selecting one of the following options:
  * **Public Network:** HCX creates an encrypted connection between sites over the public network. License registration and metering are performed over the public network.
  * **Private Interconnect:** HCX creates an encrypted connection between sites over the private network. License registration and metering are performed over the public network.
  * **Private Network:** HCX creates an encrypted connection between sites over the private network. License registration and metering are performed over private network through HTTP proxy.
4. If you select **Private Network**, complete the following fields:
  * **Proxy Address:** The IPv4 address of the proxy server.
  * **Proxy Port:** The proxy server port. The port number is typically 8080 or 3128.
  * **Username:** The user name if proxy authentication is required.
  * **Password:** The password if proxy authentication is required.
  * **Reenter Password:** Reenter the password for proxy authentication validation.
5. Specify the **Public Endpoint Certificate Type**. If you select **CA Certificate**, configure the following settings:
  * **Certificate Contents:** Enter the contents of the CA certificate.
  * **Private Key:** Enter the private key of the CA certificate.
  * (Optional) **Password:** Enter the password for the private key if it is encrypted.
  * (Optional) **Reenter Password:** Enter the password for the private key again.
  * (Optional) **Hostname:** The host name to be mapped to the common name (CN) of the CA certificate. HCX requires that the format of the CA certificate must be accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}.
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Deployment process for HCX
{: #hcx_ordering-deploy}

The deployment of HCX is automated. Whether you order a vCenter Server instance with the service included or you deploy the service later into your instance, the following steps are completed by the {{site.data.keyword.vmwaresolutions_short}} automation process:
1. Three subnets are ordered for HCX from the {{site.data.keyword.cloud_notm}} infrastructure:
   * One private portable subnet for HCX management.
   * One private portable subnet for HCX interconnects. This subnet is used when the **Private network** option is selected for **HCX interconnect type**.
   * One public portable subnet for activation and maintenance with VMware. If the **Public network** option is selected for **HCX interconnect type**, this subnet is also used for HCX interconnects.

   The IP addresses in the subnets that are ordered for HCX are intended to be managed by the VMware on {{site.data.keyword.cloud_notm}} automation. These IP addresses cannot be assigned to VMware resources, such as VMs and NSX Edges, that are created by you. If you need more IP addresses for your VMware artifacts, you must order your own subnets from {{site.data.keyword.cloud_notm}}.
   {:important}
2. If **Private Network** was selected for **HCX Network Connection**, a port group that is named **SDDC-DPortGroup-HCX-Private** is created on the private Distributed Virtual Switch (DVS).
3. An HCX activation key is ordered from VMware.
4. Three resource pools and VM folders for HCX are created, which are needed for the HCX interconnects, local HCX components, and remote HCX components.
5. A pair of VMware NSX Edge Services Gateways (ESGs) for the HCX management traffic is deployed and configured:
   * Public and private uplink interfaces are configured by using the ordered subnets.
   * The ESGs are configured as a pair of extra large edge appliances with High Availability (HA) enabled.
   * The firewall rules and network address translation (NAT) rules are configured to allow inbound and outbound HTTPS traffic to and from the HCX Manager.
   * The load balancer rules and resource pools are configured. These rules and resource pools are used to forward HCX-related inbound traffic to the appropriate virtual appliances of HCX Manager and vCenter Server (with embedded Platform Services Controller).
   * An SSL certificate to encrypt the HCX-related inbound HTTPS traffic that is coming through the ESGs is applied.

   The HCX management edge is dedicated to the HCX management traffic between the on-premises HCX components and the cloud-side HCX components. Do not modify the HCX management edge or use it for HCX network extensions. Instead, create separate edges for network extensions. In addition, if you use a firewall or you disable the HCX management edge communications to the private IBM management components or the internet, the HCX functions might be impacted.
   {:important}

6. The HCX Manager is deployed, activated, and configured:
   * The HCX Manager is registered with vCenter Server.
   * The HCX Manager, vCenter Server (with embedded Platform Services Controller), and NSX Manager are configured.
   * The HCX fleet is configured.
   * Local and remote HCX deployment containers are configured.
7. The host name and IP address of the HCX Manager is registered with the DNS server of VMware vCenter Server.

## Related links
{: #hcx_ordering-related}

* [HCX overview](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [Managing HCX ](/docs/services/vmwaresolutions?topic=vmware-solutions-managinghcx)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices)
* [Glossary of HCX terms](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_glossary)
* [Contacting IBM Support](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx){:external}
* [VMware Hybrid Cloud Extension documentation](https://cloud.vmware.com/vmware-hcx/resources){:external}
