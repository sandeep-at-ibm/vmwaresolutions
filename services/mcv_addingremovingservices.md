---

copyright:

  years:  2021

lastupdated: "2021-06-14"

keywords: VMware Mission Critical, request Mission Critical, tech specs Mission Critical, Multizone add services, Multizone on services, services for multizone instances

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering, viewing, and deleting services for vCenter Server multizone instances
{: #mcv_addingremovingservices}

When you order a VMware vCenter Server® multizone instance, you can also order add-on services. The following services are supported on vCenter Server multizone instances:
{: shortdesc}

* Caveonix RiskForesight™
* HyTrust® CloudControl™
* Juniper® vSRX
* Veeam®
* vRealize Operations™ and Log Insight™ vROps and vRLI.

## Resource requirements for services
{: #mcv_addingremovingservices-resource-reqs}

Some services require a minimum amount of resources to be installed.

For certain services, the system completes a capacity check on the targeted clusters before it installs the service in your environment. The check is completed against the available capacity of the targeted cluster in the environment to ensure that the service components can fit.

During deployment, if the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email. The message displays the expected capacity for all services that do not meet the requirements.

To install the service, you must increase the capacity in your cluster either by adding more VMware ESXi™ servers or by freeing up RAM, CPU, or disk space. After that, you can add the service or services again. To remove the existing service in the **Capacity Validation Failed** state, click the delete icon next to it.

The following table provides the resource requirements for the services that the
system performs a capacity check for. The table includes only the add-on services that are supported on vCenter Server multizone instances:

* Caveonix RiskForesight
* HyTrust CloudControl
* Juniper vSRX
* Veeam
* vRealize Operations and Log Insight


| Service name | Resource requirements |
|:------------ |:--------------------- |
| Caveonix RiskForesight | CPU - 8 CPUs<br>RAM - 32 GB<br>Storage - 100 GB |
| HyTrust CloudControl | CPU - 4 CPUs<br>RAM - 16 GB<br>Storage - 186 GB VMDK resident on vSAN™ |
| Juniper vSRX | You must have enough available capacity to accommodate two VMs with the following requirements, on different hosts:<br>CPU - 6 CPUs<br>RAM - 16 GB<br>Storage - 18 GB |
| Veeam | If you select Veeam as a VSI option, you do not have a capacity requirement.<br><br>If you select Veeam as a VM option, the following capacity is required:<br>CPU - 8 CPUs<br>RAM - 32 GB<br>Storage - 100 GB<br><br>If you select Veeam as a bare metal server option, you do not have a capacity requirement. |
| vRealize Operations and Log Insight | CPU - 18 CPUs<br>RAM - 208 GB<br><br>You must have an estimated 750 GB of vSAN storage. |
{: caption="Table 1. Resources required for multizone services that the system checks for capacity requirements" caption-side="top"}

### Formulas for calculating space requirements for services
{: #mcv_addingremovingservices-resource-requirements-spacecalc-forms}

The following formulas are used to calculate the space requirements for the services and the management overheads. The formulas apply to management clusters, workload clusters, edge services clusters, and single-node management clusters.

For management clusters on multizone instances, approximately half of the resources are available for service installs. Therefore, for management clusters, use the formulas that are provided with approximately half of the resources.

#### Formula to calculate the number of available cores
{: #mcv_addingremovingservices-resource-requirements-spacecalc-forms-cores}

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
{: caption="Table 2. Description of variables in formula 1" caption-side="top"}

[^mgmtcores]: Management cluster only. No core reservation for the workload cluster, the edge services cluster, and the single-node management cluster.

[^vspherehacores]: Management and workload clusters only. No hosts are reserved for the edge services cluster or the single-node management cluster.

#### Formula to calculate the available memory
{: #mcv_addingremovingservices-resource-requirements-spacecalc-forms-memory}

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
{: caption="Table 3. Description of variables in formula 2" caption-side="top"}

[^mgmtmem]: Management cluster only. No memory reservation for the workload cluster, the edge services cluster, and the single-node management cluster.

[^vspherehamem]: Management and workload clusters only. No hosts are reserved for the edge services cluster or the single-node management cluster.

## Procedure to add services to vCenter Server multizone instances
{: #mcv_addingremovingservices-add-services-procedure}

You can easily add one or more of the services that are supported on vCenter Server multizone instances when you order your instance. The supported services are:

* Caveonix RiskForesight
* HyTrust CloudControl
* Juniper vSRX
* Veeam
* vRealize Operations and Log Insight

Follow the steps that are described in [Ordering vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_ordering). You select the values for various items, such as licensing, cluster information, and the network interface. The services section displays the services you can install. Choose your services and configure them, as needed.

For more information about each service's considerations and to check the components that are deployed, see the topics below. To add a service to your instance, follow the instructions in the service ordering topic.

* [Caveonix RiskForesight overview](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations)
* [Ordering Caveonix RiskForesight](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_ordering)
* [HyTrust CloudControl overview](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [Ordering HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_ordering)
* [Juniper vSRX overview](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-overview)
* [Ordering Juniper vSRX](/docs/vmwaresolutions?topic=vmwaresolutions-juniper-ordering)
* [Veeam v11 overview](/docs/vmwaresolutions?topic=vmwaresolutions-veeamvm_overview)
* [Ordering Veeam](/docs/vmwaresolutions?topic=vmwaresolutions-veeam_ordering)
* [vRealize Operations and Log Insight overview](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_overview)
* [Ordering vRealize Operations and Log Insight](/docs/vmwaresolutions?topic=vmwaresolutions-vrops_ordering)

### Service installation results
{: #mcv_addingremovingservices-adding-results}

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Services** page of the instance with the **Installed** status.

The services are deployed only to a single zone of your multizone instance. If you want to operate the services across both availability zones, you must modify the configuration.

## Procedure to view services for vCenter Server multizone instances
{: #mcv_addingremovingservices-viewing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** on the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to view services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, click a service to review information about it, such as the service status and other details.
5. Depending on the viewed service, you can access the service consoles by using the credentials that are provided on the service details and you can manage the service from here.

## Procedure to delete services for vCenter Server multizone instances
{: #mcv_addingremovingservices-removing-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **vCenter Server instances** table, click the instance for which you want to delete services.
3. Click **Services** on the left navigation pane.
4. On the **Services** page, locate the service instance that you want to delete, click the vertical overflow menu next to the **Status** column, and then click **Delete service**.
5. In the **Remove service** window, review the considerations or warnings if there are any and select **I Understand**. Click **Delete**.

## Related links
{: #mcv_addingremovingservices-related-links}

* [IBM Cloud for VMware Mission Critical Workloads overview](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_overview)
* [Requesting managed IBM Cloud for VMware Mission Critical Workloads](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_ordering-managed)
* [Adding, viewing, and deleting clusters for vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_addviewdeleteclusters)
* [Expanding and contracting capacity for vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_addingremovingservers)
* [Viewing and deleting vCenter Server multizone instances](/docs/vmwaresolutions?topic=vmwaresolutions-mcv_viewinginstance)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [VMware vSphere Introduction to Stretched Clusters](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vsan-planning.doc/GUID-1BDC7194-67A7-4E7C-BF3A-3A0A32AEECA9.html){:external}
