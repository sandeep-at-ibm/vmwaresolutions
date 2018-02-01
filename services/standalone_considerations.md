---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-31"

---

# Considerations for on-premises HCX instances

Review the following considerations before you install or delete the HCX instances that you ordered for on-premises use.

## Considerations when installing on-premises HCX instances

The HCX components must be installed both on {{site.data.keyword.cloud}} and in your on-premises vSphere environment. It is recommended that you install the HCX on {{site.data.keyword.cloud_notm}} service into your Cloud Foundation instance or vCenter Server instance on {{site.data.keyword.cloud_notm}} before you install the on-premises HCX instance. For more information, see [Considerations for HCX on IBM Cloud](../services/hcx_considerations.html).

You must complete the following tasks for a successful installation of the on-premises HCX instance:
1. In the {{site.data.keyword.vmwaresolutions_short}} console, complete the following steps:
    1. Click **Deployed Instances** from the left navigation pane.
    2. Click the Cloud Foundation instance or vCenter Server instance with the HCX on {{site.data.keyword.cloud_notm}} service installed. This is the cloud side that you want to connect to from your on-premises vSphere environment.
    3. On the **Services** tab, click **Installed Services**.
    4. Click the **HCX on IBM Cloud** card.
    5. Click **View HCX Cloud Console**, and then log in to the console by using the vCenter Server credentials to view the details of the cloud-side HCX service.
2. In the **HCX Cloud Console**, complete the following steps:
    1. Click the **Administration** tab.
    2. On the **System Updates** tab, click **REQUEST DOWNLOAD LINK**.
    3. Click **COPY LINK**, and then use this link to download the HCX Enterprise Client onto an on-premises environment with access to your on-premises vSphere environment.
3. In the VMware vSphere Web Client, deploy the HCX Enterprise Client as an HCX Manager virtual appliance (HCX Manager) into your on-premises environment.

   **Note**: You must deploy the on-premises HCX Manager on a private network and allow it to access the public network. You can use an NSX Edge, Vyatta, or similar gateways to allow Internet access to the on-premises HCX Manager. If the gateways used for private network access and public network access are different, it is recommended that you use the default gateway to allow for public network access and the on-premises **HCX Manager Admin Console** to create a static route for private network access.
4. After the HCX Manager deployment is completed, use the **HCX Manager Admin Console** to activate the on-premises HCX Manager. To obtain an activation key for the on-premises HCX Manager, order an on-premises HCX instance in the {{site.data.keyword.vmwaresolutions_short}} console. For more information, see [Ordering on-premises HCX instances](../services/standalone_orderingserviceinstances.html).
5. If you used a self-signed SSL certificate when ordering the HCX on {{site.data.keyword.cloud_notm}} service, you must import the certificate into the on-premises HCX Manager by completing the following steps:
    1. In the on-premises **HCX Manager Admin Console**, click the **Administration** tab.
    2. From the left navigation pane, click **Trusted CA Certificate**, and then click **IMPORT** on the right.
    3. Click **URL** and then enter the URL of the certificate you want to apply, that is the **HCX Cloud IP** (``https://<cloud-side public IP>``), which you can find on the HCX on {{site.data.keyword.cloud_notm}} service details page in the {{site.data.keyword.vmwaresolutions_short}} console.
    4. Click **APPLY**.

You now completed the basic setup of the on-premises HCX Manager. You can proceed to pair the on-premises HCX site with the cloud-side HCX site.

For more information, see [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx).

## Considerations when deleting on-premises HCX instances

Review the following considerations before you delete an HCX instance that was ordered for on-premises use:
1. In the VMware vSphere Web Client, go to the HCX user interface, and then check the following items:
    1. Ensure that no HCX migration or disaster recovery operation is running.
    2. Ensure that all the extended networks are removed.
    3. Ensure that all the interconnect components with paired cloud sites are removed.

   **Important**: You must complete all the above checkings before you proceed to the next step. Otherwise, the license for the on-premises HCX instance is cancelled, because of which migrations cannot be performed and errors might occur to the HCX components.  
2. In the {{site.data.keyword.vmwaresolutions_short}} console, delete the on-premises HCX instance that was ordered to obtain the activation key for the on-premises HCX Manager. Ensure that the deleted instance is no longer available in the console before you proceed to the next step.

   For more information, see [Deleting on-premises HCX instances](../services/standalone_deletingserviceinstances.html).
3. In the VMware vSphere Web Client, delete the on-premises HCX Manager.

For more information, see [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx).

## Related links

* [Viewing on-premises HCX instances](../services/standalone_viewingserviceinstances.html)
* [Glossary of HCX terms](hcx_glossary.html)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#vm-documentation)
<!--* [VMware HCX Enterprise installation and user guide](https://hcx.vmware.com/content/docs/vmware-hcx-enterprise-install-guide.pdf){:new_window}-->
* [Contacting IBM Support](../vmonic/trbl_support.html)
