---

copyright:

  years:  2021

lastupdated: "2021-06-18"

keywords: vCenter Server add service

subcollection: vmwaresolutions

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering services for vCenter Server instances
{: #vc_addingservices}

You can order services for your VMware vCenter Server® instances, such as a disaster recovery solution.

Services support varies between vCenter Server with NSX-V and vCenter Server with NSX-T™ instances.
{:important}

## Available services for vCenter Server instances
{: #vc_addingservices-available-services}

The tables in the following two sections show the services that are available to vCenter Server instances, together with the installed service versions.

### Available services for vCenter Server with NSX-T instances
{: #vc_addingservices-available-services-nsx-t}

The following table shows the services available for vCenter Server with NSX-T instances:

| Service name | Current version |
|--------------|-----------------|
| [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations) | 3.0 |
| [F5 BIG-IP](/docs/vmwaresolutions?topic=vmwaresolutions-f5_considerations) | BIG-IP VE v15.1.2.1 |
| [VMware HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations) | Version periodically updated to the latest version |
| [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations) | 6.3.1 |
| [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)  | 5.3 |
| [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview) | 3.0 (20.4R1.12) |
| [Red Hat OpenShift for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_overview) | 4.6[^nsxtver] |
| [Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations) | 11 |
| [vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview) | vROps 8.2 and vRLI 8.2 |
{: caption="Table 1. Available services for vCenter Server with NSX-T instances" caption-side="top"}

[^nsxtver]: If you add the service to an existing instance, you must upgrade NSX-T from 2.5.1 to 3.1.

### Available services for vCenter Server with NSX-V instances
{: #vc_addingservices-available-services-nsx-v}

The following table shows the services available for vCenter Server with NSX-V instances:

| Service name | Current version |
|--------------|-----------------|
| [Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations) | 3.0 |
| [F5 BIG-IP](/docs/vmwaresolutions?topic=vmwaresolutions-f5_considerations) | BIG-IP VE v15.1.2.1 |
| [FortiGate Virtual Appliance](/docs/vmwaresolutions?topic=vmwaresolutions-fortinetvm_considerations) | 6.4.4 |
| [VMware HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations) | Version periodically updated to the latest version |
| [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)  | 5.3 |
| [{{site.data.keyword.IBM}} Security Services for SAP](/docs/vmwaresolutions?topic=vmwaresolutions-managing-ss-sap) | N/A |
| [IBM Spectrum Protect Plus](/docs/vmwaresolutions?topic=vmwaresolutions-spp_considerations) | V10.1.5 |
| [Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview) | 3.0 (20.4R1.12) |
| [KMIP for VMware](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations) | 2.0 |
| [PrimaryIO HDM](/docs/vmwaresolutions?topic=vmwaresolutions-managing_pio) | N/A |
| [Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_considerations) | 11 |
| [vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview) | vROps 8.2 and vRLI 8.2 |
| [Zerto](/docs/vmwaresolutions?topic=vmwaresolutions-addingzertodr) | 7.5 Update 3 |
{: caption="Table 2. Available services for vCenter Server with NSX-V instances" caption-side="top"}

## Promotions for services
{: #vc_addingservices-service-promotions}

{{site.data.keyword.vmwaresolutions_full}} offers promotion pricing for some services. The promotions offer a number of months free of charge for service licenses, if the service has license charges. For more information about the promotions that are available, see the [pricing options](https://www.ibm.com/cloud/vmware/pricing){:external}.

You can use one promotion (promo) code for one or more services for:
* Ordering a new VMware vCenter Server instance
* Adding a service to a vCenter Server instance
* Ordering a stand-alone service license, such as Caveonix or Veeam®

For services that charge per host, for example, HCX™, HyTrust CloudControl™, HyTrust DataControl®, and vRealize Operations™ and Log Insight™, a promo code applies only to the hosts in the order or in the current environment.

You can use one promo code per order. Multiple promo codes are not allowed. However, you can use a promo code multiple times per account. A promo code might apply to multiple services, for example, Veeam and Caveonix RiskForesight™.

After you start an order, enter the promo code for one or more services in the promo code box and click **Apply**. If you decide to use a different promo code, enter that code in the box and click **Apply** again to calculate a new price.

If you apply a promo code for a service and then remove the service from your order, you must also remove the promo code from the order.

Promotion pricing starts when the promo is applied. The pricing is automatically changed to the recurring price when the promotion period ends. You can see the discounts, promotion price, and recurring price in the PDF file generated for your order.

## Services support for vCenter Server multizone instances
{: #vc_addingservices-multizone-vcs-instances}

The following services are supported on vCenter Server multizone instances:

* Caveonix RiskForesight
* HyTrust CloudControl
* Juniper vSRX
* Veeam
* vRealize Operations and Log Insight

The services are deployed only to a single zone of your multizone instance. If you want to operate the service across both availability zones, you must modify the configuration.

For more information about multizone instances, see the following topics:

* [Ordering vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_ordering).
* [Ordering, viewing, and deleting services for vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_addingremovingservices)

## Resource requirements for services
{: #vc_addingservices-resource-requirements}

Some services require a minimum amount of resources to be installed.

For certain services, the system completes a capacity check on the targeted clusters before it installs the service in your environment. The check is completed against the available capacity of the targeted cluster in the environment to ensure that the service components can fit.

During deployment, if the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email. The message displays the expected capacity for all services that do not meet the requirements.

To install the service, you must increase the capacity in your cluster either by adding more VMware ESXi™ servers or by freeing up RAM, CPU, or disk space. After that, you can add the service or services again. To remove the existing service in the **Capacity Validation Failed** state, click the delete icon next to it.

The following table provides the resource requirements for the services that the system performs a capacity check on.

| Service name | Resource requirements |
|:------------ |:--------------------- |
| Caveonix RiskForesight | CPU: 8 CPUs<br>RAM: 32 GB<br>Storage: 100 GB |
| F5 BIG-IP[^f5bigip] | CPU: 4, 8, or 16 CPUs, depending on license and bandwidth chosen<br>RAM: 8, 16, or 32 GB depending on license and bandwidth chosen |
| FortiGate Virtual Appliance | CPU: 2, 4, 8, or 16 CPUs, depending on license chosen<br>RAM: 4, 6, or 12 GB depending on license chosen |
| HyTrust CloudControl | CPU: 4 CPUs<br>RAM: 16 GB<br>Storage: 186 GB VMDK resident on vSAN™ |
| IBM Spectrum Protect Plus | CPU: 16 CPUs<br>RAM: 48 GB |
| Juniper vSRX | You must have enough available capacity to accommodate two VMs with the following requirements, on different hosts:<br>CPU: 6 CPUs<br>RAM: 16 GB<br>Storage: 18 GB |
| Red Hat OpenShift | CPU: 27 CPUs<br>RAM: 155 GB<br><br> If you install Red Hat OpenShift with vSAN™ storage, you must have an estimated 952 GB of vSAN storage. This storage requirement is only applicable to vSAN because the installation of Red Hat OpenShift on an NFS instance orders its own NFS storage. |
| Veeam | If you select Veeam as a VSI option, there is no capacity requirement.<br><br>If you select Veeam as a VM option, the following capacity is required:<br>CPU: 8 CPUs<br>RAM: 32 GB<br>Storage: 100 GB<br><br>If you select Veeam as a bare metal server option, there is no capacity requirement. |
| VMware HCX | For each gateway in the active-passive pair of VMware NSX® edge services gateways:<br>CPU: 6 CPUs<br>RAM: 8 GB<br>Storage: 3 GB VMDK<br><br>For HCX Management Appliance VM:<br>CPU: 4 CPUs<br>RAM: 12 GB<br>Storage: 60 GB VMDK |
| vRealize Operations and Log Insight | CPU: 18 CPUs<br>RAM: 208 GB<br><br>If you install vRealize Operations with vSAN storage, you must have an estimated 750 GB of vSAN storage. This storage requirement is only applicable to vSAN because the installation of vROps on an NFS instance orders its own NFS storage. |
| Zerto | CPU: 2 CPUs<br>RAM: 4 GB |
{: caption="Table 3. Resources required for the services that the system checks for capacity requirements" caption-side="top"}

[^f5bigip]: For more information, see the table in [Considerations when you install F5 BIG-IP](/docs/vmwaresolutions?topic=vmwaresolutions-f5_considerations#f5_considerations-install).

### Formulas for calculating space requirements for services
{: #vc_addingservices-resource-requirements-spacecalc-forms}

The following formulas are used to calculate the space requirements for the services and the management overheads. The formulas apply to management clusters, workload clusters, edge services clusters, and single-node management clusters.

#### Formula to calculate the number of available cores
{: #vc_addingservices-resource-requirements-spacecalc-forms-cores}

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

The following table lists the variables that are used in the previous formula.

| Variable | Description | Unit | vSAN example | NFS example |
|:-------- |:----------- |:---- |:------------ |:----------- |
| AvailableCores | The number of cores available for workloads and services in the environment | Cores | 38 | 43 |
| HostCount | The number of hosts in the default cluster | Hosts | 4 | 4 |
| HostCoreCount | The number of raw cores available in each host in the default cluster | Cores | 16 | 16 |
| HostOverheadCores | The number of cores that are reserved by the ESXi server as overhead | Cores | 0.1 | 0.1 |
| MgmtOverheadCores[^mgmtcores] | The number of cores reserved by the vCenter Server management components (vCenter Server, PSC, AD/DNS, Edges) | Cores | 5 | 5 |
| vSphereHAHostTolerance[^vspherehacores] | The number of hosts to tolerate in the vSphere HA configuration | Hosts | 1 | 1 |
| HostVsanOverheadCorePercentage | The percentage of a host's cores used by vSAN | % | 10 | 0 |
{: caption="Table 4. Description of variables in formula 1" caption-side="top"}

[^mgmtcores]: Management cluster only. No core reservation for the workload cluster, the edge services cluster, and the single-node management cluster.

[^vspherehacores]: Management and workload clusters only. No hosts are reserved for the edge services cluster or the single-node management cluster.

#### Formula to calculate the available memory
{: #vc_addingservices-resource-requirements-spacecalc-forms-memory}

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

The following table lists the variables that are used in the previous formula.

| Variable | Description | Unit | vSAN example | NFS example |
|:-------- |:----------- |:---- |:------------ |:----------- |
| AvailableMemory | The number of GB of memory available for workloads and services in the environment | GB | 693 | 860 |
| HostCount | The number of hosts in the default cluster | Hosts | 6 | 6 |
| HostMemory | The number of raw GB of memory available in each host in the default cluster | GB | 192 | 192 |
| HostVsanCapacityDiskSize | The number of GB of a capacity of each vSAN capacity SSD disk on this host | GB | 960, 1,946, or 3,891 | 0 |
| HostOverheadMemory | The number of GB of memory that is reserved by the ESXi server as overhead | GB | 4.6 | 4.6 |
| MgmtOverheadMemory[^mgmtmem] | The number of GB of memory reserved by the vCenter Server management components (vCenter Server, PSC, AD/DNS, Edges) | GB | 77 | 77 |
| vSphereHAHostTolerance[^vspherehamem] | The number of hosts to tolerate in the vSphere HA configuration | Hosts | 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | The number of GB of memory reserved by vSAN management (represented as percentage of one of the capacity vSAN disks) | % | 2.75% | 2.75% |
| HostVsanOverheadMemory | The number of GB of memory reserved by vSAN management regardless of disk size | GB |  7 | 0 |
{: caption="Table 5. Description of variables in formula 2" caption-side="top"}

[^mgmtmem]: Management cluster only. No memory reservation for the workload cluster, the edge services cluster, and the single-node management cluster.

[^vspherehamem]: Management and workload clusters only. No hosts are reserved for the edge services cluster or the single-node management cluster.

## Procedure to order services for vCenter Server instances
{: #vc_addingservices-procedure}

To order a service for your vCenter Server instance, click the appropriate service link in the previous tables in [Available services for vCenter Server instances](#vc_addingservices-available-services) to review the considerations for the service and to check the components that are deployed. Then, follow the instructions in the service ordering topic to add the service to your instance.

## Results after you order a service
{: #vc_addingservices-results}

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Services** page of the instance with the **Installed** status.

## Related links
{: #vc_addingservices-related}

* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
