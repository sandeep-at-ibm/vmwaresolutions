---

copyright:

  years:  2019, 2021

lastupdated: "2021-08-05"

keywords: Red Hat OpenShift for VMware, OpenShift configuration, order OpenShift

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Red Hat OpenShift for VMware
{: #ocp_ordering}

You can include the Red Hat® OpenShift® for VMware® service with a new VMware vCenter Server® instance or add the service to your existing vCenter Server instance.

1. In the {{site.data.keyword.vmwaresolutions_full}} console, scroll down to the services section and click **Red Hat OpenShift for VMware**.
2. On the **Red Hat OpenShift for VMware** page, click the **About** tab to review the description and technical specifications for Red Hat OpenShift for VMware.
3. Click the **Create** tab.
4. To add the service while you order a new instance, click **Add to new instance**, and then continue with [ordering a new vCenter Server instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance).
5. To add the service to an existing instance, click **Add to existing instance**. Then, select the instance that you want to use and complete the requested information.

## Red Hat OpenShift for VMware configuration
{: #ocp_ordering-config}

When you order the service, you must provide a Red Hat pull secret. This pull secret is used to associate the new OpenShift cluster with your existing Red Hat account. You can obtain a copy of your pull secret by [logging in to your Red Hat account](https://cloud.redhat.com/openshift/install/vsphere/user-provisioned){:external} and clicking **Copy Pull Secret**.

## Setting up DNS to access your OpenShift console
{: #ocp_ordering-dns-setup}

Red Hat OpenShift depends on DNS to function properly. The `ocp` wildcard zone in your VMware environment root zone resolves all names to the IP address of the Red Hat OpenShift cluster application. This way, all applications that run within Red Hat OpenShift are routed through the Load Balancer, as needed.

Because the Red Hat OpenShift web console runs as an application within Red Hat OpenShift, your system must properly resolve DNS names before you can connect to the Red Hat OpenShift web console. You must complete the following steps before you open the Red Hat OpenShift console:

1. Ensure you are connected to your environment by using the {{site.data.keyword.cloud_notm}} infrastructure VPN.

2. Ensure the system that you use to connect to the Red Hat OpenShift web console can properly resolve hostnames in the DNS zone for your VMware environment. For anexisting DNS infrastructure, configure the DNS delegation so that queries for hostnames within the VMware instance's root zone are handled by the AD DNS server that is running within your VMware environment.

Alternately, you can configure your local `hosts` file with the following entries so you can access the OpenShift web console. Use the following details for the example.
* Replace APPLICATION_IP with the OpenShift application IP address shown in the Red Hat OpenShift service details page.
* Replace ROOTDOMAIN with the root domain shown on the Summary page for the vCenter Server instance.

   `APPLICATION_IP  console-openshift-console.apps.ocp.ROOTDOMAIN`
   `APPLICATION_IP  oauth-openshift.apps.ocp.ROOTDOMAIN`


## Related links
{: #ocp_ordering-related}

* [Ordering services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
