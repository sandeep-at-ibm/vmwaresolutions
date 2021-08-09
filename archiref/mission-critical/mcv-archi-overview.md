---

copyright:

  years:  2019, 2021

lastupdated: "2021-07-14"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:term: .term}

# VMware multizone introduction
{: #mcv-archi-overview}

VMware® multizone is a highly available offering that is built around a VMware vSAN™ stretched cluster deployment, which spans across three data centers. It provides low-latency connections and supports automated failover of workloads if an outage in one of the component data centers (availability zones) occurs.

The offering has the following key features.
- Multiple clusters with redundant vSphere infrastructure spread across three {{site.data.keyword.cloud}} data centers. Because the design relies on vSAN stretched clusters and extremely low-latency, deployment is restricted to {{site.data.keyword.cloud_notm}} multizone region (MZR) data centers.
- vCenter HA
- vSAN stretched cluster support for management plane and customer workloads.
- NSX-T with pre–configured Transport Zones and overlay networks.
- High availability of storage and compute resources, which allows for complete loss of one of the three {{site.data.keyword.cloud_notm}} data centers without disruption to any of the management or customer workloads.
- VMware Solutions automation to add and remove workload capacity for both compute and storage.
  - Add and remove host is supported, with a minimum of six hosts in initial consolidated cluster and a minimum of two hosts in witness cluster.
  - Add and remove stretched vSAN clusters is supported.
  - Add and remove of non-stretched clusters is supported.
  - Add and remove of NFS and iSCSI storage is supported.

## Automation
{: #mcv-archi-overview-auto}

The most significant part of the {{site.data.keyword.vmwaresolutions_short}} Multizone offering is the automated deployment of the instance.

The only action that you take is to select the configuration of the multizone instance. All other operations are provided by the automation.

Automation refers to ordering and setup of the instance. Automation does not include ongoing operation.
{:note}

The automation begins with fully ordering of infrastructure, networking components, software licenses supplied by IBM (not including Bring Your Own License), and add-on services.

After the ordered infrastructure is provisioned in the {{site.data.keyword.cloud_notm}} data centers, the automation flow begins.

The following steps outline the process:

1. Go to the {{site.data.keyword.cloud_notm}} portal.
2. Select the MZR and specify the configuration of the multizone instance.
3. Review the price estimate and terms of service, then select to provision the instance.

The VMware Solutions automation then completes the following tasks:
1. Orders {{site.data.keyword.cloud_notm}} bare metal servers, {{site.data.keyword.cloud_notm}} networking components (such as VLANs and subnets), storage, software licenses, and support systems.
2. Deploys vCenter.
3. Deploys vSAN and NSX.
4. Configures vSAN stretched clusters and vCenter HA according to the chosen configuration.
5. Registers the VMware multizone instance in your {{site.data.keyword.vmwaresolutions_short}} console for ongoing day 2 operations.

## Consumability
{: #mcv-archi-overview-consume}

Multizone instances are offered in the standard {{site.data.keyword.vmwaresolutions_short}} ordering flow, similar to the standard VCenter Server offering. A new {{site.data.keyword.cloud_notm}} user experience is available to support the Multizone order flow due to the overall complexity of the process.

## Ordering and management
{: #mcv-archi-overview-order}

Day 2 operation and management activities are not part of the automation process and are the responsibility of customer personnel.

Day 2 operation and management include the following activities:
* Monitoring
* Management and operation
* Disaster recovery
* Failure operations
* Manual recovery
* Backup and restore
* Network failure recovery

**Next topic:** [VMware multizone architecture design](/docs/vmwaresolutions?topic=vmwaresolutions-mcv-archi-design)

## Related links
{: #mcv-archi-overview-related}

* [VMware multizone BOM](/docs/vmwaresolutions?topic=vmwaresolutions-mcv-archi-bom)
* [VMware multizone components](/docs/vmwaresolutions?topic=vmwaresolutions-mcv-archi-comp)
