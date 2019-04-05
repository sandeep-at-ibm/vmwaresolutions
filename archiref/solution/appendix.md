---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmware-solutions


---

# Comparison chart for VMware component editions
{: #solution-appendix}

## VMware NSX edition comparison
{: #solution-appendix-nsx-editions}

Within this design, there are multiple components that require licenses. This information captures the minimum licenses that are required for the environment to operate correctly.

Table 1. License requirements

Component | Purpose | License
----------|---------|-------------
**vSphere** | Compute virtualization | vSphere 6.7 Enterprise Plus
**vCenter Server** | Infrastructure Management | vCenter Server 6.7 Standard
**NSX** | Network virtualization | NSX Base for Service Providers 6.4
**vSAN** | Storage virtualization | vSAN 6.6 Advanced  

NSX Base for Service Providers edition is only available for service providers through the VMware vCloud Air Network (vCAN). The features in this edition can be found in the following table.
{:note}

Table 2. VMware NSX edition comparison chart

| NSX Feature                                   | Base | Advanced | Enterprise |
|-----------------------------------------------|------|----------|------------|
| Distributed switching and routing             | •    | •        | •          |
| NSX Edge firewall                             | •    | •        | •          |
| NAT                                           | •    | •        | •          |
| NSX Edge load balancing                       | •    | •        | •          |
| VPN (IPsec)                                   | •    | •        | •          |
| VPN (SSL)                                     | •    | •        | •          |
| API-driven automation                         | •    | •        | •          |
| Integration with vRealize and OpenStack\*     | •    | •        | •          |
| Automation of security policies with vRealize |      | •        | •          |
| SW L2 bridging to physical environment        |      | •        | •          |
| Dynamic routing with ECMP (active-active)     |      | •        | •          |
| Distributed firewalling                       |      | •        | •          |
| Integration with Active Directory             |      | •        | •          |
| Server activity monitoring                    |      | •        | •          |
| Service insertion (3rd party integration)     |      | •        | •          |
| Distributed load balancing                    |      |          | •          |
| Cross vCenter NSX                             |      |          | •          |
| Multi-site NSX optimizations                  |      |          | •          |
| Remote Gateway                                |      |          | •          |
| Integration with HW VTEPs                     |      |          | •          |
\*L2, L3 & NSX Edge integration only. No consumption of Security Groups

## VMware vSAN edition comparison
{: #solution-appendix-vsan-editions}

The following table lists the available features for the **Advanced** and **Enterprise** editions of VMware vSAN that the solution supports.

Table 3. VMware vSAN edition comparison chart

| vSAN Feature                                    | Advanced | Enterprise |
|-------------------------------------------------|----------|------------|
| Storage policy-based management                 | •        | •          |
| Flash read/write caching                        | •        | •          |
| Distributed RAID                                | •        | •          |
| Virtual Distributed Switch                      | •        | •          |
| Rack awareness                                  | •        | •          |
| vSphere replication                             | •        | •          |
| Software checksum                               | •        | •          |
| All-Flash hardware                              | •        | •          |
| iSCSI target service                            | •        | •          |
| IOPS limit                                      | •        | •          |
| Deduplication and compression                   | •        | •          |
| RAID-5/6 erasure coding                         | •        | •          |
| Data at rest encryption                         |          | •          |
| Stretched cluster with local failure protection |          | •          |

## Related links
{: #solution-appendix-related}

* [Solution overview](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [Design overview](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Backing up components](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
