---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: planning vCenter Server, data center, vCenter Server data centers

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requirements and planning for vCenter Server instances
{: #vc_planning}

Review the following requirements before you order your VMware vCenter Server instances. Plan your instance based on the {{site.data.keyword.CloudDataCent}} location, your workload capacity requirements, and add-on service requirements.

## IBM Cloud account requirements
{: #vc_planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).

## IBM Cloud Data Center availability
{: #vc_planning-dc-availability}

The vCenter Server deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.CloudDataCents_notm}} that meet the requirements. The following {{site.data.keyword.CloudDataCents_notm}} are available for vCenter Server deployment.

Cascade Lake {{site.data.keyword.baremetal_short}} are available on Multi-Zone Region
{{site.data.keyword.CloudDataCents_notm}}. For more information, see [Multi-Zone Region (MZR) Overview
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).
{:note}

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region | Server options |
|:----------------------|:---------|:-------|:---------------|
| AMS01 | Amsterdam | Europe | Skylake, SAP-certified, Broadwell |
| AMS03 | Amsterdam | Europe | Skylake, SAP-certified, Broadwell |
| CHE01 | Chennai | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| DAL09 | Dallas | NA South | Skylake, SAP-certified, Broadwell |
| DAL10 | Dallas | NA South | Skylake, SAP-certified, Broadwell |
| DAL12 | Dallas | NA South | Skylake, SAP-certified, Broadwell |
| DAL13 | Dallas | NA South | Skylake, SAP-certified, Broadwell |
| FRA02 | Frankfurt | Europe | Skylake, SAP-certified, Broadwell |
| FRA04 | Frankfurt | Europe | Skylake, SAP-certified, Broadwell |
| FRA05 | Frankfurt | Europe | Skylake, SAP-certified, Broadwell |
| HKG02 | Hong Kong | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| LON02 | London | Europe | Skylake, Broadwell |
| LON04 | London | Europe | Skylake, SAP-certified, Broadwell |
| LON05 | London | Europe | Skylake, Broadwell |
| LON06 | London | Europe | Skylake, SAP-certified, Broadwell |
| MEL01 | Melbourne | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| MEX01 | Queretaro | NA South | Skylake, SAP-certified, Broadwell |
| MIL01 | Milan | Europe | Skylake, SAP-certified, Broadwell |
| MON01 | Montreal | NA East | Skylake, SAP-certified, Broadwell |
| OSL01 | Oslo | Europe | Skylake, SAP-certified, Broadwell |
| PAR01 | Paris | Europe | Skylake, SAP-certified, Broadwell |
| SAO01 | Sao Paulo | South America | Skylake, SAP-certified, Broadwell |
| SEO01 | Seoul | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| SJC03 | San Jose | NA West | Skylake, Broadwell |
| SJC04 | San Jose | NA West | Skylake, Broadwell |
| SNG01 | Singapore | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| SYD01 | Sydney | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| SYD04 | Sydney | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| SYD05 | Sydney | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| TOK02 | Tokyo | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| TOK04 | Tokyo | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| TOK05 | Tokyo | Asia-Pacific | Skylake, SAP-certified, Broadwell |
| TOR01 | Toronto | NA East | Skylake, SAP-certified, Broadwell |
| WDC04 | Washington, DC | NA East | Skylake, SAP-certified, Broadwell |
| WDC06 | Washington, DC | NA East | Skylake, SAP-certified, Broadwell |
| WDC07 | Washington, DC | NA East | Skylake, SAP-certified, Broadwell |
{: caption="Table 1. Available {{site.data.keyword.CloudDataCents_notm}} for vCenter Server instances" caption-side="top"}

Depending on availability and inventory supply, {{site.data.keyword.CloudDataCents_notm}} might display a status indicator in the {{site.data.keyword.vmwaresolutions_short}} console to help you plan your deployments.

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.CloudDataCent_notm}} is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.CloudDataCent_notm}} has no availability currently. |
| Limited Inventory             | The {{site.data.keyword.CloudDataCent_notm}} has limited availability and the order might not be completed. |
{: caption="Table 2. Status indicators for {{site.data.keyword.CloudDataCents_notm}} when ordering vCenter Server instances" caption-side="top"}

## Backup of management components
{: #vc_planning-backup-mgmt-components}

You are responsible for maintaining and ensuring the availability of all instance components. It is strongly recommended that you plan for backup or high availability of all management components. For more information, see [Backing up components](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Services for vCenter Server instances
{: #vc_planning-addon-services}

You can order add-on services for your instance base on your needs, for example, disaster recovery. For more information, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

Services are supported for vCenter Server with NSX-T instances.
{:note}

### Planning for VMware HCX on IBM Cloud
{: #vc_planning-addon-services-hcx}

The VMware HCX on {{site.data.keyword.cloud_notm}} service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

When you deploy this service, complete the following settings:
* Specify the **HCX interconnect type** by selecting one of the following options:
  * **Public network**: HCX creates an encrypted connection between sites over the public network.
  * **Private network**: HCX creates an encrypted connection between sites over the private network.
* Specify the **Public endpoint certificate type**. If you select **CA Certificate**, configure the following settings:
  * **Certificate Contents**: Enter the contents of the CA certificate.
  * **Private Key**: Enter the private key of the CA certificate.
  * (Optional) **Password**: Enter the password for the private key if it is encrypted.
  * (Optional) **Reenter Password**: Enter the password for the private key again.
  * (Optional) **Hostname**: Enter the host name to be mapped to the common name (CN) of the CA certificate. HCX on {{site.data.keyword.cloud_notm}} requires the CA certificate to be in a format that is accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}.

## Capacity considerations
{: #vc_planning-capacity-considerations}

For more information about capacity considerations, see [Scaling capacity](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Related links
{: #vc_planning-related}

* [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Expanding and contracting capacity for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
