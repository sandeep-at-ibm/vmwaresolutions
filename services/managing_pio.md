---

copyright:

  years:  2019, 2020

lastupdated: "2020-08-07"

keywords: primary io hdm, hdm intro, tech specs hdm

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# PrimaryIO Hybrid Cloud Data Management (HDM) overview
{: #managing_pio}

The PrimaryIO Hybrid Cloud Data Management (HDM) service decouples virtual machines (VMs) and storage (VMDKs) to seamlessly move workloads to and from {{site.data.keyword.cloud}} faster and efficiently. The PrimaryIO HDM solution enables a hybrid cloud environment to extend on-premises VMware environments to the public cloud for on-demand compute capacity.

HDM has built-in functions to identify frequently used data, called hot data. Hot data is moved into an intelligent cloud cache, while less used data is moved to the background. This way, HDM can provision workloads in the {{site.data.keyword.cloud_notm}} within minutes.

​HDM combines data I/O analysis with an intelligent cloud cache to decouple VMs and VMDKs for workload portability. It accomplishes workload mobility in three steps:
1. Analyze: Analyzes on-premises VMs and VMDKs and identifies VMs that are most suitable for the cloud.
  1. Identifies active data (hot data set) between VMs and VMDKs.
  2. Predicts the active data set to prefetch data.
  3. Recommends the minimal size of cache that is required for the VMs to quickly run in the cloud.
2. Cloud cache: Copies only the hot data set into the cloud cache instead of replicating the entire VMDK in the cloud storage. Minimizes the data footprint in the cloud.
3. Flex: Securely migrates the VMs (compute only) to the cloud, by using the hot data set in the cloud cache.

## Key benefits of HDM
{: #managing_pio-benefits}

PrimaryIO HDM enables the following use cases:
* **VM I/O Profiling**. HDM gives visibility into a VM’s disk I/O performance, including read/write patterns and disk access block size histograms for read/write transactions from and to the VMDKs.
* **Try-Before-Commit**. HDM enables rapid testing of applications in the cloud. It requires only a working set in the cloud cache and it avoids full data replication. The key benefits are reduced time and cost of testing in the cloud.
* **Cloud Extension**. HDM enables Development and Testing (Dev/Test) and seasonal workloads to use the cloud infrastructure for temporary use with minimal data exposure. Therefore, full replication of production data set in the cloud is avoided. The key benefits are: on-demand capacity, control on data exposure, and reduced costs.
* **Agile Migration**. HDM provides two different modes to migrate workloads to cloud:
  * Warm migration enables VMs to be migrated while the workloads are running in the cloud with only the working set until all the data is transferred. Upon successful transfer of the full data set, all data changes are synced and an updated VM is started in the cloud.
  * Cold migration migrates the VM along with data to the cloud. The VM is powered off until the transfer is completed.

## Technical specifications for PrimaryIO HDM
{: #managing_pio-specs}

For information about resource requirements and capacity checking for some services, see [Resource requirements for add-on services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

The following technical specifications apply to PrimaryIO HDM.

### HDM deployment configuration
{: #managing_pio-deploy-config}

* Cluster: Requires at least two ESXi servers to ensure that HA requirements for the HDM product are met.
* Stand-alone: Requires at least one ESXi server.
* Appliance only: Requires that only the PIO Appliance is deployed. Recommended for cold migration only.

### HDM on-premises components
{: #managing_pio-onprem-comp}

The following components belong to HDM on-premises.

#### Virtual instances for HDM on-premises
{: #managing_pio-onprem-virt-inst}

* **PrimaryIO Appliance**
  * 4 vCPU
  * 8 GB RAM
  * 144 GB storage

* **Performance**. The configuration that is deployed uses no more than 15% of compute and memory resources. The storage that is allocated is 320 GB per ESXi server approximately.
  * PrimaryIO Prem Manager
  * PrimaryIO ESX Manager

* **Standard**. The configuration that is deployed uses no more than 8% of compute and memory resources. The storage that is allocated is 192 GB per ESXi server approximately.
  * PrimaryIO Prem Manager
  * PrimaryIO ESX Manager

* **Lite**. The configuration that is deployed uses 6 vCPU and 8 GB RAM of compute and memory. The total storage that is allocated is 96 GB per instance. The maximum instance in cluster mode is 2.
  * PrimaryIO ESX Manager

#### Networking for HDM on-premises
{: #managing_pio-onprem-netw}

* **Connectivity**
  * \>1 Gbps internet of cloud Interconnect
  * Network Latencies < 30 msec
  * One private subnet for HDM components with access to cloud Interconnect or WAN link, vCenter Management Network, and vMotion network.

* **Firewall**. Firewall ports need to be opened for:
    * PrimaryIO Appliance access to IBM vCenter (TCP port 443)
    * PrimaryIO Appliance access to internet (TCP port 8085)

### HDM on IBM Cloud components
{: #managing_pio-ibm-cloud-comp}

The following components belong to HDM on {{site.data.keyword.cloud_notm}}.

#### Virtual instances for HDM on IBM Cloud
{: #managing_pio-ibm-cloud-virt-inst}

* **Performance**. The configuration that is deployed uses no more than 15% of compute and memory resources. The cache that is allocated is 2 TB per ESXi server.
  * PrimaryIO Cloud Manager
  * PrimaryIO Cloud Cache

* **Standard**. The configuration that is deployed uses no more than 8% of compute and memory resources. The cache that is allocated is 544 GB per ESXi server.
  * PrimaryIO Cloud Manager
  * PrimaryIO Cloud Cache

* **Lite**. The configuration that is deployed uses 6 vCPU and 12 GB RAM of compute and memory. The total storage that is allocated for cache and OS is 544 GB per instance. The maximum instance in cluster mode is 2.
  * PrimaryIO Cloud Cache

#### Networking for HDM on IBM Cloud
{: #managing_pio-ibm-cloud-netw}

* **Connectivity**: One private subnet for HDM components with access to:
  * The cloud vCenter Server on port 443
  * The cloud ESXi server on port 443 and 902

* **Firewall**. Firewall ports need to be opened for:
  * PIO Appliance access to HDM components on cloud (TCP Port 22)
  * HDM components access to PIO Appliance (TCP Port 2379)
  * PIO Appliance access to HDM components on cloud (Port 6000-6020)
  * PIO Appliance access to HDM components on cloud (TCP Port 7000-7020)
  * PIO Appliance access to HDM components on cloud (TCP Port 8000-8020)

## Related links
{: #managing_pio-related}

* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [PrimaryIO Hybrid Cloud Data Management](https://www.primaryio.com/){:external}
