---

copyright:

  years:  2020, 2021

lastupdated: "2021-01-15"

keywords: release notes, what's new, version 3.7

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Release notes for V3.7
{: #relnotes_v37}

This release includes new features, component updates, usability enhancements, and bug fixes.

## Updates for VMware Solutions Shared
{: #relnotes_v37-shared}

This release applies the following upgrades when you order VMware Solutions Shared instances.

### Private Network Endpoint add-on service
{: #relnotes_v37-shared-private-endpoints}

VMware Solutions Shared now supports both public and private network endpoints. Use the Private Network Endpoint service to access your virtual data center from your {{site.data.keyword.cloud}} infrastructure account resources. Connections to private network endpoints do not require public internet access.

### Off-site copy mode availability for Veeam Availability Suite
{: #relnotes_v37-shared-veeam-second-copy}

Veeam Availability Suite v10 provides off-site copy mode for new and existing VMware Solutions Shared instances. You must contact IBM support to enable off-site copy.

## Updates for VMware Solutions Dedicated
{: #relnotes_v37-dedicated}

This release applies the following updates when you order VMware Solutions Dedicated instances.

### IBM Cloud for VMware Regulated Workloads
{: #relnotes_v37-fss}

(Updated on July 14, 2020) You can now order {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads instances through predefined vCenter Server instance configurations as part of your vCenter Server order flow. The {{site.data.keyword.cloud_notm}} for VMware Regulated Workloads architecture is an extension of the vCenter Server offering, which enhances the basic vCenter Server architecture to deliver a secure, high-performance platform.

### New SAP-certified Cascade server support
{: #relnotes_v37-sapserver}

Starting with the v3.7 release, the following new {{site.data.keyword.cloud_notm}} bare metal server CPU models are available for deployment for VMware vCenter Server instances and VMware vSphere clusters with vSphere 6.7:
* Dual Intel Xeon Gold 5218 processor / 32 cores total, 2.30 GHz / 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB
* Dual Intel Xeon Gold 6248 processor / 40 cores total, 2.50 GHz / 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB
* Dual Intel Xeon Platinum 8280M processor / 56 cores total, 2.70 GHz / 192 GB, 384 GB, 768 GB, 1.5 TB, 3 TB
* Quad Intel Xeon Platinum 8280M processor / 112 cores total, 2.70 GHz / 3 TB, 6 TB

The new servers are not supported for **Chennai 01**.

### Removed support for Broadwell servers
{: #relnotes_v37-broadwell-eos}

Broadwell servers are no longer available for new or existing deployments of vCenter Server and vSphere instances and clusters.

### Minimum number of bare metal servers
{: #relnotes_v37-vcs-2-bms}

For vCenter Server with NSX-T instances, you can now order an instance with only two bare metal servers for the management cluster. The minimum RAM size for the instance to function properly is 192 GB.

Configurations with only two servers in the management cluster are not recommended for production use.

## Updates for add-on services
{: #relnotes_v37-services}

This release provides the following service versions on newly deployed instances:

* Caveonix RiskForesight v2.3. A dedicated private subnet with 32 IP addresses is now ordered, rather than 64 IP addresses.
* HyTrust DataControl v5.1.1
* Red Hat OpenShift for VMware v4.4.5.
* Zerto 7.5 Update 3. The host Windows platform for the Zerto VSI is now Windows Server 2019 Standard Edition (64-bit).

You can now install the following services on vCenter Server with NSX-T instances:

* Caveonix RiskForesight
* HyTrust DataControl
* Veeam

### Updates for HyTrust CloudControl
{: #relnotes_v37-services-htcc}

Starting with the v3.7 release, additional configuration is done for HyTrust CloudControl v6.1 for vCenter Server with NSX-T instances.

### Known issues with Red Hat OpenShift for VMware
{: #relnotes_v37-services-redhat-openshift}

You might encounter the following problems, which cause false alarms about unhealthy etcd members. Review the following problem reports and update the cluster, as needed, when the problems have been fixed:
* [Red Hat Bugzilla – Bug 1832986 - EtcdMembersDegraded false alarms](https://bugzilla.redhat.com/show_bug.cgi?id=1832986){:external}
* [Red Hat Bugzilla – Bug 1838781 - EtcdMembersDegraded false alarms](https://bugzilla.redhat.com/show_bug.cgi?id=1838781){:external}

### Updates for Veeam
{: #relnotes_v37-services-veeam}

Veeam v9.5u4b has known vulnerabilities and it is no longer installed with new VMware Solutions deployments. However, if you installed the service in a previous release, you can continue to use Veeam v9.5u4b.
{:note}

The new Veeam Availability Suite v10 known as Veeam v10 is now installed.

There are two deployment types for Veeam v10:
* Windows Server VM on the management cluster
* Single public Windows VSI

The host Windows platform for the Veeam VSI is now Windows Server 2019 Standard Edition (64-bit).

The process of installing and deleting Veeam licenses is different starting with Veeam v10, in that the license is not deleted when you delete Veeam 10. To avoid being charged, you must delete the license yourself.

## Security and compliance updates
{: #relnotes_v37-security}

In June 2020, IBM Cloud for VMware Solutions acquired a PCI DSS attestation of compliance (AOC), validated by a third-party Qualified Service Assessor (QSA). For more information about IBM Cloud compliance and trust certifications, see  [IBM Cloud compliance programs](https://www.ibm.com/cloud/compliance).

## Updates to REST APIs
{: #relnotes_v37-api}

* Application programming interfaces (APIs) are now available for the following services: Caveonix RiskForesight, HyTrust DataControl (HTDC), and Veeam.
* Various updates are made to the [VMware Solutions API](https://cloud.ibm.com/apidocs/vmware-solutions) and the [VMware Solutions Shared API](https://cloud.ibm.com/apidocs/vmware-solutions-shared).

## New and updated documentation
{: #relnotes_v37-updated-doc}

* (Updated on July 14, 2020) The [{{site.data.keyword.cloud_notm}} for VMware Regulated Workloads reference architecture](/docs/vmwaresolutions?topic=vmwaresolutions-fss-overview) is updated.
* Documentation about the responsibilities of IBM vs the customer's is available at [Understanding your responsibilities when using VMware Solutions](/docs/vmwaresolutions?topic=vmwaresolutions-understand-responsib).
* Documentation is available about the access type that {{site.data.keyword.cloud_notm}} Support has to your environment and the steps that you can take to limit the access, if required. For more information, see [{{site.data.keyword.cloud_notm}} Support access](/docs/vmwaresolutions?topic=vmwaresolutions-data-security-mng-data#data-security-ibm-access).
* Documentation is now available about the various ports that are  used in VMware Solutions. The documentation includes details about:
  * VLANs and subnets that are used
  * Ports for deployment and day 2 operations
  * Ports that VMware uses
  * Ports that the optional services use, such as Caveonix RiskForesight, Juniper vSRX, and Veeam.
* New FAQ about VMware Solutions Shared is now provided at [General FAQ about VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions-shared). Various updates to the existing FAQs have also been made.

## User interface updates and enhancements
{: #relnotes_v37-ui}

The user interface is updated and provides the following enhancements:

* Various error messages and tooltip enhancements are available to assist you in selecting the appropriate setting on the user interface.
