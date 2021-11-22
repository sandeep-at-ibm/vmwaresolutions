---

copyright:

  years:  2016, 2021

lastupdated: "2021-11-22"

keywords: planning vCenter Server, data center, vCenter Server data centers

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Requirements and planning for vCenter Server instances
{: #vc_planning}

Plan your instance based on the {{site.data.keyword.cloud}} data center location, your workload capacity requirements, and add-on services requirements. Review the following requirements before you order your VMware vCenter Server® instance.

* New deployments of vCenter Server instances with VMware vSphere® 6.5 are not supported.
* New deployments of vCenter Server multizone instances are not supported.
* Add-on services support varies between vCenter Server with NSX-V and vCenter Server with NSX-T™ instances.

## IBM Cloud account requirements
{: #vc_planning-account-req}

The {{site.data.keyword.cloud_notm}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/vmwaresolutions?topic=vmwaresolutions-cloud-infra-acct-req).

## IBM Cloud data center availability
{: #vc_planning-dc-availability}

The vCenter Server deployment has strict requirements on the physical infrastructure. Therefore, you can deploy instances only in {{site.data.keyword.cloud_notm}} data centers that meet the requirements. The following {{site.data.keyword.cloud_notm}} data centers are available for vCenter Server deployment.

| {{site.data.keyword.cloud_notm}} data center | Region | Server options for NSX-V | Server options for NSX-T[^nsx-t-7] |
|:----------------------|:-------|:---------------|:-----------------|
| Amsterdam 03 | Europe | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Chennai 01 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified[^sap-che01] | Skylake, Cascade Lake |
| Dallas 09 | NA South | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Dallas 10 | NA South | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Dallas 12 | NA South | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Dallas 13 | NA South | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Frankfurt 02 | Europe | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Frankfurt 04 | Europe | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Frankfurt 05 | Europe | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Hong Kong 02 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| London 02 | Europe | Skylake, Cascade Lake | Skylake, Cascade Lake, SAP-certified |
| London 04 | Europe | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| London 05 | Europe | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| London 06 | Europe | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Mexico 01 | NA South | Skylake, Cascade Lake, SAP-certified[^sap-mex01] | Skylake, Cascade Lake, SAP-certified |
| Milan 01 | Europe | Skylake, Cascade Lake, SAP-certified[^sap-mil01] | Skylake, Cascade Lake, SAP-certified |
| Montreal 01 | NA East | Skylake, Cascade Lake, SAP-certified[^sap-mon01] | Skylake, Cascade Lake, SAP-certified |
| Osaka 21 | Asia-Pacific | Cascade Lake, SAP-certified | Cascade Lake, SAP-certified |
| Osaka 22 | Asia-Pacific | Cascade Lake, SAP-certified | Cascade Lake, SAP-certified |
| Osaka 23 | Asia-Pacific | Cascade Lake, SAP-certified | Cascade Lake, SAP-certified |
| Paris 01 | Europe | Skylake, Cascade Lake, SAP-certified[^sap-par01] | Skylake, Cascade Lake, SAP-certified |
| Sao Paulo 01 | South America | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Sao Paulo 04 | South America | Cascade Lake, SAP-certified | Cascade Lake, SAP-certified |
| Sao Paulo 05 | South America | Cascade Lake, SAP-certified | Cascade Lake, SAP-certified |
| Seoul 01 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| San Jose 03 | NA West | Skylake, Cascade Lake | Skylake, Cascade Lake, SAP-certified |
| San Jose 04 | NA West | Skylake, Cascade Lake | Skylake, Cascade Lake, SAP-certified |
| Singapore 01| Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Sydney 01 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Sydney 04 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Sydney 05 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Tokyo 02 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Tokyo 04 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Tokyo 05 | Asia-Pacific | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Toronto 01 | NA East | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Toronto 04 | NA East | Cascade Lake | Cascade Lake |
| Toronto 05 | NA East | Cascade Lake | Cascade Lake |
| Washington DC 04 | NA East | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Washington DC 06 | NA East | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
| Washington DC 07 | NA East | Skylake, Cascade Lake, SAP-certified | Skylake, Cascade Lake, SAP-certified |
{: caption="Table 1. Available {{site.data.keyword.cloud_notm}} data centers for vCenter Server instances" caption-side="top"}

[^nsx-t-7]: Skylake is not supported for vSphere 7 instances

[^sap-che01]: Existing vSphere 6.5 clusters only

[^sap-mex01]: Existing vSphere 6.5 clusters only

[^sap-mil01]: Existing vSphere 6.5 clusters only

[^sap-mon01]: Existing vSphere 6.5 clusters only

[^sap-par01]: Existing vSphere 6.5 clusters only

## Backup of management components
{: #vc_planning-backup-mgmt-components}

You are responsible for maintaining and ensuring the availability of all instance components. It is recommended that you plan for backup or high availability of all management components. For more information, see [Backing up components](/docs/vmwaresolutions?topic=vmwaresolutions-solution_backingup).

## Services for vCenter Server instances
{: #vc_planning-addon-services}

You can order services for your instance based on your needs, for example, disaster recovery. For more information, see [Ordering services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices).

Services support varies between vCenter Server with NSX-V and vCenter Server with NSX-T instances.
{: important}

### Planning for VMware HCX
{: #vc_planning-addon-services-hcx}

The VMware HCX™ service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}. This process, which allows virtual machines (VMs) to be moved to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

When you deploy this service, complete the following settings:
* Specify the **HCX Interconnect type** by selecting one of the following options:
   * **Public network**: HCX creates an encrypted connection between sites over the public network.
   * **Private network**: HCX creates an encrypted connection between sites over the private network.
* Specify the **Public endpoint certificate type**. If you select **CA Certificate**, configure the following settings:
   * **Certificate Contents**: Enter the contents of the CA certificate.
   * **Private Key**: Enter the private key of the CA certificate.
   * (Optional) **Password**: Enter the password for the private key if it is encrypted.
   * (Optional) **Reenter Password**: Enter the password for the private key again.
   * (Optional) **Hostname**: Enter the hostname to be mapped to the common name (CN) of the CA certificate. HCX requires the CA certificate to be in a format that is accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){: external}.

## Capacity considerations
{: #vc_planning-capacity-considerations}

For more information about capacity considerations, see [Scaling capacity](/docs/vmwaresolutions?topic=vmwaresolutions-solution_scaling).

## Related links
{: #vc_planning-related}

* [vCenter Server overview](/docs/vmwaresolutions?topic=vmwaresolutions-vc_vcenterserveroverview)
* [Ordering vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance)
* [Expanding and contracting capacity for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservers)
* [Ordering services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingservices)
