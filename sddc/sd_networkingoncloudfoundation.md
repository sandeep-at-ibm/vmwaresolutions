---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-10"

---

# Networking considerations for Cloud Foundation instances

Review the following information for details about networking considerations and requirements for your Cloud Foundation instances. Ensure that you meet the requirements so that your instance functions properly.

## Networking components for Cloud Foundation instances

To review the networking components that are included in your Cloud Foundation instance, see [Cloud Foundation instance components](sd_cloudfoundationoverview.html#cloud-foundation-instance-components).

## Firewall considerations

If you are using NSX Distributed Firewalls (DFW), review the following requirements:
* You must configure rules for all communications from the IBM CloudDriver and the SDDC Manager virtual machines (VMs) to allow all protocols to communicate on the IP addresses `10.0.0.0/8` and `161.26.0.0/16`.
* You must create a DFW rule that allows for HTTPS traffic from the IBM CloudDriver VM to any destination.
* The DFW rule must come before any other rules that would block traffic to or from these VMs.

## Using VMware NSX with your VMs

During Cloud Foundation instance deployment, VMWare NSX is ordered, installed, licensed, and configured in your instance. Also, NSX Manager, NSX Controllers, and NSX Transport Zone are set up, and each ESXi server is configured with the NSX components.

However, if your workload VMs need to communicate with each other and to access the Internet, it is your responsibility to configure NSX for use by your VMs.

For information about how to set up NSX:
* For a primary (single) Cloud Foundation instance, see [Setting up NSX for workload VMs on VMware vCenter Server on IBM Cloud](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* For a multi-site Cloud Foundation instance, see [Securely connect your private VMware workloads in the IBM Cloud](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html).

## Considerations when changing passwords for NSX components

Review the following considerations before you change the passwords for the NSX Manager, NSX Controllers, and NSX Edge:
* Do not change the NSX Manager password. You can find this password on the **Summary** tab of the instance details page in the {{site.data.keyword.vmwaresolutions_short}} console.
* You can change passwords for NSX Controllers. For instructions on how to change passwords for NSX Controllers, see [Change Controller Password]{https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html}.
* Do not change the password for the management VMware NSX Edge Services Gateway (ESG).

## Related links

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/content/architecture/virtVCenterServerPlatform/nsx-esg){:new_window}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
