---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-07"

keywords: FortiGate security, FortiGate Sirtual Appliance, tech specs FortiGate

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Security Appliance overview
{: #fsa_considerations}

The FortiGate Security Appliance service deploys a pair of FortiGate Security Appliance (FSA) 300 series devices in a highly available mode to provide firewall, routing, NAT, and VPN services to protect all the servers and virtual machines on the public VLAN of your instances.

You can manage this service by using the FortiOS Web Client or the command line interface via SSH.

This service is available only to instances that are deployed in V1.8 or later releases.
{:note}

## Technical specifications for FortiGate Security Appliance
{: #fsa_considerations-specs}

The following components are ordered and included in the FortiGate Security Appliance service:

### Hardware
{: #fsa_considerations-hardware}

The FortiGate 300 series Security Appliance.

### High availability
{: #fsa_considerations-ha}

Two appliances are deployed in active-passive configuration.

### Networking
{: #fsa_considerations-networking}

* Dual 1 GbE bonded on both upstream and downstream networks
* One new upstream {{site.data.keyword.cloud_notm}} public VLAN
* One existing downstream {{site.data.keyword.cloud_notm}} public VLAN

## Considerations when you install FortiGate Security Appliance
{: #fsa_considerations-install}

Review the following considerations before you install the FortiGate Security Appliance service:
* Ensure that the {{site.data.keyword.cloud_notm}} account that you're using has the **Hardware Firewall** permission. This permission is required to edit or view firewall logs and settings for the FortiGate Security Appliance service of your instance.
* If you want to add the FortiGate Security Appliance service to a deployed instance, ensure that no other firewall from {{site.data.keyword.cloud_notm}} infrastructure is already in place on the public VLAN of the instance.
* Installing the FortiGate Security Appliance service adds a new public VLAN.
* During the service deployment, your instance might not be able to access the internet temporarily.
* After the FortiGate Security Appliance service is installed successfully, you can manage and configure firewall rules for the FSA from the FortiGate console. You must ensure that the FSA firewall rules are defined to allow outbound HTTPS (TCP port 443) communications that are started by management components such as the Zerto Virtual Manager to communicate with the external management database on {{site.data.keyword.cloud_notm}} over the internet. The outbound HTTPS (TCP port 443) communications originate from the public IP address of the management services VMware NSX Edge Services Gateway (ESG) in your instance.
* You must manage the FortiGate Security Appliance configuration carefully to allow only necessary communications and deny all other communications.
* If you order additional clusters, the public VLANs for these newly added clusters do not have the HA-pair of Security Appliances.

**Notes**:

* Before the service is installed in your environment, a check is performed against the available capacity of the default cluster in the environment to ensure that the service components can fit.
* If the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email.
* To install the service, you must increase the capacity in your default cluster by either adding more hosts or by freeing up RAM, CPU, or disk space, and then add the service again in the console. After that, you can remove the existing service in the **Capacity Validation Failed** state by clicking the delete icon next to it.

## Considerations when you remove FortiGate Security Appliance
{: #fsa_considerations-remove}

Review the following considerations before you remove the FortiGate Security Appliance service:
* Removing the FortiGate Security Appliance service removes the public VLAN that was added.
* During the service removal, your instance might not be able to access the internet temporarily.
* All FortiGate rules to permit, inspect, block, and route NAT traffic are removed together with the Fortinet service. If you have any NAT rules, you must reconfigure them.

## Related links
{: #fsa_considerations-related}

* [Ordering FortiGate Security Appliance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Managing FortiGate Security Appliance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Fortinet website](https://www.fortinet.com/){:external}
* [Fortinet Document Library](https://docs.fortinet.com/product/fortigate/6.2){:external}
