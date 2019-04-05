---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmware-solutions


---

# Step 2 - Virtual machine deployment
{: #caveonix-step2}

The {{site.data.keyword.vmwaresolutions_full}} automation requests an additional portable private IP subnet and the “all-in-one” virtual machine (VM) is configured with an IP address from this subnet so that the Caveonix RiskForesight components can:

- Connect to vCenter and NSX Manager through the BCR.
- Connect to Remote Collectors, either on VXLANs or hosted off-premise.
- Allow the client to manage the IP address space when scaling up.


## Related links
{: #caveonix-step2-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
