---

copyright:

  years:  2019

lastupdated: "2019-11-07"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Active Directory Domain Services introduction
{: #adds-intro}

{{site.data.keyword.vmwaresolutions_full}} is a deployment service that delivers the automated deployment of a VMware Software Defined Data Center (SDDC), along with optional third-party products, while using IBM Cloud bare metal servers and network. After deployment, the systems are managed by the customer, who is responsible for ongoing software patches and updates. The customer has full access to the systems. For more information, see [Customer Responsibilities](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-responsibility). To enable the deployment lifecycle (additions, removals), {{site.data.keyword.vmwaresolutions_short}} retains userIDs with administrator rights to deploy and configure the SDDC software.

Active Directory (AD) is a foundation of the IT infrastructure for many large enterprises. This document covers best practices for integrating Active Directory Domain Services (AD DS) architecture in {{site.data.keyword.vmwaresolutions_short}}. For the design of AD DS, see [Active Directory Domain Service](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/active-directory-domain-services){:external}. AD serves as a distributed hierarchical data storage for information about corporate IT infrastructure; devices and users, user credentials, and access rights based on group membership. It also includes the Domain Name System (DNS) zones and records.

This document uses the following terms to avoid confusion:

* {{site.data.keyword.vmwaresolutions_short}} infrastructure domain - This domain is configured as part of the automation process when your vCenter Server instance is initially deployed. It is used for the user credentials and service accounts of your system administrators and the computer objects for the underlay connected infrastructure components only. This document describes the components and configuration of this domain and how it can be incorporated in your AD design.
* {{site.data.keyword.vmwaresolutions_short}} workload domain - This term is used for the domain that needs to be designed and implemented by you after the deployment of the vCenter Server instance. This domain becomes the resource domain where your workload VMs computer objects are located and optionally the user credentials and service accounts of your users. This document describes some typical deployment patterns that are used in {{site.data.keyword.vmwaresolutions_short}}.
* Underlay networks - These networks use the IBM Cloud IP address schema. The {{site.data.keyword.vmwaresolutions_short}} automation deploys bare metal servers, physical appliances, Virtual Server Instances (VSI), virtual machines (VMs), and appliances onto these networks. Do not deply customer workload VMs onto these networks. The domain controllers for the {{site.data.keyword.vmwaresolutions_short}} infrastructure domain are connected to these underlay networks.
* Overlay networks - These networks are virtual networks that are enabled by VMware NSX and use your IP address schema. You are free to design your network topology to suit your requirements. Your workload VMs are connected to these networks. If connection to these networks from on-premises is required, then these networks are connected typically through layer 3 IP connectivity over the internet or through Direct-Link connection. The domain controllers for your {{site.data.keyword.vmwaresolutions_short}} workload domain are connected to these overlay networks.

**Next topic:** [Active Directory overview](/docs/services/vmwaresolutions?topic=vmware-solutions-adds-overview)

## Related links
{: #adds-intro-related}

* [Overview of {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
* [Getting started with IBM Cloud for VMware Solutions](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [IBM Cloud for VMware Solutions: Take a look under the hood](/docs/services/vmwaresolutions?topic=vmware-solutions-under_the_hood)
