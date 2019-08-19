---

copyright:

  years: 2016, 2019

lastupdated: "2019-08-16"

keywords: user IDs vCenter, PSC user, user ID service

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM user IDs
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_full}} maintains a set of users in your account for use by {{site.data.keyword.cloud_notm}} automation when you perform operations such as adding hosts, clusters, or storage to your VMware instance. Users in your account can also be used for installation and configuration of services by {{site.data.keyword.cloud_notm}} services automation. Review the following sections for {{site.data.keyword.cloud_notm}} automation user IDs.

VMware instance operations fail if the IBM user IDs are deleted, disabled, or if their passwords are changed.
{:important}

## vCenter and Platform Services Controller user IDs
{: #audit_user_ids-vcenter-psc}

Starting with V2.5, {{site.data.keyword.vmwaresolutions_short}} uses the following user IDs to add an identity source, embedded by default, into vCenter.

| User     | User ID      | Method | Description |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | Used for VMware configuration such as setting up VMware High Availability and creating distributed switches. Used post deployment to pair primary and secondary vCenter Server instances. |
| Customer | customerroot | SSH    | Created for customer use only. |
| IBM      | automation@``root_domain``<br/>(Active Directory user) | HTTP | Used post deployment to add and remove hosts and clusters and to deploy and configure virtual machines for add-on services. |
| Customer | Administrator@vsphere.local | HTTP | Created for customer use only. |
{: caption="Table 1. vCenter and Platform Services Controller user IDs" caption-side="top"}

HTTP is used for vCenter set up and configuration, as well as VMware operations such as adding hosts, clusters, or storage for vCenter management of resources.
{:note}

## NSX Manager user IDs
{: #audit_user_ids-nsx-mgr}

| User     | User ID      | Description |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(Active Directory user) | Used post deployment to manage NSX VTEP IP addresses, manage host and cluster configuration when adding and removing hosts and clusters, and manage ESG configuration for add-on services that require public network access for licensing, activation, or usage reporting. |
| Customer | Admin        | Created for customer use only. |
{: caption="Table 2. NSX Manager user IDs" caption-side="top"}

## ESXi host user IDs
{: #audit_user_ids-esxi}

| User     | User ID      | Description |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Used post deployment to add additional NFS storage, to configure routes for that storage, and to run all server validation code. |
| Customer | root         | Created for customer use only. |
{: caption="Table 3. ESXi host user IDs" caption-side="top"}

## Microsoft Active Directory user IDs
{: #audit_user_ids-ad}

| User     | User ID       | Description |
|:---------|:------------- |:------------|
| IBM      | automation    | Used to add a host, to add a virtual machine for service, and to set up Active Directory and DNS entries. |
| Customer | Administrator | Created for customer use only. |
{: caption="Table 4. Active Directory user IDs" caption-side="top"}


## Service user IDs
{: #audit_user_ids-services}

| User ID                                    | Description |
|:-------------------------------------------|:----------- |
| prod-BigIP-``dynamicID``-@``domainName`` | Used for installation and configuration of the F5 on  {{site.data.keyword.cloud_notm}} service. |
| prod-Caveonix-``dynamicID``-@``domainName`` | Used for installation and configuration of the Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service. |
| prod-Fortigate-``dynamicID``-@``domainName`` | Used for installation and configuration of the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service. |
| prod-FortigateVM-``dynamicID``-@``domainName`` | Used for installation and configuration of the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service. |
| prod-HyTrustCC-``shortID``-@``domainName`` | Used for installation and configuration of the HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service. |
| prod-HyTrustDC-``shortID``-@``domainName`` | Used for installation and configuration of the HyTrust DataControl on {{site.data.keyword.cloud_notm}} service. |
| prod-HyTrustKC-``shortID``-@``domainName`` | Used for installation and configuration of the HyTrust KeyControl on {{site.data.keyword.cloud_notm}} service. |
| prod-KMIPAdapter-``dynamicID``-@``domainName`` | Used for installation and configuration of the KMIP for VMware on {{site.data.keyword.cloud_notm}} service. |
| prod-ICP-``dynamicID``-@``domainName`` | Used for installation and configuration of the {{site.data.keyword.cloud_notm}} Private Hosted service. |
| prod-SPPlus-``dynamicID``-@``domainName`` | Used for installation and configuration of the IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} service. |
| prod-Veeam-``dynamicID``-@``domainName`` | Used for installation and configuration of the Veeam on {{site.data.keyword.cloud_notm}} service. |
| prod-HCX-``dynamicID``-@``domainName`` | Used for installation and configuration of the VMware HCX on {{site.data.keyword.cloud_notm}} service. |
| prod-Zerto-``dynamicID``-@``domainName`` | Used for installation and configuration of the Zerto on {{site.data.keyword.cloud_notm}} service. |
{: caption="Table 5. Service user IDs" caption-side="top"}

where:

* ``dynamicID`` is the 8-10 characters that generated dynamically during the service installation.
* ``shortID`` is the five characters that generated dynamically during the service installation.
* ``domainName`` is the domain name of your instance.

## Related links
{: #audit_user_ids-related}

* [Considerations about changing vCenter Server artifacts](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker events](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
