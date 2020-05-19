---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}


# Release notes for V2.4
{: #relnotes_v24}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Spectre and Meltdown remediation
{: #relnotes_v24-spectre}

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715, and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Globalization
{: #relnotes_v24-nls}

Starting with the V2.4 release, globalization is available for {{site.data.keyword.vmwaresolutions_short}}.
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

Starting with the V2.4 release, the following new bare metal server CPU models are available for deployment for VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} and VMware vSphere on {{site.data.keyword.cloud_notm}} instances and clusters:

* Dual Intel Skylake Xeon Silver 4110 processor / 16 cores total, 2.1 GHz
* Dual Intel Skylake Xeon Gold 5120 processor / 28 cores total, 2.2 GHz
* Dual Intel Skylake Xeon Gold 6140 processor / 36 cores total, 2.3 GHz

## Updates for VMware vCenter Server instances
{: #relnotes_v24-vcs}

### Network File System performance enhancement
{: #relnotes_v24-nfs}

The performance level of 10 IOPS/GB, designed for the most demanding workload types, is no longer limited to specific {{site.data.keyword.cloud_notm}} data centers, but is now available to all.

## Updates for add-on services
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

The current release installs IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1 on all newly deployed instances.

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

A new option is now available for you to choose between public network and private network for HCX interconnects when you order this service.

## New and updated documentation
{: #relnotes_v24-new-docs}

### Reference architecture documentation
{: #relnotes_v24-ref-archi}

The {{site.data.keyword.vmwaresolutions_short}} architecture document is now available in the *Reference* section of the user documentation.

### Services documentation
{: #relnotes_v24-docs-services}

The services information is restructured and the navigation is improved to easily locate relevant information when you order services.

## User interface updates and enhancements
{: #relnotes_v24-ui}

The user interface is updated and provides the following enhancements:

* The add cluster and add service panes now use a page format with a better organized layout so that you can complete tasks more efficiently.
* The **Resources** page is enhanced with search, pagination, and sorting features so that you can locate your instances quickly.
* The instance detail page now uses a left navigation menu so that you can access the instance information easily and quickly.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
