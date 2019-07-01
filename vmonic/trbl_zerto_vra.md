---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, Zerto VRA, Zerto uninstall

subcollection: vmware-solutions


---

# Zerto VRA visible on ESXi host in the vCenter console after Zerto on IBM Cloud is uninstalled
{: #trbl_zerto_vra}

## Problem
{: #trbl_zerto_vra-problem}

Zerto Virtual Replication Appliances (VRAs) are not removed after using the {{site.data.keyword.slportal}} to successfully uninstall the Zerto on {{site.data.keyword.cloud}} service.

## Resolution
{: #trbl_zerto_vra-resolution}

Manually remove the VRAs from the vCenter console.

1. Log in to the vCenter console.
2. Click **Hosts and Clusters** and locate the virtual machines with names that start with **Z-VRA-**. For example, **Z-VRA-host0-vcs40dal.vcs.icvs.org**.
3. Right-click the **Z-VRA-** virtual machine and click **Delete from Disk**.
