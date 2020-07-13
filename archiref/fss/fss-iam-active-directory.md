---

copyright:

  years:  2020

lastupdated: "2020-07-10"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Active Directory
{: #fss-iam-active-directory}

Microsoft Active Directory serves to authenticate accesses to manage the VMware instance only and not to house users of the workloads in the deployed instances. The forest root domain name of the Active Directory server equals to the Domain Name Services (DNS) domain name that you specify for the initial instance deployment.

Domain name services (DNS) in this design are for the Cloud Management and infrastructure components only. The DNS zone files are also replicated on the Active Directory servers.

## Active Directory groups and users
{: #fss-iam-active-directory-account}

The IBM Cloud for VMware Regulated Workloads Active Directory is used for the ISV administrators, service accounts, and the VMware Solutions `automation` service ID.

### Microsoft Active Directory user IDs
{: #fss-iam-active-directory-account-users}

| User     | User ID       | Description |
|:---------|:------------- |:------------|
| IBM      | `automation`    | Used to add a host or a virtual machine for service. Also, to set up Active Directory and DNS entries |
| ISV      | `Administrator` | Default Windows user |
| ISV | `cloudadmin`    | Default user for the customer to access vCenter Server |
| ISV | `cloudreadonly` | Read-only account for the customer |
{: caption="Table 1. Active Directory user IDs" caption-side="top"}

### Microsoft Active Directory groups
{: #fss-iam-active-directory-account-groups}

| User     | User ID       | Description |
|:---------|:------------- |:------------|
| IBM/ISV      | `IC4v-vCenter`    | vCenter Administration Group |
{: caption="Table 2. Active Directory groups" caption-side="top"}

**Next topic**: [vCenter identity and access management](/docs/vmwaresolutions?topic=vmwaresolutions-fss-iam-vsphere)

## Related links
{: #fss-iam-active-directory-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
* [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)
* [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto)
