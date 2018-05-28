---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Managing Veeam on IBM Cloud

For instances that were deployed in releases earlier than V1.8, if you want to use the Veeam on {{site.data.keyword.cloud}} service, you must replace the existing Veeam VSI in the instances. After the service is deployed into your instance, you can access the Veeam console by using RDP to manage the backup and restore of all the virtual machines in your environment, including the backup and restore of the management components. You can also upgrade the service by downloading and installing the Veeam updates from the Veeam website.

## Replacing the Veeam VSI of pre-V1.8 instances with Veeam on IBM Cloud

The Veeam on {{site.data.keyword.cloud_notm}} service, which can back up both management components and workloads, supersedes the previous Veeam VSI that was integrated into VMware Cloud Foundation and VMware vCenter Server in releases earlier than V1.8 for the backup of management components only. Because of this change, the previous **Backup and Restore** tab on the instance details page is removed and the backup points for the instances are no longer available in the {{site.data.keyword.vmwaresolutions_short}} console, although the Veeam VSI in the pre-V1.8 instances keeps working. You must create an {{site.data.keyword.cloud_notm}} Support ticket to get assistance with a restore. In addition, the license of the Veeam VSI in pre-V1.8 instances expired on October 14, 2017. Therefore, you must replace the previous Veeam VSI with the new Veeam on {{site.data.keyword.cloud_notm}} service.

Complete the following steps:
1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane, and then click the target instance.
2. On the instance details page, click the **Update and Patch** tab. Ensure that you upgraded the instance to the V1.8 release.
3. Click the **Services** tab.
4. On the **Add Services** tab, install the Veeam on {{site.data.keyword.cloud_notm}} service.

After the new Veeam on {{site.data.keyword.cloud_notm}} service is deployed and a successful backup of your management components is completed, you can remove the existing Veeam VSI from your account by creating an {{site.data.keyword.cloud_notm}} Support ticket. IBM Support will then identify and delete the existing Veeam VSI and storage.

## Accessing the Veeam console by using RDP

To manage the Veeam on {{site.data.keyword.cloud_notm}} service, you must access the Veeam console by completing the following steps:
1. Use Remote Desktop Protocol (RDP) to connect to the Windows IP address that you can find on the Veeam on {{site.data.keyword.cloud_notm}} service details page.
2. Log in to the Windows console by using the Administrator credentials that you can find on the Veeam on {{site.data.keyword.cloud_notm}} service details page.
3. Access the Veeam console from the Windows console by using the Administrator credentials that you can find on the Veeam on {{site.data.keyword.cloud_notm}} service details page.

For more information, see the following topics:
* [Ordering and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)

## Backing up and restoring management components for instances that have Veeam on IBM Cloud installed

The Veeam on {{site.data.keyword.cloud_notm}} service is preconfigured with a management backup job that automatically runs to back up the management components daily with up to 14 points of restoration.

You can also back up the management components manually by using the Veeam console. Starting with the V1.8 release, the configuration changes to your environment are not automatically backed up. Therefore, it is recommended that you perform a manual backup of the management components by running the preconfigured management backup job in the Veeam console before you change the configuration of your environment. For more information on how to perform the manual backup job, see the [Veeam technical instructions](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}.

When failures occur on the management components, you can restore the management components to a previous backup by using the Veeam console. For more information on how to perform the manual restore job, see the [Veeam technical instructions]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}.

## Upgrading Veeam on IBM Cloud

To upgrade the Veeam on {{site.data.keyword.cloud_notm}} service, download the Veeam updates from the Veeam website, copy the updates to the Veeam VSI, and then install them.

## Related links

* [Components and considerations for Veeam on {{site.data.keyword.cloud_notm}}](veeam_considerations.html#components-and-considerations-for-veeam-on-ibm-cloud)
* [Requesting managed services for Veeam on {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam.com website](https://www.veeam.com/)
* [Veeam technical documentation](https://www.veeam.com/documentation-guides-datasheets.html)
