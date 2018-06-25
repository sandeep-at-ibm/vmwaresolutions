---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-05"

---

# Removal process for Zerto on IBM Cloud
<!-- Do not remove this topic. Though it's no longer in the TOC, it's referenced from the V1.3 release notes -->

The removal process of the Zerto on IBM® Cloud service is automated. The following steps are completed for the successful removal of the Zerto on IBM Cloud service.

## How to remove Zerto on IBM Cloud

1. Click **Deployed Instances** from the left navigation pane and click the instance from which you want to remove the service.
2. Click the **Services** tab.
3. On the **Installed Services** tab, click the overflow menu icon in the upper right of the service card, and then click **Remove Service**.
4. In the **Remove Service** window, review the considerations or warnings if there are any. Click **I Understand**.
5. After your request for service removal is accepted, the service status is changed to **Removing** and the following removal steps are completed:   
   1. Remove the Zerto Virtual Replication Appliances that were deployed to all ESXi servers.
   2. Uninstall Zerto Virtual Replication.
   3. Delete the Windows VSI (Virtual Service Instance) on which Zerto Virtual Replication was installed.
   4. Return the private portable subnet that was ordered for Zerto Virtual Replication communication to IBM Cloud  infrastructure.   
   5. Remove the charges of the Zerto disaster recovery service from your IBM Cloud billing statement.

      **Note**: You are billed until the end of the billing cycle for the removed Zerto disaster recovery service.

## Results

After the service removal is completed successfully, you are notified by email and the service entry is deleted from the **Installed Services** tab.

## Related links

* [Ordering Zerto on IBM Cloud](zerto_ordering.html)
* [Managing Zerto on IBM Cloud](managingzertodr.html)
* [Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server instances](../vcenter/vc_vcenterserveroverview.html)
* [zerto.com website](https://www.zerto.com){:new_window}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
