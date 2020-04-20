---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-17"

keywords: release notes, what's new, version 3.3

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V3.3
{: #relnotes_v33}

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## VMware Horizon 7
{: #relnotes_v33-horizon}

VMware Horizon 7 is now available to vCenter Server instances that are deployed in or upgraded to V3.3 or later releases.

This service delivers a seamlessly integrated hybrid cloud for virtual desktops and applications. It combines the enterprise capabilities of the VMware Software-Defined Data Center (SDDC), delivered as a service on {{site.data.keyword.cloud_notm}}, with the market-leading capabilities of VMware Horizon 7 for a simple, secure, and scalable solution.

For more information, see [vCenter Server and Horizon 7 architecture overview](/docs/vmwaresolutions?topic=vmware-solutions-horizon-arch-ovw).

## Updates for VMware vCenter Server instances
{: #relnotes_v33-vcs}

### Customizable hostname prefix in additional clusters
{: #relnotes_v33-cluster}

When you add a cluster to an instance, you can choose to continue to use the default hostname prefix or to specify a new one for easy identification and management.

For more information, see [Adding, viewing, and deleting clusters for vCenter Server instances](/docs/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters-adding-network-interface-settings).

## Updates for add-on services
{: #relnotes_v33-services}

### Updates for HCX
{: #relnotes_v33-hcx-services-mesh}

HCX now uses Multi-Site Services Mesh to provide its services. Multi-Site Services Mesh provides:

* Increased flexibility in the configuration and scalability of HCX.
* Numerous usability improvements, such as deployment diagrams and diagnostic tools.
* Compute and Network profiles that are shareable across multiple sites that are connected to the HCX cloud instance.

The {{site.data.keyword.vmwaresolutions_short}} automation configures the Compute profile and Network profiles on the cloud side HCX instance when it is installed, so the instance is ready for pairings with on-premises data centers.

For more information, see [About the HCX Multi-Site Services Mesh](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-59FC4E76-5DE4-444C-ADDD-50A3D31AA677.html){:external}.

### Updates for Mission Critical VMware on IBM Cloud
{: #relnotes_v33-mission-critical}

The Mission Critical VMware on {{site.data.keyword.cloud_notm}} product name is changed to {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads. For more information, see [{{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads](/docs/vmwaresolutions?topic=vmware-solutions-mcv_overview).

### Updates for NetApp ONTAP Select on IBM Cloud
{: #relnotes_v33-ontap}

Beginning with the V3.3 release, NetApp ONTAP Select is deployed as a partner service through IBM Global Services to provide greater availability, resiliency, and support. For more information, see [NetApp ONTAP Select](/docs/vmwaresolutions?topic=vmware-solutions-netapp).

### Updates for Zerto
{: #relnotes_v33-zerto-version}

This release installs the Zerto 7.0 Update 2 service version on newly deployed instances.

## New and updated documentation
{: #relnotes_v33-updated-doc}

* New parameters are added to the following APIs:
    * Two new parameters `check_price` and `disk_groups` are added to the **Order a new VMware vCenter Server instance or verify the order** API.
    * A new parameter `disk_groups` is added to the **Add a cluster for a specified VMware vCenter Server instance or verify the order** API and the **Add new hosts to a specified cluster** API.

  For more information, see [API reference](https://cloud.ibm.com/apidocs/vmware-solutions).

* The following architecture reference documentation is available in the *Reference* section of the user documentation:
  * [Active Directory Domain Services guide](/docs/vmwaresolutions?topic=vmware-solutions-adds-intro)
  * [vCenter Server and Red Hat OpenShift architecture](/docs/vmwaresolutions?topic=vmware-solutions-vcs-openshift-intro)
  * [vCenter Server and Red Hat OpenShift guide](/docs/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-intro)
  * [vCenter Server and VMware Horizon 7 architecture](/docs/vmwaresolutions?topic=vmware-solutions-horizon-arch-ovw)

* A new topic is available in the *Troubleshooting* section to help you find someone who is an IAM account administrator if you do not have an administrator role and you want to complete an IAM task that requires one. For more information, see [Locating an IAM account administrator](/docs/vmwaresolutions?topic=vmware-solutions-iam_verify_permissions).

## User interface updates and enhancements
{: #relnotes_v33-ui}

The user interface is updated and provides the following enhancements:

* Enhancements are made to the landing page of {{site.data.keyword.vmwaresolutions_short}} console to better assist you in learning and selecting the appropriate offering and services according to your needs. To be specific,
   * The **Getting Started** page is renamed to **Overview**.
   * The deployment offerings are categorized into **Start Provisioning** and **Single-Node Trials**.
   * The add-on services are categorized into **Business Continuity and Migration**, **Security and Compliance**, **Partner Services**, **Management Tools**, and **App Modernization**. Their names are also simplified.
   * A **Learning Resources** section is added.   
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
