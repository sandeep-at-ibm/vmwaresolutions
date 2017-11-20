---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-10"

---

# Networking considerations for vCenter Server instances

Review the following information for details about networking considerations and requirements for your vCenter Server instances. Ensure that you meet the requirements so that your instance functions properly.

## Networking components for vCenter Server instances

To review the networking components that are included in your vCenter Server instance, see [vCenter Server instance components](vc_vcenterserveroverview.html#vcenter-server-instance-components).

## Firewall considerations

If you are using NSX Distributed Firewalls (DFW), review the following requirements:
* You must configure rules for all communications from the IBM CloudDriver virtual machine (VM) to allow all protocols to communicate on the IP addresses `10.0.0.0/8` and `161.26.0.0/16`.
* You must create a DFW rule that allows for HTTPS traffic from the IBM CloudDriver VM to any destination.
* The DFW rule must come before any other rules that would block traffic to or from these VMs.

## Using NSX with your Virtual Machines

During vCenter Server instance deployment, VMWare NSX is ordered, installed, licensed, and configured in your instance. Also, NSX Manager, NSX Controllers, and NSX Transport Zone are set up, and each ESXi server is configured with the NSX components.

An NSX Edge Services Gateway is also deployed to be used by your workload VMs. For more information, see [Configuring your network to use the customer-managed NSX ESG with your VMs](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Considerations when changing passwords for NSX components

Review the following considerations before you change the passwords for the NSX Manager, NSX Controllers, and NSX Edges:
* Do not change the NSX Manager's password that you can find on the **Summary** tab of the instance details page in the {{site.data.keyword.vmwaresolutions_short}} console.
* You can change passwords for NSX Controllers. For instructions on how to change passwords for NSX Controllers, see https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html.
* You can change the password and SSH settings for the customer-managed VMware NSX Edge Services Gateway (ESG). Do not change the password for the Management VMware NSX Edge Services Gateway (ESG) and related Distributed Logical Router.

## Related links

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/content/architecture/virtVCenterServerPlatform/nsx-esg){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
