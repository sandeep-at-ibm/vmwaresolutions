---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Virtual machine vSAN redundancy

When you place a vSphere ESXi host into maintenance mode on a vSAN cluster, you are required to select a data evacuation mode. The selection of the mode can have an impact upon the virtual machines and appliances that are consuming the vSAN datastore:
* A **full data migration** evacuates all data from the host and moves it to the other vSphere ESXi hosts in the vSAN cluster. This evacuation mode results in the largest amount of data transfer and consumes the most time and resources. All the components on the local storage of the selected host are migrated elsewhere in the cluster. When the host enters maintenance mode, all virtual machines and appliances have access to their storage components and are still compliant with their assigned storage policies. Full data evacuation can take a long time and can make the maintenance window for an upgrade long in duration.
* The **ensure accessibility data evacuation** mode is the default option and when the vSphere ESXi host is placed in maintenance mode, vSAN ensures that all accessible virtual machines or appliances on the host remain accessible. As, only partial data evacuation occurs, the virtual machine or appliance might no longer be fully compliant to a VM storage policy during evacuation and it might not have access to all its replicas. If a failure occurs while the host is in maintenance mode and the primary level of failures to tolerate is set to 1, data loss will occur, and the virtual machine or appliance might be unavailable.
* In the **no data migration** mode, vSAN does not evacuate any data from the host whist entering maintenance mode. While this reduces the time to enter maintenance mode and hence reduces the duration of the maintenance window, some virtual machines or appliances might become inaccessible.

This section creates a new virtual machine storage policy that allows the **ensure accessibility data evacuation** mode to be selected to reduce maintenance windows, but reducing the risk that a failure of a host while another is in maintenance mode will make a virtual machine or appliance inaccessible. For any virtual machine or appliance, where becoming non-redundant when a vSAN host is placed into maintenance mode is not acceptable, carry out the following process before carrying out any remediation actions A cluster with at least 6 hosts will be required.

1. Create a new vSAN profile with the settings of RAID 5/6 and FTT =2 (RAID 6), and then apply this policy against the required virtual machines or appliances.

2. Wait until vSAN has completed syncing before initiating any remediation actions. The completion status can be checked by navigating to the **vSAN Virtual Objects monitoring page** for the cluster and reviewing the **Completion Status**.

### Related links

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
