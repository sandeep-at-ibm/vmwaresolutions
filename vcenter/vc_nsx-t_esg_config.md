---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuring your network to use the customer-managed NSX-T ESG with your VMs
{: #vc_nsx-t_esg_config}

Configure the network for your virtual machines so you can take advantage of the VMware NSX-T Edge Services Gateway (ESG) that is deployed in your VMware vCenter Server instances. For more information about the security measures that are in place to help minimize security risk, see [Does the management services NSX Edge pose a security risk?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX-T is a network virtualization platform that allows the virtualization of isolated networks and provides several networking
services such as switches, routing, and firewalls. For more information about NSX, see [Overview of NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

As part of the ordering process for your vCenter Server with NSX-T instance, the following actions are completed on your behalf:
* A private customer subnet is ordered to be used by your VMs (virtual machines) to access the {{site.data.keyword.cloud}} infrastructure private network.
* A public customer subnet is ordered to allow your VMs to access the internet.
* NSX-T is deployed and configured in your vCenter Server with NSX-T instance.
* A sample NSX-T Logical Switch is deployed to be used by the customer workload VMs.
* A sample NSX-T Tier 1 router is deployed for potential east-west communication between local workloads that are connected to layer 2 (L2) networks.
* An NSX-T Edge appliance is deployed and configured to perform network address translation (NAT) from the range of IP addresses of the workload logical switch to a public IP address on the NAT rules.

  The NSX-T edge is not deployed for instances that are private only.
  {:note}

## Procedure to configure the networking settings for your VMs
{: #vc_nsx-t_esg_config-procedure-config-networking}

To take advantage of NSX-T for your workload VMs, you must configure a number of settings by completing the following steps when you create your VMs:

1. Set the network adapter of the VM to the workload logical switch:
   1. On the **New Virtual Machine** dialog box, click the **Customize Hardware** tab.
   2. On the **new device** menu, select **Network** and click **Add**.
   3. On the newly added network adapter, select the workload overlay logical switch from the menu. The example name of the switch is **overlay-ls**.

   Ensure that you do not select the **Workload Transit** switch.
   {:important}

2. Identify an available IP address for the VM:
   *  The IP address must be in the range of `192.168.10.0/24`. Note that the IP address `192.168.10.1` is reserved (see **Step 3**).
   *  When you configure the networking of the operating system that runs on the VM, use the selected IP address and the netmask
   `255.255.255.0`.

   You are responsible for managing the range of IP addresses to which you assigned your VMs.
   {:note}

3. Assign the default gateway of the VM as `192.168.10.1`. This is the IP address of the downlink router port on the customer Tier 1 logical router and is connected to the same overlay logical switch as the workload VMs.

## Enabling the SNAT rule
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

NSX-T enables the SNAT rule by default. For information about modifying the existing rules, see [Configure Source and Destination NAT on a Tier-0 Logical Router](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.4/administration/GUID-45949ACD-9029-4674-B29C-C2EABEB39E1D.html){:new_window}.

## Procedure to identify customer subnets details
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

The logical routers **Customer-T1-LR** and **Customer-T0-LR** as well as edges **cust-nsx-edge0** and **cust-nsx-edge1** are intended for your own usage, so you can modify it to define more NAT rules for inbound or outbound traffic. These rules must use only the IP addresses on the public or private customer subnets that are ordered on your behalf.

To identify the details for the customer subnets so you can use the IP addresses ordered, complete the following steps in the NSX-T Web Client:

1. Click the **Advanced Networking & Security** tab.
2. On the left pane, click **Fabric**, then on the drop-down list select **Nodes**.
3. On the tab, select **Edge Transport Nodes**.
4. Click one of the customer edges. For example, **cust-nsx-edge0**. The public and private customer subnets are displayed in the **Description** field.

Additionally, you can find more details about the customer subnets by completing the following steps in the {{site.data.keyword.slportal}}:

1. Click **Networking > IP Management > Subnets**.
2. Click the filter menu and in the **Subnet** field enter the identifier as seen in the description of **customer-nsx-edge0** in the NSX-T Web Client.
3. Review the notes that are shown for the IP addresses. These notes identify which of the subnets and IP addresses are ordered and used during the initial setup.

   Do not use the IP addresses that are ordered and used during the initial setup. However, you can use other IP addresses on these subnets according to your requirements. To set up additional network address translation rules, see [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.
   {:important}

## Related links
{: #vc_nsx-t_esg_config-related}

* [Considerations about changing vCenter Server artifacts](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [FAQs](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
