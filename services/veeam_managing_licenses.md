
---

copyright:

  years:  2020

lastupdated: "2020-06-10"

keywords: Veeam, Veeam license, manage Veeam license, Veeam 10

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}

# Managing Veeam licenses
{: #veeam_managing_licenses}

You can view, edit notes, or delete the Veeam licenses that you ordered for stand-alone use.

## Procedure to view Veeam licenses
{: #veeam_managing_licenses-procedure-view}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. Scroll down to the **Veeam licenses** table.
3. To view the details of a specific license, click the license.

A license key is not displayed. When licenses are ordered, the system does not generate a key. We are applying a master key.
{:note}

The following information is displayed for the Veeam license:
* License name
* License notes
* Number of VMs licensed
* Creation date
* Status - the status can be:
   * Modifying - license is being created
   * Installed - license is ready to use
   * Removing - license is being deleted

## Procedure to edit notes for Veeam licenses
{: #veeam_managing_licenses-procedure-edit}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. Scroll down to the **Veeam licenses** table.
3. Click the license that you want to edit the notes for.
4. On the license details page, edit the license notes, and then click **Confirm**.

## Known issues about license date display
{: #veeam_managing_licenses-considerations-date}

If you are using Mozilla Firefox as your browser, the license start and end dates might be displayed with no values on the Veeam console. To resolve the issue, view the license information in another browser, such as Google Chrome.

If you are experiencing this problem and the only browser you can use is Firefox, contact [Veeam support](https://www.veeam.com/support.html){:external} for assistance.

## Procedure to delete Veeam licenses
{: #veeam_managing_licenses-procedure-delete}

Deleting a Veeam license does not delete the Veeam service that is installed on a vCenter Server instance. To delete the service, you must do so in the {{site.data.keyword.vmwaresolutions_full}} console.

For more information, see [Procedure to delete services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure).

To delete a Veeam license:

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. Scroll down to the **Veeam licenses** table and select the license you want to delete.
3. From the **Actions** drop-down menu, click **Delete instance**.
4. In the **Delete license** window, click **Delete**.
   The status of the license is changed to **Removing**. When the license deletion is completed, the license is no longer listed in the **Veeam licenses** table.

## Related links
{: #veeam_managing_licenses-related}

* [Veeam v9.5 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations)
* [Veeam v10 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Ordering Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering)
* [Managing Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-managingveeam)
* [Ordering Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering_licenses)
* [Ordering and configuring IBM Cloud Object Storage with Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-icos_ordering)
