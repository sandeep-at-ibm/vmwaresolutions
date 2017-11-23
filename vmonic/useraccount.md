---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-20"

---

# Managing user accounts and settings

{{site.data.keyword.vmwaresolutions_full}} communicates with the {{site.data.keyword.cloud}} infrastructure through {{site.data.keyword.slapi_short}} calls. To access the {{site.data.keyword.slapi_short}} securely, you must associate the credentials of your {{site.data.keyword.cloud}} account to your {{site.data.keyword.vmwaresolutions_short}} user account.

**Note**: The {{site.data.keyword.cloud_notm}} account was previously known as the IBM SoftLayer account.

On the {{site.data.keyword.vmwaresolutions_short}} console, you can also specify whether you want to receive email notifications for various events.

## Before you begin

* You can associate only one {{site.data.keyword.cloud_notm}} account to your {{site.data.keyword.vmwaresolutions_short}} user account.
* The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [{{site.data.keyword.cloud_notm}} account requirements](slaccountrequirement.html).
* If the API key from your {{site.data.keyword.cloud_notm}} account changes, you must update the key in your {{site.data.keyword.vmwaresolutions_short}} user account.

   **Important**: It is your responsibility to ensure that the API key that is saved on the **Settings** page is correct and up-to-date.
   Otherwise, operations that require API key validation might fail.

To associate the {{site.data.keyword.vmwaresolutions_short}} account with the {{site.data.keyword.cloud_notm}} account, enter the {{site.data.keyword.cloud_notm}} account credentials on the **Settings** page on the {{site.data.keyword.vmwaresolutions_short}} console.

After you associate the {{site.data.keyword.cloud_notm}} account, the console automatically retrieves the {{site.data.keyword.cloud_notm}} account credentials to communicate with your VMware environment on {{site.data.keyword.cloud_notm}}.

## Procedure

1. Click **Settings** from the left navigation pane.
2. If you want to be notified by email when events occur, select the **Enable email notifications** check box.
3. If you want to be notified on the console when events occur, select the **Enable console notifications** check box.
4. In the **IBM Cloud infrastructure Credentials** area, enter the user name of your {{site.data.keyword.cloud_notm}}  account, and then follow the instructions on the console to enter the {{site.data.keyword.slapi_short}} key.
5. Click **Save Credentials**.

## Results

The stored {{site.data.keyword.cloud_notm}} account credentials are used in future operations that require interaction with the {{site.data.keyword.cloud_notm}} infrastructure. If email or console notifications are enabled for certain instance events, you are notified by email or console messages when these events occur.

## Related links

* [FAQ](faq.html)
* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)
* [Notifications](notifications.html)
* [SoftLayer Development/API](http://knowledgelayer.softlayer.com/topic/developmentapi){:new_window}
