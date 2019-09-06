---

copyright:

  years:  2019

lastupdated: "2019-08-26"

keywords: private network access, firewall rule vCloud Director, NAT rule vCloud Director

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Enabling access to IBM Cloud Services by using the private network
{: #shared-private_network}

vApps and virtual machines (VMs) running inside of the virtual data center can be configured to use the IBM Cloud private network to access IBM Cloud services. Accessing IBM Cloud services through a private network can save on outbound public networking costs and can provide a higher degree of reliability. Virtual data centers route to the IBM Cloud private network through a virtual data center service network that is configured as an available external network on virtual data centers edge.

The following services are available:

| Service | IP address |
|---|---|
| NTP | 52.117.132.3 |
| RHEL and CentOS YUM repository | 52.117.132.3 |
| Microsoft Windows Update Server | 52.117.132.5 |
| Cloud Object Storage | 52.117.132.6 |

Enabling access to the service network is done in two edge configuration steps.

## Adding the NAT rule
{: #shared-private_network-nat-rule}

Add a NAT rule for translating internal network addresses into the service network IP address space.
1. Log in to the VMware vCloud Director portal.
2. Click the virtual datacenter **Edges** tab and open the single preconfigured edge.
3. Find the name of the service network and the IP address that is assigned for the service network interface from the **IP Addresses** table in the **Edge Gateway Settings** section. The format for the service network name is `w<idx>-service<idx>`, for example, `w02-service02`.
4. Click **CONFIGURE SERVICES** to open the Edge Gateway configuration page, click the SNAT tab and click **+SNAT RULE** to add a SNAT rule.
5. Select the service network next to the **Applied on** field, add the IP addresses or range from one of the virtual datacenter internal networks to the **Original** field.
6. Add the IP address assigned for the service network interface, which is found next to the **Translated** field, for example,  `52.117.132.68`.
7. Specify `Any` for the **Port** field for the **Original**, **Translated**, and **Protocol** fields.
8. Click **Save changes**.

## Adding the firewall rule
{: #shared-private_network-firewall-rule}

Add a firewall rule to allow the traffic from the internal network to the service network.
1. Click the **Firewall** tab and click **+** to add a firewall rule.
2. Add the IP addresses or range from your internal network to the **Source** field.
3. Add `52.117.132.1/24` in the **Destination** field.
4. Specify `Any` for the **Service** field and `Accept` for the **Action** field.
5. Click **Save changes**.

After the previous configuration is completed, you can use the supported IBM Cloud services on the VMs in your virtual data center.

If your vApp or VM is deployed from the IBM templates provided in the public catalog, the services are already configured on the VM. To enable the connection, you must complete the steps in [Adding the NAT rule](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared-private_network#shared-private_network-nat-rule) and [Adding the firewall rule](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared-private_network#shared-private_network-firewall-rule).

The service network is a shared network among all virtual data center customers and should be treated similarly to a public network connection.
{:note}

## Related links
{: #shared_private_network-related}

* [Ordering Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Ordering Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [Managing {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [IBM Cloud for VMware Solutions Shared operations](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vcd-ops-guide)
* [VMware vCloud Director](https://docs.vmware.com/en/vCloud-Director/9.7/com.vmware.vcloud.tenantportal.doc/GUID-74C9E10D-9197-43B0-B469-126FFBCB5121.html){:external}
