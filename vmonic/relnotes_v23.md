---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}


# Release notes for V2.3
{: #relnotes_v23}

This release includes new features, component updates, usability enhancements, and bug fixes. For a list of fixed issues in different releases, known issues with the product, and tips to use {{site.data.keyword.vmwaresolutions_full}}, see [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## Spectre and Meltdown remediation
{: #relnotes_v23-spectre}

{{site.data.keyword.vmwaresolutions_short}} has released patches from VMware in response to the vulnerabilities known as Spectre and Meltdown (CVE-2017-5753, CVE-2017-5715 and CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## VMware vCenter Server on IBM Cloud with Hybridity Bundle
{: #relnotes_v23-vcs-hybrid}

This release introduces the VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle offering. The vCenter Server with Hybridity Bundle is a hosted private cloud that helps quickly and easily extend your on-premises infrastructure into the cloud. The VMware environment is based on IBM-provided VMware Software Defined Data Center licenses and includes the VMware HCX on {{site.data.keyword.cloud_notm}} service that easily and securely connects a vSphere 5.0+ environment on-premises with {{site.data.keyword.cloud_notm}} sites for seamless infrastructure hybridity and true application mobility.

The HCX on {{site.data.keyword.cloud_notm}} service is available only through the vCenter Server with Hybridity Bundle instance. You can upgrade your existing vCenter Server instance to a vCenter Server with Hybridity Bundle instance after first applying the base vCenter Server V2.3 software update. For more information, see [Applying updates to vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_applyingupdates).

For more information about the vCenter Server with Hybridity Bundle, see [vCenter Server with Hybridity Bundle overview](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_hybrid_overview).

## Delete cluster support for vCenter Server and Cloud Foundation instances
{: #relnotes_v23-delete-cluster}

You can now delete clusters from an instance without having to delete the entire instance. For clusters deployed in V2.2 or earlier instances, you must upgrade the instance to V2.3 to be able to delete the clusters that you added to the instance.

For more information, see [Adding, viewing, and deleting clusters for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters).

## Updates for VMware vCenter Server instances
{: #relnotes_v23-vcs}

This release applies the following upgrades and improvements:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 with patch level ESXi650-201803001 applied)
*	VMware vCenter Server 6.5 Update 1g

Starting with the V2.3 release, the following new CPU models are available for deployment when you choose the **Customized** Bare Metal setting:
* Dual Intel Xeon Silver 4110 processor / 16 cores total, 2.1 GHz
* Dual Intel Xeon Gold 5120 processor / 28 cores total, 2.2 GHz

For more information, see the following topics:

* [Ordering vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [Adding, viewing, and deleting clusters for vCenter Server instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)

## Updates for VMware Cloud Foundation instances
{: #relnotes_v23-vcf}

This release applies the following upgrades and improvements:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 with patch level ESXi650-201803001 applied)
*	VMware vCenter Server 6.5 Update 1g
*	VMware NSX for vSphere 6.3.5

## Updates for add-on services
{: #relnotes_v23-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v23-htcc}

The HyTrust CloudControl on {{site.data.keyword.cloud_notm}} service is now available to VMware Cloud Foundation instances and VMware vCenter Server instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.3 or later releases. The service enforces and controls compliance against security standards, and provides role-based access control (RBAC). When combined with HyTrust DataControl, the service can ensure that virtual machines and workload data do not leave a particular region, cluster, or ESXi server within the {{site.data.keyword.cloud_notm}} data center.

You can order instances with the service included when you order your instance, or add this service to your existing instances later.

For more information, see the following topics:
* [Components and considerations for HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-htcc_considerations)
* [Managing HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managinghtcc)

### HyTrust DataControl on IBM Cloud
{: #relnotes_v23-htdc}

The HyTrust DataControl on {{site.data.keyword.cloud_notm}} service is now available to VMware Cloud Foundation instances and VMware vCenter Server instances that are running vSphere 6.5 and that are deployed in or upgraded to V2.3 or later releases. The service offers strong encryption with integrated key management to secure workloads throughout their lifecycles. The service can provide encryption at both the operating system level and data level, which means that any directory, folder, or file within a workload can be encrypted and decrypted.

You can order instances with the service included when you order your instance, or add this service to your existing instances later.

For more information, see the following topics:
* [Components and considerations for HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-htdc_considerations)
* [Managing HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managinghtdc)

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v23-spp}

The current release installs IBM Spectrum Protect&trade; Plus V10.1.1, as the default backup service, on all newly deployed instances. For more information about the new features in IBM Spectrum Protect Plus V10.1.1, see [IBM Spectrum Protect Plus updates](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:external}.

## New and updated documentation
{: #relnotes_v23-new-docs}

A new IBM Developer recipe is available with step-by-step instructions on how to add storage to IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment. For more information, see [Adding storage to IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## User interface updates and enhancements
{: #relnotes_v23-ui}

The user interface is updated and provides the following enhancements:
* **Consistency**: The user interface now provides a consistent look and feel with other services on {{site.data.keyword.cloud_notm}}.
* **Ease of access**: You can now access the VMware offerings directly from the {{site.data.keyword.cloud_notm}} **Catalog**.
* **Streamlined and simplified ordering experience**: You can now complete ordering a VMware instance and deploying its add-on services in a single interface. In addition, estimated cost is calculated and shown instantly in the same interface so that you can adjust your configuration based on your cost plan.
* The option to Bring Your Own License (BYOL) when ordering instances or adding clusters is not available to Business Partner users.
* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
