---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Zerto on IBM Cloud
{: #zerto_ordering}

You can order the Zerto on {{site.data.keyword.cloud}} service when you order a new instance with the service included or by adding the service to your existing instance.

## Ordering Zerto on IBM Cloud for a new instance
{: #zerto_ordering-new}

You can order a new instance with Zerto on {{site.data.keyword.cloud_notm}} by using one of the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, when you order a new instance, select **Zerto on IBM Cloud** in the **Services** section.
* From the {{site.data.keyword.cloud_notm}} catalog, select **Zerto on IBM Cloud**, specify the service settings, and select **Add to New Instance**.

## Ordering Zerto on IBM Cloud for an existing instance
{: #zerto_ordering-existing}

You can add the Zerto on {{site.data.keyword.cloud_notm}} service to an existing instance by using one the following methods:
* From the {{site.data.keyword.vmwaresolutions_short}} console, view the instance that you want to add the service for, click **Services** on the left navigation pane, and click **Add**.
* From the {{site.data.keyword.cloud_notm}} catalog, select **Zerto on IBM Cloud**, specify the service settings, and select **Add to Existing Instance**.

If you add Zerto for {{site.data.keyword.cloud_notm}} to a vCenter Server instance that has an ESXi server that is in maintenance mode, you must use the Zerto Virtual Manager (ZVM) console and the pre-populated Zerto Virtual Replication Appliance (VRA) IP address to manually deploy the VRA virtual machine (VM).
{:note}

## Ordering Zerto on IBM Cloud for private-only instances
{: #zerto_ordering-private-only}

If you want to add Zerto on {{site.data.keyword.cloud_notm}} to a private-only instance, ensure that the following requirements are met:
* You are responsible for setting up your own proxy server to connect to the internet. For more information, see [Public network connectivity](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* You must also configure the Call Home feature for Zerto. For more information about Zerto Call Home, see [Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:new_window}.

## Related links
{: #zerto_ordering-related}

* [Zerto on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Managing Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Requesting managed services for Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com website](https://www.zerto.com){:new_window}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
