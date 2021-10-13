---

copyright:

  years:  2021

lastupdated: "2021-09-23"

keywords: manage shared resources, view shared virtual data centers details

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Viewing virtual data center details
{: #shared_viewing-vdc-details}

You can view the details of an {{site.data.keyword.cloud}} for VMware® Solutions Shared virtual data center, including property, operating system, resource reservation, private network endpoint, and recommended services that are enabled or available for the virtual data center.

## Procedure to view virtual data center details
{: #shared_viewing-vdc-details-procedure}

1. In the **VMware Solutions Shared** table, click a virtual data center name.
2. Under **Properties**, view the details for the virtual data center.

| Property        | Description       |
|:------------- |:------------- |
| Name | The name of the virtual data center. |
| Type | The virtual data center type. |
| Region | The {{site.data.keyword.cloud_notm}} data center region where your organization is created and the organization password is maintained. |
| Location | The {{site.data.keyword.cloud_notm}} data center where the virtual data center is hosted. |
| ID | The ID of the virtual data center. |
| Creation time | The date and time when the virtual data center was created, which is also when billing starts. |
| Red Hat activation key | The activation key that you use to register the Red Hat virtual machine (VM). |
| Public IP | Every virtual data center comes with five public IP addresses that can be used to connect virtual applications (vApps) and VMs to the internet. |
{: caption="Table 1. Virtual data center property details" caption-side="top"}

### Opening a support ticket for additional IP addresses or subnet
{: #shared_viewing-vdc-details-support}

You can open an {{site.data.keyword.cloud_notm}} Support ticket to request five additional public IP addresses or an entire subnet for your virtual data center. Include the following details in your support ticket.
* Virtual data center region and location
* Organization ID
* Virtual data center name
* Number of additional IPs required
* Specify whether you plan to use the additional IPs by using Network Address Translate through the virtual data center Edge Services Gateway or by directly assigning the IPs to a VM.

For more information about opening a support ticket, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support).

### Viewing virtual data center resource reservation details
{: #shared_viewing-vdc-details-resource}

Review the following information for viewing virtual data center resource reservation details.

Under **Resource Reservation**, view the total reserved virtual CPU (vCPU) and RAM for the virtual data center.

| Resource        | Description       |
|:------------- |:------------- |
| vCPU limit | The limit or reserved amount of vCPU that can be used at any time by the virtual data center.  |
| RAM limit | The limit or reserved amount of memory that can be used at any time by the virtual data center.  |
{: caption="Table 2. Virtual data center resource reservation details" caption-side="top"}

### Viewing virtual data center private network endpoint details
{: #shared_viewing-vdc-details-network}

Review the following information for viewing virtual data center private network endpoint details.

For information about private network endpoint details, see [Procedure to view a private network endpoint for a virtual data center](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-endpoints#shared_viewing-endpoints-procedure).

### Viewing virtual data center recommended services details
{: #shared_viewing-vdc-details-services}

Review the following information for viewing virtual data center recommended services details.

For more information about recommended services details, see [Managing Veeam for VMware Solutions Shared virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_veeam) and [Managing Zerto for VMware Solutions Shared virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_zerto-portal).

## Related links
{: #shared_viewing-vdc-details-related}

* [Resizing virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_resize)
* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide)
* [Deleting VMware Solutions Shared virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_deletinginstance)
* [Viewing the virtual data center summary](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-vdc-summary)
* [Accessing the vCloud Director Management console](/docs/vmwaresolutions?topic=vmwaresolutions-shared_accessing-vcd-console)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){: external}
