---

copyright:

  years:  2016, 2021

lastupdated: "2021-09-10"

keywords: troubleshooting, vSphere configuration issue, HA cluster issue

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Why do I see a vSphere console configuration issue when I add a high-availability cluster?
{: #trbl_add_ha_cluster_config}
{: troubleshoot}

When you add a High Availability (HA) cluster configuration with only one file share, the following configuration issue is seen on the ESXi hosts:
{: tsSymptoms}

`The number of heartbeat datastores for host is 1, which is less than required: 2`

This issue occurs if redundancy is not in shared storage to allow for data store heart beating.
{: tsCauses}

For more information about how to fix the problem, see [How to add the number of vSphere HA heartbeat datastores for the ESXi host](https://communities.vmware.com/t5/VMware-vSphere-Discussions/How-to-add-the-number-of-vSphere-HA-heartbeat-datastores-for-the/td-p/1415119){: external}.
{: tsResolve}
