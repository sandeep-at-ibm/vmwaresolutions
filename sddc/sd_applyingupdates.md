---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-26"

---

{:tip: .tip}

# Applying updates to Cloud Foundation instances

The {{site.data.keyword.vmwaresolutions_full}} console periodically detects and lists the available software updates that you can apply to your VMware virtual environment.

An available update is a record in the software updates list of the instance, which can be applied immediately or scheduled for a later time. The update is a bundle that contains one or more packages for updating the IBM management components and the VMware components.

## Before you begin

<!-- **Note**: Because the V1.7 release updates the VMware NSX for vSphere version from 6.2.4 to 6.2.6, it is recommended to review and complete any required steps from the VMware documentation. For more information, see [Preparing for the NSX Upgrade](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.upgrade.doc/GUID-CCA34724-2621-4A5C-B2DC-65596AC46EBB.html){:new_window}. -->

Before you attempt to apply an update, expand the update entry by clicking the down arrow and verify the following information:
*  The version of the update. You must apply the updates in chronological sequence that is from the earliest one to the most recent one. Ensure that you applied all the previous updates before you apply the most recent one. For example, you must apply the V1.6 update before attempting to apply the V1.7 update.
*  Whether downtime is required.
*  The total estimated time to complete the update.
*  The impact of the update on the VMware virtual environment. The following list shows how different levels of impact affect the
system:

    <dl class="dl"><dt class="dt dlterm">Low</dt>
    <dd class="dd">This update does not affect any systems. You do not have to apply it during scheduled
    downtime.</dd>
    <dt class="dt dlterm">Medium</dt>
    <dd class="dd">This update might affect some systems. It is recommended that you apply it during scheduled
    downtime. </dd>
    <dt class="dt dlterm">Major</dt>
    <dd class="dd">This update affects some or all systems. You must apply it during scheduled downtime.</dd>
    </dl>
* The update details.

**Notes**:

* Before an update operation is started, a health check for the instance is completed. If the health check fails, you are notified so you can fix the problem before applying the update.
* Before an update operation is started, a backup of the management virtual machines (VMs) is done automatically, if your instance has the [Veeam service](vc_addingremovingservices.html#available-services-for-vcenter-server-instances) installed. After the backup is completed, the update is applied. During the update operation, do not attempt any provisioning or add ESXi server operations.
* During updates that include VMware components updates, VMs may need to be migrated from ESXi servers to go into maintenance mode. If a VM has a local datastore, or CD-ROM mounted, this might prevent the VM migration.
* During the provisioning of a new environment, {{site.data.keyword.vmwaresolutions_short}} creates the **automationuser** ID that is used for instance management, including for applying updates. Do not change the password for this user ID. Changing the password might cause the update to fail.

## Procedure

1. Click **Deployed Instances** from the left navigation pane.
2. Click the instance to update.
3. Click the **Update and Patch** tab.
4. Click the down arrow to expand the update that you want to apply and then complete one of the following steps:
   *  To start the update immediately, click the overflow menu icon in the **Actions** column of the update entry, and then click
   **Update Now**.
   *  To schedule a future update, click the overflow menu icon in the **Actions** column of the update entry, and then click **Schedule Update**. Select the date, time, and time zone when you want the update to be started. Click **OK**.
5. If you are applying updates to Cloud Foundation instances in multi-site deployment configuration, a section titled **Steps Required to Update** is displayed. This section lists the update operations required for all instances in the multi-site deployment. You must complete the steps in sequence by clicking **Apply Update** for each step. You must wait for the previous step to complete before you start the next step.

## Results

After you apply an update, a record appears in the software update status list, where you can view the detailed progress and status of the update. When the update is completed successfully, a record appears in the installed software updates list.

To retrieve the most recent status for an update job, click the refresh icon in the upper right of the page.
{:tip}

If the update process fails at a specific step, [contact IBM Support](../vmonic/trbl_support.html) for assistance. You will be advised how to resolve the problem and guided to restart the upgrade from the step that failed.

For details about the update statuses, see the following list:
<dl class="dl">
<dt class="dt dlterm">Available</dt>
<dd class="dd">The update is available to be applied. You cannot select an available update until all its previous updates are applied.
</dd>
<dt class="dt dlterm">In progress</dt>
<dd class="dd">The update job is initiated but not finished yet. You cannot apply any other updates until the current update job is
completed.</dd>
<dt class="dt dlterm">Installed</dt>
<dd class="dd">The update job is completed. The corresponding component of the VMware platform is updated.</dd>
<dt class="dt dlterm">Failed</dt>
<dd class="dd">The update job fails. The console reports an error for the update failure. Review the error and fix the reported issue
before you reapply the update.</dd>
<dt class="dt dlterm">Scheduled</dt>
<dd class="dd">The update job is scheduled for a later time. The update job starts automatically at the time that you scheduled.</dd><dt class="dt dlterm">Unknown</dt>
<dd class="dd">The status of the update job cannot be obtained. Contact IBM Support for assistance.</dd>
</dl>

## Related links

* [Cloud Foundation overview](../sddc/sd_cloudfoundationoverview.html)
* [Veeam on IBM Cloud](../services/veeam_considerations.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQs](../vmonic/faq.html)
