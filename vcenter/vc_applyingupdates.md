---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

keywords: vCenter Server update, patch vCenter Server, IBM component update

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Applying IBM management component updates to vCenter Server instances
{: #vc_applyingupdates}

The procedure in this section applies to updating IBM management components for instances that are deployed in V2.1 to V2.4 releases.

For instances deployed in (or upgraded to) V2.5 or later, updates and patches for the IBM management components are applied automatically, as needed.

For instances that are deployed in V2.0 and earlier, you must apply the updates manually.

In addition, note the following behavior when you complete certain operations on your instance:
* When you order new services, the instance is updated to the latest version.
* When you add new clusters, these clusters are provisioned with the latest VMware components, but the existing clusters are not.
* When you add new ESXi servers, these ESXi servers are provisioned with the latest VMware components, but the existing ESXi servers are not.

{{site.data.keyword.vmwaresolutions_short}} does not offer support for applying updates and patches for VMware components. You must monitor and apply these updates yourself.
{:important}

## Before you apply IBM management component updates
{: #vc_applyingupdates-prereq}

Expand the update entry by clicking the down arrow and verify the following information:
* The version of the update. You must apply the updates in chronological sequence that is from the earliest one to the most recent one. Ensure that you applied all the previous updates before you apply the most recent one. For example, you must apply the V2.3 update before attempting to apply the V2.4 update.
* Whether downtime is required.
* The total estimated time to complete the update.
* The impact of the update on the VMware virtual environment. Table 1 shows how different levels of updates impact the system.
* The update details.

| Update level | Impact |
|:------------ |:------ |
| Low | This update does not affect any system. You do not have to apply it during scheduled downtime. |
| Medium | This update might affect some systems. It is recommended that you apply it during scheduled downtime. |
| Major | This update affects some or all systems. You must apply it during scheduled downtime. |
{: caption="Table 1. Update levels and impact" caption-side="top"}

## Procedure to apply IBM management component updates (instances V2.1 to V2.4)
{: #vc_applyingupdates-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server Instances** table, click the instance to update.
3. On the **Summary** page, verify that all instance details are displayed correctly. Then click **Infrastructure** on the left navigation pane to verify the details on the **Infrastructure** page.

   If the details are not displayed, this might indicate a connectivity problem with the IBM CloudDriver Virtual Server Instance (VSI), as a result of a firewall rule or a networking issue. Resolve the problem before continuing with the next step, otherwise the update might fail.

4. Click **Update and Patch** on the left navigation pane and click the down arrow to expand the IBM management update that you want to apply and then complete one of the following steps:
   * To start the update immediately, click the overflow menu icon in the **Actions** column of the update entry, and then click **Update Now**.
   * To schedule a future update, click the overflow menu icon in the **Actions** column of the update entry, and then click **Schedule update**. Select the date, time, and time zone when you want the update to be started. Click **OK**.
5. If you are applying updates to instances in multi-site deployment configuration, a section titled **Steps Required to Update** is displayed. This section lists the update operations required for all instances in the multi-site deployment. You must complete the steps in sequence by clicking **Apply Update** for each step. You must wait for the previous step to complete before you start the next step.

## Results after you apply IBM management component updates
{: #vc_applyingupdates-results}

1. After you apply an update, a record appears in the software update status list, where you can view the detailed progress and status of the update. When the update is completed successfully, a record appears in the installed software updates list.

  To retrieve the most recent status for an update job, click the refresh icon on the upper right corner of the page.
  {:tip}

2. For details about the update statuses, see the following table.

| Status | Details |
|:------ |:------- |
| Available | The update is available to be applied. You cannot select an available update until all its previous updates are applied. |
| In progress | The update job is initiated but not finished yet. You cannot apply any other updates until the current update job is completed. |
| Installed | The update job is completed. The corresponding component of the VMware platform is updated. |
| Failed | The update job fails. The console reports an error for the update failure. Review the error and fix the reported issue before you reapply the update. |
| Scheduled | The update job is scheduled for a later time. The update job starts automatically at the time that you scheduled. |
| Unknown | The status of the update job cannot be obtained. Contact IBM Support for assistance. |
{: caption="Table 2. Details of update statuses" caption-side="top"}

3. If the update process fails at a specific step, [contact IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) for assistance. You will be advised how to resolve the problem and guided to apply the updates and patches from the step that failed.

## Related links
{: #vc_applyingupdates-related}

* [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Upgrading licenses for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQs](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
