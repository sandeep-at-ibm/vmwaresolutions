---

copyright:

  years:  2016, 2019

lastupdated: "2019-11-07"

keywords: troubleshooting, Zerto Virtual Replication, Zerto ESXi server

subcollection: vmware-solutions


---

# Zerto Virtual Replication Appliances are not displayed for newly created ESXi servers
{: #trbl_no_zerto_vra}

## Problem
{: #trbl_no_zerto_vra-problem}

Virtual Replication Appliances (VRA) are not displayed on the Zerto Virtual Replication console after you add ESXi servers to a VMware vCenter Server instance with Zerto disaster recovery installed.

## Resolution
{: #trbl_no_zerto_vra-resolution}

The Zerto disaster recovery service is installed only on the ESXi server from the default cluster (**cluster1** for instances that are deployed in V3.1 or earlier).

If new clusters are created in the same vCenter Server environment or if ESXi servers are added to new clusters, Zerto disaster recovery is not installed on them.

On those clusters, you must install Zerto disaster recovery separately.

Open an {{site.data.keyword.cloud}} Support ticket and work with IBM Support to obtain available IP addresses for you to install the VRAs from the Zerto console, instead of the {{site.data.keyword.vmwaresolutions_short}} console.

To access the Zerto console, click the Zerto card from the **Services** tab of the instance and click **View Details** then, **View Zerto Console**.

For more information about contacting IBM Support, see [Contacting IBM Support](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support#trbl_support).
