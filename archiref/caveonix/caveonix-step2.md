---

copyright:

  years:  2016, 2020

lastupdated: "2020-03-30"

subcollection: vmware-solutions


---

# Step 2 - Virtual machine deployment
{: #caveonix-step2}

The {{site.data.keyword.vmwaresolutions_full}} automation requests an additional portable private IP subnet and the “all-in-one” virtual machine (VM) is configured with an IP address from this subnet so that the Caveonix RiskForesight components can:

- Connect to vCenter and NSX Manager through the BCR.
- Connect to Remote Collectors, either on VXLANs or hosted off-premise.
- Allow the client to manage the IP address space when scaling up.

**Next topic:** [Step 3 - Application configuration](/docs/vmwaresolutions?topic=vmware-solutions-caveonix-step3)
