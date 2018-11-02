---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Common services components

Common services provide the services that are used by other services in the cloud
management platform. This includes identity and access services, domain
name services, NTP services.

Figure 1. ICP common services
![ICP common services](vcscar-common-services.svg)

## Identity and access services

As part of the VCS automation, a Microsoft Active Directory (AD) is
employed for identity management. A single AD virtual server instance
(VSI) is deployed. The vCenter is configured to utilize MS AD
authentication and ICP can be configured as well for LDAP
Authentication.

## Domain Name services

The VCS deployment utilizes the deployed Microsoft Active Directory (AD)
VSIs as DNS servers for the instance. All deployed components (vCenter,
PSC, NSX, ESXi hosts) are configured to point to the MS AD as their
default DNS.

## NTP services

The VCS deployment utilizes the {{site.data.keyword.cloud}} infrastructure NTP servers.
All deployed components will be configured to utilize these NTP servers.
Having all components within the design utilizing the same NTP servers
is critical for certificates and MS AD authentication to function
correctly

### Related links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
