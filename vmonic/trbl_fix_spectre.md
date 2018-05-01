---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-19"

---

# Addressing Spectre and Meltdown vulnerabilities

To address the Spectre and Meltdown vulnerabilities, you must apply a number of patches in a specific order.

## Updating the firmware

For the most recent information about updating the firmware, see [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/).

## Updating instances that were deployed in V2.0 or later

Instances from V2.0 or later were deployed with VMware vSphere 6.5 and VMware vCenter Server 6.5. Both these software components require patching.

### vCenter Server instances deployed in V2.0 or later

For VMware vSphere 6.5:
* For all your new V2.2 instances, vSphere will be deployed with the ESXi650-201712101-SG patch applied.
* For all your existing instances deployed prior to V2.2, all new clusters and ESXi servers will be updated with the  ESXi650-20171201-SG patch.
* For all your existing ESXi servers, as well as any clusters or ESXi servers that you continue to deploy before you upgrade to V2.2, you must apply the ESXi650-20171201-SG patch from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch).

For VMware vCenter Server 6.5:
* For all your new V2.1 instances, vCenter Server will be deployed with the vCenter 6.5 U1e patch applied.
* For all existing instances deployed prior to V2.1, you must apply the vCenter 6.5 U1e patch from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch).


### Cloud Foundation instances deployed in V2.0 or later

To apply the required patches for VMware vSphere 6.5 and VMware vCenter Server 6.5, you must upgrade your Cloud Foundation instances to the current V2.2 version.

For all your existing instances and ESXi servers, you will be prompted to apply the patches (ESXi650-201712101-SG for vSphere and vCenter 6.5 U1e for vCenter Server) on the **Update and Patch** page from the {{site.data.keyword.vmwaresolutions_short}} console. For more information, see [Applying updates to Cloud Foundation instances](../sddc/sd_applyingupdates.html).

### VMware vSphere clusters deployed in V2.0 or later

For VMware vSphere 6.5, you must apply the ESXi650-201712101-SG patch from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch) to all your vSphere clusters and ESXi servers, newly deployed or existing.

For VMware vCenter Server 6.5, you must apply the vCenter 6.5 U1e patch from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch) to all your vCenter servers, newly deployed or existing.

## Instances that were deployed in V1.9 or earlier

Cloud Foundation and vCenter Server instances, as well as VMware vSphere clusters from V1.9 or earlier, were deployed with VMware vSphere 6.0 and VMware vCenter Server 6.0.

### vCenter Server instances deployed in V1.9 or earlier

For both VMware vSphere 6.0 and VMware vCenter Server 6.0, you must apply the patches (ESXi600-201711101-SG for vSphere and vCenter 6.0 U3d for vCenter Server) from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch) to all your instances and ESXi servers, newly deployed or existing.

### Cloud Foundation instances deployed in V1.9 or earlier

Updates for these instances will be available when the necessary vendor updates upon which these instances depend are released.

### VMware vSphere clusters deployed in V1.9 or earlier

For both VMware vSphere 6.0 and VMware vCenter Server 6.0, you must apply the patches (ESXi600-201711101-SG for vSphere and vCenter 6.0 U3d for vCenter Server) from the [VMware Product Patches site](https://my.vmware.com/group/vmware/patch) to all your vSphere clusters and ESXi servers, newly deployed or existing.

## Related links

* [Applying updates to Cloud Foundation instances](../sddc/sd_applyingupdates.html)
* [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [VMware Product Patches site](https://my.vmware.com/group/vmware/patch)
