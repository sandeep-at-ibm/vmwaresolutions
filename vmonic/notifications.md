---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-20"

---

# Managing system notifications

You can check notifications for the status of system or user operations. You can also use the information to diagnose and troubleshoot problems that might occur.

## Viewing notifications

1. Click **Notifications** from the left navigation pane. In the **Notification History** table, view the summary about all notifications.

   * **Severity**: The severity of the event that is reported by the notification.
       <dl class="dl"><dt class="dt dlterm">Informational</dt>
       <dd class="dd">A system or user operation is completed. Typically, the following events report informational notifications:
       <ul class="ul">
       <li class="li">A service is installed.</li>
       <li class="li">A service is upgraded.</li>
       <li class="li">A service is removed.</li>
       <li class="li">All services are reconfigured for the added ESXi servers.</li>
       <li class="li">All services are reconfigured for the removed ESXi servers.</li>
       </ul>
       </dd>
       <dt class="dt dlterm">Warning</dt>
       <dd class="dd">A component fails or is not working properly. However, the failure does not disrupt the ongoing process of the
       component.</dd>
       </dl>                                                
   * **Type**: The type of component that the reported event is related to:                                      
      * vCenter Server instances
      * Cloud Foundation instances                                         
      * Services                                      
      * System                                        
   * **Resource**: The name of the instance or service that sends the notification.                                
   * **Description**: A short description of the notification.         
   * **Date**: The date and time when the notification is sent.
2. Click a notification row to view the details of the notification.

## Filtering notifications

By default, all notifications are displayed. You can filter the notifications by status, severity, and type. To filter the notifications, click the drop-down lists at the top of the page and select the check boxes only for the items that you want to be displayed.

## Related links

* [FAQ](faq.html)
* [User account and settings](useraccount.html)
