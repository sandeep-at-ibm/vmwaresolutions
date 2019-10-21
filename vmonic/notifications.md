---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-03"

keywords: notifications console, filter notifications, system notification

subcollection: vmware-solutions


---

# Managing system notifications
{: #notifications}

You can check notifications for the status of system or user operations. You can also use the information to investigate problems that might occur.

## Viewing notifications
{: #notifications-view}

From the {{site.data.keyword.vmwaresolutions_full}} console, click **Notifications** from the left navigation pane to view a summary about all notifications. To view the details of a notification, click the notification row.

| Column | Description |
|:------ |:----------- |
| Severity | The severity of the event that is reported by the notification.<br>**Critical**: A critical event might impact the entire system or service.<br>**Error**: An error event occurs during an operation that might need intervention from the administrator or the user.<br>**Warning**: A component fails or is not working properly. However, the failure does not disrupt the ongoing process of the component.<br>**Informational**: A system or user operation is completed. Typically, the following events report informational notifications:<br>A service is installed.<br>A service is upgraded.<br>A service is removed.<br>All services are reconfigured for the added ESXi servers.<br>All services are reconfigured for the removed ESXi servers. |
| Type | The type of component that the reported event is related to: vCenter Server instances, Services, System |
| Resource | The name of the instance or service that sends the notification. |
| Description | A short description of the notification. |
| Date | The date and time when the notification is sent. |
{: caption="Table 1. Notification history" caption-side="top"}

## Filtering notifications
{: #notifications-filter}

By default, all unread notifications are displayed. You can filter the notifications by status, severity, and type. To filter the notifications, select the check boxes only for the items that you want to display in the **Status**, **Severity**, or **Type** lists.

## Related links
{: #notifications-related}

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [User account and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
