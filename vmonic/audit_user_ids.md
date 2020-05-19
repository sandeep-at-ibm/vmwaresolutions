---

copyright:

  years: 2016, 2020

lastupdated: "2020-03-31"

keywords: user IDs vCenter, PSC user, user ID service

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM user IDs
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_full}} maintains a set of users in your account for use by {{site.data.keyword.cloud_notm}} automation when you run operations such as adding hosts, clusters, or storage to your VMware instance. Users in your account can also be used for installation and configuration of services by {{site.data.keyword.cloud_notm}} services automation. Review the following sections for {{site.data.keyword.cloud_notm}} automation user IDs.

VMware instance operations fail if the IBM user IDs are deleted, disabled, or if their passwords are changed.
{:important}

## vCenter and Platform Services Controller user IDs
{: #audit_user_ids-vcenter-psc}

Starting with V2.5, {{site.data.keyword.vmwaresolutions_short}} uses the following user IDs to add an identity source, which is embedded by default, into vCenter.

| User     | User ID      | Method | Description |
|:---------|:-------------|:-------|:------------|
| IBM      | `root`       | SSH    | Used for VMware configuration such as setting up VMware High Availability and creating distributed switches. Used post deployment to pair primary and secondary vCenter Server instances. |
| Customer | `customerroot` | SSH    | Created for customer use only. |
| IBM      | `automation@root_domain`<br/>(Active Directory user) | HTTP | Used post deployment to add and remove hosts and clusters and to deploy and configure virtual machines for add-on services. |
| Customer | Administrator@vsphere.local | HTTP | Created for customer use only. |
{: caption="Table 1. vCenter and Platform Services Controller user IDs" caption-side="top"}

HTTP is used for vCenter setup, configuration, and VMware operations such as adding hosts, clusters, or storage for vCenter management of resources.
{:note}

## NSX Manager user IDs
{: #audit_user_ids-nsx-mgr}

| User     | User ID      | Description |
|:---------|:-------------|:------------|
| IBM      | `automation@root_domain`<br/>(Active Directory user) | Used post deployment to manage NSX VTEP IP addresses, manage host and cluster configuration when you add and remove hosts and clusters. Also used to manage ESG configuration for add-on services that require public network access for licensing, activation, or usage reporting. |
| Customer | Admin        | Created for customer use only. |
{: caption="Table 2. NSX Manager user IDs" caption-side="top"}

## ESXi host user IDs
{: #audit_user_ids-esxi}

| User     | User ID      | Description |
|:---------|:-------------|:------------|
| IBM      | `ic4vroot`     | Used post deployment to add more NFS storage, configure routes for that storage, and run all server validation code. |
| Customer | `root`         | Created for customer use only. |
{: caption="Table 3. ESXi host user IDs" caption-side="top"}

## Microsoft Active Directory user IDs
{: #audit_user_ids-ad}

| User     | User ID       | Description |
|:---------|:------------- |:------------|
| IBM      | `automation`    | Used to add a host, add a virtual machine for service, and set up Active Directory and DNS entries. |
| Customer | Administrator | Created for customer use only. |
{: caption="Table 4. Active Directory user IDs" caption-side="top"}


## Service user IDs
{: #audit_user_ids-services}

| User ID                                    | Description |
|:-------------------------------------------|:----------- |
| prod-BigIP-``dynamicID``-@``domainName`` | Used for installation and configuration of the F5 on {{site.data.keyword.cloud_notm}} service. |
| prod-Caveonix-``dynamicID``-@``domainName`` | Used for installation and configuration of the Caveonix RiskForesight service. |
| prod-Fortigate-``dynamicID``-@``domainName`` | Used for installation and configuration of the FortiGate Security Appliance (Deprecated) service. |
| prod-FortigateVM-``dynamicID``-@``domainName`` | Used for installation and configuration of the FortiGate Virtual Appliance service. |
| prod-HyTrustCC-``shortID``-@``domainName`` | Used for installation and configuration of the HyTrust CloudControl service. |
| prod-HyTrustDC-``shortID``-@``domainName`` | Used for installation and configuration of the HyTrust DataControl service. |
| prod-HyTrustKC-``shortID``-@``domainName`` | Used for installation and configuration of the HyTrust KeyControl service. |
| prod-KMIPAdapter-``dynamicID``-@``domainName`` | Used for installation and configuration of the KMIP for VMware service. |
| prod-ICP-``dynamicID``-@``domainName`` | Used for installation and configuration of the {{site.data.keyword.cloud_notm}} Private Hosted service. |
| prod-SPPlus-``dynamicID``-@``domainName`` | Used for installation and configuration of the IBM Spectrum Protect Plus service. |
| prod-Veeam-``dynamicID``-@``domainName`` | Used for installation and configuration of the Veeam service. |
| prod-HCX-``dynamicID``-@``domainName`` | Used for installation and configuration of the VMware HCX service. |
| prod-Zerto-``dynamicID``-@``domainName`` | Used for installation and configuration of the Zerto service. |
{: caption="Table 5. Service user IDs" caption-side="top"}

Where:

* ``dynamicID``: the 8 - 10 characters that generated dynamically during the service installation.
* ``shortID``: the 5 characters that generated dynamically during the service installation.
* ``domainName``: the domain name of your instance.

## Related links
{: #audit_user_ids-related}

* [Considerations about changing vCenter Server artifacts](/docs/vmwaresolutions?topic=vmwaresolutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events#at-events)
