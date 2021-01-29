---

copyright:

  years:  2016, 2020

lastupdated: "2020-12-10"

keywords: Caveonix view license, Caveonix manage license, delete Caveonix license

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing Caveonix RiskForesight licenses
{: #caveonix_license_managing}

You can view, edit notes, or delete the Caveonix RiskForesight™ licenses that you ordered for stand-alone use.

## Procedure to view Caveonix RiskForesight licenses
{: #caveonix_license_managing_procedure-view}

1. Click **Resources** from the left navigation pane and scroll down to the **Caveonix RiskForesight Licenses** table.
2. To view the details of a specific license, click the license.

Review the following Caveonix RiskForesight license details.

| Item | Description |
|:-----|:------------|
| Name | The name of the license. |
| Creation time | The date and time when the license was created. |
| Status | The status of the license:<br>Modifying: The license is being created.<br>Installed: The license is ready to use.<br>Removing: The license is being deleted. |
{: caption="Table 1. Description of Caveonix RiskForesight license items" caption-side="top"}

## Procedure to edit notes for Caveonix RiskForesight licenses
{: #caveonix_license_managing_procedure-edit}

1. Click **Resources** from the left navigation pane.
2. Scroll down to the **Caveonix RiskForesight Licenses** table and click the license that you want to edit the notes for.
3. On the license details page, edit the license notes, and then click **Confirm**.

## Known issues about license date display
{: #caveonix_license_considerations-date}

If you are using Mozilla® Firefox® as your browser, the license start and end dates might be displayed with no values on the Caveonix RiskForesight console. To resolve the issue, view the license information in another browser, such as Google Chrome™.

If you are experiencing this problem and the only browser you can use is Firefox, contact [Caveonix Support](https://www.caveonix.com/support/){:external} for assistance.
{:note}

## Procedure to delete Caveonix RiskForesight licenses
{: #caveonix_license_managing_procedure-delete}

Deleting a Caveonix RiskForesight license does not delete the Caveonix RiskForesight service that is installed on a vCenter Server® instance. To delete the service, you must do so in the {{site.data.keyword.vmwaresolutions_full}} console. For more information, see [Procedure to delete services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure).
{:note:}

1. Click **Resources** from the left navigation pane.
2. Scroll down to the **Caveonix RiskForesight Licenses** table and find the license to delete.
3. In the **Actions** column, click the delete icon.
4. In the **Delete License** window, click **OK**.
   The status of the license is changed to **Removing**. When the license deletion is completed, the license is no longer available in the **Caveonix RiskForesight Licenses** table.

## Related links
{: #caveonix_license_managing-related}

* [Caveonix RiskForesight overview]()
* [Ordering Caveonix RiskForesight licenses](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_license_ordering)
