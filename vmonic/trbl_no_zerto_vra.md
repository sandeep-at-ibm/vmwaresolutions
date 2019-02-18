---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Zerto Virtual Replication Appliances are not displayed for newly created ESXi servers
{: #trbl_no_zerto_vra}

## Problem
{: #trbl_no_zerto_vra-problem}

Virtual Replication Appliances (VRA) are not displayed on the Zerto Virtual Replication console after you add ESXi servers to a VMware vCenter Server instance that has Zerto disaster recovery installed.

## Resolution
{: #trbl_no_zerto_vra-resolution}

For vCenter Server instances, the Zerto disaster recovery service is installed only on the ESXi server from the default cluster, **cluster1**. Any additional clusters in the same vCenter Server environment do not have Zerto disaster recovery that is installed automatically when the additional cluster is created nor when the ESXi server is added to that additional cluster.

On the additional clusters, you must install Zerto disaster recovery separately.

Open an {{site.data.keyword.cloud}} Support ticket and work with IBM Support to obtain available IP addresses for you to install the VRAs from the Zerto console, instead of the {{site.data.keyword.vmwaresolutions_short}} console.

To access the Zerto console, click the Zerto card from the **Services** tab of the instance and click **View Details** then, **View Zerto Console**.

For more information about contacting IBM Support, see [Contacting IBM Support](/docs/services/vmwaresolutions//vmonic/trbl_support.html).
