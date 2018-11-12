---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Detailed design

## Common services components
Common services provide the services used by other services in the cloud management platform. This includes identity and access services, domain name services, NTP services.

Figure 1. ICP common services

![ICP Common Services](vcsicp-icp-commonservices.svg)

### Identity and access services
As part of the VCS automation, a Microsoft Active Directory (AD) is employed for identity management. A single AD virtual server instance (VSI) is deployed. The vCenter is configured to utilize MS AD authentication and ICP can be configured as well for LDAP Authentication.

###	Domain Name Services
The VCS deployment utilizes the deployed Microsoft Active Directory (AD) VSIs as DNS servers for the instance. All deployed components (vCenter, PSC, NSX, ESXi hosts) are configured to point to the MS AD as their default DNS.

###	NTP services
The VCS deployment utilizes the {{site.data.keyword.cloud}} infrastructure NTP servers. All deployed components will be configured to utilize these NTP servers. Having all components within the design utilizing the same NTP servers is critical for certificates and MS AD authentication to function correctly

## Networking

### NSX-V networking

NSX-V is architected so that a single NSX-V manager platform is tied to a single vCenter Server instance. It provides networking services to applications running within a vSphere environment.

Utilizing the NSX-V networking included in the VCS deployment, we can deploy ICP into a VXLAN overlay network.

ICP is deployed with the default Calico networking stack for Kubernetes, which provides network isolation within your cluster.

Figure 2. ICP with NSX-V networking

![ICP with NSX-V Networking](vcsicp-nsxv-networking.svg)

For more information, see [vCenter Server networking guide](../vcsnsxt/vcsnsxt-intro.html).

### NSX-T networking

NSX-T is architected so that a single networking platform that can connect to any type of application, being virtual machine or container based, running inside or outside a vSphere environment.

ICP provides an option to replace the Calico networking with an NSX-T instance, providing a single location for managing networking and security.

Figure 3. ICP with NSX-T networking

![ICP with NSX-T Networking](vcsicp-icp-nsxt-networking.svg)

### Related links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)
