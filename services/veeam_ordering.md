---

copyright:

  years:  2016, 2020

lastupdated: "2020-07-22"

keywords: Veeam, Veeam configuration, order Veeam

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering Veeam
{: #veeam_ordering}

You can include the Veeam service with a new vCenter Server instance or add the service to your existing vCenter Server instance.

## Ordering Veeam for a new instance
{: #veeam_ordering-new}

When you [order the instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the **Optional services** section and click **Veeam** in the **Business continuity and migration** category. Follow the steps to add the service to your instance.

## Ordering Veeam for an existing instance
{: #veeam_ordering-existing}

On the [instance details page](/docs/vmwaresolutions?topic=vmwaresolutions-vc_viewinginstances), click **Services** on the left navigation pane, click **Veeam** in the **Business continuity and migration** category, and then click **Add**. Follow the steps to add the service to your instance.

## Veeam service configuration
{: #veeam_ordering-config}

When you order the service, provide the following settings.

### Number of VMs to license
{: #veeam_ordering-config-vms}

At least 10 VMs are required for license management.

### Storage size
{: #veeam_ordering-config-storage-size}

The capacity that meets your storage needs. For an example that shows what the capacity might be like, see [Capacity planning for backup repositories](https://helpcenter.veeam.com/docs/one/reporter/capacity_planning_for_repositories.html?ver=100){:external}.

### Storage performance
{: #veeam_ordering-config-storage-performance}

The IOPS (input/output operations per second) per GB based on your workload requirements.

## Related links
{: #veeam_ordering-related}

* [Veeam v9.5 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations)
* [Veeam v10 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Managing Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-managingveeam)
* [Ordering Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering_licenses)
* [Managing Veeam licenses](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_managing_licenses)
* [Ordering and configuring IBM Cloud Object Storage with Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-icos_ordering)
* [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices)
* [Veeam backup and replication](https://www.ibm.com/cloud/architecture/architectures/virtualization_backup_veeam){:external}
* [Veeam website](https://www.veeam.com/){:external}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:external}
