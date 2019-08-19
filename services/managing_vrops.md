---

copyright:

  years:  2019

lastupdated: "2019-08-16"

keywords: vRealize console, vRealize license, login vRealize console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #managing_vrops}

## Accessing the vRealize Operations Manager console
{: #managing_vrops-access-vrops-console}

To access the vRealize Operations Manager console, click **vRealize Operations Manager Console** on the service details page for VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud}}, and then log in by using the credentials listed on the same service details page.

When you log into the vRealize Operations Manager console for the first time after installation, the vRealize Operations Manager Configuration wizard prompts you to enter your license (product key). Ensure that you select the **Product evaluation (no key required)** option to proceed.
{: note}

## Starting the adapter instance for vSAN
{: #managing_vrops-start-adapter}

The Management Pack adapter instance for vSAN must be manually started. Complete the following steps:

1. Log in to the vRealize Operations Manager console.
2. Click the vSAN adapter.
3. Click Edit, then test the connection and accept the certificate when prompted.
4. Start the adapter instance.

## Accessing the vRealize Log Insight console
{: #managing_vrops-access-vlog-console}

To access the vRealize Log Insight console, click **vRealize Log Insight Console** on the service details page for VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}, and then log in by using the credentials listed on the same service details page.

## Related links
{: #managing_vrops-related}

* [VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vrops_overview)
* [Ordering VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vrops_ordering)
