---

copyright:

  years:  2016, 2021

lastupdated: "2021-01-28"

keywords: HTKC WebGUI, HTKC console, enable internet HTKC

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing HyTrust KeyControl
{: #managinghtkc}

To manage the HyTrust® KeyControl™ service (HTKC), access the HTKC Web GUI from the {{site.data.keyword.vmwaresolutions_full}} console, or access the HTKC console from the vSphere® Web Client.

## Accessing the HyTrust KeyControl Web GUI from the VMware Solutions console
{: #managinghtkc-accessing-webgui}

To log in to the Web GUI of the primary or secondary HTKC appliance, use the WebGUI credentials found on the HyTrust KeyControl service details page.

## Accessing the HyTrust KeyControl console from the vSphere Web Client
{: #managinghtkc-accessing-console}

To access the HTKC console from the vSphere Web Client, use the following procedure:
1. In the vSphere Web Client, find the virtual machines starting with the names **KC1** and **KC2** that have the matching IP address found on the HyTrust KeyControl service details page.
2. Right-click **KC1** or **KC2**, and then click **Open Console**.
3. Log in to the console by using the console credentials that you can find on the HyTrust KeyControl service details page.

For more information, see [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices).

## Enabling internet access for the HyTrust KeyControl virtual machines
{: #managinghtkc-internet-access}

For HTKC 4.3.2 and later, {{site.data.keyword.vmwaresolutions_short}} provides automatic renewal support for HyTrust licenses that have the Call Home feature enabled. For VMware vCenter Server® instances that are not private-only, HTKC is deployed with firewall and SNAT (Source Network Address Translation) rules that are defined on the management services ESG **mgmt-nsx-edge**.

These rules allow you to enable internet access for the HyTrust virtual machines (VMs). If internet access is not enabled, the license that is applied to your HTKC installation will expire after a year.

For private-only vCenter Server environments, the VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge** is not added, therefore the firewall and SNAT rules are not defined. As a result, internet connectivity cannot be enabled for private-only instances and HyTrust licenses expire annually.
{:note}

### Procedure to find the firewall and SNAT rules defined
{: #managinghtkc-proc-find-firewall}

1. Log in to the VMware vSphere Web Client (FLEX) and find the ESG **mgmt-nsx-edge**.
2. Click **Home > Networking & Security > NSX Edges**.
3. Double-click the ESG **mgmt-nsx-edge** and click the **Manage** tab.
4. Go to the **Firewall** tab and find the HyTrust rules. Note the source IP addresses. These are the IP addresses for the HyTrust VMs.
5. Go to the **NAT** tab and find the SNAT rules that are created for the HyTrust VMs. The source IP addresses will match the IP addresses that you noted in the previous step.

### Procedure to enable internet connectivity for HTKC
{: #managinghtkc-proc-enable-internet}

1. Complete steps 1 - 3 in the previous procedure.
2. Click **Settings** and then **Interfaces**. Note the IP address for the private uplink. This address will be the new default gateway.
3. Click **Home > Hosts and Clusters** and find the HyTrust VMs. Right-click one of the VMs and click **Open Console**.
4. Log in to the console by using the console credentials that you can find on the HyTrust KeyControl service details page on the {{site.data.keyword.vmwaresolutions_short}} console.
5. To get the current default gateway IP address from the VM, click **Manage Network Settings > Show Current Network Configuration**. Note the IP address that is listed for **Gateway**. This address becomes the gateway used for the static route.
6. To set a static route for the VM, click **Manage Network Settings > Manage Static Routes > Add Static Route**. Set **Network address** to `10.0.0.0/8` and **Gateway** to the IP address noted in the previous step.
7. To set the default gateway IP for the VM, click **Manage Network Settings > Change Current Network Configuration**. If you get a warning message, click **OK**, then click **Custom Configuration**. Set the **Gateway** field to the private uplink IP address noted in step 2 and click **OK**. Wait until the new network configuration is installed and the network services are restarted.
8. If you see a message asking for HyTrust SecureOS reauthentication, click **OK** and enter the IP address of the other HyTrust VM for this installation. If you are asked for a 16-character passphrase, press Enter to return to the main menu. Verify the current network configuration to ensure that your changes are applied.
9. To confirm that the VM has access to the internet, ping a public IP address or website. Click **Manage Network Settings > Network Diagnostic Tools > Test Inbound Ports of Another Server**. Type a public website address, for example, `www.ibm.com`, click **OK**, type `80 443` for the ports (or any other ports you want to test), and you should get an immediate response showing the inbound ports with a message similar to `80 (OK) 443 (OK)`.
10. Repeat steps 3 - 9 for the other HyTrust VM.

## Related links
{: #managinghtkc-related}

* [HyTrust KeyControl overview](/docs/vmwaresolutions?topic=vmwaresolutions-htkc_considerations)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [HyTrust website](https://www.hytrust.com/){:external}
