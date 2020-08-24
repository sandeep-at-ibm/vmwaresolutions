---

copyright:

  years:  2020

lastupdated: "2020-08-21"

keywords: cloud for vmware regulated workloads, cloud for vmware instance, instance config cloud for vmware

subcollection: vmwaresolutions

---

# IBM Cloud for VMware Regulated Workloads instance configurations
{: #fss-cloud-vmware-config}

{{site.data.keyword.cloud}} for VMware® Regulated Workloads are an extension of the VMware vCenter Server® offering, which enhances the basic vCenter Server architecture to deliver a secure, high-performance platform.

## Before you begin
{: #fss-cloud-vmware-config-before}

* Some of the included add-on services require configuration setup. Review each service and ensure that you configure its settings properly, as indicated.
* All configurations are based on a primary vCenter Server with NSX-T instance and VMware vSphere 6.7.
* For configurations that are listed as BYOL, ensure that you have the complete list of BYOL licenses that are required.

### Available IBM Cloud for VMware Regulated Workloads instance configurations
{: #fss-cloud-vmware-config-before-avail-inst}

The following instance configurations are available:
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package A
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package A (BYOL)
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package B
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package B (BYOL)
* {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Configurable

### Options not available for IBM Cloud for VMware Regulated Workloads instance configurations
{: #fss-cloud-vmware-config-before-not-avail-options}

The following options or settings are not available for any of the {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instance configurations:
* VMware Subscription Purchasing Program
* Local disks
* vSAN compression and deduplication
* Selection of existing VLANs. Only the option to order new VLANs is available.
* Single public Windows VSI for Active Directory/DNS configuration. Only the option to order two highly available dedicated Windows server virtual machines (VMs) on the management cluster is available.

## IBM Cloud for VMware Regulated Workloads - Package A
{: #fss-cloud-vmware-config-medium}

The following table provides information about the components and settings for an **IBM Cloud for VMware Regulated Workloads - Package A** instance configuration.

| Component or setting | Details |
|:-------------------- |:------- |
| Required services[^req_services_a] | Hyper Protect Crypto Services</br>KMIP for VMware (recommended) or HyTrust DataControl</br>Direct Link Dedicated |
| Optional services | vRealize Network Insight |
| Included services | Veeam Availability Suite v10, Windows Server VM on the management cluster, 100 VMs, Shared/NFS storage with 2,000 GB and 2 IOPS/GB</br>Caveonix RiskForesight, 100 VMs</br>HyTrust CloudControl</br>Juniper vSRX Standard edition</br>vRealize Operations and Log Insight (Include with purchase) |
| Licensing | Included with purchase:</br>vCenter Server license</br>vSphere license</br>NSX license (Advanced edition) |
| Management cluster | Dual Intel Xeon Silver 4210 (Cascade) 20 Cores, 2.20 GHz</br>192 GB RAM</br>Four {{site.data.keyword.cloud_notm}} bare metal servers</br>vSAN storage, two vSAN disks 1.9 TB SSD SED, vSAN license (Advanced edition)</br>Enable private NICs for private network only</br>All other available options are customizable |
| Workload cluster | Dual Intel Xeon Gold 5218 (Cascade) 32 Cores, 2.30 GHz</br>768 GB RAM</br>Four {{site.data.keyword.cloud_notm}} bare metal servers</br>vSAN storage, six vSAN disks 1.9 TB SSD SED, vSAN license (Advanced edition)</br>Enable private NICs for private network only</br>All other available options are customizable |
| Edge services cluster | Dual Intel Xeon Gold 5120 Processor (Skylake) 28 cores, 2.20 GHz</br>64 GB RAM</br>Two {{site.data.keyword.cloud_notm}} bare metal servers</br>All other available options are customizable |
{: caption="Table 1. Components and settings for {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package A" caption-side="top"}

## IBM Cloud for VMware Regulated Workloads - Package A (BYOL)
{: #fss-cloud-vmware-config-medium-byol}

The following table provides information about the components and settings for an **IBM Cloud for VMware Regulated Workloads - Package A (BYOL)** instance configuration.

| Component or setting | Details |
|:-------------------- |:------- |
| Required services[^req_services_a_b] | Hyper Protect Crypto Services</br>KMIP for VMware (recommended) or HyTrust DataControl</br>Direct Link Dedicated |
| Optional services | vRealize Network Insight |
| Included services | Veeam Availability Suite v10, Windows Server VM on the management cluster, 100 VMs, Shared/NFS storage with 2,000 GB and 2 IOPS/GB</br>Caveonix RiskForesight, 100 VMs</br>HyTrust CloudControl</br>Juniper vSRX Standard edition</br>vRealize Operations and Log Insight (BYOL) |
| Licensing | BYOL:</br>vCenter Server license</br>vSphere license</br>NSX license |
| Management cluster | Dual Intel Xeon Silver 4210 (Cascade) 20 Cores, 2.20 GHz</br>192 GB RAM</br>Four {{site.data.keyword.cloud_notm}} bare metal servers</br>vSAN storage, two vSAN disks 1.9 TB SSD SED, vSAN license (BYOL)</br>Enable private NICs for private network only</br>All other available options are customizable |
| Workload cluster | Dual Intel Xeon Gold 5218 (Cascade) 32 Cores, 2.30 GHz</br>768 GB RAM</br>Four {{site.data.keyword.cloud_notm}} bare metal servers</br>vSAN storage, six vSAN disks 1.9 TB SSD SED, vSAN license (BYOL)</br>Enable private NICs for private network only</br>All other available options are customizable |
| Edge services cluster | Dual Intel Xeon Gold 5120 Processor (Skylake) 28 cores, 2.20 GHz</br>64 GB RAM</br>Two {{site.data.keyword.cloud_notm}} bare metal servers</br>All other available options are customizable |
{: caption="Table 2. Components and settings for {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package A (BYOL)" caption-side="top"}

## IBM Cloud for VMware Regulated Workloads - Package B
{: #fss-cloud-vmware-config-large}

The following table provides information about the components and settings for an **IBM Cloud for VMware Regulated Workloads - Package B** instance configuration.

| Component or setting | Details |
|:-------------------- |:------- |
| Required services[^req_services_b] | Hyper Protect Crypto Services</br>KMIP for VMware (recommended) or HyTrust DataControl</br>Direct Link Dedicated |
| Optional services | vRealize Network Insight |
| Included services | Veeam Availability Suite v10, Windows Server VM on the management cluster, 100 VMs, Shared/NFS storage with 2,000 GB and 2 IOPS/GB</br>Caveonix RiskForesight, 100 VMs</br>HyTrust CloudControl</br>Juniper vSRX Standard edition</br>vRealize Operations and Log Insight (Include with purchase) |
| Licensing | Included with purchase:</br>vCenter Server license</br>vSphere license</br>NSX license (Advanced edition) |
| Management cluster | Dual Intel Xeon Silver 4210 (Cascade) 20 Cores, 2.20 GHz</br>192 GB RAM</br>Four {{site.data.keyword.cloud_notm}} bare metal servers</br>vSAN storage, two vSAN disks 1.9 TB SSD SED, vSAN license (Advanced edition)</br>Enable private NICs for private network only</br>All other available options are customizable |
| Workload cluster | Dual Intel Xeon Gold 6248 (Cascade) 40 Cores, 2.50 GHz</br>1.5 TB RAM</br>Four {{site.data.keyword.cloud_notm}} bare metal servers</br>vSAN storage, six vSAN disks 3.8 TB SSD, vSAN license (Advanced edition)</br>Enable private NICs for private network only</br>All other available options are customizable |
| Edge services cluster | Dual Intel Xeon Gold 5120 Processor (Skylake) 28 cores, 2.20 GHz</br>64 GB RAM</br>Two {{site.data.keyword.cloud_notm}} bare metal servers</br>All other available options are customizable |
{: caption="Table 3. Components and settings for {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package B" caption-side="top"}

## IBM Cloud for VMware Regulated Workloads - Package B (BYOL)
{: #fss-cloud-vmware-config-large-byol}

The following table provides information about the components and settings for an **IBM Cloud for VMware Regulated Workloads - Package B (BYOL)** instance configuration.

| Component or setting | Details |
|:-------------------- |:------- |
| Required services[^req_services_b_b] | Hyper Protect Crypto Services</br>KMIP for VMware (recommended) or HyTrust DataControl</br>Direct Link Dedicated |
| Optional services | vRealize Network Insight |
| Included services | Veeam Availability Suite v10, Windows Server VM on the management cluster, 100 VMs, Shared/NFS storage with 2,000 GB and 2 IOPS/GB</br>Caveonix RiskForesight, 100 VMs</br>HyTrust CloudControl</br>Juniper vSRX Standard edition</br>vRealize Operations and Log Insight (BYOL) |
| Licensing | BYOL:</br>vCenter Server license</br>vSphere license</br>NSX license |
| Management cluster | Dual Intel Xeon Silver 4210 (Cascade) 20 Cores, 2.20 GHz</br>192 GB RAM</br>Four {{site.data.keyword.cloud_notm}} bare metal servers</br>vSAN storage, two vSAN disks 1.9 TB SSD SED, vSAN license (BYOL)</br>Enable private NICs for private network only</br>All other available options are customizable |
| Workload cluster | Dual Intel Xeon Gold 6248 (Cascade) 40 Cores, 2.50 GHz</br>1.5 TB RAM</br>Four {{site.data.keyword.cloud_notm}} bare metal servers</br>vSAN storage, six vSAN disks 3.8 TB SSD, vSAN license (BYOL)</br>Enable private NICs for private network only</br>All other available options are customizable |
| Edge services cluster | Dual Intel Xeon Gold 5120 Processor (Skylake) 28 cores, 2.20 GHz</br>64 GB RAM</br>Two {{site.data.keyword.cloud_notm}} bare metal servers</br>All other available options are customizable |
{: caption="Table 4. Components and settings for {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Package B (BYOL)" caption-side="top"}

## IBM Cloud for VMware Regulated Workloads - Configurable
{: #fss-cloud-vmware-config-custom}

The following table provides information about the components and settings for an **IBM Cloud for VMware Regulated Workloads - Configurable** instance configuration.

| Component or setting | Details |
|:-------------------- |:------- |
| Required services[^req_services_config] | Hyper Protect Crypto Services</br>KMIP for VMware (recommended) or HyTrust DataControl</br>Fortigate Security Appliance or Edge services cluster with Juniper vSRX (recommended)</br>Direct Link Dedicated |
| Optional services | vRealize Network Insight</br>Veeam Availability Suite v10[^veeam_remove], Windows Server VM on the management cluster</br>Juniper vSRX[^juniper_remove] Standard edition |
| Included services | Caveonix RiskForesight</br>HyTrust CloudControl</br>vRealize Operations and Log Insight |
| Licensing | All options are customizable |
| Management cluster | CPU generation: Cascade Lake</br>Enable private NICs for private network only</br>All other available options are customizable |
| Workload cluster | CPU generation: Cascade Lake</br>vSAN storage</br>Enable private NICs for private network only</br>All other available options are customizable |
| Edge services cluster | Dual Intel Xeon Gold 5120 Processor (Skylake) 28 cores, 2.20 GHz</br>64 GB RAM</br>Two {{site.data.keyword.cloud_notm}} bare metal servers</br>All other available options are customizable |
{: caption="Table 5. Components and settings for {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads - Configurable" caption-side="top"}

[^req_services_a]: These services are required to ensure compliance with the IBM Cloud for VMware Regulated Workloads architecture.

[^req_services_a_b]: These services are required to ensure compliance with the IBM Cloud for VMware Regulated Workloads architecture.

[^req_services_b]: These services are required to ensure compliance with the IBM Cloud for VMware Regulated Workloads architecture.

[^req_services_b_b]: These services are required to ensure compliance with the IBM Cloud for VMware Regulated Workloads architecture.

[^req_services_config]: These services are required to ensure compliance with the IBM Cloud for VMware Regulated Workloads architecture.

[^veeam_remove]: The Veeam 10 service is optional. If you do not want to use this service, click the **Veeam 10** service card, and then click **Remove service** in the **Configure Veeam** window.

[^juniper_remove]: The Juniper vSRX service is optional. If you do not want to use this service, click the **Juniper vSRX 18.4** service card, and then click **Remove service** in the **Configure Juniper vSRX** window.

## Related links
{: #fss-cloud-vmware-config-related}

* [Ordering {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instances](/docs/vmwaresolutions?topic=vmwaresolutions-fss-cloud-orderinginstance)
* [{{site.data.keyword.cloud_notm}} for VMware Regulated Workloads reference architecture overview](/docs/vmwaresolutions?topic=vmwaresolutions-fss-overview)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)
* [vCenter Server overview](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview)
