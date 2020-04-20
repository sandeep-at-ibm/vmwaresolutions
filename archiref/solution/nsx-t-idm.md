---

copyright:

  years:  2019, 2020

lastupdated: "2020-04-07"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware Identity Manager
{: #nsx-t-idm}

VMware Identity Manager delivers multi-factor authentication (MFA), conditional access, and single sign-on (SSO) services for VMware solutions. It has recently been changed to a new name called VMware Workspace ONE Access, but for consistency, VMware Identity Manager (vIDM) is used.

By acting as a broker to identity stores, VMware Identity Manager can also be used to provide role base access control (RBAC) to NSX-T, which is its primary use case with {{site.data.keyword.vmwaresolutions_short}}. By default, NSX-T data center appliances have two built-in users: **admin** and **audit**, which might be feasible for lab environments. However, for production deployments, clients require granular access control for various use cases and the built-in users are not sufficient.

VMware Identity Manager is necessary to provide RBAC to NSX-T. NSX-T data center integrates with VMware Identity Manager, and NSX-T Manager is then configured to use role-based access control for the users that vIDM manages. This way, clients can restrict NSX-T system access with multiple levels to authorized users.

Users are assigned to NSX-T roles and each role has specific permissions. With this integration enabled, you can add, change, and delete role assignments to users or user groups in NSX-T Controller Manager GUI.

NSX-T data center has the following roles:

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

Each NSX-T role has specific permissions for operations:

* Full access
* Execute
* Read
* None

To understand which permissions each role has for different operations, see the [NSX-T documentation](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.3/com.vmware.nsxt.admin.doc/GUID-26C44DE8-1854-4B06-B6DA-A2FD426CDF44.html){:external}.

For users managed by vIDM, the applicable authentication policy is the one configured by the vIDM administrator. The NSX-T authentication policy applies to local **admin**  and **audit** users only.
{:note}

NSX-T roles are built in and you cannot add any new roles.
{:note}

{{site.data.keyword.vmwaresolutions_short}} does not currently provide an automated vIDM deployment. For more information, see [VMware Workspace ONE Access Documentation](https://docs.vmware.com/en/VMware-Workspace-ONE-Access/index.html){:external}.

**Next topic:** [Common services design](/docs/vmwaresolutions?topic=vmware-solutions-design_commonservice)

## Related links
{: #nsx-t-idm-related}

* [VMware Workspace ONE Access Documentation](https://docs.vmware.com/en/VMware-Workspace-ONE-Access/index.html){:external}
* [RBAC Configuration in NSX-T](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.3/com.vmware.nsxt.admin.doc/GUID-26C44DE8-1854-4B06-B6DA-A2FD426CDF44.html){:external}
