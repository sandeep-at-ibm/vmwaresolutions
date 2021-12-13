---

copyright:

  years:  2019, 2021

lastupdated: "2021-10-21"

keywords: vRealize console, vRealize license, login vRealize console

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Managing vRealize Operations and Log Insight
{: #managing_vrops}

## Accessing the vRealize Operations Manager console
{: #managing_vrops-access-vrops-console}

To access the vRealize Operations™ Manager console, complete the following steps:

1. On the service details page for vRealize Operations and Log Insight, click **vRealize Operations Manager console**.
2. Log in by using the credentials listed on the same service details page.
3. When you log in to the vRealize Operations Manager console for the first time after installation, the vRealize Operations Manager Configuration wizard prompts you to enter your license (product key). Ensure that you select the **Product evaluation (no key required)** option to proceed.

## Starting the adapter instance for vSAN
{: #managing_vrops-start-adapter}

You must manually start the Management Pack adapter instance for vSAN™. Complete the following steps:

1. Log in to the vRealize Operations Manager console.
2. Click the vSAN adapter.
3. Click Edit, then test the connection and accept the certificate when prompted.
4. Start the adapter instance.

## Accessing the vRealize Log Insight console
{: #managing_vrops-access-vlog-console}

To access the vRealize Log Insight console, complete the following steps:

1. On the service details page for vRealize Operations and Log Insight, click **vRealize Log Insight console**.
2. Log in by using the credentials listed on the same service details page.

## Redeploying vRealize Operations and Log Insight
{: #managing_vrops-redeploy-vrops}

You might encounter a situation where the file systems become filled to approximately 98% capacity. This scenario can result in inconsistencies with a Cassandra database or with the vRealize suite of products that are deployed with IBM automation.

If vRealize Operations and Log Insight was deployed with IBM automation, you can remove the service or product. Use the VMware Solutions console to remove the service or product. Then, use the VMware Solutions console to redeploy it.

If you deployed the service or product in another way, you must redeploy it using the process you originally used for deployment.

## Known issues
{: #managing_vrops-issues}

Some of the following warnings might appear. You can ignore these warning messages:
* NSX Logical Router is violating NSX Hardening guide (targeting workload-nsx-dlr)
* NSX Routing Edge Service is violating the NSX Hardening guide (targeting customer-nsx-edge)
* NSX Manager is violating NSX Hardening guide
* No backup of the environment is recorded

## Related links
{: #managing_vrops-related}

* [vRealize Operations and Log Insight overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview)
* [Ordering vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_ordering)
