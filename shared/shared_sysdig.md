---

copyright:

  years:  2020

lastupdated: "2020-10-21"

keywords: sysdig, default dashboard, custom dashboard, virtual data center, platform metrics, monitoring

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visualizing your virtual data center instance environment with IBM Cloud Monitoring with Sysdig
{: #shared_sysdig}

{{site.data.keyword.vmwaresolutions_full}} Shared provides an integration with {{site.data.keyword.cloud}} Monitoring for Sysdig, which allows you to use a VMware® Solutions Shared provided default dashboard to view metrics for your virtual data centers. Alternatively, you can create your own dashboard to visualize performance, volume of usage, and to define alerts to monitor your environment.

{{site.data.keyword.cloud_notm}} Monitoring for Sysdig dashboards allows you to:

* Explore and easily visualize your environment.
* Accelerate a diagnosis and a resolution for performance incidents.
* Control cost of monitoring infrastructure.
* Mitigate impact of abnormal situations with proactive notifications.

For more information about the benefits of using {{site.data.keyword.cloud_notm}} Monitoring with Sysdig, see the *Features* section in the [IBM Cloud Monitoring with Sysdig Getting Started Tutorial](/docs/Monitoring-with-Sysdig#features).

## Provisioning an IBM Cloud Monitoring for Sysdig instance
{: #shared_sysdig-create-instance}

Before you can view platform metrics for your virtual data center, you must order an {{site.data.keyword.cloud_notm}} Monitoring for Sysdig instance.

Review the following requirements for your instance order.

* Order the instance with the Graduated Tier plan, not the Lite plan.
* The instance must be within the same region as your virtual data center instance.
* You must enable the automatic collection of platform metrics.

Order the {{site.data.keyword.cloud_notm}} Monitoring for Sysdig instance.

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **VMware Solutions Shared** table, select the instance for which you want to collect platform metrics.
3. From the instance details page, click the **Actions** drop down and click **Add monitoring**. The {{site.data.keyword.cloud_notm}} Monitoring for Sysdig provisioning page displays.
4. Complete the steps in [Provisioning an instance](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-provision) to order an {{site.data.keyword.cloud_notm}} Monitoring for Sysdig instance and enable the automatic platform metrics collection.

## Viewing platform metrics for your virtual data center instance
{: #shared_sysdig-view-metrics}

After you order your {{site.data.keyword.cloud_notm}} Monitoring for Sysdig instance, you can view the platform metrics in the Sysdig dashboard.

1. In the **VMware Solutions Shared** table, select the instance for which you want to view platform metrics.
2. From the instance details page, click the **Actions** drop down and click **Monitoring**. The {{site.data.keyword.cloud_notm}} Monitoring for Sysdig dashboard displays the metrics for the associated instance.

VMware Solutions Shared provides the following metrics for the default dashboard:

* vCPU usage
* vCPU allocation
* Memory usage
* Memory allocation
* Storage usage

Metrics updates can be delayed by up to 60 minutes.
{:note}

## Customizing your VMware Solutions Shared dashboard
{: #shared_sysdig-view-customize}

You can optionally customize your dashboard.

1.  In the {{site.data.keyword.cloud_notm}} Monitoring for Sysdig console, click **Dashboards** from the left navigation pane.
2. Click the **IBM** menu and click **VMware Solutions Shared**.
3. Customize your dashboard. For more information, see [Working with dashboards](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-dashboards).

## Related links
{: #shared_sysdig-related}

* [{{site.data.keyword.cloud_notm}} Monitoring for Sysdig Getting Started Tutorial](/docs/Monitoring-with-Sysdig)
