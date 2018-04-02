---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-19"

---

# Impacts of changing artifacts for vCenter Server instances

Changing users, resources, or subnets that are reserved for {{site.data.keyword.vmwaresolutions_full}} can impact management operations.

## automationuser ID

The **automationuser** ID is a user account that is used by the automated operations provided in the {{site.data.keyword.vmwaresolutions_short}} console.

Users and passwords for the automated operations in the console must not be changed because the console operations that depends on those credentials might fail.

Do not update the properties of the **automationuser** ID in the **Users and Groups** page on the VMware vSphere Web Client. Such changes include: changing the user name, deleting the user, or changing its password.

## VMware resources for vCenter Server instances (V1.9 and later)

For instances deployed in V1.9 and later, if the vCenter Server instance is in a **Ready to Use** state, you can modify the VMware virtual datacenter, cluster, switches, port groups, and customer datastore names from the VMware vSphere Web Client. However, you must not change the name of the management datastore from its default value, **management-datastore**.

## VMware resources for vCenter Server instances (V1.8 and earlier)

The following table lists the operations that might be impacted if the SSO administrator changes VMware vCenter Server resources outside of the {{site.data.keyword.vmwaresolutions_short}} console. If a solution to recover is available, it is provided as well.

This table is applicable to versions V1.8 and earlier only.

Table 1. Operations that are impacted by changing VMware resources

| Attempted change  | Impacted operations  | Severity  | Recovery method  |
|:------------- |:------------- |:--------------|:--------------|
| Change the VMware virtual datacenter name. | Adding a VMware virtual datacenter might fail because the new ESXi server cannot join the changed virtual datacenter. | Important | Change the VMware virtual datacenter name back to the original name. |
| Change any port group names.    | Adding an ESXi server might fail. | Important | Change the port group name back to the original name. |
| Change the cluster name. | Adding an ESXi server might fail. | Important | Change the cluster name back to the original name.
| Change the public or private Distributed Virtual Switch (DVS) name. | Adding an ESXi server might fail. | Important | Change the public or private Distributed Virtual Switch (DVS) name to the original name.
| Change any Network File System (NFS) datastore names. | Adding an ESXi server might fail. | Important | Remount the NFS datastore as read-only on the ESXi server. The NFS datastore name must match the one provisioned when the system started.

The following table lists the operations that might be impacted if the VC/PSC root user changes vCenter Server resources outside of the {{site.data.keyword.vmwaresolutions_short}} console.

Table 2. Operations that are impacted by for the VC/PSC root access (local)

| Attempted change  | Impacted operations  | Severity  | Recovery method  |
|:------------- |:------------- |:--------------|:--------------|
| Enable or disable shell access.    | Patching and updating for PSC and vCenter Server might fail.    | Important    | N/A    |

## Management subnets for vCenter Server instances

The following information discusses the subnets that are ordered by {{site.data.keyword.vmwaresolutions_short}} and it provides options for you to order extra subnets for your own use.

**CAUTION**: Do not use these components for other purposes, or the stability of your environment is severely compromised.

With each {{site.data.keyword.cloud_notm}} Bare Metal Server order, the following ranges of IP addresses are ordered by default:
*  A primary public range of 32 IP addresses
*  A primary private range of 64 IP addresses

In addition, the following management subnets are also reserved for {{site.data.keyword.vmwaresolutions_short}}:
*  Two portable private subnets of 64 IP addresses on the first VLAN: one for management and the other one for VTEPS
*  Two portable private subnets of 64 IP addresses on the second VLAN: one for VMotion and one for vSAN
*  A public portable subnet of 16 IP addresses on the public VLAN

If you need more subnets to use, you can obtain IP addresses to use in one of the following ways:
*  **Option 1 (recommended)**: Use VMware NSX virtual network overlays. A sample VXLAN template is provided upon order. This VXLAN can be used as a starting point for building software-defined networking (SDN). For more information, see [Configuring your network to use the customer-managed NSX Edge](vc_esg_config.html).
*  **Option 2**: Order your own portable public or private subnets to obtain IP addresses. To distinguish the subnets that you order from the management subnets, you can add notes to all the subnets that you are ordering.
