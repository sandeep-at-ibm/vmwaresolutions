---

copyright:

  years:  2019

lastupdated: "2019-08-21"

---

# Exporting VMware inventory
{: #vmware-inventory-export}

You can export a vCenter resource inventory into CSV files. The contents of the exported CSV files is used to size a target IBM Cloud for VMware Solutions vCenter Server environment. It can also provide insights to the virtual machines in the source environment to help with migration planning.

## Exporting lists
{: #export-lists}

You can export the contents of an inventory list into a CSV file.

### Procedure to export lists
{: #export-procedure}

1. From the VMware vSphere Web Client, open a list view for an object type, for example, Virtual Machines or Hosts.

    You can access list views of objects from the Global Inventory Lists and the search results.

2. Click the Export icon at the lower right corner of a Global Inventory or Resources list view. From the vCenter user interface, pressing <CTRL><ALT><7> opens the navigator view.

3. Select each row to be listed in the CSV file for each of the following sections:
    - Global Inventory Lists -> Virtual Machines
    - Resources -> vCenter Servers
    - Resources -> Datacenters
    - Resources -> Hosts
    - Resources -> Clusters
    - Resources -> Resource Pools
    - Resources -> Datastores
    - Resources -> Datastore Clusters
    - Resources -> Networks
    - Resources -> Distributed Port Groups
    - Resources -> Distributed Switches

4. For each of the previous items, click **Export** and save to a file name that is labeled with the contents, as such:
    - Global Inventory Lists -> Virtual Machines
    - Resources -> vCenter Servers -> exportlist-vcenters.csv
    - Resources -> Datacenters -> exportlist-datacenters.csv
    - Resources -> Hosts -> exportlist-hosts.csv
    - Resources -> Clusters -> exportlist-clusters.csv
    - Resources -> Resource Pools -> exportlist-respools.csv
    - Resources -> Datastores -> exportlist-datastores.csv
    - Resources -> Datastore Clusters -> exportlist-dsclusters.csv
    - Resources -> Networks -> exportlist-networks.csv
    - Resources -> Distributed Port Groups -> exportlist-dpgs.csv
    - Resources -> Distributed Switches -> exportlist-dswitches.csv

5. Package all CSV files into a single compressed file, for example, vCenterName-Inventory.zip

6. Use the contents to size the target environment.

## Related links
{:vmware-inventory-export-related}

* [VMware vCenter Server on IBM Cloud with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
