---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# ESXi server displays configuration issue
{: #trbl_host_displays_warning_msg}

## Problem
{: #trbl_host_displays_warning_msg-problem}

A configuration issue is displayed in the **Issues** tab of the **Monitor** tab of the VMware ESXi server in the vSphere client.

The following message is displayed in the **Issues** tab for the ESXi server:

`This host currently has no management network redundancy`

The message is displayed even though there are two available uplinks for the private distributed switch, which provides a redundancy.

## Resolution
{: #trbl_host_displays_warning_msg-resolution}

This is a VMware known issue. To resolve the problem, follow the instructions in [ESX/ESXi host displays warning message when test condition is false (2008602)](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2008602){:new_window}.
