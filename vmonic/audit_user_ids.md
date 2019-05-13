---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM user IDs
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_short}} maintains a set of users in your account for use by {{site.data.keyword.cloud_notm}} automation when you perform operations such as adding hosts, clusters, or storage to your VMware instance. Review the following sections for {{site.data.keyword.cloud_notm}} automation user IDs.

VMware instance operations fail if the IBM user IDs are deleted, disabled, or if their passwords are changed.
{:important}

## vCenter and Platform Services Controller user IDs
{: #audit_user_ids-vcenter-psc}

Starting with V2.5, {{site.data.keyword.vmwaresolutions_short}} uses the following user IDs to add an identity source, embedded by default, into vCenter.

Table 1. vCenter and Platform Services Controller user IDs

| User     | User ID      | Method | Description |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | Used for VMware configuration such as setting up VMware High Availability and creating distributed switches. Used post deployment to pair primary and secondary vCenter Server instances. |
| Customer | customerroot | SSH    | Created for customer use only. |
| IBM      | automation@``root_domain``<br/>(Active Directory user) | HTTP | Used post deployment to add and remove hosts and clusters and to deploy and configure virtual machines for add-on services. |
| Customer | Administrator@vsphere.local | HTTP | Created for customer use only. |

HTTP is used for vCenter set up and configuration, as well as VMware operations such as adding hosts, clusters, or storage for vCenter management of resources.
{:note}

## NSX Manager user IDs
{: #audit_user_ids-nsx-mgr}

Table 2. NSX Manager user IDs

| User     | User ID      | Description |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(Active Directory user) | Used post deployment to manage NSX VTEP IP addresses, manage host and cluster configuration when adding and removing hosts and clusters, and manage ESG configuration for add-on services that require public network access for licensing, activation, or usage reporting. |
| Customer | Admin        | Created for customer use only. |

## ESXi host user IDs
{: #audit_user_ids-esxi}

Table 3. ESXi host user IDs

| User     | User ID      | Description |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Used post deployment to add additional NFS storage, to configure routes for that storage, and to run all server validation code. |
| Customer | root         | Created for customer use only. |

## Microsoft Active Directory user IDs
{: #audit_user_ids-ad}

Table 4. Active Directory user IDs

| User     | User ID       | Description |
|:---------|:------------- |:------------|
| IBM      | automation    | Used to add a host, to add a virtual machine for service, and to set up Active Directory and DNS entries. |
| Customer | Administrator | Created for customer use only. |

## Related links
{: #audit_user_ids-related}

* [Considerations about changing vCenter Server artifacts](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker events](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
