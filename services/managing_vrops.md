---

copyright:

  years:  2019

lastupdated: "2019-12-11"

keywords: vRealize console, vRealize license, login vRealize console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing vRealize Operations and Log Insight
{: #managing_vrops}

## Accessing the vRealize Operations Manager console
{: #managing_vrops-access-vrops-console}

To access the vRealize Operations Manager console, complete the following steps:

1. On the service details page for vRealize Operations and Log Insight, click **vRealize Operations Manager Console**.
2. Log in by using the credentials listed on the same service details page.
3. When you log in to the vRealize Operations Manager console for the first time after installation, the vRealize Operations Manager Configuration wizard prompts you to enter your license (product key). Ensure that you select the **Product evaluation (no key required)** option to proceed.

## Starting the adapter instance for vSAN
{: #managing_vrops-start-adapter}

The Management Pack adapter instance for vSAN must be manually started. Complete the following steps:

1. Log in to the vRealize Operations Manager console.
2. Click the vSAN adapter.
3. Click Edit, then test the connection and accept the certificate when prompted.
4. Start the adapter instance.

## Accessing the vRealize Log Insight console
{: #managing_vrops-access-vlog-console}

To access the vRealize Log Insight console, complete the following steps:

1. On the service details page for vRealize Operations and Log Insight, click **vRealize Log Insight Console**.
2. Log in by using the credentials listed on the same service details page.

## Known issues
{: #managing_vrops-issues}

Some of the following warnings might appear. You can ignore these warning messages:
* NSX Logical Router is violating NSX Hardening guide (targeting workload-nsx-dlr)
* NSX Routing Edge Service is violating the NSX Hardening guide (targeting customer-nsx-edge)
* NSX Manager is violating NSX Hardening guide
* No backup of the environment has been recorded

## Related links
{: #managing_vrops-related}

* [vRealize Operations and Log Insight overview](/docs/services/vmwaresolutions?topic=vmware-solutions-vrops_overview)
* [Ordering vRealize Operations and Log Insight](/docs/services/vmwaresolutions?topic=vmware-solutions-vrops_ordering)
