---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-17"

keywords: planning vCenter Server, data center, vCenter Server data centers

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requirements and planning for vCenter Server instances
{: #vc_planning}

Review the following requirements before you order your VMware vCenter Server instances. Plan your instance based on the {{site.data.keyword.cloud}} data center location, your workload capacity requirements, and add-on service requirements.

Only a limited number of add-on services are supported for vCenter Server with NSX-T instances.
{:important}

## IBM Cloud account requirements
{: #vc_planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmware-solutions-cloud-infra-acct-req).

## IBM Cloud data center availability
{: #vc_planning-dc-availability}

The vCenter Server deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements. The following {{site.data.keyword.cloud_notm}} data centers are available for vCenter Server deployment.

| {{site.data.keyword.cloud_notm}} data center | Location | Region | Server options for NSX-V| Server options for NSX-T |
|:----------------------|:---------|:-------|:---------------|:-----------------|
| AMS03 | Amsterdam | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| CHE01 | Chennai | Asia-Pacific | Skylake, SAP-certified[^sap-che01], Broadwell | Skylake |
| DAL09 | Dallas | NA South | Skylake, SAP-certified, Broadwell | Skylake, SAP-certified |
| DAL10 | Dallas | NA South | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| DAL12 | Dallas | NA South | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| DAL13 | Dallas | NA South | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| FRA02 | Frankfurt | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| FRA04 | Frankfurt | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| FRA05 | Frankfurt | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| HKG02 | Hong Kong | Asia-Pacific | Skylake, SAP-certified, Broadwell | Skylake, SAP-certified |
| LON02 | London | Europe | Skylake, Cascade Lake, Broadwell | Skylake, Cascade Lake |
| LON04 | London | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| LON05 | London | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| LON06 | London | Europe | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| MEX01 | Queretaro | NA South | Skylake, SAP-certified[^sap-mex01], Broadwell | Skylake |
| MIL01 | Milan | Europe | Skylake, SAP-certified[^sap-mil01], Broadwell | Skylake |
| MON01 | Montreal | NA East | Skylake, Cascade Lake, SAP-certified[^sap-mon01], Broadwell | Skylake, Cascade Lake |
| OSL01 | Oslo | Europe | Skylake, SAP-certified[^sap-osl01], Broadwell | Skylake |
| PAR01 | Paris | Europe | Skylake, Cascade Lake, SAP-certified[^sap-par01], Broadwell | Skylake, Cascade Lake |
| SAO01 | Sao Paulo | South America | Skylake, SAP-certified, Broadwell | Skylake, SAP-certified |
| SEO01 | Seoul | Asia-Pacific | Skylake, SAP-certified, Broadwell | Skylake, SAP-certified |
| SJC03 | San Jose | NA West | Skylake, Broadwell | Skylake |
| SJC04 | San Jose | NA West | Skylake, Broadwell | Skylake |
| SNG01 | Singapore | Asia-Pacific | Skylake, SAP-certified, Broadwell | Skylake, SAP-certified |
| SYD01 | Sydney | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| SYD04 | Sydney | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| SYD05 | Sydney | Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| TOK02 | Tokyo | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| TOK04 | Tokyo | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| TOK05 | Tokyo | Asia-Pacific | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| TOR01 | Toronto | NA East | Skylake, SAP-certified, Broadwell | Skylake, SAP-certified |
| WDC04 | Washington, DC | NA East | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| WDC06 | Washington, DC | NA East | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
| WDC07 | Washington, DC | NA East | Skylake, Cascade Lake, SAP-certified, Broadwell | Skylake, Cascade Lake, SAP-certified |
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for vCenter Server instances" caption-side="top"}

[^sap-che01]: vSphere 6.5 only

[^sap-mex01]: vSphere 6.5 only

[^sap-mil01]: vSphere 6.5 only

[^sap-mon01]: vSphere 6.5 only

[^sap-osl01]: vSphere 6.5 only

[^sap-par01]: vSphere 6.5 only

### Cascade Lake notes
{: #vc_planning-dc-notes}

* Cascade Lake (4-CPU Quad Intel Xeon Gold 6248) is available only in the **DAL10 - Dallas** IBM Cloud Data Center.
* Cascade Lake bare metal servers are also available on Multi-Zone Region
{{site.data.keyword.cloud_notm}} data centers. For more information, see [Multi-Zone Region (MZR) Overview](/docs/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

Depending on availability and inventory supply, {{site.data.keyword.cloud_notm}} data centers might display a status indicator in the {{site.data.keyword.vmwaresolutions_short}} console to help you plan your deployments.

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.cloud_notm}} data center is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.cloud_notm}} data center has no availability currently. |
| Limited Inventory             | The {{site.data.keyword.cloud_notm}} data center has limited availability and the order might not be completed. |
{: caption="Table 2. Status indicators for {{site.data.keyword.cloud_notm}} data centers when you order vCenter Server instances" caption-side="top"}

## Backup of management components
{: #vc_planning-backup-mgmt-components}

You are responsible for maintaining and ensuring the availability of all instance components. It is recommended that you plan for backup or high availability of all management components. For more information, see [Backing up components](/docs/vmwaresolutions?topic=vmware-solutions-solution_backingup).

Backup operations are not supported for vCenter Server with NSX-T instances.
{:important}

## Services for vCenter Server instances
{: #vc_planning-addon-services}

You can order add-on services for your instance base on your needs, for example, disaster recovery. For more information, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices).

Only a limited number of add-on services are supported for vCenter Server with NSX-T instances.
{:important}

### Planning for VMware HCX
{: #vc_planning-addon-services-hcx}

The VMware HCX service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}. This process, which allows virtual machines (VMs) to be moved to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

When you deploy this service, complete the following settings:
* Specify the **HCX Interconnect type** by selecting one of the following options:
  * **Public network**: HCX creates an encrypted connection between sites over the public network.
  * **Private network**: HCX creates an encrypted connection between sites over the private network.
* Specify the **Public endpoint certificate type**. If you select **CA Certificate**, configure the following settings:
  * **Certificate Contents**: Enter the contents of the CA certificate.
  * **Private Key**: Enter the private key of the CA certificate.
  * (Optional) **Password**: Enter the password for the private key if it is encrypted.
  * (Optional) **Reenter Password**: Enter the password for the private key again.
  * (Optional) **Hostname**: Enter the hostname to be mapped to the common name (CN) of the CA certificate. HCX requires the CA certificate to be in a format that is accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}.

## Capacity considerations
{: #vc_planning-capacity-considerations}

For more information about capacity considerations, see [Scaling capacity](/docs/vmwaresolutions?topic=vmware-solutions-solution_scaling).

## Related links
{: #vc_planning-related}

* [vCenter Server overview](/docs/vmwaresolutions?topic=vmware-solutions-vc_vcenterserveroverview)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices)
