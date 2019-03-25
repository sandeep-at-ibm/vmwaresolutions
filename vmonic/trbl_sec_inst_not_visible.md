---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# Secondary vCenter Server system does not appear in the vSphere Web Client inventory
{: #trbl_sec_inst_not_visible}

## Problem
{: #trbl_sec_inst_not_visible-problem}

In a multi-site configuration, after you add a new secondary instance, its vCenter Server system is not visible when logged in to the VMware vSphere Web Client of a previously ordered instance.

## Resolution
{: #trbl_sec_inst_not_visible-resolution}

This is a known VMware 6.5 issue.

To resolve the problem, you must restart the vSphere Web Client:

1. Using the **root** account, connect over **ssh** to the vCenter VM (virtual machine) of the previously ordered instance.
2. Type ``shell`` to enter the bash shell.
3. Enter `service-control --stop vsphere-client` to stop the client.
4. Enter `service-control --start vsphere-client` to restart the client.
5. After the vSphere Web Client of the previously ordered instance is restarted, confirm that the vCenter Server system for the newly added secondary instance is visible in the vSphere Web Client.
