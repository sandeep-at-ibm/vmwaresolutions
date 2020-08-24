---

copyright:

  years:  2016, 2020

lastupdated: "2020-08-19"

keywords: vCenter Server add service, view service vCenter Server, remove service vCenter Server

subcollection: vmwaresolutions

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and deleting services for vCenter Server instances
{: #vc_addingremovingservices}

You can order services for your VMware vCenter Server® instances, such as a disaster recovery solution. When you no longer need these services, you can delete them from your instances.

Only a limited number of add-on services are supported for vCenter Server with NSX-T instances.
{:important}

## Available services for vCenter Server instances
{: #vc_addingremovingservices-available-services}

The tables in the following two sections show the services that are available to vCenter Server instances, together with the installed service versions.

### Available services for vCenter Server with NSX-V instances
{: #vc_addingremovingservices-available-services-nsx-v}

The following table shows the services available for vCenter Server with NSX-V instances:

| Service name | Current version |
|--------------|-----------------|
| [Caveonix RiskForesight™](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations) | 2.3 |
| [F5® BIG-IP®](/docs/vmwaresolutions?topic=vmwaresolutions-f5_considerations) | BIG-IP VE v15.1.0.4 |
| [FortiGate® Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations) | 6.2.3 |
| [HyTrust® CloudControl™](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations) | 5.6 |
| [HyTrust DataControl®](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)  | 5.1.1 |
| [HyTrust KeyControl™](/docs/vmwaresolutions?topic=vmwaresolutions-htkc_considerations) | 5.0.1 |
| [{{site.data.keyword.IBM}} Security Services for SAP®](/docs/vmwaresolutions?topic=vmwaresolutions-managing-ss-sap) | N/A |
| [IBM Spectrum® Protect Plus](/docs/vmwaresolutions?topic=vmwaresolutions-spp_considerations) | V10.1.5 |
| [Juniper® vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-vsrx_overview) | 19.4R2.6 |
| [KMIP™ for VMware®](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations) | 2.0 |
| [PrimaryIO™ HDM](/docs/vmwaresolutions?topic=vmwaresolutions-managing_pio) | N/A |
| [Red Hat® OpenShift® for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_overview) | 4.4.13 |
| [Veeam®](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations) | 10 |
| [vRealize® Operations™ and Log Insight™](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview) | vROps 7.5 and vRLI 4.8 |
| [Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-addingzertodr) | 7.5 Update 3 |
{: caption="Table 1. Available services for vCenter Server with NSX-V instances" caption-side="top"}

### Available services for vCenter Server with NSX-T instances
{: #vc_addingremovingservices-available-services-nsx-t}

The following table shows the services available for vCenter Server with NSX-T instances:

| Service name | Current version |
|--------------|-----------------|
| [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations) | 2.3 |
| [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations) | 6.1.1 |
| [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)  | 5.1.1 |
| [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-vsrx_overview) | 19.4R2.6 |
| [Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations) | 10 |
| [vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview) | vROps 7.5 and vRLI 4.8 |
{: caption="Table 2. Available services for vCenter Server with NSX-T instances" caption-side="top"}

## Promotions for VMware Solutions add-on services
{: #vc_addingremovingservices-service-promotions}

{{site.data.keyword.vmwaresolutions_full}} offers promotion pricing for some add-on services. The promotions offer a number of months free of charge for a service’s licenses, if the service has license charges. For information about the promotions that are currently in effect, see the [pricing options](https://www.ibm.com/cloud/vmware/pricing){:external}.

You can use one promotion (promo) code for one or more services for:
* Ordering a new VMware vCenter Server instance
* Adding a service to a vCenter Server instance
* Ordering a stand-alone service (license), such as Caveonix or Veeam

For services that charge per host, for example, HCX, HyTrust CloudControl, HyTrust DataControl, and vRealize Operations and Log Insight, a promo code applies only to the hosts in the order or in the current environment.

You can use one promo code per order. Multiple promo codes are not allowed. However, you can use a promo code multiple times per account. Also, a promo code might apply to multiple services, for example, there might be a promo code that you can use for Veeam and Caveonix RiskForesight.

The UI provides a link for the available promotions, which displays a web page with information about the current promotions, including the promo codes for the services that are offering a promotion.

After you start an order, enter the promo code for one or more services in the promo code box and click **Apply**. If you decide to use a different promo code, enter that code in the box and click **Apply** again to calculate a new price.

If you apply a promo code for a service and then remove the service from your order, you must also remove the promo code from the order.

Promotion pricing starts when the promo is applied. The pricing is automatically changed to the recurring price when the promotion period ends. You can see the line-item discounts, promotion price, and recurring price in the generated PDF file.

## Resource requirements for add-on services
{: #vc_addingremovingservices-resource-requirements}

There are specific resource requirements for several add-on services.

For certain services, the system performs a capacity check before installing the service in your environment. Some services require a minimum amount of resources in order to be installed. The check is performed against the available capacity of the default cluster in the environment to ensure that the service components can fit.

During deployment, if the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email. The message displays the expected capacity for all of the services that failed the check.

If you are installing Red Hat OpenShift on a workload cluster, a capacity check is not performed before installation. However, an informational message is displayed with the expected capacity required to install the service.

To install the service, you must increase the capacity in your default cluster either by adding more hosts or by freeing up RAM, CPU, or disk space. After that, add the service or services again in the console and delete the existing service in the **Capacity Validation Failed** state by clicking the delete icon next to it.

The following table provides the resource requirements for services that the system performs a capacity check for before installing the service.

| Service name | Resource requirements |
|--------------|-----------------|
| Caveonix RiskForesight | CPU: 8 vCPUs<br>RAM: 32 GB<br>Storage: 100 GB |
| F5 BIG-IP[^f5bigip] | CPU: 4, 8, or 16 vCPUs depending on license and bandwidth chosen<br>RAM: 8, 16, or 32 GB depending on license and bandwidth chosen |
| FortiGate Virtual Appliance | CPU: 4, 8, or 16 vCPUs depending on license chosen<br>RAM: 8, 12, or 24 GB depending on license chosen |
| HyTrust CloudControl | CPU: 4 vCPUs<br>RAM: 16 GB<br>Storage:<br>For version 5.6: 70 GB VMDK resident on vSAN<br> For version 6.1.1: 186 GB VMDK resident on vSAN |
| IBM Spectrum Protect Plus | CPU: 16 vCPUs<br>RAM: 48 GB |
| Juniper vSRX | You must have enough available capacity to accommodate two VMs with the following requirements, on different hosts:<br>CPU: 12 vCPUs<br>RAM: 16 GB<br>Storage: 32 GB |
| Red Hat OpenShift | CPU: 27 vCPUs<br>RAM: 155 GB<br>Storage: 952 GB |
| Veeam | If you select Veeam as a VSI option, there is no capacity requirement.<br>If you select Veeam as a VM option, the following capacity is required:<br>CPU: 8 vCPUs<br>RAM: 32 GB<br>Storage: 100 GB |
| vRealize Operations and Log Insight | CPU: 18 vCPUs<br>RAM: 208 GB |
| Zerto | CPU: 2 vCPUs<br>RAM: 4 GB |
{: caption="Table 3. Resources required for services the system checks for capacity problems" caption-side="top"}

[^f5bigip]: For more information, see the table in [Considerations when you install F5 BIG-IP](/docs/vmwaresolutions?topic=vmwaresolutions-f5_considerations#f5_considerations-install).

### Formulas for calculating space requirements for services
{: #vc_addingremovingservices-resource-requirements-spacecalc-forms}

The following formulas are used to calculate the space requirements for the services and the management overheads.

#### Formula to calculate the number of available cores
{: #vc_addingremovingservices-resource-requirements-spacecalc-forms-cores}

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

The following table lists the variables that are used in the previous formula.

| Variable | Description | Unit | vSAN example | NFS example |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores | The number of cores available for workloads and services in the environment | Cores | 38 | 43 |
| HostCount | The number of hosts in the default cluster | Hosts | 4 | 4 |
| HostCoreCount | The number of raw cores available in each host in the default cluster | Cores | 16 | 16 |
| HostOverheadCores | The number of cores that are reserved by the ESXi server as overhead | Cores | 0.1 | 0.1 |
| MgmtOverheadCores | The number of cores reserved by the vCenter Server management components (vCenter Server, PSC, AD/DNS, Edges) | Cores | 5 | 5 |
| vSphereHAHostTolerance | The number of hosts to tolerate in the vSphere HA configuration | Hosts | 1 | 1 |
| HostVsanOverheadCorePercentage | The percentage of a host cores used by vSAN | % | 10 | 0 |
{: caption="Table 4. Description of variables in Formula 1" caption-side="top"}

#### Formula to calculate the available memory
{: #vc_addingremovingservices-resource-requirements-spacecalc-forms-memory}

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

The following table lists the variables that are used in the previous formula.

| Variable | Description | Unit | vSAN example | NFS example |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory | The number of GB of memory available for workloads and services in the environment | GB | 693 | 860 |
| HostCount | The number of hosts in the default cluster | Hosts | 6 | 6 |
| HostMemory | The number of raw GB of memory available in each host in the default cluster | GB | 192 | 192 |
| HostVsanCapacityDiskSize | The number of GB of a capacity of each vSAN capacity SSD disk on this host | GB | 960, 1,946, or 3,891 | 0 |
| HostOverheadMemory | The number of GB of memory that is reserved by the ESXi server as overhead | GB | 4.6 | 4.6 |
| MgmtOverheadMemory | The number of GB of memory reserved by the vCenter Server management components (vCenter Server, PSC, AD/DNS, Edges) | GB | 77 | 77 |
| vSphereHAHostTolerance | The number of hosts to tolerate in the vSphere HA configuration | Hosts	| 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | The number of GB of memory reserved by vSAN management (represented as percentage of one of the capacity vSAN disks) | % | 2.75% | 2.75% |
| HostVsanOverheadMemory | The number of GB of memory reserved by vSAN management regardless of disk size | GB |  7 | 0 |
{: caption="Table 5. Description of variables in Formula 2" caption-side="top"}

## Procedure to add services to vCenter Server instances
{: #vc_addingremovingservices-adding-procedure}

To add a service to your vCenter Server instance, click the appropriate service link in the previous table to review the considerations for the service and to check the components that are deployed. Then, follow the instructions in the service ordering topic to add the service to your instance.

### Service installation results
{: #vc_addingremovingservices-adding-results}

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Services** page of the instance with the **Installed** status.

## Procedure to view services for vCenter Server instances
{: #vc_addingremovingservices-viewing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** on the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to view services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, click a service to review information about it, such as the service status and other details.
5. Depending on the viewed service, you can access the service consoles by using the credentials that are provided on the service details and you can manage the service from here.

The 12-month commitment expiration date for the VMware HCX is available on the HCX details page.
{:note}

## Procedure to delete services for vCenter Server instances
{: #vc_addingremovingservices-removing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to delete services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, locate the service instance that you want to delete, click the vertical overflow menu next to the **Status** column, and then click **Delete service**.
5. In the **Remove service** window, review the considerations or warnings if there are any and select **I Understand**. Click **Delete**.

### Results after you delete a service
{: #vc_addingremovingservices-removing-results}

After your request to delete a service is accepted, the service status is changed to **Removing**.

When the service deletion is completed successfully, you are notified by email, and the service is deleted from the **Services** page of the instance.

You are billed until the end of the {{site.data.keyword.cloud}} infrastructure billing cycle for the deleted services.
{:note}

## Related links
{: #vc_addingremovingservices-related}

* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
