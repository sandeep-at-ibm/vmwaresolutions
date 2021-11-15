---

copyright:

  years:  2016, 2021

lastupdated: "2021-11-15"

keywords: IBM Spectrum Protect Plus, SPP configuration, order SPP

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}

# Ordering IBM Spectrum Protect Plus
{: #spp_ordering}

You can include the IBM Spectrum® Protect Plus service with a new VMware vCenter Server® instance or add the service to your existing vCenter Server instance.

## Ordering IBM Spectrum Protect Plus for a new instance
{: #spp_ordering-new}

When you [order the instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the services section and click **IBM Spectrum Protect Plus** in the **Business continuity and migration** category. Follow the steps to add the service to your instance.

## Ordering IBM Spectrum Protect Plus for an existing instance
{: #spp_ordering-existing}

1. On the instance details page, click **Services** on the left navigation pane.
2. Click **Add** to add the service.
3. On the **Services** page, locate the **IBM Spectrum Protect Plus** service and toggle its switch on.
4. Follow the steps to configure and add the service to your instance.

## IBM Spectrum Protect Plus service configuration
{: #spp_ordering-config}

When you order the service, provide the following settings.

### Number of storage volumes
{: #spp_ordering-config-number-vol}

The number of volumes that meet your storage needs.

### Storage size per volume
{: #spp_ordering-config-size}

The storage capacity per volume.

### Storage performance
{: #spp_ordering-config-performance}

The IOPS (Input/output Operations Per Second) per GB based on your workload requirements.
* If you want to order licenses for IBM Spectrum Protect Plus, specify the **Number of VMs to license** on the **Order licenses** tab.
* If you want to Bring Your Own License (BYOL), click the **IBM Spectrum Protect Plus license** tab, and then click **Add license file** to upload the IBM Spectrum Protect Plus license files that you own.

## Deployment process for IBM Spectrum Protect Plus
{: #spp_ordering-deploy}

The deployment of IBM Spectrum Protect Plus is automated. Whether you order an instance with this service included or you deploy the service later into your instance, the following steps are completed by the {{site.data.keyword.vmwaresolutions_full}} automation process:

1. Based on the settings you specify, endurance NFS storage is ordered from the {{site.data.keyword.cloud_notm}} infrastructure for the IBM Spectrum Protect Plus backup repository.
2. Based on the settings you specify, a number of licenses for IBM Spectrum Protect Plus are ordered from the {{site.data.keyword.cloud_notm}} infrastructure. The licenses are ordered in increments of 10 virtual machine (VM) license packs, based on the number of VMs that you specified to license when you ordered the IBM Spectrum Protect Plus service. If you want to bring an existing IBM Spectrum Protect Plus license, no license order is placed from the {{site.data.keyword.cloud_notm}} infrastructure.
3. The NFS storage that is ordered for this service is mounted to all the VMware® ESXi™ servers in the default cluster of the instance. Correct static routes are added on each ESXi server to the storage private subnet.
4. NFS datastores are created in vCenter Server for all NFS storage volumes that are mounted to the ESXi servers.
5. The IBM Spectrum Protect Plus VMs are deployed, activated, and configured in the default cluster of the instance.
6. The NFS storage that was ordered for this service is attached to the IBM Spectrum Protect Plus VM and the backup repository is configured.
7. The hostname and IP address of the IBM Spectrum Protect Plus VM are registered with the DNS server of the instance.

## Related links
{: #spp_ordering-related}

* [IBM Spectrum Protect Plus overview](/docs/vmwaresolutions?topic=vmwaresolutions-spp_considerations)
* [IBM Spectrum Protect Plus Preventive Service Planning](https://www-01.ibm.com/support/docview.wss?uid=swg22012650)
* [Managing IBM Spectrum Protect Plus](/docs/vmwaresolutions?topic=vmwaresolutions-managingspp)
* [Ordering services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices)
* [IBM Spectrum Protect Plus documentation](https://www.ibm.com/docs/en/spp/10.1.5)
* [Opening a case for IBM Spectrum Protect Plus](https://www.ibm.com/mysupport/s/article/How-to-Open-a-Case)
