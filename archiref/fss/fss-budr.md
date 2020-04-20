---

copyright:

  years:  2020

lastupdated: "2020-03-30"

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# FSS Cloud business continuity
{: #fss-budr}

The FSS (Financial Services Sector) Cloud provides business continuity only at the management and edge layers.

## Management cluster
{: #fss-budr-management}

The management cluster relies upon native vSphere DRS capabilities to keep management services available to the platform administrators. Even with the configuration of the vSphere DRS features there are times when manual intervention is necessary to restore access to management services. Veeam is included in the management layer to back up all management service VMs continuously in the FSS Cloud in the vCenter appliance.

The use of shared storage, where permissible, minimizes the necessity of manual restoration activities if an ESXi host is lost.

## Edge cluster
{: #fss-budr-edge}

The edge cluster does not use any vSphere resiliency features and back up of the gateway VMs is not performed. The gateway appliances deliver resilience at the application layer through formation of a high-availability cluster at the time of deployment. When you use vSRX, it is recommended that the rescue configuration is set anytime a change is made to the running configuration. In operational mode, run `request system configuration rescue save` to update it. The use of an FTP server to automatically back up the configuration anytime changes are made is optional and left to the client to implement.

## Workload cluster
{: #fss-budr-workload}

Business continuity at the workload layers is the responsibility of the client to design, implement, and maintain.

**Next topic**: [FSS Cloud HyTrust integration](/docs/vmwaresolutions?topic=vmware-solutions-fss-hytrust)

## Related links
{: #fss-budr-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
* [Veeam](/docs/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
