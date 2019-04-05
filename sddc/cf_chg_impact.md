---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-14"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Considerations about changing Cloud Foundation artifacts
{: #cf_chg_impact}

Changing users, resources, or subnets that are reserved for {{site.data.keyword.vmwaresolutions_full}} can impact management operations for VMware Cloud Foundation instances.

Do not change the global permissions of the **ic4v-vCenter** group in the **Users and Groups** page on the VMware vSphere Web Client. The following examples are global permission changes: changing the user name, deleting the user, or changing its password.
Use the **customerroot** host user ID in place of the **root** host user ID.
{:important}

## Service-specific user accounts
{: #cf_chg_impact-service-usr-account}
{: faq}

Each service creates an internal user account in vCenter Server. This account is necessary so that management operations that are associated to a service can connect to vCenter Server to perform the operations on the service.

To prevent outages and connection problems, if you change the user ID, password, or password expiration settings for this user account, ensure that you also update the information in the associated service.
{:important}

The user ID for this account is in the format `<service_name>-<truncated service_uuid>@test.local` or `<service_name>-<truncated service_uuid>@example-domain.local`. For example, the user ID that the Veeam on {{site.data.keyword.cloud_notm}} service uses to connect to vCenter Server to perform scheduled backups is `Veeam-<Veeam_uuid>@test.local`.

The `<service_name>` together with the `<service_uuid>` truncates to 20 characters.
{:note}

## VMware resources for Cloud Foundation instances
{: #cf_chg_impact-vmware-resources}
{: faq}

The following table lists the operations that might be impacted if you change VMware resources outside of the {{site.data.keyword.vmwaresolutions_short}} console. If a solution to recover is available, it is provided as well.

Table 1. Operations that are impacted for the SSO admin (customer)

| Attempted change  | Impacted operations  | Severity  | Recovery method  |
|:------------- |:------------- |:--------------|:--------------|
| Change the VMware virtual datacenter name. | Adding a VMware datacenter might fail because the new ESXi server cannot join the changed datacenter. | Important | Change the VMware virtual datacenter name back to the original name. |
| Change any port group names.    | Adding an ESXi server might fail. | Important | Change the port group name back to the original name. |
| Change the cluster name. | Adding an ESXi server might fail. | Important | Change the cluster name back to the original name.
| Change the public or private Distributed Virtual Switch (DVS) name. | Adding an ESXi server might fail. | Important | Change the DVS name back to the original name.
| Change the VSAN datastore name. | Adding an ESXi server might fail.<br><br>Upgrading the instance might fail. | Important | Change the VSAN datastore name back to the original name, **vsanDatastore**.
| Change the instance name or the domain name. | Instance is unusable. | Critical | N/A

The following table lists the operations that might be impacted if SSH or shell access is disabled for various resources.

Table 2. Operations that are impacted by SSH and shell access (local)

| Attempted change  | Impacted operations  | Severity  | Recovery method  |
|:------------- |:------------- |:--------------|:--------------|
| Disable SSH or shell access for vCenter Server or PSC.    | Pairing a primary and secondary instance might fail. Applying patches to the resources might fail.    | Important    | N/A    |

If you choose to disable SSH or shell access, you should re-enable it temporarily before performing the indicated operations.

## Management subnets for Cloud Foundation instances
{: #cf_chg_impact-mgmt-subnets}
{: faq}

The following information discusses the subnets that are ordered by {{site.data.keyword.vmwaresolutions_short}} and it provides options for you to order extra subnets for your own use.

**CAUTION:** Do not use these components for other purposes, or the stability of your environment is severely compromised.

With each {{site.data.keyword.cloud_notm}} Bare Metal Server order, the following ranges of IP addresses are ordered by default:
*  A primary public range of 32 IP addresses
*  A primary private range of 64 IP addresses

In addition, the following management subnets are also reserved for {{site.data.keyword.vmwaresolutions_short}}:
*  Two portable private subnets of 64 IP addresses on the first VLAN: one for management and the other one for VTEPS.
*  Two portable private subnets of 64 IP addresses on the second VLAN: one for vMotion and one for vSAN.
*  A public portable subnet of 16 IP addresses on the public VLAN.

If you need more subnets to use, you can obtain IP addresses to use in one of the following ways:
* **Option 1 (recommended):** Use VMware NSX virtual network overlays. A sample VXLAN template is provided when ordering. This VXLAN template can be used as a starting point for building SDN.
* **Option 2:** Order your own portable public or private subnets to obtain IP addresses. To distinguish the subnets that you order from the management subnets, you can add notes to all the subnets that you are ordering.
