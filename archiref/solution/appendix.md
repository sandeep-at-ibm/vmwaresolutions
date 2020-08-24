---

copyright:

  years:  2016, 2020

lastupdated: "2020-07-22"

keywords: nsx editions, vsan editions, nsx edition comparison, vsan edition comparison

subcollection: vmwaresolutions


---

# Comparison chart for VMware NSX and VMware vSAN editions
{: #solution-appendix}

## NSX edition comparison
{: #solution-appendix-nsx-editions}

Within this design, there are multiple components that require licenses. This information captures the minimum licenses that are required for the environment to operate correctly.

Component | Purpose | License
----------|---------|-------------
VMware vSphere | Compute virtualization | vSphere 6.7 Enterprise Plus
VMware vCenter Server | Infrastructure Management | vCenter Server 6.7 Standard
NSX | Network virtualization | NSX Base for Service Providers 6.4
vSAN | Storage virtualization | vSAN 6.6 Advanced  
{: caption="Table 1. License requirements" caption-side="bottom"}

NSX Base for Service Providers edition is only available for service providers through the VMware vCloud Air Network (vCAN). The features in this edition can be found in the following table.
{:note}

| NSX feature                                   | Base | Advanced | Enterprise |
|-----------------------------------------------|------|----------|------------|
| Distributed switching and routing             | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| NSX Edge firewall                             | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| NAT                                           | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| NSX Edge load balancing                       | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| VPN (IPsec)                                   | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| VPN (SSL)                                     | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| API-driven automation                         | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Integration with vRealize and OpenStack[^OpenStack]  | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Automation of security policies with vRealize |      | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| SW L2 bridging to physical environment        |      | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Dynamic routing with ECMP (active-active)     |      | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Distributed firewalling                       |      | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Integration with Active Directory             |      | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Server activity monitoring                    |      | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Service insertion (3rd party integration)     |      | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Distributed load balancing                    |      |          | ![Available](../../../icons/checkmark-icon.svg) |
| Cross vCenter NSX                             |      |          | ![Available](../../../icons/checkmark-icon.svg) |
| Multi-site NSX optimizations                  |      |          | ![Available](../../../icons/checkmark-icon.svg) |
| Remote Gateway                                |      |          | ![Available](../../../icons/checkmark-icon.svg) |
| Integration with HW VTEPs                     |      |          | ![Available](../../../icons/checkmark-icon.svg) |
{: caption="Table 2. NSX edition comparison chart" caption-side="top"}

[^OpenStack]: L2, L3 & NSX Edge integration only. No consumption of security groups.

## vSAN edition comparison
{: #solution-appendix-vsan-editions}

The following table lists the available features for the **Advanced** and **Enterprise** editions of VMware vSAN that the solution supports.

| vSAN feature                                    | Advanced | Enterprise |
|-------------------------------------------------|----------|------------|
| Storage policy-based management                 | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Flash read/write caching                        | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Distributed RAID                                | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Virtual Distributed Switch                      | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Rack awareness                                  | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| vSphere replication                             | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Software checksum                               | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| All-Flash hardware                              | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| iSCSI target service                            | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| IOPS limit                                      | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Deduplication and compression                   | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| RAID-5/6 erasure coding                         | ![Available](../../../icons/checkmark-icon.svg) | ![Available](../../../icons/checkmark-icon.svg) |
| Data at rest encryption                         |          | ![Available](../../../icons/checkmark-icon.svg) |
| Stretched cluster with local failure protection |          | ![Available](../../../icons/checkmark-icon.svg) |
{: caption="Table 3. vSAN edition comparison chart" caption-side="top"}

## Related links
{: #solution-appendix-related}

* [Overview of {{site.data.keyword.vmwaresolutions_short}}](/docs/vmwaresolutions?topic=vmwaresolutions-solution_overview)
* [Design overview](/docs/vmwaresolutions?topic=vmwaresolutions-design_overview)
* [Backing up components](/docs/vmwaresolutions?topic=vmwaresolutions-solution_backingup)
