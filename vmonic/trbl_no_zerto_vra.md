---

copyright:

  years:  2016, 2020

lastupdated: "2020-09-17"

keywords: troubleshooting, Zerto Virtual Replication, Zerto ESXi server

subcollection: vmwaresolutions

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Why aren't Zerto VRAs displaying for newly created ESXi servers?
{: #trbl_no_zerto_vra}
{: troubleshoot}
{: support}

Virtual Replication Appliances (VRAs) are not displayed on the Zerto Virtual Replication console after you add ESXi servers to a VMware vCenter Server instance with Zerto disaster recovery installed.
{: tsSymptoms}

The Zerto disaster recovery service is installed only on the ESXi server from the default cluster (**cluster1** for instances that are deployed in V3.1 or earlier). If new clusters are created in the same vCenter Server environment or if ESXi servers are added to new clusters, Zerto disaster recovery is not installed on them. On those clusters, you must install Zerto disaster recovery separately.
{: tsCauses}

Open an {{site.data.keyword.cloud}} Support ticket and work with IBM Support to obtain available IP addresses for you to install the VRAs from the Zerto console, instead of the {{site.data.keyword.vmwaresolutions_short}} console.
{: tsResolve}

To access the Zerto console, click the Zerto card from the **Services** tab of the instance and click **View details** then, **View Zerto console**.

For more information about contacting IBM Support, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support#trbl_support).
