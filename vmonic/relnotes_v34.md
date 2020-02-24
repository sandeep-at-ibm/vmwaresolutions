---

copyright:

  years:  2016, 2019

lastupdated: "2019-12-16"

keywords: release notes, what's new, version 3.4

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V3.4
{: #relnotes_v34}

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## IBM Security Services for SAP
{: #relnotes_v34-ss-sap}

IBM Security Services for SAP is now available as a service for your VMware instances in {{site.data.keyword.cloud_notm}}. IBM Security Services for SAP offers a cybersecurity solution to automate the monitoring and protection of SAP applications on IBM {{site.data.keyword.cloud_notm}}, and to keep workloads compliant and secure from inside and outside threats.

For more information, see [IBM Security Services for SAP](/docs/services/vmwaresolutions?topic=vmware-solutions-managing-ss-sap).

## PrimaryIO Hybrid Cloud Data Management
{: #relnotes_v34-hdm}

PrimaryIO Hybrid Cloud Data Management (HDM) is now available for your VMware instances in {{site.data.keyword.cloud_notm}}. This service delivers a seamlessly integrated hybrid cloud for virtual desktops and applications. It provides the enterprise capabilities of the VMware Software-Defined Data Center (SDDC) delivered as a service on {{site.data.keyword.cloud_notm}}, for a simple, secure, and scalable solution.

For more information, see [PrimaryIO Hybrid Cloud Data Management](/docs/services/vmwaresolutions?topic=vmware-solutions-managing_pio).

## Red Hat OpenShift for VMware
{: #relnotes_v34-openshift}

* Red Hat OpenShift for VMware on {{site.data.keyword.cloud_notm}} is now available to vCenter Server instances that are deployed in or upgraded to V3.4 or later releases. This service brings together the power of the Red Hat OpenShift Container Platform and the VMware software-defined data center stack. The service offers a consistent hybrid cloud foundation for building and scaling containerized applications.

  For more information, see [Red Hat OpenShift for VMware overview](/docs/services/vmwaresolutions?topic=vmware-solutions-ocp_overview).

* For the Single-node Trial for Migration and App Modernization, Red Hat OpenShift Version 4.2 replaces {{site.data.keyword.cloud_notm}} Private Hosted. For more information, see [Single-node Trial for Migration and App Modernization overview](/docs/services/vmwaresolutions?topic=vmware-solutions-cloud_modern_bundle_overview).

## IBM Cloud Private Hosted - Deprecated
{: #relnotes_v34-icpdeprecated}

The {{site.data.keyword.cloud_notm}} Private Hosted service has been deprecated and replaced by Red Hat OpenShift for VMware. For more information, see [Red Hat OpenShift for VMware overview](/docs/services/vmwaresolutions?topic=vmware-solutions-ocp_overview).
{:deprecated}

## Updates for VMware vCenter Server instances
{: #relnotes_v34-vcs}

This release applies the following upgrades and improvements for newly deployed instances, clusters, and hosts:

* VMware vSphere ESXi 6.5 EP 15 (build 6.5.0-14320405). Applicable only to 6.5u3 hosts, and not to 6.5u2 hosts.
* VMware vCenter Server Appliance 6.5 Update 3d (build 6.5.0-14836121)
* VMware Platform Services Controller 6.5 Update 3d (build 6.5.0-14836121)

For more information, see [vCenter Server Bill of Materials](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_bom).

### VMware vSphere 6.5u3 support
{: #relnotes_v34-vcs-vsphere}

VMware vSphere 6.5u3 replaces vSphere 6.5u2 for all new VMware vCenter Server instance orders. vSphere 6.7u2 is also available. For more information, see [Ordering vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance).

### Add cluster enhancements
{: #relnotes_v34-vcs-add-cluster}

* You can now simultaneously add or remove a cluster while another cluster is being created or removed.
* A minimum of 1 ESXi server is required when you add a cluster to a vCenter Server instance.

For more information, see [Adding, viewing, and deleting clusters for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters).

## Updates for add-on services
{: #relnotes_v34-services}

This release installs the following service versions on newly deployed instances:

* F5 BIG-IP 15.0.1
* HyTrust CloudControl 5.6
* HyTrust DataControl 5.0.1
* HyTrust KeyControl 5.0.1
* IBM Spectrum Protect Plus 10.1.5

### Updates for IBM Cloud for VMware Mission Critical Workloads
{: #relnotes_v34-mission-critical}

Enterprises can now migrate VMware-based Mission Critical Workloads to the {{site.data.keyword.cloud_notm}}, capable of delivering maximum uptime in six multi-zone regions (MZRs) around the world.

You can deploy VMware’s stretched vSAN clusters in an automated and self-managed infrastructure allowing you the flexibility to control and manage all aspects of your solution set. This option is available in on-demand ordering from the **vCenter Server** page on the {{site.data.keyword.vmwaresolutions_short}} console.

You can deploy a fully managed solution delivered by IBM Services. {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads delivers greater availability, resiliency, and support than many enterprises currently maintain on premises.  This option is available as a fully and coordinated engagement with IBM Services teams.

For more information, see:

* [Ordering multi-zone stretched clusters](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv_ordering)
* [Requesting managed {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv_ordering-managed)

## New and updated documentation
{: #relnotes_v34-updated-doc}

* Technical documentation is available in the *Reference* section for {{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads and ordering multi-zone stretch clusters. For more information, see [{{site.data.keyword.cloud_notm}} for VMware Mission Critical Workloads architecture overview](/docs/services/vmwaresolutions?topic=vmware-solutions-mcv-archi-overview).
* The [Upgrading VMware NSX](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade-procedure-nsx) section of **Upgrading vCenter Server vSphere software from VMware vSphere 6.5 to 6.7** has additional information to help you determine whether you must upgrade your current version of NSX. You might have to upgrade NSX so it’s compatible with VMware vCenter Server 6.7.
* The [Technical specifications for IBM Spectrum Protect Plus](/docs/services/vmwaresolutions?topic=vmware-solutions-spp_considerations#spp_considerations-specs) are updated.
* The [vCenter Server and vSRX guide](/docs/services/vmwaresolutions?topic=vmware-solutions-vcsvsrx-intro) is now available in the *Reference* section of the user documentation.
* (Updated on Dec 20, 2019) The [HyTrust DataControl with IBM Cloud Hyper Protect Crypto Services architecture
](/docs/services/vmwaresolutions?topic=vmware-solutions-htdc-hpcs-encryption-overview) is now available in the *Reference* section of the user documentation.
* Various [REST API documentation](https://cloud.ibm.com/apidocs/vmware-solutions) updates are made.

## User interface updates and enhancements
{: #relnotes_v34-ui}

The user interface is updated and provides the following enhancements:

* The following enhancements are made to the landing page of {{site.data.keyword.vmwaresolutions_short}} console to better assist you in learning and selecting the appropriate offering and services according to your needs:
   * The **Single-Node Trials** section is removed.
   * A new **Featured Services** section is added, where you can find the services and single-node trial offerings that are highlighted.
   * In the **Services** section:
     * A new **Featured Workload Solutions** category is added.
     * The previous **Partner Services** category is renamed to **Professional Services**, and the previous **App Modernization** category is renamed to **Transformation and Modernization of VMware Applications**.
* The following enhancements are made to the **Network Interface** section when you order vCenter Server instances or vCenter Server with NSX-T instances and when you add clusters for these instances:
   * A new **Allocate a new one** option is added to the drop-down lists on the **Select Existing VLANs** tab.
   * The **Public VLAN** and **Public Primary Subnet** drop-down lists are removed from the **Select Existing VLANs** tab for the **Private Network Only** option.
* A new **Allocate a new one** option is added to the **Public VLAN**, **Private VLAN**, and **Secondary Private VLAN** drop-down lists on the **Select Existing VLANs** tab when you order vSphere clusters.
* A new **Save Configuration** button is added to the **Order Summary** pane of the ordering page for vCenter Server instances, by using which you can now save your instance settings as a configuration template without placing an order. You can manage the configuration templates by further editing or deleting them as well.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
