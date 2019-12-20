---

copyright:

  years:  2019

lastupdated: "2019-12-19"

keywords: Red Hat OpenShift for VMware, OpenShift configuration, order OpenShift

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Red Hat OpenShift for VMware
{: #ocp_ordering}

You can order the Red Hat OpenShift for VMware service when you order a new VMware vCenter Server instance with the service included or by adding the service to your existing instance.

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
2. Scroll down to the **Services** section, and then click **Red Hat OpenShift for VMware** on the **Transformation and Modernization of VMware Applications** card.
3. On the **Red Hat OpenShift for VMware** page, review the description and technical specifications for Red Hat OpenShift for VMware, and then click **Continue**.
4. To add the service while you order a new instance, click **Add to New Instance**, and then continue with [ordering a new vCenter Server instance](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance).
5. To add the service to an existing instance, click **Add to Existing Instance**, select the instance that you want from the list, and then confirm that you want to proceed with the order by clicking **Provision**.

## Red Hat OpenShift for VMware configuration
{: #ocp_ordering-config}

When you order the service, you must provide a Red Hat Pull Secret. This Pull Secret is used to associate the new OpenShift cluster with your existing Red Hat account. You can obtain a copy of your Pull Secret by [logging in to your Red Hat account](https://cloud.redhat.com/openshift/install/vsphere/user-provisioned){:external} and clicking **Copy Pull Secret**.

## Setting up DNS to access your OpenShift console
{: #ocp_ordering-dns-setup}

Red Hat OpenShift depends on DNS to function properly. There is a wildcard zone named `ocp`, which is configured under your VMware environment root zone. This wildcard zone resolves all names to the IP address of the Red Hat OpenShift cluster application. This way, all applications that run within Red Hat OpenShift are routed through the Load Balancer, as needed.

Because the Red Hat OpenShift web console runs as an application within Red Hat OpenShift, your system must properly resolve DNS names before you can connect to the Red Hat OpenShift web console. You must complete the following steps before you open the Red Hat OpenShift console:

1. Ensure you are connected to your environment by using the IBM Cloud infrastructure VPN.

2. Ensure the system that you will be using to connect to the Red Hat OpenShift web console can properly resolve hostnames in the DNS zone for your VMware environment. If you have an existing DNS infrastructure, it is recommended that you configure the DNS delegation so that queries for hostnames within the VMware instance's root zone are handled by the AD DNS server that is running within your VMware environment.

Alternately, you can configure your local `hosts` file with the following entries so you can access the OpenShift web console. In the following example:
* Replace APPLICATION_IP with the OpenShift application IP address shown in the Red Hat OpenShift service details page. 
* Replace SUBDOMAIN with the subdomain shown on the Summary page for the vCenter Server instance.

   `APPLICATION_IP  console-openshift-console.apps.ocp.SUBDOMAIN`

   `APPLICATION_IP  oauth-openshift.apps.ocp.SUBDOMAIN`

## Related links
{: #ocp_ordering-related}

* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices)
* [Contacting IBM Support](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions?topic=vmware-solutions-faq)
