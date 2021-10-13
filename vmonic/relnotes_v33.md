---

copyright:

  years:  2016, 2021

lastupdated: "2021-09-20"

keywords: release notes, what's new, version 3.3

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Release notes for V3.3
{: #relnotes_v33}

This release includes new features, component updates, usability enhancements, and bug fixes.

## VMware Horizon 7
{: #relnotes_v33-horizon}

VMware Horizon 7 is now available to vCenter Server instances that are deployed in or upgraded to V3.3 or later releases.

This service delivers a seamlessly integrated hybrid cloud for virtual desktops and applications. It combines the enterprise capabilities of the VMware Software-Defined Data Center (SDDC), delivered as a service on {{site.data.keyword.cloud_notm}}, with the market-leading capabilities of VMware Horizon 7 for a simple, secure, and scalable solution.

## Updates for VMware vCenter Server instances
{: #relnotes_v33-vcs}

### Customizable hostname prefix in additional clusters
{: #relnotes_v33-cluster}

When you add a cluster to an instance, you can choose to continue to use the default hostname prefix or to specify a new one for easy identification and management.

## Updates for add-on services
{: #relnotes_v33-services}

### Updates for HCX
{: #relnotes_v33-hcx-services-mesh}

HCX now uses Multi-Site Services Mesh to provide its services. Multi-Site Services Mesh provides:

* Increased flexibility in the configuration and scalability of HCX.
* Numerous usability improvements, such as deployment diagrams and diagnostic tools.
* Compute and Network profiles that are shareable across multiple sites that are connected to the HCX cloud instance.

The {{site.data.keyword.vmwaresolutions_short}} automation configures the Compute profile and Network profiles on the cloud side HCX instance when it is installed, so the instance is ready for pairings with on-premises data centers.

### Updates for Mission Critical VMware on IBM Cloud
{: #relnotes_v33-mission-critical}

The Mission Critical VMware on {{site.data.keyword.cloud_notm}} product name is changed to {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads.

### Updates for NetApp ONTAP Select on IBM Cloud
{: #relnotes_v33-ontap}

Beginning with the V3.3 release, NetApp ONTAP Select is deployed as a partner service through IBM Global Services to provide greater availability, resiliency, and support.

### Updates for Zerto
{: #relnotes_v33-zerto-version}

This release installs the Zerto 7.0 Update 2 service version on newly deployed instances.

## New and updated documentation
{: #relnotes_v33-updated-doc}

* New parameters are added to the following APIs:
    * Two new parameters `check_price` and `disk_groups` are added to the **Order a new VMware vCenter Server instance or verify the order** API.
    * A new parameter `disk_groups` is added to the **Add a cluster for a specified VMware vCenter Server instance or verify the order** API and the **Add new hosts to a specified cluster** API.

* The following architecture reference documentation is available in the *Reference* section of the user documentation:
   * [Active Directory Domain Services guide](/docs/vmwaresolutions?topic=vmwaresolutions-adds-intro)
   * [vCenter Server and Red Hat OpenShift architecture](/docs/vmwaresolutions?topic=vmwaresolutions-vcs-openshift-intro)
   * [vCenter Server and Red Hat OpenShift guide](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-intro)
   * [vCenter Server and VMware Horizon 7 architecture](/docs/vmwaresolutions?topic=vmwaresolutions-horizon-arch-ovw)

* A new topic is available in the *Troubleshooting* section to help you find someone who is an IAM account administrator if you do not have an administrator role and you want to complete an IAM task that requires one.

## User interface updates and enhancements
{: #relnotes_v33-ui}

The user interface is updated and provides the following enhancements:

* Enhancements are made to the landing page of {{site.data.keyword.vmwaresolutions_short}} console to better assist you in learning and selecting the appropriate offering and services according to your needs. To be specific,
   * The **Getting Started** page is renamed to **Overview**.
   * The deployment offerings are categorized into **Start Provisioning** and **Single-Node Trials**.
   * The add-on services are categorized into **Business Continuity and Migration**, **Security and Compliance**, **Partner Services**, **Management Tools**, and **App Modernization**. Their names are also simplified.
   * A **Learning Resources** section is added.   
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
