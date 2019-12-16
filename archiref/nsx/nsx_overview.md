---

copyright:

  years:  2016, 2019

lastupdated: "2019-11-30"

subcollection: vmware-solutions


---

# About NSX Edge Services Gateway
{: #nsx_overview}

The VMware NSX Edge Services Gateway (ESG) solution is an extension of the VMware vCenter Server offering that is currently available on the {{site.data.keyword.cloud}}. The solution architecture for vCenter Server details the components of the solution and the high-level configuration of each component in the design.

For more information about the vCenter Server design, see [Overview of {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview).

## Overview of NSX Edge Services Gateway
{: #nsx_overview-nsx-esg}

The NSX Edge Services Gateway connects isolated, stub networks to shared (uplink) networks by providing common gateway services such as Dynamic Host Configuration Protocol (DHCP), Virtual Private Network (VPN), Network Address Translation (NAT), dynamic routing, and load balancing. Common deployments of NSX Edge include demilitarized zone (DMZ), VPN Extranets, and multi-tenant Cloud environments where the NSX Edge creates virtual boundaries for each tenant, workload, or management component. The following features are available within the NSX Edge Service Gateway.

| Feature | Description |
|:------- |:----------- |
| NSX Edge Service Routing | Provides the necessary forwarding information between layer 2 broadcast domains, allowing you to decrease layer 2 broadcast domains and improve network efficiency and scale. NSX extends this intelligence to where the workloads reside for doing East-West routing. This allows more direct virtual machine to virtual machine communication without the costly or timely need to extend hops. At the same time, NSX also provides North-South connectivity, enabling tenants to access public networks. |
| Firewall | The supported rules of the firewall include IP 5-tuple configuration with IP and port ranges for stateful inspection for all protocols. |
| NAT | Provides separate controls for Source and Destination IP addresses and port translation. |
| DHCP | Provides configuration of IP pools, gateways, DNS servers, and search domains. |
| Site-to-Site VPN | Uses standardized IPSec protocol settings to inter-operate with all major VPN vendors. |
| L2VPN | Stretches L2 networks across L3 topologies. |
| SSL VPN-Plus |  SSL VPN-Plus enables remote users to connect securely to private networks behind an NSX Edge gateway. |
| Load Balancing | Provides simple and dynamically configurable virtual IP addresses and server groups. |
| High Availability | Ensures an active NSX Edge on the network in case the primary NSX Edge virtual machine is unavailable. |
{: caption="Table 1. Features available with the NSX Edge Service Gateway" caption-side="bottom"}

**Next topic:** [NSX Edge Services Gateway design](/docs/services/vmwaresolutions?topic=vmware-solutions-nsx_design)

## Related links
{: #nsx_overview-related}

* [Overview of {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
