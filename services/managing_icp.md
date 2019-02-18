---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Requesting IBM Cloud Private Hosted - Deprecated
{: #managing_icp}

The information in this topic is being deprecated. For the most updated information about IBM Cloud Private Hosted, see [IBM Cloud Private Hosted overview](icp_overview.html).
{:deprecated}

{{site.data.keyword.cloud}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} automatically deploys {{site.data.keyword.cloud_notm}} Private Hosted on your VMware vCenter Server instances.

{{site.data.keyword.cloud_notm}} Private Hosted brings the power of microservices and containers to your VMware environment on {{site.data.keyword.cloud_notm}}. With this service, you can extend the same familiar VMware and {{site.data.keyword.cloud_notm}} Private operational model and tools from on-premises into the {{site.data.keyword.cloud_notm}}.

## Technical specifications for IBM Cloud Private Hosted
{: #managing_icp-specs}

The following are the minimum requirements to request the {{site.data.keyword.cloud_notm}} Private Hosted service:

* VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
  **Note:** VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle is not supported.
* VMware NSX Advanced or Enterprise edition
* Three {{site.data.keyword.baremetal_long}}
* Dual Intel Xeon Gold 5120 processor / 28 cores total, 2.2 GHz
* 384 GB RAM per server
* One file share of shared NFS storage with 8,000 GB at 4 IOPS/GB
* 33 IBM Cloud Private Virtual processor core licenses
* For data backup, the Veeam on IBM Cloud service is recommended.

## Procedure to request IBM Cloud Private Hosted
{: #managing_icp-procedure}

1. Order a new vCenter Server instance by following the steps in [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html). You can also request IBM Cloud Private Hosted for an existing instance.
  **Important:** Ensure that your environment meets the minimum requirements that are listed previously.
2. Ensure that you have your IBM Cloud Private entitlements.
3. After you received confirmation that your vCenter Server instance is ready to use, proceed with the following steps to request IBM Cloud Private Hosted.
4. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Getting Started** from the left navigation pane.
5. Scroll down the page and under **Order additional services** click the **IBM Cloud Private Hosted** card.
6. On the **IBM Cloud Private Hosted on vCenter Server on IBM Cloud** page, in the **Contact the IBM Cloud Private Hosted DevOps Team** box, enter a description of your requirements and click **Request a consultation**.

An {{site.data.keyword.cloud_notm}} Private Hosted DevOps representative contacts you through your {{site.data.keyword.cloud_notm}} contact information to get you started.
