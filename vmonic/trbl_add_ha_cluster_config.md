---

copyright:

  years:  2016, 2020

lastupdated: "2020-10-23"

keywords: troubleshooting, vSphere configuration issue, HA cluster issue

subcollection: vmwaresolutions


---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:external: target="_blank" .external}

# Why do I see a vSphere console configuration issue when I add a High Availability cluster?
{: #trbl_add_ha_cluster_config}
{: troubleshoot}

When you add a High Availability (HA) cluster configuration with only one file share, the following configuration issue is seen on the ESXi hosts:
{: tsSymptoms}

`The number of heartbeat datastores for host is 1, which is less than required: 2`

This issue occurs if there is no redundancy in shared storage to allow for data store heart beating.
{: tsCauses}

For more information and steps how to fix the problem, see [HA error: The number of heartbeat data stores for host is 1, which is less than required: 2](https://kb.vmware.com/articleview?docid=2004739){:external}.
{: tsResolve}
