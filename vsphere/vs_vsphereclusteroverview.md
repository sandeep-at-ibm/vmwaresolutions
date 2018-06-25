---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# VMware vSphere on IBM Cloud overview

VMware vSphere on {{site.data.keyword.cloud}} is a streamlined and optimized ordering platform for VMware, which allows you to build your own IBM-hosted VMware environment by customizing and ordering the VMware-compatible hardware based on your selected VMware components.

The {{site.data.keyword.vmwaresolutions_short}} console filters the hardware automatically, based on the VMware components that you select. For example, when creating a new all-flash VMware vSAN cluster, only the hardware that is validated against the [VMware Compatibility Guide](https://www.vmware.com/resources/compatibility/search.php) is presented and a minimum of four ESXi servers is required.

VMware vSphere on {{site.data.keyword.cloud_notm}} does not automate the installation, configuration, and bring-up of the optional VMware components and it allows maximum of flexibility to design and build your hosted VMware environment while incorporating VMware-compatible hardware.

Use this offering to create a new cluster of ESXi servers or scale out an existing cluster of ESXi servers in an {{site.data.keyword.CloudDataCent_notm}}. Depending on the VMware components that you select, you can start with just one ESXi server and then scale the cluster later as needed.

## Components of VMware vSphere on IBM Cloud

Review the components of VMware vSphere on {{site.data.keyword.cloud_notm}}.

**Note**: The availability and pricing of standardized hardware configurations might vary based on the {{site.data.keyword.CloudDataCent_notm}} that is selected for deployment.

### VMware components

Licenses (IBM-provided or BYOL) for the following VMware components:
* VMware vSphere Enterprise Plus 6.0u2 or 6.5u1
* Optional VMware components:
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced, or Enterprise)
   * VMware vSAN (Advanced or Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Bare Metal Server

One or more {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} with with your selected CPU model and RAM size:
* 2-CPU Intel Broadwell generation (Intel Xeon E5-2600 v4 series)
* 2-CPU Intel Skylake generation (Intel Xeon 4100/5100/6100 series)

The options available depend on whether you selected the VMware vSAN component.

In addition, the following disk and networking specifications:
* 10 Gbps dual public and private network uplinks
* One RAID disk controller

### Networking

* Three VLANs (Virtual LANs): one public VLAN and two private VLANs
* (Optional) An HA-pair of FortiGate Security Appliance devices

### Storage

User-customized storage for vSAN configuration when the VMware vSAN component is selected:
* Storage disk options:  960 GB SSD SED, 1.9 TB SSD SED, or 3.8 TB SSD SED
* Disk quantity options: 2, 4, 6, or 8

**Note:** 3.8 TB SSD (Solid State Disk) drives will be supported when they are made generally available in a data center.

## Components of vSphere cluster expansion nodes

Each vSphere cluster expansion node will deploy and incur charges for the following components in your {{site.data.keyword.slportal}} account.

### Hardware for expansion nodes

One IBM Cloud Bare Metal Server with the hardware configuration presented in [Components of VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud).

### Networking for expansion nodes

One IBM Cloud Bare Metal Server with the networking configuration presented in [Components of VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud).

### VMware components for expansion nodes

* One IBM Cloud Bare Metal Server with VMware vSphere Enterprise Plus 6.0u2 or 6.5u1  
* Optional VMware components presented in [Components of VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud).

**Important**: You must manage the ESXi servers, optional VMware components, and additional hardware that are ordered and delivered to your {{site.data.keyword.cloud_notm}} account only from the {{site.data.keyword.slportal}}. After creating a new cluster in the {{site.data.keyword.vmwaresolutions_short}} console, you can return to the console to scale the new cluster using the saved configuration. For more information, see [Scaling existing vSphere clusters](vs_scalingexistingclusters.html).

## Related links

* [VMware vSphere Software Bill of Materials](vs_bom.html)
* [Planning vSphere clusters](vs_planning.html)
* [Ordering vSphere clusters](vs_orderinginstances.html)
* [Scaling existing vSphere clusters](vs_scalingexistingclusters.html)
