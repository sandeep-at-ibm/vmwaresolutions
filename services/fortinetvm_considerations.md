---

copyright:

  years:  2016, 2020

lastupdated: "2020-02-03"

keywords: FortiGate VA, FortiGate Virtual Appliance, tech specs FortiGate VA

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Virtual Appliance overview
{: #fortinetvm_considerations}

The FortiGate Virtual Appliance service deploys a pair of FortiGate Virtual Appliances to your environment, which can help you reduce risk by implementing critical security controls within your virtual infrastructure.
{: shortdesc}

You can install multiple instances of this service as needed. You can manage this service by using the FortiOS web Client or the CLI through SSH.

The current FortiGate Virtual Appliance version that is installed is 6.2.3.
{:note}

## Technical specifications for FortiGate Virtual Appliance
{: #fortinetvm_considerations-specs}


The following components are ordered and included in the FortiGate Virtual Appliance service:

### Virtual machines
{: #fortinetvm_considerations-specs-vms}

* All options include a highly available (HA) pair of virtual machines (VMs).
* 2, 4, or 8 vCPUs per VM. The number depends on the deployment size and subscription type.
* 4, 6, or 12 GB RAM per VM. The number depends on the deployment size and subscription type.

### High availability
{: #fortinetvm_considerations-specs-ha}

Two VMs are deployed and ready for HA or Virtual Router Redundancy Protocol (VRRP) configuration.

### Networking
{: #fortinetvm_considerations-specs-network}

Access to the FortiGate® console is provided through a private management network.

### License and fees
{: #fortinetvm_considerations-specs-license}

License fees for each VM are applied to each billing cycle. The fees depend on the selected deployment size and monthly subscription license model.

You cannot change the licensing level after service installation. To change the licensing level, you must remove the existing service and reinstall the service by using a different licensing option.
{:important}

## Considerations when you install FortiGate Virtual Appliance
{: #fortinetvm_considerations-install}

Review the following considerations before you install the FortiGate Virtual Appliance service:
* The FortiGate VMs are deployed only into the default cluster.
* 100% of CPU and RAM for the two FortiGate VMs is reserved. The VMs are in the data plane of the network communications and it is critical that resources are still available for them.

  To calculate the CPU and RAM reservation for a single FortiGate VM, use the following formula:
   * `CPU reservation = CPU speed of ESXi server * number of vCPUs`
   * `RAM reservation = RAM size`
* When you deploy an HA-pair of FortiGate Virtual Appliances to your instance, SNAT and firewall rules are defined on the Management NSX Edge Services Gateway (ESG). In addition, static routes on the FortiGate Virtual Appliances are defined to allow outbound HTTPS communications from your instance to the public network. These communications are needed for license activation and for acquiring the most updated security policies and content.
* You cannot change the license level after service installation. To change the license level, you must remove the existing service and then reinstall the service by selecting a different license option.
* You must meet the following requirements to avoid failures with FortiGate Virtual Appliance:
   * At least two active ESXi servers are available for the two FortiGate VMs to be deployed with the anti-affinity rule of keeping the VMs on separate servers.
   * The two active ESXi servers have enough resources available so that one FortiGate VM can be hosted on each ESXi server with 100% CPU and RAM reservation.
   * VMware vSphere HA has enough resources to host two FortiGate VMs with 100% CPU and RAM.

  Due to these requirements, you must plan carefully for the space that is needed for the FortiGate Virtual Appliance. If needed, before you order FortiGate Virtual Appliance, add 1 - 2 ESXi servers to your instance, or reduce the vSphere HA CPU reservation for failover, or both.

**Notes**:

* Before the service is installed in your environment, a check is done against the available capacity of the default cluster in the environment to ensure that the service components can fit.
* If the capacity check fails, the service is not installed and the service state is set to **Capacity Validation Failed** on the console. In addition, a console message with more details is displayed and you are notified by email.
* To install the service, you must increase the capacity in your default cluster by adding more hosts, by freeing up RAM, CPU, or disk space. After that, add the service again in the console and remove the existing service in the **Capacity Validation Failed** state by clicking the delete icon next to it.

## FortiGate Virtual Appliance order example
{: #fortinetvm_considerations-example}

You order a VMware vCenter Server **Small** instance with 2 ESXi servers with the following configuration: 16 cores at 2.10 GHz each with 128 GB RAM. For FortiGate Virtual Appliance, you select the **Large** (8 vCPUs / 12 GB RAM) for deployment size and any subscription license model.

In this case, a single FortiGate VM requires, on each server:
* 2.1 GHz * 8 vCPU = 16.8 GHz of CPU, and
* 12 GB RAM

In total, that is 33.6 GHz CPU and 24 GB RAM for two FortiGate VMs.

Each ESXi server has a capacity of 16 cores * 2.1 GHz = 33.6 GHz. So the first two requirements are met if both servers are active and there are at least 16.8 GHz of CPU and 12 GB RAM available on each server.

However, by default, vSphere HA reserves 50% of CPU and RAM for failover on vCenter Server instances that were initially deployed with 2 ESXi servers, so the capacity is:

`50% of 2 * 16 cores * 2.1 GHz = 33.6 GHz available`

Since other workloads exist on the ESXi servers, for example, VMware vCenter Server, VMware NSX Controller, or VMware NSX Edge, by using these resources, the third requirement is not met. The reason is because 33.6 GHz of CPU and 24 GB RAM for the two FortiGate VMs are needed.

In this case, the FortiGate Virtual Appliance installation might fail, unless at least one ESXi server is added to the environment. Also, the vSphere HA failover reservations must be updated to ensure that there are enough resources for two FortiGate VMs.

If more resources are needed to run the FortiGate Virtual Appliance service, you can add more ESXi servers before you install the service.

## Considerations when you remove FortiGate Virtual Appliance
{: #fortinetvm_considerations-remove}

Before you remove the FortiGate Virtual Appliance service, ensure that the configuration of the existing FortiGate Virtual Appliances is removed correctly. Specifically, network traffic must be routed around FortiGate Virtual Appliances instead of through FortiGate Virtual Appliances. Otherwise, the existing data traffic within your environment might be impacted.

## Related links
{: #fortinetvm_considerations-related}

* [Ordering FortiGate Virtual Appliance](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_ordering)
* [Managing FortiGate Virtual Appliance](/docs/services/vmwaresolutions?topic=vmware-solutions-managingfortinetvm)
* [Contacting {{site.data.keyword.IBM}} Support](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions?topic=vmware-solutions-faq)
* [Fortinet website](https://www.fortinet.com/){:external}
* [Fortinet Document Library](https://docs.fortinet.com/product/fortigate/6.2){:external}
