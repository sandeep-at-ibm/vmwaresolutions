---

copyright:

  years:  2020, 2021

lastupdated: "2021-08-16"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:external: target="_blank" .external}

# Active Directory
{: #vrw-iam-active-directory}

Microsoft® Active Directory serves to authenticate accesses to manage the VMware® instance only and not to house SaaS consumer users of the workloads in the deployed instances. The forest root domain name of the Active Directory server equals to the Domain Name Services (DNS) domain name that you specify for the initial instance deployment.

Domain name services (DNS) in this design are for the cloud management and infrastructure components only. The DNS zone files are also replicated on the Active Directory servers.

## Active Directory groups and users
{: #vrw-iam-active-directory-account}

The {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads Active Directory is used for the privileged administrators, service accounts, and the {{site.data.keyword.cloud_notm}} for VMware Solutions `automation` service ID.

### Microsoft Active Directory user IDs
{: #vrw-iam-active-directory-account-users}

| User     | User ID       | Description |
|:---------|:------------- |:------------|
| IBM automation     | `automation`    | Used to add a host or a virtual machine for service. Also, to set up Active Directory and DNS entries |
| Privileged user | `Administrator` | Default Windows® user |
| Privileged user | `cloudadmin`    | Default user for the customer to access vCenter Server |
| Non-privileged | `cloudreadonly` | Read-only account for the customer |
{: caption="Table 1. Active Directory user IDs" caption-side="top"}

### Microsoft Active Directory groups
{: #vrw-iam-active-directory-account-groups}

| User     | User ID       | Description |
|:---------|:------------- |:------------|
| IBM automation or privileged users | `IC4v-vCenter` | vCenter Administration Group |
{: caption="Table 2. Active Directory groups" caption-side="top"}

**Next topic**: [vCenter identity and access management](/docs/vmwaresolutions?topic=vmwaresolutions-vrw-iam-vsphere)

## Related links
{: #vrw-iam-active-directory-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
* [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)
* [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto)
