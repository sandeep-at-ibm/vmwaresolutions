---

copyright:

  years:  2016, 2020

lastupdated: "2020-03-18"

keywords: troubleshooting, configuration issue, ESXi server issue

subcollection: vmware-solutions

---

{:external: target="_blank" .external}
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# ESXi server displays configuration issue
{: #trbl_host_displays_warning_msg}
{: troubleshoot}
{: support}

## Problem
{: #trbl_host_displays_warning_msg-problem}

A configuration issue is displayed in the **Issues** tab of the **Monitor** tab of the VMware ESXi server in the vSphere client.
{: tsSymptoms}

The following message is displayed in the **Issues** tab for the ESXi server:

`This host currently has no management network redundancy`

The message is displayed even though there are two available uplinks for the private distributed switch, which provides a redundancy.

## Resolution
{: #trbl_host_displays_warning_msg-resolution}

This configuration issue is a VMware known issue.
{: tsCauses}

To resolve the problem, follow the instructions in [ESX/ESXi host displays warning message when test condition is false (2008602)](https://kb.vmware.com/s/article/2008602){:external}.
{: tsResolve}
