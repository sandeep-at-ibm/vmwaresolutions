---

copyright:

  years:  2016, 2020

lastupdated: "2020-01-14"

---

{:external: target="_blank" .external}

# vRealize Network Insight
{: #opsmgmt-vrni}

The vRealize Network Insight (vRNI) environment consists of two virtual machines (VMs), a Platform (UI) and a Controller Node.

![Network Insights diagram](../../images/opsmgmt-vrninw.svg "Network Insights diagram"){: caption="Figure 1. Network Insights networking" caption-side="bottom"}

The vRNI Platform appliance provides the analytics, user interface, and data management and connects to the Controller Appliance, which collects from the various data sources such as NSX Edges, vCenter. All vRNI components use {{site.data.keyword.cloud}} Private portable IP addresses. vRLI is configured as the syslog server for vRNI.

![Network Insights components](../../images/opsmgmt-vrnicomponents.svg "Network Insights components"){: caption="Figure 2. Network Insights components" caption-side="bottom"}

## System requirements
{: #opsmgmt-vrni-requirements}

This architecture supports 3000 VMs by using a Medium brick size.

| Attribute | Specification |
|---|---|
| vCPU | 8 |
| Memory | 32 GB |
| Disk (thin provisioned) | 1 TB |
{: caption="Table 1. Network Insight Platform system requirements" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the attribute of the Network Insight Platform. The column headers indentify the specification of the attribute. To find the specification of an attribute, navigate to the row, and then find the value in the specification column."}
{: #table1}
{: tab-title="Platform system requirements"}
{: tab-group="System requirements"}
{: class="comparison-tab-table"}
{: row-headers}

| Attribute | Specification |
|---|---|
| vCPU | 4 |
| Memory | 12 GB |
| Disk (thin provisioned) | 200 GB |
{: caption="Table 2. Network Insight Collector system requirements" caption-side="bottom"}
{: summary="This table has row and column headers. The row headers identify the attribute of the Network Insight Collector. The column headers indentify the specification of the attribute. To find the specification of an attribute, navigate to the row, and then find the value in the specification column."}
{: #table2}
{: tab-title="Collector system requirements"}
{: tab-group="System requirements"}
{: class="comparison-tab-table"}
{: row-headers}

## Networking
{: #opsmgmt-vrni-network}

Deployment of the vRNI appliance requires two IP addresses from the Tooling private portable subnet. Network connectivity vRNI requires access to:
* vCenter Appliance
* vRealize Log Insight Appliance
* NSX-V/T Appliances
* Tooling Expansion VXLAN
* Customer Networks
* NTP server (`time.services.softlayer.com`)
* {{site.data.keyword.vmwaresolutions_short}} Active Directory/DNS

## Ports
{: #opsmgmt-vrni-ports}

| Description |Port | Protocol |
|---|---|---|
| Communication between the VMs of vRealize Network Insight | 443 | HTTPS |
| Services that require internet access<br>svc.ni.vmware.com<br>support2.ni.vmware.com<br>reg.ni.vmware.com|443|HTTPS
| Log Insight Ingestion API | 9000 | TCP |
| Log Insight Ingestion API over SSL | 9543 | TCP |
| User Interface | 80,443 | TCP |
| NTP |123 | UDP |
| SMTP | 25 | TCP |
| DNS| 53 | UDP |
| LDAP/LDAPS | 389, 636 | TCP |
| ESXi | 2055 | TCP |
| VMware vSphere / NSX | 443 | TCP |
{: caption="Table 3. Network Insight ports" caption-side="bottom"}

## Authentication
{: #opsmgmt-vrni-auth}

vRNI user authentication is directly with an Active Directory Server.

**Next topic:** [VMware Update Manager](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-vum)
