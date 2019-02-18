---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Removal process for Zerto on IBM Cloud
{: #removingzertodr}

The removal process of the Zerto on {{site.data.keyword.cloud}} service is automated. The following steps are completed for the successful removal of the Zerto on {{site.data.keyword.cloud_notm}} service.

## How to remove Zerto on IBM Cloud
{: #removingzertodr-remove}

1. Click **Deployed Instances** from the left navigation pane and click the instance from which you want to remove the service.
2. Click the **Services** tab.
3. On the **Installed Services** tab, click the overflow menu icon in the upper right of the service card, and then click **Remove Service**.
4. In the **Remove Service** window, review the considerations or warnings if there are any. Click **I Understand**.
5. After your request for service removal is accepted, the service status is changed to **Removing** and the following removal steps are completed:   
   1. Remove the Zerto Virtual Replication Appliances that were deployed to all ESXi servers.
   2. Uninstall Zerto Virtual Replication.
   3. Delete the Windows VSI (Virtual Service Instance) on which Zerto Virtual Replication was installed.
   4. Return the private portable subnet that was ordered for Zerto Virtual Replication communication to {{site.data.keyword.cloud_notm}}  infrastructure.   
   5. Remove the charges of the Zerto disaster recovery service from your {{site.data.keyword.cloud_notm}} billing statement.

      You are billed until the end of the billing cycle for the removed Zerto disaster recovery service.
      {:note}

## Results
{: #removingzertodr-results}

After the service removal is completed successfully, you are notified by email and the service entry is deleted from the **Installed Services** tab.

## Related links
{: #removingzertodr-related}

* [Ordering Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Managing Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Cloud Foundation instances](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server instances](../vcenter/vc_vcenterserveroverview.html)
* [zerto.com website](https://www.zerto.com){:new_window}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
