---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

{:tip: .tip}

# Applying updates to vCenter Server instances

The process of applying patches and updates to vCenter Server instances is automated for the management components only. The VMware updates must be applied manually.

## Before you begin

**Important:** When upgrading a vCenter Server instance to a vCenter Server with Hybridity Bundle instance, you must first apply the base vCenter Server V2.3 software update before you can perform the license upgrade to the Hybridity Bundle.

Before you attempt to apply an update, expand the update entry by clicking the down arrow and verify the following information:
* The version of the update. You must apply the updates in chronological sequence that is from the earliest one to the most recent one. Ensure that you applied all the previous updates before you apply the most recent one. For example, you must apply the V2.2 update before attempting to apply the V2.3 update.
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

## Applying updates and patches to vCenter Server instances

This procedure applies to instances that are deployed in V2.1 or later. For instances that are deployed in V2.0 and earlier, you must apply the VMware updates manually.

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane. All instance resources are displayed.

   **Note:** Verify that all details are displayed correctly. If the details are not displayed, this might indicate a connectivity problem with the IBM CloudDriver virtual machine, as a result of a firewall rule or other networking issue. Resolve the problem before continuing with the next step, otherwise the update might fail.

2. In the **vCenter Server Instances** table, click the instance to update.
3. Click the **Update and Patch** tab.

   **Note**: The **Update and Patch** page for an instance contains only the packages for updating the IBM management components, and not the VMware updates. VMware updates must be applied manually.

   {{site.data.keyword.vmwaresolutions_short}} applies VMware updates for the following operations:
   * When a new vCenter Server instance is deployed.
   * When new ESXi servers are added.
   * When new clusters are added.

4. For NSX license upgrades, click **Upgrade License**. Select the edition that you want to upgrade to and click **Upgrade**. License edition downgrades are not available.

   **Note:** The license upgrade replaces all existing NSX licenses on the instance. Additional charges may be incurred from an overlap of old and new licenses if you upgrade in the middle of a billing cycle. To avoid additional charges, it is recommended to upgrade the license at the end of the billing cycle.

5. For software updates, click the down arrow to expand the update that you want to apply and then complete one of the following steps:
   *  To start the update immediately, click the overflow menu icon in the **Actions** column of the update entry, and then click **Update Now**.
   *  To schedule a future update, click the overflow menu icon in the **Actions** column of the update entry, and then click **Schedule Update**. Select the date, time, and time zone when you want the update to be started. Click **OK**.
6. If you are applying updates to vCenter servers instances in multi-site deployment configuration, a section titled **Steps Required to Update** is displayed. This section lists the update operations required for all instances in the multi-site deployment. You must complete the steps in sequence by clicking **Apply Update** for each step. You must wait for the previous step to complete before you start the next step.   

## Upgrading to the vCenter Server with Hybridity Bundle instance

During the license upgrade to the Hybridity Bundle, you are automatically upgraded to the VMware NSX Advanced edition if your vCenter Server instance is currently using the VMware NSX Base edition.

Complete the following steps to upgrade a vCenter Server instance to the vCenter Server with Hybridity Bundle.

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Deployed Instances** from the left navigation pane. All instance resources are displayed.

   **Note:** Verify that all details are displayed correctly. If the details are not displayed, this might indicate a connectivity problem with the IBM CloudDriver virtual machine, as a result of a firewall rule or other networking issue. Resolve the problem before continuing with the next step, otherwise the update might fail.

2. In the **vCenter Server Instances** table, click the instance to upgrade.
3. Click the **Update and Patch** tab.
4. Apply the Hybridity Bundle license upgrade. In the **License Upgrades** table, click **Upgrade** in the **Action** column, review the estimated cost, and click **Upgrade**.
5. Optionally deploy the VMware HCX on {{site.data.keyword.cloud_notm}} service. When the Hybridity Bundle is enabled on the **License Upgrades** table, complete the following steps:
  1. In the **License Upgrades** table, click **Deploy HCX on {{site.data.keyword.cloud_notm}}** in the **Action** column.
  2. Scroll to the **HCX on {{site.data.keyword.cloud_notm}}** card and click **Select Service**.
  3. Scroll down and specify the required settings for the service and click **Next**.
  4. Review the terms that apply to the service, review the estimated cost, and click **Place Order**.

## Results

1. Before an update operation is started, a backup of the management virtual machines is done automatically, if your instance has a backup service installed. After the backup is completed, the update is applied.

2. After you apply an update, a record appears in the software update status list, where you can view the detailed progress and status of the update. When the update is completed successfully, a record appears in the installed software updates list.

  To retrieve the most recent status for an update job, click the refresh icon in the upper right of the page.
  {:tip}

3. For details about the update statuses, see the following table.

   Table 2. Details of update statuses

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

4. If the update process fails at a specific step, [contact IBM Support](../vmonic/trbl_support.html) for assistance. You will be advised how to resolve the problem and guided to attempt the upgrade again from the step that failed.

## Related links

* [vCenter Server overview](../vcenter/vc_vcenterserveroverview.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQs](../vmonic/faq.html)
