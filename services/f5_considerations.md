---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-08"

---

# Considerations for F5 on IBM Cloud

The F5 on {{site.data.keyword.cloud}} service (F5 BIG-IP® Virtual Edition) provides intelligent L4-L7 load balancing and traffic management services at a local and global scale, robust network and web application firewall protection, and secure and federated application access.

This service is available only to instances that are deployed in V1.9 or later releases.

You can order an instance with BIG-IP Virtual Edition (VE) included. For more information, see:
* [Ordering Cloud Foundation instances](../sddc/sd_orderinginstance.html)
* [Ordering vCenter Server instances](../vcenter/vc_orderinginstance.html)

You can also deploy BIG-IP VE into your existing instances after initial deployment. For more information, see:
* [Ordering and removing services for Cloud Foundation instances](../sddc/sd_addingremovingservices.html)
* [Ordering and removing services for vCenter Server instances](../vcenter/vc_addingremovingservices.html)

## License model for F5 on IBM Cloud

The license model for F5 on {{site.data.keyword.cloud_notm}} service offers the following options:
* **Good**: This offer leverages the BIG-IP Local Traffic Manager™ (LTM) VE, operating as a full-proxy architecture, to provide intelligent local traffic management, complete SSL traffic visibility, and analytics and health monitoring to ensure application servers are always available to your users.
* **Better**: This offer is built on the benefits of the **Good** option, with the addition of BIG-IP DNS™, BIG-IP Advanced Firewall Manager™ (AFM), and BIG-IP Application Acceleration Manager™ (AAM) modules. It delivers global traffic management services, application performance optimization, and advanced network firewall and Distributed Denial of Service (DDoS) mitigation capabilities.
* **Best**: In addition to the **Good** and **Better** offers, BIG-IP Application Security Manager™ (ASM) provides comprehensive application protection against L7 DDoS, Open Web Application Security Project (OWASP) top 10 threats and common application vulnerabilities. BIG-IP Access Policy Manager™ (APM) offers users secure, simplified access to applications located anywhere within a multi-cloud environment, incorporating features such as SSO (Single Sign-On) and MFA (Multi-Factor Authentication).

## Considerations when installing F5 on IBM Cloud

Before you install the F5 on {{site.data.keyword.cloud_notm}} service, review the following considerations.

Based on the license model and bandwidth that you select, two BIG-IP VE VMs (virtual machines) are deployed with the following configuration:

Table 1: CPU and RAM deployments for different bandwidth and license model selections

| Maximum Bandwidth | License Model: Good | License Model: Better | License Model: Best |
|:------------------|:--------------------|:----------------------|:--------------------|
| 25 Mbps           | 2 vCPU, 4 GB RAM    | 4 vCPU, 8 GB RAM      | 8 vCPU, 16 GB RAM   |
| 200 Mbps          | 2 vCPU, 4 GB RAM    | 4 vCPU, 8 GB RAM      | 8 vCPU, 16 GB RAM   |
| 1 Gbps            | 2 vCPU, 4 GB RAM    | 4 vCPU, 8 GB RAM      | 8 vCPU, 16 GB RAM   |
| 3 Gbps            | 8 vCPU, 16 GB RAM   | 8 vCPU, 16 GB RAM     | 8 vCPU, 16 GB RAM   |
| 5 Gbps            | 8 vCPU, 16 GB RAM   | 8 vCPU, 16 GB RAM     | 8 vCPU, 16 GB RAM   |

**Note:** The HA (High Availability) pair of BIG-IP VE VMs will be deployed only into the default cluster.

In addition, 100% of CPU and RAM for the two BIG-IP VE VMs are also reserved because these VMs are in the data plane of the network communications and it is critical that resources are still available for them.

To calculate the CPU and RAM reservation for a single BIG-IP VE VM, use the following formula:

`CPU reservation = CPU speed of ESXi server * number of vCPUs` (from Table 1)

`RAM reservation = RAM size` (from Table 1)

You must meet the following requirements to avoid failures with F5 on {{site.data.keyword.cloud_notm}}:
* At least two active ESXi servers are available for the two BIG-IP VE VMs to be deployed with the anti-affinity rule of keeping the VMs on separate servers.
* The two active ESXi servers have enough resources available so that one BIG-IP VE VM can be hosted on each ESXi server with 100% CPU and RAM reservation.
* VMware vSphere HA  has enough resources to host two BIG-IP VMs with 100% CPU and RAM.

Due to these requirements, you must plan for the space needed for F5 on {{site.data.keyword.cloud_notm}}. If needed, before ordering F5 on {{site.data.keyword.cloud_notm}}, add 1-2 ESXi servers to your instance, or reduce vSphere HA CPU reservation for failover, or both.

### Reservation example

You order a VMware vCenter Server **Small** instance with 2 ESXI servers with the following configuration: 16 cores at 2.10 GHz each with 128 GB RAM. For F5 on {{site.data.keyword.cloud_notm}}, you select the **Best** license model and a value of 5 Gbps for **Maximum Bandwidth**.

In this case, a single BIG-IP VM requires, on each server:
* 2.1 GHz * 8 vCPU = 16.8 GHz of CPU, and
* 16 GB RAM

In total, that is 33.6 GHz CPU and 32 GB RAM for two BIG-IP VMs.

Each ESXi server has a capacity of 16 cores * 2.1 GHz = 33.6 GHz, so we meet the first two requirements if both servers are active and there is at least 16.8 GHz of CPU and 16 GB RAM available on each server.

By default however, vSphere HA reserves 50% of CPU and RAM for failover on vCenter Server instances that were initially deployed with 2 ESXi servers, so we only have:

`50% of 2 * 16 cores * 2.1 GHz = 33.6 GHz available`

Since there will be other workloads present on the ESXi servers, for example, IBM CloudDriver, VMware NSX Controller, VMware NSX Edge, using these resources we cannot satisfy the third requirement, because we need 33.6 GHz of CPU and 32 GB RAM for the two BIG-IP VMs.

In this case, the F5 on {{site.data.keyword.cloud_notm}} installation might fail, unless at least one ESXi server is added to the environment and vShpere HA failover reservations are updated appropriately to ensure that there are enough resources for two BIG-IP VE VMs. If additional resources are needed to run the F5 on {{site.data.keyword.cloud_notm}} service, you can add more ESXi servers before installing F5 on {{site.data.keyword.cloud_notm}}.

### Changing the license model

You cannot change the license model after service installation. To change the license model, you must remove the existing service and reinstall the service using a different license model.

## Considerations when removing F5 on IBM Cloud

Before you remove the F5 on {{site.data.keyword.cloud_notm}} service, ensure that the existing BIG-IP VE configuration is removed correctly. Specifically, network traffic must be routed around BIG-IP VE instead of through BIG-IP VE. Otherwise, the existing data traffic into your environment might be impacted.

## Related links

* [Managing F5 on {{site.data.keyword.cloud_notm}}](managing_f5.html)
* [Contacting IBM Support](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [F5 website](https://f5.com/){:new_window}
* [F5 Deployment Guides](https://f5.com/solutions/deployment-guides){:new_window}
