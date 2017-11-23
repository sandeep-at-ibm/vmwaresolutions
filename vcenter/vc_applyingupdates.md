---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-20"

---

{:tip: .tip}

# Applying updates to vCenter Server instances

The {{site.data.keyword.vmwaresolutions_full}} console periodically detects and lists the available software updates and patches that you can apply to your VMware virtual environment.

An available update is a record in the software updates list of the instance, which can be applied immediately or scheduled for a later time. The update is a bundle that contains one or more packages for updating the IBM management components.

## Before you begin

Before you attempt to apply an update, expand the update entry by clicking the down arrow and verify the following information:
*  The version of the update. You must apply the updates in chronological sequence that is from the earliest one to the most recent one. Ensure that you applied all the previous updates before you apply the most recent one. For example, you must apply the V1.6 update before attempting to apply the V1.7 update.
*  Whether downtime is required.
*  The total estimated time of the update.
*  The impact of the update on the VMware virtual environment. The following list shows how different levels of impact affect the system:

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

Before an update operation is started, a backup of the management virtual machines is done automatically, if your instance has the optional [Veeam service](vc_addingremovingservices.html#available-services-for-vcenter-server-instances) installed. After the backup is completed, the update is applied.

## Procedure

1. Click **Deployed Instances** from the left navigation pane. Click the **vCenter Server** tab.
2. Click the instance to update.
3. Click the **Update and Patch** tab.
4. For license upgrades, click **Upgrade License** to upgrade to one of the available NSX editions.

    **Note**: The license upgrade replaces all existing NSX licenses in your {{site.data.keyword.cloud_notm}} account with the new license. Additional charges may be incurred from an overlap of old and new licenses if you upgrade in the middle of a billing cycle. Upgrade the license at the end of the billing cycle to avoid additional charges.

5. For software updates, click the down arrow to expand the update that you want to apply and then complete one of the following steps:
   *  To start the update immediately, click the overflow menu icon in the **Actions** column of the update entry, and then click
   **Update Now**.
   *  To schedule a future update, click the overflow menu icon in the **Actions** column of the update entry, and then click **Schedule
   Update**. Select the date, time, and time zone when you want the update to be started. Click **OK**.
6. If you are applying updates to vCenter servers instances in multi-site deployment configuration, a section titled **Steps Required to Update** is displayed. This section lists the update operations required for all instances in the multi-site deployment. You must complete the steps in sequence by clicking **Apply Update** for each step. You must wait for the previous step to complete before you start the next step.   

## Results

After you apply an update, a record appears in the software update status list, where you can view the detailed progress and status of
the update. When the update is completed successfully, a record appears in the installed software updates list.

To retrieve the most recent status for an update job, click the refresh icon in the upper right of the page.
{:tip}

If the update process fails at a specific step, [contact IBM Support](../vmonic/trbl_support.html) for assistance. You will be advised how to resolve the problem and guided to attempt the upgrade again from the step that failed.

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
<dd class="dd">The update job is scheduled for a later time. The update job starts automatically at the time that you scheduled.</dd>
<dt class="dt dlterm">Unknown</dt>
<dd class="dd">The status of the update job cannot be obtained. Contact IBM Support for assistance.</dd>
</dl>
