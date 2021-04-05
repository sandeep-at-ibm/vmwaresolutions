---

copyright:

  years:  2016, 2021

lastupdated: "2021-03-17"

keywords: troubleshooting, secondary vCenter, vSphere inventory issue

subcollection: vmwaresolutions

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Why doesn't the secondary vCenter Server display in the vSphere Web Client inventory?
{: #trbl_sec_inst_not_visible}
{: troubleshoot}
{: support}

In a multi-site configuration, after you add a secondary instance, its VMware vCenter Server® system is not visible when logged in to the VMware vSphere® Web Client of a previously ordered instance.
{: tsSymptoms}

This is a known VMware 6.5 issue.
{: tsCauses}

To resolve the problem, you must restart the vSphere Web Client:
{: tsResolve}

1. Using the **root** account, connect over **ssh** to the vCenter VM (virtual machine) of the previously ordered instance.
2. Type ``shell`` to enter the bash shell.
3. Enter `service-control --stop vsphere-client` to stop the client.
4. Enter `service-control --start vsphere-client` to restart the client.
5. After the vSphere Web Client of the previously ordered instance is restarted, confirm that the vCenter Server system for the newly added secondary instance is visible in the vSphere Web Client.
