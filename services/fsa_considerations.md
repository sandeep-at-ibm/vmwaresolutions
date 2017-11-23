---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-20"

---

# Components and considerations for FortiGate Security Appliance on IBM Cloud

The FortiGate Security Appliance on {{site.data.keyword.cloud}} service deploys a pair of FortiGate Security Appliance (FSA) service 300 series devices in a highly available mode to provide firewall, routing, NAT, and VPN services to protect all the servers and virtual machines on the public VLAN of your instances. You can manage this service by using the FortiOS Web Client or the command line interface via SSH.

This service is available only to V1.8 and later instances.

You can order an instance with the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service included. For more information, see:
* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)

You can also deploy the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service into your existing instances after initial deployment. For more information, see:
* [Ordering and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)

## FortiGate Security Appliance on IBM Cloud components

As part of the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service, an HA-pair of FortiGate 300 series Security Appliances is ordered in the default public VLAN.

**Note:** The HA-pair of Security Appliances is ordered and will be located on the default public VLAN with the original instance or cluster. If you order additional clusters, the public VLANs for these newly added clusters will not have the HA-pair of Security Appliances.

## Considerations when installing FortiGate Security Appliance on IBM Cloud

Review the following considerations before you install the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service:
* Ensure that the {{site.data.keyword.cloud_notm}} account that you are using has the **Hardware Firewall** permission. This permission is required to edit or view firewall logs and settings for the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service of your instance.
* If you want to add the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service to a deployed instance, ensure that there is no other firewall from {{site.data.keyword.cloud_notm}} infrastructure already in place on the public VLAN of the instance.
* Installing the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service will add a new public VLAN.
* During the service deployment, your instance might not be able to access the internet temporarily.
* After the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service is installed successfully, you can manage and configure firewall rules for the FSA from the FortiGate console. You must ensure that the FSA firewall rules are defined to allow outbound HTTPS (TCP port 443) communications that are started by management components such as the IBM CloudDriver virtual machine or Zerto Virtual Manager to communicate with the external management database on {{site.data.keyword.cloud_notm}} over the Internet. The outbound HTTPS (TCP port 443) communications originate from the public IP address of the management services VMware NSX Edge Services Gateway (ESG) in your instance.
* If you deploy a pair of FortiGate Security Appliance devices as part of a new instance, the FortiGate Security Appliance devices are configured to allow only the required outbound communications from your instance to the public network and deny all other communications.
* If you deploy a pair of FortiGate Security Appliance devices as part of an existing instance, the FortiGate Security Appliance devices are configured with an explicit rule to allow all the required outbound management communications from your instance to the public network. Also, the FortiGate Security Appliance devices are configured with an additional rule to allow all other communications so that your existing application traffic is not interrupted. You must manage the FortiGate Security Appliance  configuration carefully to allow only necessary communications and deny all other communications.

## Considerations when removing FortiGate Security Appliance on IBM Cloud

Review the following considerations before you remove the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service:
* Removing the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service will remove the public VLAN that was added.
* During the service removal, your instance might not be able to access the Internet temporarily.
* All FortiGate rules to permit, inspect, block, and route NAT traffic are removed together with the Fortinet service. If you have any NAT rules, you must reconfigure them.

## Related links

* [Managing FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](managingfsa.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet website](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
