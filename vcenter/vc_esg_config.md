---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-19"

---

# Configuring your network to use the customer-managed NSX ESG with your VMs

Configure the network for your virtual machines so you can take advantage of the VMware NSX Edge Services Gateway (ESG) that is deployed in your VMware vCenter Server instances. For information about the security measures that are in place to help minimize security risk, see [Does the management services NSX Edge pose a security risk?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX is a network virtualization platform that allows the virtualization of isolated networks and provides several networking
services such as switches, routing, and firewalls. For more information about NSX, see [Overview of NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

As part of the ordering process for your vCenter Server instance, the following actions are completed on your behalf:
* A private customer subnet is ordered to be used by your VMs (virtual machines) to access the {{site.data.keyword.cloud}} infrastructure (SoftLayer) private network.
* A public customer subnet is ordered to allow your VMs to access the internet.
* NSX is deployed and configured in your vCenter Server instance.
* A sample NSX Logical Switch is deployed to be used by the customer workload VMs.
* A sample NSX Distributed Logical Router (DLR) is deployed for potential east-west communication between local workloads that are connected to layer 2 (L2) networks.
* An NSX Edge appliance is deployed and configured to perform network address translation (NAT) from the range of IP addresses of the
workload logical switch to a public IP address on the NAT rules.
* The NSX Manager is configured to do a daily backup of the NSX configurations. For more information, see [Considerations when installing Veeam on IBM Cloud](../services/veeam_considerations.html#considerations-when-installing-the-veeam-on-ibm-cloud-service).


## Configuring the networking settings for your VMs

To take advantage of NSX for your workload VMs, you must configure a number of settings by completing the following steps when you create your VMs:

1. Set the network adapter of the VM to the workload logical switch:
   1. On the **New Virtual Machine** dialog box, click the **Customize Hardware** tab.
   2. On the **new device** menu, select **Network** and click **Add**.
   3. On the newly added network adapter, select the workload logical switch from the menu. An example name of the workload logical switch
   is **vxw-dvs-17-virtualwire-1-sid-6000-Workload**.

   **Important:** Ensure that you do not select the **Workload Transit** switch.

2. Identify an available IP address for the VM:
   *  The IP address must be in the range of `192.168.10.0/24`. Note that the IP address `192.168.10.1` is reserved (see **Step 3**).
   *  When you configure the networking of the operating system that runs on the VM, use the selected IP address and the netmask
   `255.255.255.0`.

   **Note:** You are responsible for managing the range of IP addresses to which you assigned your VMs.

3. Assign the default gateway of the VM as `192.168.10.1`. This address is the IP address of the NSX DLR on the same logical switch as the workload VMs.

## Enabling the SNAT rule

If you want your workload VMs to have outbound access to the internet, you must enable the associated SNAT (Source Network Address Translation) rule. Enabling the SNAT rule allows internet access from your VMs to be translated to a single public IP address. Complete the following steps in the VMware vSphere Web Client:

1. Click **Home > Networking & Security**.
2. On the navigator pane, click **NSX Edges** and double-click the edge that is named **customer-nsx-edge**.
3. Click **Management > NAT** to open the **NAT** tab.
4. Select the default SNAT rule in the table and click the green check mark above the table to enable the rule.

For more information about NSX Edge NAT rules, see [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.

## Identifying customer subnets details

The edge **customer-nsx-edge** is intended for your own usage, so you can modify it to define more NAT rules for inbound or outbound traffic. These rules must use only the IP addresses on the public or private customer subnets that are ordered on your behalf.

To identify the details for the customer subnets so you can use the IP addresses ordered, complete the following steps in the VMware vSphere Web Client:

1. Click **Home > Networking & Security**.
2. On the navigator pane, click **NSX Edges** and double-click the **customer-nsx-edge edge**.
3. On the **Summary** tab for this edge, review the edge description, which contains the subnet identifiers for both the private and public customer subnets.

Additionally, you can find more details about the customer subnets by completing the following steps in the IBM Cloud infrastructure customer portal:

1. Click **Networking > IP Management > Subnets**.
2. Click the filter menu and in the Subnet field enter the identifier as seen in the description of the **customer-nsx-edge** edge on the **Summary** tab in the VMware vSphere Web Client.
3. Review the notes that are shown for the IP addresses. These notes identify which of the subnets and IP addresses are ordered and used during the initial setup.

   **Warning:** Do not use the IP addresses that are ordered and used during the initial setup. However, you can use other IP addresses on
   these subnets according to your requirements. To set up additional network address translation rules, see [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.

## Related links

* [NSX Edge Services Gateway](https://www.ibm.com/devops/method/content/architecture/virtVCenterServerPlatform/nsx-esg){:new_window}
