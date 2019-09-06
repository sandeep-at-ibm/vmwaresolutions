---

copyright:

  years:  2019

lastupdated: "2019-08-29"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Single Sign On
{: #adds-sso}

vCenter Single Sign-On (SSO) is an authentication broker and security token exchange infrastructure, which allows vSphere components to communicate with each other through a secure token mechanism and uses the following services:

* Security Token Service (STS).
* SSL for secure traffic.
* Authentication of users via an identity source such as Active Directory or OpenLDAP.

The vSphere SSO flow is as follows:

1. A user logs in to the vSphere Client with a user name and password to access vCenter or a vCenter service.
2. The vSphere Client passes the login information to the SSO service, which checks the SAML token of the vSphere Client. If the vSphere Client has a valid token, SSO then checks whether the userID
    * If the userID is @vsphere.local, then it checks the user against the local SSO domain
    * If the userID is @DOMAIN, then SSO uses the identity source to check that domain.
3. If authentication is successful SSO returns a token that represents the user to the vSphere Client.
4. The vSphere Client passes the token to vCenter.
5. vCenter checks with SSO that the token is valid and has not expired.
6. The user can view and modify any objects that the user's role has privileges for.

The vSphere SSO domain is used as the initial authentication mechanism it is also serves to connect an instance or multiple linked instances to the AD servers in the {{site.data.keyword.vmwaresolutions_full}} infrastructure domain. In the {{site.data.keyword.vmwaresolutions_short}} vCenter Server design, the following SSO configuration is applied:

* The SSO domain of vsphere.local is always used.
* The SSO site name equals the <subdomain_label> captured during the ordering process.
* An identity source, the {{site.data.keyword.vmwaresolutions_short}} infrastructure domain, <root_domain>, is configured.
* The VSPHERE.LOCAL\Administrator user is configured as an Administrator role.
* The following groups are configured with Administrator roles:
  * <root_domain>\ic4v-vCenter.
  * vsphere.local\Administrators.

After deployment, the administrator@vsphere.local user has administrator access to both SSO and vCenter and can manage identity sources and default domains, specify password policies, and perform other administrative tasks in the vsphere.local domain. This user is integral to the VMware vSphere and NSX infrastructure authentication, however, they are not part of AD but created automatically when vSphere is deployed. As this account is not part of AD, they can be used in situations when AD is not working correctly.

As the customer, you have full access to manage the vSphere SSO users and groups as needed. For changing these policies, see [Managing vCenter Single Sign-On Users and Groups](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.psc.doc/GUID-31F302A6-D622-4FEC-9007-EE3BA1205AEA.html){:external}.

## Identity sources
{: #adds-sso-identity}

Identity sources are used to attach one or more domains to vCenter SSO. A domain is a repository for users and groups that the vCenter SSO can use for user authentication. vCenter SSO has the following domains configured after the vCenter Server instance deployment:

* Local OS - Local operating system users are local to the operating system where the vCenter Single Sign-On server is running. The local operating system identity source exists only in basic vCenter SSO deployments and is not available in deployments with multiple vCenter SSO instances. Only one local operating system identity source is allowed. Shown as localos in the vSphere Client.
* vsphere.local – Enables administrator@vsphere.local to be authenticated.
* {{site.data.keyword.vmwaresolutions_short}} infrastructure domain – This will be the <root_domain> configured on the ADDNS server based on the parameters collected during the ordering process. This allows the user automation@<root_domain> to be authenticated.

Users can log in to vCenter only if they are in a domain that has been added as a vCenter SSO identity source. You add additional identity sources to give your AD or LDAP users access if required.

## vSphere SSO configuration
{: #adds-sso-config}

The following sections provide the settings configured in vSphere SSO:

* Token trustworthiness.
* Lockout policy.
* Password policy.

As the customer, you have full access to tailor these settings as needed to apply your enterprise security policies. For changing these policies, see [Managing vCenter Single Sign-On Policies](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.psc.doc/GUID-43527B09-63BB-44A6-91D3-E3A470904698.html){:external}.

| Parameter | Value |
|:----------|:------|
| Clock tolerance | 600000 milliseconds |
| Maximum token renewal count | 10 |
| Maximum token delegation count | 10 |
| Maximum bearer token lifetime | 300 seconds |
| Maximum holder-of-key token lifetime | 2592000 seconds |
{: caption="Table 1. Token trustworthiness" caption-side="top"}

| Parameter | Value |
|:----------|:------|
| Maximum number of failed login attempts | 5 |
| Time interval between failures | 180 seconds |
| Unlock time | 300 seconds |
{: caption="Table 2. Lockout policy" caption-side="top"}

| Parameter | Value |
|:----------|:------|
| Maximum lifetime | Password must be changed every 365 days |
| Restrict reuse | Users cannot reuse any previous 5 passwords |
| Maximum length | 20 characters |
| Minimum length | 8 characters |
| Character requirements | At least 2 alphabetic characters<br>At least 1 special character<br>At least 1 uppercase character<br>At least 1 lowercase character<br>At least 1 numeric character<br>Identical adjacent characters: 3 |
{: caption="Table 3. Password policy" caption-side="top"}

## vSphere ESXi hosts
{: #adds-sso-esxi}

Each vSphere ESXi host has its own root account along with its own password. To identify this password, you will need to navigate to the IBM Cloud portal and then navigate to; VMware,  Infrastructure, Resources, <instance_name>, Infrastructure, <cluster_name>. It is also possible to have the vSphere ESXi hosts join AD, so that each system administrator can log in with their own account.

## Related links
{: #adds-sso-related}

* [Common services design](/docs/services/vmwaresolutions?topic=vmware-solutions-design_commonservice)
* [Post-deployment considerations for your VMware instance - Active Directory](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_considerations#solution_considerations-ad)
