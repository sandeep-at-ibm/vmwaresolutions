---

copyright:

  years:  2016, 2020

lastupdated: "2020-07-14"

subcollection: vmwaresolutions


---

# HCX client deployment
{: #hcxclient-vcs-client-deployment}

A minimal HCX installation consists of a single cloud and client-side deployment.

The HCX client side can install on any version of vSphere supported by HCX assuming that there is network connectivity between the client and cloud sides.

## Requirements
{: #hcxclient-vcs-client-deployment-req}

| Component | CPU count | Memory (GB) | Disk (GB) |
|--------|--------|---------|-------|
| HCX Manager | 4 | 12G |  60G |
| HCX Interconnect (HCX-IX) | 4 | 3G |  2G |
| HCX Network Extension (HCX-NE) | 4 | 3G |  2G |
| HCX WAN Optimizer (HCX-WAN) | 8 | 14G |  100G |
{: caption="Table 1. Requirements" caption-side="bottom"}

## Client licensing
{: #hcxclient-vcs-client-deployment-licensing}

HCX is a service. HCX is licensed per site and per virtual machine (VM) managed through licensing servers that are maintained by VMware. The HCX cloud and client-side instances require communication with the VMware registration site throughout their lifecycle.
- Traffic on 80 and 443 must be allowed to `https://connect.hybridity.vmware.com`
- A one-time use registration key is provided by the {{site.data.keyword.vmwaresolutions_full}} console is for the client-side installation. A key is required for each client-side HCX installation.

### Procedure to order on-premises HCX licenses
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. Scroll to the **On-premises HCX licenses** table and click **Provision new**.
3. Specify the license name.
4. Click the link or links of the terms that apply to your order, and ensure that you agree with these terms before you order the license.
5. Click **Provision**.

## IP address requirements
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

To deploy the HCX, the proper number of IP addresses must be available both on-premises and in the
target {{site.data.keyword.cloud_notm}}.

* vMotion address
  Maintaining a separate network for vMotion is a common practice in the on-premises data center. The Cloud Gateway must have access to the vMotion network. If it does not, an extra IP address is needed to communicate with the vMotion network.

* On-premises
  * One IP address for the HCX Manager appliance.
  * One for each InterConnect Appliance, add one if there is a separate vMotion network.
  * One for each standard Network Extension

* {{site.data.keyword.cloud_notm}}
  * Two IP addresses per HCX Manager appliance connected to {{site.data.keyword.cloud_notm}}. The addresses can be used to connect to the internet or one or more Direct Connect lines.
  * Add one if there is a separate vMotion network connection.

## Client-side OVA download
{: #hcxclient-vcs-client-deployment-client-ova}

The client-side HCX is user-deployed and it requires administrator level permissions to the source vCenter. As of this writing, the HCX client-side manager ova is approximately 1.7 GB. When use the {{site.data.keyword.vmwaresolutions_short}} console to order HCX, a URL is provided with a link to download the version of HCX for the client-side that matches the version of HCX deployed on the cloud side. This link is provided in the cloud side HCX Manager user interface (UI).

A one-time use registration key is also provided. Use the following steps to configure the use registration.

1. Download HCX client (enterprise) OVA from the link provided in the
cloud side HCX UI.
    1. Log in to the cloud side HCX UI by using the HCX registration UI provided by IBM.
    2. Use the cloud vCenter ID and password to log in to the UI.
    3. On the **Administration** tab, select **request download link** to download the client-side OVA. Use a “jump box” that is local to the source vCenter where the OVA is deployed to complete this step.

## Installing and configuring HCX on the source
{: #hcxclient-vcs-client-deployment-install-cfg-src}

The on-premises installation entails deploying the HCX management appliance and registering it with the vCenter environment.

### Installing the HCX Manager Appliance
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

Install the HCX Manager appliance in the on-premises vCenter.
1. Log in to **My VMware** and download the Hybrid Cloud Services OVA file from the product download page.
2. Open a browser and log in to the vSphere Web Client. View the **Home** tab.
3. In the **Inventories Trees** list, click **Host and Clusters**.
4. Expand the hierarchy to show the data centers.
5. Right-click the target data center and select **Deploy OVF Template** from the menu. It might take a few seconds for the **Deploy OVF template** menu item to appear.
6. Choose **Deploy OVF template**.
  1. Select **Local file** and click **Browse** to find the OVA file downloaded to the computer. Click **Next**.
  2. On the **Review details** page, check the **Accept extra configuration options** box and click **Next**.
  3. On the **Accept EULAs** page, scroll down to review the VMware user license agreement. Click **Accept** and **Next**.
  4. On the **Select name and folder** page, edit the name if necessary and select the location for the Hybrid Cloud Services. Click **Next**.
  5. On the **Select a resource** page, select the installation location.
  6. On the **Select storage** page, select the storage for the Hybrid Cloud Services and click **Next**. From the **Select virtual disk format** list, you can select either **thin provisioning** or **thick provisioning**.
  7. On the **Setup networks** page, map the Hybrid Cloud Services adapter to a host network chosen from the **Destination** list.
7. On the **Customized template** page, enter the values specific to the environment:
  * For the passwords, the default user name for both the command-line interface (CLI) and the web user interface is **admin**. The **admin** user and password to log in to the web user interface is required as is also a **root** user account that has a password that can be set.
  * Enter and reenter the CLI **admin** user password.
  * Enter and reenter the **root** user password. In the future, if help is needed from VMware Global Support Services (GSS), this password might have to be shared so they can troubleshoot the system.
  * For the network properties, enter the host name for the HCX Manager VM. Enter the network IPv4 address, the IPv4 prefix (the CIDR), and the default gateway. The following table shows sample values:

| Field                    | Value           |
|--------------------------|-----------------|
| Hostname                 | HCM_1           |
| Network 1 IPv4 Address   | 192.168.200.101 |
| Network 1 IPv4 Prefix    | 24              |
| Default IPv4 Gateway     | 192.168.200.1   |
| Network 1 IPv6 Address   |                 |
| Network 1 IPv6 Prefix    |                 |
{: caption="Table 2. Sample values for network properties" caption-side="bottom"}

8. Review the vService bindings page. Click **Next** to continue.
9. On the **Ready to complete** page, follow these steps:
  * Check the **Power on after deployment** box.
  * Review the Hybrid Cloud Services settings, and click **Finish**. It might take several minutes for the Hybrid Cloud Services appliance to power on.
  * To check the status, go to the vSphere Web Client home page, and on the **Home** tab, go to **Inventories** and click **Hosts and Clusters**. Expand the data center hierarchy, and click the Hybrid Cloud Services service virtual machine to display a summary in the center pane.
  * View the **Summary** tab, the console reads **Powered On** and the **Play** icon is green.
10. The HCX Manager is powered on and ready to be registered with the on-premises vCenter.

## Initial configuration of the HCX Manager Appliance
{: #hcxclient-vcs-client-deployment-inital-config}

1. Ensure that the Hybrid Cloud Service virtual appliance has outbound access to `https://connect.hcx.vmware.com` and `https://hybridity-depot.vmware.com`
2. Log in to Hybrid Cloud Services virtual appliance admin interface `https://<IP>:9443` with **admin**
3. Provide the license key collected in Client-Side Prerequisites.
4. HCX Cloud Datacenter Location
    - Enter the city nearest to the Datacenter where the HCX Cloud Instance resides. If the city is not present, select the nearest major city.
5. Provide System name

## Import vSphere Server certificate
{: #hcxclient-vcs-client-deployment-import-cert}

1. Log in to HCX Manager Admin Interface `https://<IP>:9443`
2. Select the **Administration** tab, under **Certificate** -> **Trusted CA Certificate**
3. Import vSphere Server website

## Procedure to register HCX Manager with vCenter/SSO/NSX
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. Log in to Hybrid Cloud Services service virtual appliance.
2. On the **Dashboard** pane, complete the following steps:
  1. In the left pane, under **Configure Systems**, select vCenter.
  2. Click **Add vCenter** on the upper right.
  3. Enter the IP address of the vCenter Server in the form `https://vCenter-host-name` or `https://vCenter-IP-address`. For example, `https://My-vCenter` or `https://1.1.1.1`
  4. Enter the vCenter Server user name and password. The account that is used must have the vCenter Administrator role.
  5. Click **OK**. Do not restart when the _You need to restart the app_ message is displayed.
3. Configure the SSO / lookup service.
  6. Click the **Manage** tab.
  7. Click **Edit** next to the **Lookup Service URL** text box.
  8. Enter the lookup network service endpoint in the following form:
    * For vCenter Server 6.5 `https://psc/`
  9.  Provide NSX details if required.
  10. Click **OK**. Do not restart when a message to restart the web engine is displayed.
4. Click the **Summary** tab and find the **Hybridity Management Components** section. Stop and start both the application engine and the web engine.
5. To finalize the registration, log out of the vSphere Web Client. Log back in to vSphere Web Client verify that HCX Tab is present.

## Results
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

Notice the existing **Hybrid Cloud** icon and the **Hybrid Cloud Services** menu item on the left. The Hybrid Cloud Services registration updates these labels. In the inventory, the icon label becomes **Hybrid Cloud Services**.

**Next topic:** [HCX on-premises Service Mesh](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-vcs-mesh-deployment)

## Related links
{: #hcxclient-vcs-client-deployment-related}

* [Glossary of HCX components and terms](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-components)
* [Preparing the installation environment](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-planning-prep-install)
* [VMware Hybrid Cloud migrations](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-migrations)
* [Monitoring parameters and components](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-monitoring)
* [HCX troubleshooting](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-troubleshooting)
