---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-15"

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
{{site.data.keyword.CloudDataCents_notm}}. For more information, see [Multi-Zone Region (MZR) Overview](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).
{:note}

| {{site.data.keyword.CloudDataCent_notm}} | Location | Region | Server options |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | Amsterdam | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| CHE01 | Chennai | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| DAL09 | Dallas | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| DAL10 | Dallas | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| DAL12 | Dallas | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| DAL13 | Dallas | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| FRA02 | Frankfurt | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| FRA04 | Frankfurt | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| FRA05 | Frankfurt | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| HKG02 | Hong Kong | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| LON02 | London | Europe | <ul><li>For vSphere 6.5u2: Skylake, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| LON04 | London | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| LON05 | London | Europe | <ul><li>For vSphere 6.5u2: Skylake, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| LON06 | London | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| MEL01 | Melbourne | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| MEX01 | Queretaro | NA South | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| MIL01 | Milan | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| MON01 | Montreal | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| OSL01 | Oslo | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| PAR01 | Paris | Europe | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SAO01 | Sao Paulo | South America | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SEO01 | Seoul | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SJC03 | San Jose | NA West | <ul><li>For vSphere 6.5u2: Skylake, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SJC04 | San Jose | NA West | <ul><li>For vSphere 6.5u2: Skylake, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SNG01 | Singapore | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| SYD01 | Sydney | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| SYD04 | Sydney | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| SYD05 | Sydney | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified</li><li>For vSphere 6.7u2: Skylake, Cascade Lake</li></ul> |
| TOK02 | Tokyo | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| TOK04 | Tokyo | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| TOK05 | Tokyo | Asia-Pacific | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| TOR01 | Toronto | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Broadwell</li></ul> |
| WDC04 | Washington, DC | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| WDC06 | Washington, DC | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
| WDC07 | Washington, DC | NA East | <ul><li>For vSphere 6.5u2: Skylake, SAP-certified, Broadwell</li><li>For vSphere 6.7u2: Skylake, Cascade Lake, Broadwell</li></ul> |
{: caption="Table 1. Available {{site.data.keyword.CloudDataCents_notm}} for vCenter Server instances" caption-side="top"}

Depending on availability and inventory supply, {{site.data.keyword.CloudDataCents_notm}} might display a status indicator in the {{site.data.keyword.vmwaresolutions_short}} console to help you plan your deployments.

| Status | Status Details |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | The {{site.data.keyword.CloudDataCent_notm}} is not available currently. |
| Temporarily Out of Inventory  | The {{site.data.keyword.CloudDataCent_notm}} has no availability currently. |
| Limited Inventory             | The {{site.data.keyword.CloudDataCent_notm}} has limited availability and the order might not be completed. |
{: caption="Table 2. Status indicators for {{site.data.keyword.CloudDataCents_notm}} when you order vCenter Server instances" caption-side="top"}

## Backup of management components
{: #vc_planning-backup-mgmt-components}

You are responsible for maintaining and ensuring the availability of all instance components. It is recommended that you plan for backup or high availability of all management components. For more information, see [Backing up components](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Services for vCenter Server instances
{: #vc_planning-addon-services}

You can order add-on services for your instance base on your needs, for example, disaster recovery. For more information, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

Services are supported for vCenter Server with NSX-T instances.
{:note}

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

For more information about capacity considerations, see [Scaling capacity](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Related links
{: #vc_planning-related}

* [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Ordering vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Expanding and contracting capacity for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
