---

copyright:

  years:  2020

lastupdated: "2020-07-28"

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:note: .note}
{:important: .important}

# NSX-T administration interface identity and access management
{: #fss-iam-nsxt}

The following main principles or requirements apply:
- Infrastructure Admin has execute and full access to all components.
- Auditor has read-only access to all components.

## NSX-T role mapping
{: #fss-iam-nsxt-rolemapping}

NSX-T Component | Auditor | Infrastructure Admin |
----------------|------------------------------|--------------------|----------------|
Controllers     | Read | Full |
Transport Nodes | Read | Full |
Edge Nodes      | Read | Full |
Segments - VLAN | Read | Full |
Segments - Overlay   | Read | Full |
T0 - Tenant     | Read | Full |
T0 - Transit    | Read| Full |
T0 - Management | Read | Full |
T1s - Tenant    | Read | Full |
T1s - Addon Services | Read | Full |
T1s - Management     | Read | Full |
{: caption="Table 1. NSX-T role mapping" caption-side="top"}

The roles and privileges for load balancing, firewall rules, and VPN services follow the T0/T1 roles and privileges.

## NSX-T roles
{: #fss-iam-nsxt-roles}

NSX-T Data Center has the following built-in roles. You cannot add any new roles.

- Enterprise Administrator
- Auditor
- Network Engineer
- Network Operations
- Security Engineer
- Security Operations
- Load Balancer Administrator
- Load Balancer Auditor
- VPN Administrator
- Guest Introspection Administrator
- Network Introspection Administrator

## NSX-T user interface user IDs
{: #fss-iam-nsxt-ids}

| User     | User ID      | Description |
|:---------|:-------------|:------------|
| SaaS provider | admin | Used post-deployment to manage NSX VTEP IP addresses and to manage host and cluster configuration when hosts and clusters are added and removed. Also used to manage ESG configuration for add-on services that require public network access for licensing, activation, or usage reporting. |
| SaaS provider | `cloudadmin` | Through the HyTrust Cloud Controller URL, customers authenticate with the `cloudadmin` user who is defined in Active Directory. More users can be added from customer space through HyTrust. |
| IBM | automation_admin | Automation account used by IBM. It uses the principle identity functions to create configuration and protect it with a certificate. |
{: caption="Table 2. NSX-T user IDs" caption-side="top"}

For more information, see the [VMware documentation - RBAC for NSX-T](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.5/administration/GUID-26C44DE8-1854-4B06-B6DA-A2FD426CDF44.html){:external}.

**Next topic**: [HyTrust identity and access management](/docs/vmwaresolutions?topic=vmwaresolutions-fss-iam-hytrust)

## Related links
{: #fss-iam-nsxt-related}

* [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance)
* [HyTrust CloudControl](/docs/vmwaresolutions?topic=vmwaresolutions-htcc_considerations)
* [HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)
* [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto)
