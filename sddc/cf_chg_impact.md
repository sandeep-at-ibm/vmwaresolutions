---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-19"

---

# Impacts of changing artifacts for Cloud Foundation instances

Changing resources or subnets that are reserved for {{site.data.keyword.vmwaresolutions_full}} can impact management operations for VMware Cloud Foundation instances.

## VMware resources for Cloud Foundation instances

The following table lists the operations that might be impacted if you change VMware resources outside of the {{site.data.keyword.vmwaresolutions_short}} console. If a solution to recover is available, it is provided as well.

Table 1. Operations that are impacted for the SSO admin (customer)

| Attempted change  | Impacted operations  | Severity  | Recovery method  |
|:------------- |:------------- |:--------------|:--------------|
| Change the VMware virtual datacenter name. | Adding a VMware datacenter might fail because the new ESXi server cannot join the changed datacenter. | Important | Change the VMware virtual datacenter name back to the original name. |
| Change any port group names.    | Adding an ESXi server might fail. | Important | Change the port group name back to the original name. |
| Change the cluster name. | Adding an ESXi server might fail. | Important | Change the cluster name back to the original name.
| Change the public or private Distributed Virtual Switch (DVS) name. | Adding an ESXi server might fail. | Important | Change the DVS name back to the original name.
| Change the VSAN datastore name. | Adding an ESXi server might fail. | Important | Change the VSAN datastore name back to the original name, **vsanDatastore**.
| Change the instance name or the domain name. | Instance is unusable. | Critical | N/A

## Management subnets for Cloud Foundation instances

The following information discusses the subnets that are ordered by {{site.data.keyword.vmwaresolutions_short}} and it provides options for you to order extra subnets for your own use.

**CAUTION**: Do not use these components for other purposes, or the stability of your environment is severely compromised.

With each {{site.data.keyword.cloud_notm}} Bare Metal Server order, the following ranges of IP addresses are ordered by default:

*  A primary public range of 32 IP addresses
*  A primary private range of 64 IP addresses

In addition, the following management subnets are also reserved for {{site.data.keyword.vmwaresolutions_short}}:

*  Two portable private subnets of 64 IP addresses on the first VLAN: one for management and the other one for VTEPS.
*  Two portable private subnets of 64 IP addresses on the second VLAN: one for vMotion and one for vSAN.
*  A public portable subnet of 16 IP addresses on the public VLAN.

If you need more subnets to use, you can obtain IP addresses to use in one of the following ways:

* **Option 1 (recommended)**: Use VMware NSX virtual network overlays. A sample VXLAN template is provided when ordering. This VXLAN template can be used as a starting point for building SDN.
* **Option 2**: Order your own portable public or private subnets to obtain IP addresses. To distinguish the subnets that you order from the management subnets, you can add notes to all the subnets that you are ordering.
