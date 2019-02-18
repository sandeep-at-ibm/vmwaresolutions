---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# vSphere console configuration issue that is seen on adding HA cluster
{: #trbl_add_ha_cluster_config}

## Problem
{: #trbl_add_ha_cluster_config-problem}

When you add an HA (High Availability) cluster configuration with only one file share, the following configuration issue is seen on the ESXi hosts:

> The number of heartbeat datastores for host is 1, which is less than required: 2

## Resolution
{: #trbl_add_ha_cluster_config-resolution}

This issue occurs if there is no redundancy in shared storage to allow for data store heart beating.

For more information and steps how to fix the problem, see [HA error: The number of heartbeat data stores for host is 1, which is less than required: 2 (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739).
