---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

{:faq: data-hd-content-type='faq'}

# Networking considerations for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_networkingonvcenterserver}

Review the following information for details about networking considerations and requirements for your VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle instances. Ensure that you meet the requirements so that your instance functions properly.

## Networking components for vCenter Server with Hybridity Bundle instances
{: #vc_hybrid_networkingonvcenterserver-networking-components}
{: faq}

To review the networking components that are included in your vCenter Server with Hybridity Bundle instance, see [Technical specifications for vCenter Server with Hybridity Bundle instance](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#specs).

## Firewall considerations
{: #vc_hybrid_networkingonvcenterserver-firewall-considerations}
{: faq}

If you're using firewalls, you must configure rules for all communications from the {{site.data.keyword.IBM}} CloudDriver virtual server instance (VSI) and the SDDC Manager virtual machines (VMs). These rules must allow all protocols to communicate on the IP addresses `10.0.0.0/8` and `161.26.0.0/16`. Examples of such firewalls are NSX Distributed Firewalls (DFW) or Vyatta firewalls.

## Using NSX with your virtual machines
{: #vc_hybrid_networkingonvcenterserver-using-nsx-with-vm}
{: faq}

During vCenter Server instance deployment, VMware NSX is ordered, installed, licensed, and configured in your instance. Also, NSX Manager, NSX Controllers, and NSX Transport Zone are set up, and each ESXi server is configured with the NSX components.

An NSX Edge Services Gateway is also deployed to be used by your workload virtual machines (VMs). For more information, see [Configuring your network to use the customer-managed NSX ESG with your VMs](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Considerations when changing passwords for NSX components
{: #vc_hybrid_networkingonvcenterserver-change-nsx-component-password-considerations}
{: faq}

Review the following considerations before you change the passwords for the NSX Manager, NSX Controllers, and NSX Edges:
* Do not change the NSX Manager's password that you can find on the **Summary** page of the instance in the {{site.data.keyword.vmwaresolutions_short}} console.
* You can change passwords for NSX Controllers. For instructions on how to change passwords for NSX Controllers, see [Change Controller Password](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* You can change the password and SSH settings for the customer-managed VMware NSX Edge Services Gateway (ESG). Do not change the password for the Management VMware NSX Edge Services Gateway (ESG) and related Distributed Logical Router.

## Related links
{: #vc_hybrid_networkingonvcenterserver-related}

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
* [VMware HCX on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
