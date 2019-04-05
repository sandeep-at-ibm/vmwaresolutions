---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Release notes for V2.4
{: #relnotes_v24}

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Spectre and Meltdown remediation
{: #relnotes_v24-spectre}

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715, and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## National Language support
{: #relnotes_v24-nls}

Starting with the V2.4 release, National Language Support (NLS) is available for {{site.data.keyword.vmwaresolutions_short}}.
All features on the console, including the user documentation, are available in multiple languages.

The following languages are supported, in addition to English:
* German
* Spanish
* French
* Italian
* Japanese
* Korean
* Brazilian Portuguese
* Simplified Chinese
* Traditional Chinese

## Skylake Xeon CPU support
{: #relnotes_v24-skylake}

Starting with the V2.4 release, the following new Bare Metal Server CPU models are available for deployment for VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} and VMware vSphere on {{site.data.keyword.cloud_notm}} instances and clusters:

* Dual Intel Skylake Xeon Silver 4110 processor / 16 cores total, 2.1 GHz
* Dual Intel Skylake Xeon Gold 5120 processor / 28 cores total, 2.2 GHz
* Dual Intel Skylake Xeon Gold 6140 processor / 36 cores total, 2.3 GHz

For more information, see the *Bare Metal Server settings* section in [Ordering new vSphere clusters](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings).

## Updates for VMware vCenter Server instances
{: #relnotes_v24-vcs}

### Network File System performance enhancement
{: #relnotes_v24-nfs}

The performance level of 10 IOPS/GB, designed for the most demanding workload types, is no longer limited to specific {{site.data.keyword.CloudDataCent_notm}}, but is now available to all. For more information, see the *Storage* section in [vCenter Server overview](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#technical-specifications-for-vcenter-server-instances).

## Updates for add-on services
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

The current release installs IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1 on all newly deployed instances. For more information about the new features in IBM Spectrum Protect Plus V10.1.1 Patch 1, see [IBM Spectrum Protect Plus updates](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

A new option is now available for you to choose between public network and private network for HCX interconnects when you order this service. For more information, see [Ordering VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering).

## New and updated documentation
{: #relnotes_v24-new-docs}

### Reference architecture documentation
{: #relnotes_v24-ref-archi}

The {{site.data.keyword.vmwaresolutions_short}} architecture document is now available in the *Reference* section of the user documentation. For more information, see [Solution overview](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

### Services documentation
{: #relnotes_v24-docs-services}

The services information is restructured and the navigation is improved to easily locate relevant information when you order services.

For more information, see the following topics:

* [Ordering F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [Ordering FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Ordering FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [Ordering Hytrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Ordering Hytrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [Ordering IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [Ordering Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Ordering Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)

## User interface updates and enhancements
{: #relnotes_v24-ui}

The user interface is updated and provides the following enhancements:

* The add cluster and add service panes now use a page format, with a better organized layout, which allows you to complete tasks more efficiently.
* The functionality of the **Resources** page is enhanced with search, pagination, and sorting features. These improvements allow you to locate your instances quickly.
* The instance detail page now uses a left navigation menu, which allows you to access the instance information easily and quickly.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
