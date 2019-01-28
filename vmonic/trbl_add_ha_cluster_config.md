---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-22"

---

# vSphere console configuration issue that is seen on adding HA cluster

## Problem

When you add an HA (High Availability) cluster configuration with only one file share, the following configuration issue is seen on the ESXi hosts:

> The number of heartbeat datastores for host is 1, which is less than required: 2

## Resolution
This issue occurs if there is no redundancy in shared storage to allow for data store heart beating.

For more information and steps how to fix the problem, see [HA error: The number of heartbeat data stores for host is 1, which is less than required: 2 (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739).
