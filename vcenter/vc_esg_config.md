---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-14"

keywords: vCenter Server network config, network configuration, manage NSX ESG

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuring your network to use the customer-managed NSX ESG with your VMs
{: #vc_esg_config}

Configure the network for your virtual machines (VMs) so you can take advantage of the VMware NSX Edge Services Gateway (ESG) that is deployed in your VMware vCenter Server instances. For more information about the security measures that are in place to help minimize security risk, see [Does the management services NSX Edge pose a security risk?](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions#faq-mgmt-nsx)

VMware NSX is a network virtualization platform that allows the virtualization of isolated networks and provides several networking
services such as switches, routing, and firewalls. For more information about NSX, see [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:external}.

As part of the ordering process for your vCenter Server instance, the following actions are completed on your behalf:
* A private customer subnet is ordered to be used by your VMs to access the {{site.data.keyword.cloud}} infrastructure private network.
* A public customer subnet is ordered to allow your VMs to access the internet.
* NSX is deployed and configured in your vCenter Server instance.
* A sample NSX Logical Switch is deployed to be used by the customer workload VMs.
* A sample router (NSX Distributed Logical Router for NSX-V and NSX-T Tier 1 Router for NSX-T) is deployed for potential east-west communication between local workloads that are connected to layer 2 (L2) networks.
* An NSX Edge appliance is deployed and configured to perform network address translation (NAT) from the range of IP addresses of the workload logical switch to a public IP address on the NAT rules.

  The NSX Edge is not deployed for instances that are private only.
  {:note}

**(NSX-V only)** If you installed the Veeam service, the NSX Manager is configured to do a daily backup of the NSX configurations. For more information, see [Considerations when you install Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations#veeam_considerations-install).

## Procedure to configure the networking settings for your VMs
{: #vc_esg_config-procedure-config-networking}

To take advantage of NSX for your workload VMs, you must configure a number of settings by completing the following steps when you create your VMs:

1. Set the network adapter of the VM to the workload logical switch:
   1. On the **New Virtual Machine** dialog box, click the **Customize Hardware** tab.
   2. On the **new device** menu, select **Network** and click **Add**.
   3. On the newly added network adapter, select the workload logical switch from the menu. The example name of the workload logical switch is:
   * For NSX-V: **vxw-dvs-17-virtualwire-1-sid-6000-Workload**
   * For NSX-T: **overlay-ls**

   Ensure that you do not select the **Workload Transit** switch.
   {:important}

2. Identify an available IP address for the VM:
   *  The IP address must be in the range of `192.168.10.0/24`. Note that the IP address `192.168.10.1` is reserved (see **Step 3**).
   *  When you configure the networking of the operating system that runs on the VM, use the selected IP address and the netmask
   `255.255.255.0`.

   You are responsible for managing the range of IP addresses to which you assigned your VMs.
   {:note}

3. Assign the default gateway of the VM as `192.168.10.1`. For NSX-V, this address is the IP address of the NSX DLR on the same logical switch as the workload VMs. For NSX-T, this address is the IP address of the downlink router port on the customer Tier 1 logical router and is connected to the same overlay logical switch as the workload VMs.

## Enabling the SNAT rule for NSX-V
{: #vc_esg_config-procedure-enable-snat-rule}

If you want your workload VMs to have outbound access to the internet, you must enable the associated SNAT (Source Network Address Translation) rule. Enabling the SNAT rule allows internet access from your VMs to be translated to a single public IP address. Complete the following steps in the VMware vSphere Web Client:

1. Click **Home > Networking & Security**.
2. On the navigator pane, click **NSX Edges** and double-click the edge that is named **customer-nsx-edge**.
3. Click **Management > NAT** to open the **NAT** tab.
4. Select the default SNAT rule in the table and click the green check mark above the table to enable the rule.

For more information about NSX Edge NAT rules, see [Managing NAT rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:external}.

## Enabling the SNAT rule for NSX-T
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

NSX-T enables the SNAT rule by default. For information about modifying the existing rules, see [Configure Source and Destination NAT on a Tier-0 Logical Router](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.4/administration/GUID-45949ACD-9029-4674-B29C-C2EABEB39E1D.html){:external}.

## Procedure to identify customer subnets details for NSX-V
{: #vc_esg_config-procedure-identify-customer-subnets-details}

The edge **customer-nsx-edge** is intended for your own usage, so you can modify it to define more NAT rules for inbound or outbound traffic. These rules must use only the IP addresses on the public or private customer subnets that are ordered on your behalf.

To identify the details for the customer subnets so you can use the IP addresses ordered, complete the following steps in the VMware vSphere Web Client:

1. Click **Home > Networking & Security**.
2. On the navigator pane, click **NSX Edges** and locate **customer-nsx-edge edge** in the list of edges in the right pane.
3. In the **Description** column, hover over the edge description for **customer-nsx-edge** to see the subnet identifiers for both the private and public customer subnets.

Additionally, you can find more details about the customer subnets by completing the following steps in the {{site.data.keyword.slportal}}:

1. Click **Networking > IP Management > Subnets**.
2. Click the filter menu and in the **Subnet** field enter the identifier as seen in the description of **customer-nsx-edge** in the VMware vSphere Web Client.
3. Review the notes that are shown for the IP addresses. These notes identify which of the subnets and IP addresses are ordered and used during the initial setup.

   Do not use the IP addresses that are ordered and used during the initial setup. However, you can use other IP addresses on these subnets according to your requirements. To set up additional network address translation rules, see [Managing NAT rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:external}.
   {:important}

## Procedure to identify customer subnets details for NSX-T
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

   Do not use the IP addresses that are ordered and used during the initial setup. However, you can use other IP addresses on these subnets according to your requirements. To set up additional network address translation rules, see [Managing NAT rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:external}.
   {:important}

## Related links
{: #vc_esg_config-related}

* [Troubleshooting](/docs/vmwaresolutions?topic=vmwaresolutions-vcenter_chg_impact#vcenter_chg_impact)
* [FAQs](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:external}
