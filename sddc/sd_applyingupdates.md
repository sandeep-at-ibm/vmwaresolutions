---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

{:tip: .tip}

# Applying updates to Cloud Foundation instances

The {{site.data.keyword.vmwaresolutions_full}} console periodically detects and lists the available software updates that you can apply to your VMware virtual environment.

An available update is a record in the software updates list of the instance, which can be applied immediately or scheduled for a later time. The update is a bundle that contains one or more packages for updating the IBM management components and the VMware components.

## Before you begin

Before you attempt to apply an update, expand the update entry by clicking the down arrow and verify the following information:
* The version of the update. You must apply the updates in chronological sequence that is from the earliest one to the most recent one. Ensure that you applied all the previous updates before you apply the most recent one. For example, you must apply the V2.3 update before attempting to apply the V2.4 update.
* Whether downtime is required.
* The total estimated time to complete the update.
* The impact of the update on the VMware virtual environment. Table 1 shows how different levels of impact affect the system.
* The update details.

Table 1. Update levels and impact

<table>
  <tr>
    <th>Update level</th>
    <th>Impact</th>
  </tr>
  <tr>
    <td>Low</td>
    <td>This update does not affect any system. You do not have to apply it during scheduled downtime.</td>
  </tr>
  <tr>
    <td>Medium</td>
  <td>This update might affect some systems. It is recommended that you apply it during scheduled downtime.</td>
  </tr>
    <tr>
    <td>Major</td>
  <td>This update affects some or all systems. You must apply it during scheduled downtime.</td>
  </tr>
</table>

## Procedure

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** on the left navigation pane.
2. In the **Cloud Foundation Instances** table, click the instance to update.
3. On the **Summary** page, verify that all instance details are displayed correctly. Then click **Infrastructure** on the left navigation pane to verify the details on the **Infrastructure** page.
   If the details are not displayed, this might indicate a connectivity problem with the IBM CloudDriver Virtual Server Instance (VSI), as a result of a firewall rule or other networking issue. Resolve the problem before continuing with the next step, otherwise the update might fail.
4. Click **Update and Patch** on the left navigation pane.
5. Click the down arrow to expand the update that you want to apply and then complete one of the following steps:
   *  To start the update immediately, click the overflow menu icon in the **Actions** column of the update entry, and then click **Update Now**.
   *  To schedule a future update, click the overflow menu icon in the **Actions** column of the update entry, and then click **Schedule Update**. Select the date, time, and time zone when you want the update to be started. Click **OK**.
6. If you are applying updates to Cloud Foundation instances in multi-site deployment configuration, a section titled **Steps Required to Update** is displayed. This section lists the update operations required for all instances in the multi-site deployment. You must complete the steps in sequence by clicking **Apply Update** for each step. You must wait for the previous step to complete before you start the next step.

## Results

1. Before an update operation is started, a health check for the instance is completed. If the health check fails, you are notified so you can fix the problem before applying the update.
2. During updates that include VMware components updates, VMs may need to be migrated from ESXi servers to go into maintenance mode. If a VM has a local datastore, or CD-ROM mounted, this might prevent the VM migration.
3. During the provisioning of a new environment, {{site.data.keyword.vmwaresolutions_short}} creates the **automationuser** ID that is used for instance management, including for applying updates. Do not change the password for this user ID. Changing the password might cause the update to fail.

4. After you apply an update, a record appears in the software update status list, where you can view the detailed progress and status of the update. When the update is completed successfully, a record appears in the installed software updates list.

  To retrieve the most recent status for an update job, click the refresh icon in the upper right of the page.
  {:tip}

5. For details about the update statuses, see the following table.

   Table 2: Details of update statuses

    <table>
      <tr>
        <th>Status</th>
        <th>Details</th>
      </tr>
      <tr>
        <td>Available</td>
        <td>The update is available to be applied. You cannot select an available update until all its previous updates are applied.</td>
      </tr>
      <tr>
        <td>In progress</td>
      <td>The update job is initiated but not finished yet. You cannot apply any other updates until the current update job is completed. </td>
      </tr>
        <tr>
        <td>Installed</td>
      <td>The update job is completed. The corresponding component of the VMware platform is updated.</td>
      </tr>
        <tr>
        <td>Failed</td>
      <td>The update job fails. The console reports an error for the update failure. Review the error and fix the reported issue before you reapply the update.</td>
      </tr>
          <tr>
        <td>Scheduled</td>
      <td>The update job is scheduled for a later time. The update job starts automatically at the time that you scheduled.</td>
      </tr>
          <tr>
        <td>Unknown</td>
      <td>The status of the update job cannot be obtained. Contact IBM Support for assistance.</td>
      </tr>
    </table>

6. If the update process fails at a specific step, [contact IBM Support](../vmonic/trbl_support.html) for assistance. You will be advised how to resolve the problem and guided to restart the upgrade from the step that failed.

### Related links

* [Cloud Foundation overview](../sddc/sd_cloudfoundationoverview.html)
* [Veeam on {{site.data.keyword.cloud_notm}} overview](../services/veeam_considerations.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQs](../vmonic/faq.html)
