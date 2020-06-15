---

copyright:

  years:  2016, 2020

lastupdated: "2020-06-10"

keywords: IBM Cloud Object Storage, ICOS configuration, order Cloud Object Storage

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering and configuring IBM Cloud Object Storage with Veeam
{: #icos_ordering}

Starting with Veeam Availability Suite 9.5 Update 4 and subsequent versions, Veeam is compatible with {{site.data.keyword.cloud}} Object Storage (ICOS). The ordering of {{site.data.keyword.cloud_notm}} Object Storage is not automated when you order Veeam, but it can be added after deployment.

To order {{site.data.keyword.cloud_notm}} Object Storage, complete the following tasks in the specified order:

## Creating an Object Storage instance
{: #icos_ordering-obj}

To create an Object Storage instance, see [Creating a new service instance](/docs/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance). Follow the steps and return to this section to continue with the following tasks.

## Creating a bucket
{: #icos_ordering-bucket}

To create a bucket, see [Create some buckets to store your data](/docs/cloud-object-storage?topic=cloud-object-storage-getting-started-cloud-object-storage#gs-create-buckets). Follow the steps and return to this section to continue with the following tasks.

## Creating service credentials
{: #icos_ordering-service-cred}

To create service credentials, see [Service credentials](/docs/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials). Follow the steps and return to this section to continue with the following tasks.

## Adding a scale-out repository
{: #icos_ordering-scale-repo}

* As part of the Veeam service installation and configuration, a scale-out backup repository with the name `IC4V Scale-Out Repository` is created. `IC4V Default VM Backup Repository` is added to the scale-out repository as an extent.
* When you create the backup job, you must select `IC4V Scale-Out Repository` as the backup repository, and not `IC4V Default Config Backup Repository`. The latter repository is intended for the Veeam configuration backups.
* You can add more repositories to this default repository, such as a backup repository of type Object Storage. For more information, see [Adding scale-Out repositories](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:external}. Follow the steps and return to this section to continue with the following tasks.

## Veeam on an instance deployed with private network only
{: #icos_ordering-private-network}

If you want to access IBM COS with Veeam on a private only instance, a proxy is required.

## Maintaining and managing your cloud tier
{: #icos_ordering-manage-cloud}

For more information, see [Managing capacity tier data](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:external}.

## Related links
{: #icos_ordering-related}

* [Veeam v9.5 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations)
* [Veeam v10 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Ordering Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering)
* [Managing Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-managingveeam)
* [Ordering Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering_licenses)
* [Managing Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_managing_licenses)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [Veeam on {{site.data.keyword.cloud_notm}} - Demos](https://www.ibm.com/demos/collection/Veeam-on-IBM-Cloud/){:external}
