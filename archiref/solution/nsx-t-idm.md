---

copyright:

  years:  2019

lastupdated: "2019-12-09"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware Identity Manager introduction
{: #nsx-t-idm}

VMware Identity Manager delivers multi-factor authentication (MFA), conditional access, and single sign-on (SSO) services for VMware solutions. It has recently been changed to a new name called VMware Workspace ONE Access, but for consistency, VMware Identity Manager (vIDM) is used.

By acting as a broker to identity stores, VMware Identity Manager can also be used to provide role base access control (RBAC) to NSX-T, which is its primary use case with {{site.data.keyword.vmwaresolutions_short}}. By default, NSX-T Data Center appliances have two built-in users: admin and audit. While this might be feasible for lab environments, for production deployment this is major limitation where clients require granular access control for various use cases.

VMware Identity Manager is necessary to provide RBAC to NSX-T. NSX-T Data Center integrates with VMware Identity Manager, and NSX-T Manager is then configured to use role-based access control for the users that vIDM manages. With this, clients can restrict NSX-T system access with multiple levels to authorized users. Users are assigned to NSX-T roles (11 built-in roles) and each role has specific permissions (Full access, Execute, Read, or None).

As a broker, VMware Identity Manager sits behind the primary identity provider, which in {{site.data.keyword.vmwaresolutions_short}} is the infrastructure domain Active Directory (AD). This intrastructure AD holds the users and groups that can be used to provide users access to the various NSX-T roles.

## vIDM deployment
{: #nsx-t-idm-depl}

VMware Identity Manager is provisioned as a virtual appliance on your {{site.data.keyword.vmwaresolutions_short}} instance's management cluster, and it is placed in the management VLAN and subnet (same as vCenter and NSX/NSX-T Mananager/Controllers). Accurate time synchronization between VMware components, vIDM, and Active Directory is required for authentication to work correctly. In {{site.data.keyword.vmwaresolutions_short}}, vIDM is provisioned as a single Virtual Machine and uses its embedded database.

| Attribute          | Specification                                         |
|:-------------------|:------------------------------------------------------|
| Operating System   | VMware Identity Manager Linux-based virtual appliance |
| Number of vCPUs     | 2                                                     |
| RAM                | 6 GB                                                  |
| Disk               | 60 GB                                                 |
| Disk type          | Thin provisioned                                      |
| Network            | Private Management Port Group                         |
{: caption="Table 1. vIDM specifications" caption-side="bottom"}

The VMware Identity Manager is provisioned by using a fully qualified domain name in the form of \<instancename>-idm.<root_domain>, for example, clusterX-idm.myroot.local.

vIDM is assigned a VLAN–backed IP address from the private portable address block that is designated for management components. It is configured with the AD as the DNS server and uses the {{site.data.keyword.cloud_notm}} infrastructure NTP servers.

## Integrating vIDM with Active Directory
{: #nsx-t-idm-adds}

VMware Identity Manager is integrated with Active Directory by using VMware Identity Manager connector, which is a software component of VMware Identity Manager that provides directory integration and user authentication.

In {{site.data.keyword.vmwaresolutions_short}}, the VMware Identity Manager connector is deployed on the Active Directory Windows servers by using an activation code that is generated in VMware Identity Manager console. The connector creates a new service on the AD server listening on ports 443 and 8443 and uses outbound connection mode when communicating with the VMware Identity Manager through a websocket-based communication channel.

Authentication is done with integrated Windows Authentication. VMware Identity Manager is using a new `idmbind` user to bind to Active Directory, while the domain join authentication is done by using the `Administrator` user.  

As self-signed certificates are used here, they need to be exchanged between the Active Directory server / VMware Identity Manager connector and VMware Identity Manager.

In a default vIDM deployment, users require First Name, Last Name, and email to be configured in Active Directory, otherwise vIDM will not sync them. As the pre-populated users in the infrastructure domain AD do not have all these attributes, updates to them are required before synchronizing. Required attributes are configured via vIDM console (Identity and Access management > Setup > User Attributes), and in {{site.data.keyword.vmwaresolutions_short}} the required attributes and mappings are listed on table below.

| Attribute Name in vIDM     | Attribute Name in Active Directory            |
|:---------------------------|:----------------------------------------------|
| userName                   | sAMAccountName                                |
{: caption="Table 2. Required vIDM and AD attributes" caption-side="bottom"}

The following groups are provisioned in the Active Directory for NSX-T users. You can create new groups in a similar way. Manual addition of users to these groups is necessary.  

| Group Name in Active Directory    | Description                            |
|:----------------------------------|:---------------------------------------|
| NSXTEnterpriseAdmins              | NSX-T Enterprise Administrators        |
{: caption="Table 3. NSX-T AD Groups" caption-side="bottom"}

Default `Sync Frequency` is set to one hour.

## Integrating NSX-T Controller-Manager with vIDM
{: #nsx_t_idm_nsxt}

NSX-T Controller Manager is integrated with vIDM by using OAuth-client. For this purpose, a client connection in vIDM is created for NSX-T.

When NSX Manager is registered with vIDM, a redirect URL is specified that points to NSX Manager. You can provide either the fully qualified domain name (FQDN) or the IP address. It is important to remember whether you use the FQDN or the IP address. When you try to log in to NSX Manager through vIDM, you must specify the hostname in the URL the same way, that is, if you use the FQDN when you register the manager with vIDM, you must use the FQDN in the URL, and if you use the IP address when registering the manager with vIDM, you must use the IP address in the URL. Otherwise, login fails.

In {{site.data.keyword.vmwaresolutions_short}}, NSX-T Controller Manager system users configuration is set with vIDM integration by using the VIP FQDN. OAuth client ID, OAuth Client Secret, and SSL Thumbprint are required for the integration and they are generated in vIDM console.

With this integration enabled, you can add, change, and delete role assignments to users or user groups in NSX-T Controller Manager GUI. NSX-T Data Center has the following roles. The roles are built in and you cannot add any new roles.
* Enterprise Administrator
* Auditor
* Network Engineer
* Network Operations
* Security Engineer
* Security Operations
* Load Balancer Administrator
* Load Balancer Auditor
* VPN Administrator
* Guest Introspection Administrator
* Network Introspection Administrator

Each NSX-T role has specific permissions for various operations:
* Full access
* Execute
* Read
* None

To understand which permissions each role has for different operations, see the [NSX-T documentation](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.3/com.vmware.nsxt.admin.doc/GUID-26C44DE8-1854-4B06-B6DA-A2FD426CDF44.html){:external}.

For users managed by vIDM, the applicable authentication policy is the one configured by the vIDM administrator. The NSX-T authentication policy applies to local admin and audit users only.
{:note}

**Next topic:** [Common services design](/docs/services/vmwaresolutions?topic=vmware-solutions-design_commonservice)

## Related links
{: #nsx-t-idm-related}

* [Overview of {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
* [Getting started with IBM Cloud for VMware Solutions](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [IBM Cloud for VMware Solutions: Take a look under the hood](/docs/services/vmwaresolutions?topic=vmware-solutions-under_the_hood)
* [RBAC Configuration in NSX-T](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.3/com.vmware.nsxt.admin.doc/GUID-26C44DE8-1854-4B06-B6DA-A2FD426CDF44.html){:external}
