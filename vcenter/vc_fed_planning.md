---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Requirements and planning for VMware Federal instances
{: #vc_fed_planning}

Review the following requirements before you order a VMware Federal instance. Plan your instance based on your workload capacity requirements.

## IBM Cloud account requirements
{: #vc_fed_planning-account-req}

The {{site.data.keyword.cloud}} account that you are using must meet certain requirements. For more information, see [Requirements for the {{site.data.keyword.cloud_notm}} account](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## IBM Cloud Data Center availability
{: #vc_fed_planning-dc-availability}

The VMware Federal on {{site.data.keyword.cloud_notm}} deployment has strict requirements on the physical infrastructure. You can deploy VMware Federal instances only in the following {{site.data.keyword.CloudDataCents_notm}}:
- WDC03 - Washington, DC, POD2
- DAL08 - Dallas, TX, POD2

## Backup of management components
{: #vc_fed_planning-backup-mgmt-components}

You are responsible for maintaining and ensuring the availability of all instance components using your preferred backup solution. It is strongly recommended that you plan for backup or high availability of all management components. For more information, see [Backing up components](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Services for VMware Federal instances
{: #vc_fed_planning-addon-services}

VMware Federal on {{site.data.keyword.cloud_notm}} does not offer the option to order additional services.

## Capacity considerations
{: #vc_fed_planning-capacity-considerations}

For capacity information and considerations, see [Scaling capacity](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Related links
{: #vc_fed_planning-related}

* [vCenter Server Software Bill of Materials](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [VMware Federal on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_fed_overview)
* [Ordering VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-ordering-vmware-federal-instances)
* [Securing VMware Federal instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-securing-vmware-federal-instances)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
