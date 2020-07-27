---

copyright:

  years:  2020

lastupdated: "2020-07-20"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter identity and access management
{: #fss-iam-vsphere}

Inside the IBM Cloud for VMware Regulated Workloads solution, there are multiple levels of access. The automation uses a set of user IDs to perform operations such as adding hosts, clusters, or storage to your VMware instance.

## vCenter and Platform Services Controller user IDs
{: #fss-iam-vsphere-vcenter}

The following user IDs are used to add an identity source, which is embedded by default, into vCenter.

| User     | User ID      | Method | Description |
|:---------|:-------------|:-------|:------------|
| ISV      | `root`       | SSH    | Used for VMware configuration such as setting up VMware High Availability and creating distributed switches. Used post deployment to pair primary and secondary vCenter Server instances. |
| ISV | customerroot | SSH    | Created for customer use only. |
| IBM      | automation@``root_domain``<br/>(Active Directory user) | HTTP | Used post deployment to add and remove hosts and clusters and to deploy and configure virtual machines for add-on services. |
| ISV | `cloudadmin`@`root_domain`<br/>(Active Directory user) | HTTP | Created for ISVr use only. |
{: caption="Table 1. vCenter and Platform Services Controller user IDs" caption-side="top"}

HTTPS is used for vCenter setup and configuration, and for VMware operations such as adding hosts, clusters, or storage for vCenter management of resources.

### vCenter access
{: #fss-iam-vsphere-vcenter-access}

ISV is granted cloudadmin access to the vCenter through the HyTrust Cloud Control role, there is no direct access to the vCenter.

## NSX Manager user IDs
{: #fss-iam-vsphere-nsx}

| User     | User ID      | Description |
|:---------|:-------------|:------------|
| IBM      | ibm_automation <br/>(NSX-T Principle Identity user) | Used post deployment to manage NSX VTEP IP addresses, manage host and cluster configuration when adding and removing hosts and clusters, and manage ESG configuration for add-on services that require public network access for licensing, activation, or usage reporting. |
| ISV | admin        | Created for customer use only. |
{: caption="Table 2. NSX Manager user IDs" caption-side="top"}

## ESXi host user IDs
{: #fss-iam-vsphere-esx}

| User     | User ID      | Description |
|:---------|:-------------|:------------|
| ISV      | ic4vroot     | Used post deployment to add more NFS storage, configure routes for that storage, and to run all server validation code. |
| ISV    | root         | Created for customer use only. |
{: caption="Table 3. ESXi host user IDs" caption-side="top"}

## Microsoft Active Directory user IDs
{: #fss-iam-vsphere-aduser}

| User     | User ID       | Description |
|:---------|:------------- |:------------|
| IBM      | automation    | Used to add a host or a virtual machine for service, and to set up Active Directory and DNS entries. |
| ISV      | Administrator | Default Windows user |
| ISV | cloudadmin    | Default user for customer to access vCenter Server |
| ISV | cloudreadonly | Read-only account for customer |
{: caption="Table 4. Active Directory user IDs" caption-side="top"}

## Microsoft Active Directory groups
{: #fss-iam-vsphere-adgroup}

| User     | User ID       | Description |
|:---------|:------------- |:------------|
| ISV      | IC4v-vCenter    | vCenter Administration Group |
{: caption="Table 5. Active Directory user IDs" caption-side="top"}

## Service user IDs
{: #fss-iam-vsphere-serviceid}

| User ID                                    | Description |
|:-------------------------------------------|:----------- |
| prod-BigIP-``dynamicID``-@``domainName`` | Used for installation and configuration of the F5 on {{site.data.keyword.cloud_notm}} service. |
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
{: caption="Table 6. Service user IDs" caption-side="top"}

where:

- ``dynamicID`` is the 8 - 10 characters that generated dynamically during the service installation.
- ``shortID`` is the 5 characters that generated dynamically during the service installation.
- ``domainName`` is the domain name of your instance.

**Next topic**: [NSX-T administration interface identity and access management](/docs/vmwaresolutions?topic=vmwaresolutions-fss-iam-nsxt)

## Related links
{: #fss-iam-vsphere-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
* [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)
* [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto)
