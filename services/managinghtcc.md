---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-03"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing HyTrust CloudControl
{: #managinghtcc}

To manage the HyTrust CloudControl service (HTCC), access the HTCC WebGUI from the {{site.data.keyword.vmwaresolutions_full}} console, or access the HTCC console from the vSphere Web Client.

## Accessing the HyTrust CloudControl WebGUI from the IBM Cloud for VMware Solutions console
{: #managinghtcc-accessing-webgui}

To log in to the WebGUI of the primary or secondary HTCC appliance, use the WebGUI credentials found on the HyTrust CloudControl service details page.

## Accessing the HyTrust CloudControl console from the vSphere Web Client
{: #managinghtcc-accessing-console}

To access the HTCC console from the vSphere Web Client, use the following procedure:
1. In the vSphere Web Client, find the virtual machines that are named **CC1** and **CC2**.
2. Right-click **CC1** or **CC2**, and then click **Open Console**.
3. Log in to the console by using the console credentials that you can find on the HyTrust CloudControl service details page.

For more information, see [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices).

## Known issue about Network Time (NTP) displayed as disabled
{: #managinghtcc-known-issue-ntp}

On the web console for Hytrust CloudControl v5.6, if you navigate to General > Health, the Network Time (NTP) value in the Services section might be shown as disabled. Although the value shows disabled on the console, NTP is working as expected.

## Enabling internet access for the HyTrust CloudControl VMs
{: #managinghtcc-internet-access}

For HTCC 5.5.1 and later, {{site.data.keyword.vmwaresolutions_short}} provides automatic renewal support for HyTrust licenses that have the Call Home feature enabled. For vCenter Server instances that are not private-only, HTCC is deployed with firewall and SNAT (Source Network Address Translation) rules that are defined on the management services ESG **mgmt-nsx-edge**.

These rules allow you to enable internet access for the HyTrust virtual machines (VMs). If internet access is not enabled, the license that is applied to your HTCC installation will expire after a year.

For private-only vCenter Server environments, the VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge** is not added, therefore the firewall and SNAT rules are not defined. As a result, internet connectivity cannot be enabled for private-only instances and HyTrust licenses expire annually.
{:note}

### Procedure to find the firewall and SNAT rules defined
{: #managinghtcc-proc-find-firewall}

1. Log in to the VMware vSphere Web Client (FLEX) and find the ESG **mgmt-nsx-edge**.
2. Click **Home > Networking & Security > NSX Edges**.
3. Double-click the ESG **mgmt-nsx-edge** and click the **Manage** tab.
4. Go to the **Firewall** tab and find the HyTrust rules. Note the source IP addresses. These are the IP addresses for the HyTrust VMs.
5. Go to the **NAT** tab and find the SNAT rules that are created for the HyTrust VMs. The source IP addresses will match the IP addresses that you noted in the previous step.

### Procedure to enable internet connectivity for HTCC
{: #managinghtcc-enable-internet}

These following steps apply for updating the HTCC network settings on the primary virtual machine (VM), which is used for the license upgrades. You don't need to update the settings for the secondary VM.
{:note}

1. Complete steps 1-3 in the previous procedure.
2. Click **Settings** and then click **Interfaces**. Note the IP address for the private uplink, which becomes the new default gateway. 
3. Go to the HyTrust CloudControl service details page, click **View HTCC Web UI** and log in with the credentials from the service details page.
4. Note the existing default gateway. For example, for HTCC 5.6, click **Configuration > Network**. Note the gateway IP address that is listed, which becomes the gateway for the static route.
5. Add a static route. For example, for HTCC 5.6, click **Configuration > Static Routes**. Click **Add**, enter the following information, and click **OK**.

  ```
  Network Address: 10.0.0.0
  Mask: 255.0.0.0
  Gateway: IP noted in step 4
  Device: Network 1
  ```

6. Change the default gateway. For example, for HTCC 5.6, click **Configuration > Network** and replace the IP address in the **Gateway** field with the one you noted in Step 3 and click **Save**. 

  Ensure that you set the static route before you change the default gateway, otherwise the web console might become unreachable.
  {:important}

  The primary VM will now have access to the internet.

7. To confirm that the primary VM has internet access, run a `wget` command to a public IP address or website. To do so, go back to vCenter and right-click **CC1 > Open Console**. Log in to the console by using the console credentials from the HyTrust CloudControl service details page. Run a `wget` command such as `wget www.ibm.com`, and you should get an immediate response. Confirm that the request was sent and a `200` response was received.

## Related links
{: #managinghtcc-related}

* [HyTrust CloudControl overview](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [HyTrust website](https://www.hytrust.com/){:external}
