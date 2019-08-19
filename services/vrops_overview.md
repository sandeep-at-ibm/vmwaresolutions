---

copyright:

  years:  2019

lastupdated: "2019-08-12"

keywords: vRealize, vRealize info, tech specs vRealize

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware vRealize Operations and vRealize Log Insight on IBM Cloud overview
{: #vrops_overview}

The VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud}} service deploys the VMware vRealize Operations (vROps) and VMware vRealize Log Insight (vRLI) tools, which help you operate and monitor the performance, health, and capacity of your IBM-hosted, dedicated VMware environment.

These tools are deployed by using the IBM advanced automation and are based on a consistent highly available design. vROps includes preinstalled and configured Management Packs to provide deeper visibility into the core VMware Software Defined Data Center components like VMware NSX, vSAN, and HCX. The automation provides optimized dashboards out of the box so that you can monitor the full VMware stack  more easily.

It also includes vRLI so that you can more quickly troubleshoot issues using log files.

Like the other VMware components in the stack, you have the flexibility to bring your enterprise licenses to the cloud (per CPU or OSI) or to rent VMware licenses from {{site.data.keyword.cloud_notm}}.

This service is available only to VMware vCenter Server on {{site.data.keyword.cloud_notm}} instances that are deployed in V3.2 and later releases. The current versions that are installed are vROps 7.6 and vRLI 4.6.
{:note}

## Technical specifications for VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #vrops_overview-specs}

The following components are ordered and included in the VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} service:
* VMware vRealize Operations (vROps) 7.6
* VMware vRealize Log Insight (vRLI) 4.6

For information about the design, requirements and preconfigured management packs, see [Operations management architecture overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-arch).

### Resource requirements for VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #vrops_overview-resource-req}

The following table lists the minimum requirements to order VMware vRealize Operations and vRealize Log Insight on IBM Cloud.

| Item        | Description       |  
|:------------- |:------------- |
| Cores | 18 |
| Memory (GB) | 208 |
{: caption="Table 1. Minimum requirements for VMware vRealize Operations and vRealize Log Insight" caption-side="top"}

### Formulas for calculating vRealize Operations and vRealize Log Insight on IBM Cloud space requirements
{: #vrops_overview-formulas}

The following formulas are used to calculate the space requirements for vRealize Operations and Log Insight on IBM Cloud and the management overheads.

#### Formula to calculate the number of available cores
{: #vrops_overview-formulas-1}

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
{: #vrops_overview-formulas-2}

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

## Considerations when you install VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #vrops_overview-install}

* Before the service is installed in your environment, a check is performed against the available capacity of the default cluster in the environment to ensure that the service components can fit.
* If the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email.
* To install the service, you must increase the capacity in your default cluster by either adding more hosts or by freeing up RAM, CPU, or disk space, and then add the service again in the console. After that, you can remove the existing service in the **Capacity Validation Failed** state by clicking the delete icon next to it.

## Considerations when you remove VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #vrops_overview-remove}

Review the following considerations before you remove the service:
* Only the virtual machines (VMs) that were deployed during the initial installation of vRealize Operations and vRealize Log Insight on IBM Cloud are deleted. Any node that is deployed after the installation will not be cleaned up.
* The VXLAN, DLR, and the Edge Gateway that were created during the initial deployment of vRealize Operations and vRealize Log Insight on IBM Cloud will be deleted. The VMs that you deployed on VXLAN will lose connectivity after starting the removal of vRealize Operations and vRealize Log Insight on IBM Cloud.
* If you remove VMware vRealize Operations and vRealize Log Insight on IBM Cloud, you need to remove the Syslog Server from the NSX Manager and the NSX Controller manually.

### Removing the Syslog Server from the NSX Manager
{: #vrops_overview-remove-nsx-manager}

1. Log in to the console of the NSX Manager Appliance.
2. Select **Manage Appliance Settings**.
3. Under the **General** tab, remove the Syslog Server configuration.

### Removing the Syslog Server from the NSX Controller nodes
{: #vrops_overview-remove-nsx-controller}

1. Log in to the VMware vSphere Web Client.
2. Go to **Networking & Security > Installation and Upgrade > Management > NSX Controller Nodes**.
3. Select the NSX Manager that manages the NSX Controller nodes that you want to modify.
4. Click the Common Controller Attributes EDIT link.
5. Remove any Syslog Servers as needed.

## Related links
{: #vrops_overview-related}

* [Ordering VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vrops_ordering)
* [Managing VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_vrops)
