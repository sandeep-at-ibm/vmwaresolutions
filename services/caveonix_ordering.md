---

copyright:

  years:  2016, 2021

lastupdated: "2021-10-21"

keywords: Caveonix RiskForesight, Caveonix configuration, order Caveonix

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Ordering Caveonix RiskForesight
{: #caveonix_ordering}

You can include the Caveonix RiskForesight™ service with a new VMware vCenter Server® instance or add the service to your existing vCenter Server instance. On these standard vCenter Servers instances, Caveonix RiskForesight generates a license for the number of VMs that you select.

On VMware® Regulated Workloads and VMware Security and Compliance Readiness Bundle instances, Caveonix RiskForesight offers per host licensing. You are charged for every host on the instance, which includes management, workload, and edge services clusters.

## Ordering Caveonix RiskForesight for a new instance
{: #caveonix_ordering-new}

When you [order the instance](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance#vc_orderinginstance-procedure), scroll down to the services section and click **Caveonix RiskForesight** in the **Security and compliance** category. Follow the steps to add the service to your instance.

## Ordering Caveonix RiskForesight for an existing instance
{: #caveonix_ordering-existing}

1. On the instance details page, click **Services** on the left navigation pane.
2. Click **Add** to add the service.
3. On the **Services** page, locate the **Caveonix RiskForesight** service and toggle its switch on.
4. Follow the steps to configure and add the service to your instance.

## Caveonix RiskForesight configuration
{: #caveonix_ordering-config}

When you order the Caveonix RiskForesight service, provide the following settings.

### License name
{: #caveonix_ordering-config-license-name}

The license name does not apply to VMware Regulated Workloads or Security and Compliance Readiness Bundle instances.
{: note}

Specify a unique name for this license. The name must be unique across all Caveonix service instances and all instances in the {{site.data.keyword.cloud}} account.

### License notes
{: #caveonix_ordering-config-license-notes}

The license notes do not apply to VMware Regulated Workloads or Security and Compliance Readiness Bundle instances.
{: note}

Enter the notes for the service instance. You can edit the notes later on the license details page.

### Number of VMs to license
{: #caveonix_ordering-config-vms}

The number of VMs to license does not apply to VMware Regulated Workloads or Security and Compliance Readiness Bundle instances.
{: note}

Specify the number of VMs (virtual machines) to license, in increments of 10. At least 10 VMs are required for license management.

After you order the Caveonix RiskForesight service, if you want more VMs licensed than you specified in the order, you can:

1. Replace your Caveonix RiskForesight license by ordering a larger license.
2. Copy the license to your Caveonix RiskForesight console.
3. Delete the previous license from the {{site.data.keyword.vmwaresolutions_short}} console.

For more information, see the following procedures.

* [Procedure to order Caveonix RiskForesight licenses](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_license_ordering#caveonix_license_ordering-procedure)
* [Procedure to delete Caveonix RiskForesight licenses](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_license_managing#caveonix_license_managing_procedure-delete)

## Related links
{: #caveonix_ordering-related}

* [Caveonix RiskForesight overview](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations)
* [Managing Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-managingcaveonix)
* [Ordering services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
