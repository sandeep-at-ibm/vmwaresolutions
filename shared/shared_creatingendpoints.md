---

copyright:

  years:  2020, 2021

lastupdated: "2021-06-02"

keywords: VMware Solutions Shared create private network endpoint, VMware Solutions Shared view private network endpoint, VMware Solutions Shared delete private network endpoint

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Using and managing the Private network endpoint service
{: #shared_creatingendpoints}

{{site.data.keyword.cloud}} for VMware® Solutions Shared now supports both public and private network endpoints. The public network endpoints that are provisioned by default are the five public IP addresses that are displayed in the VMware Solutions Shared virtual data center detail page. A private network endpoint allows a customer's {{site.data.keyword.cloud_notm}} account devices or resources to connect to their virtual data centers by using the {{site.data.keyword.cloud}} private network. The **Private network endpoint** service is available and ready-to-use in all provisioned virtual data centers. After it is configured, the service allows your {{site.data.keyword.cloud_notm}} account resources to connect to virtual machines (VMs) in your virtual data center over the {{site.data.keyword.cloud_notm}} private network.

Connections to private network endpoints do not require public internet access. A private network endpoint provides a unique IP address that is accessible to you without a VPN connection. Private network endpoints support one-way traffic from {{site.data.keyword.cloud_notm}} account resources to the VMs in your virtual data center.

Service charges are incurred only if you choose to use the service.
{:note}

## Before you create a private network endpoint
{: #shared_creatingendpoints-before}

* If you have an {{site.data.keyword.cloud_notm}} Direct Link on your account, you must establish a tunnel between the cross-connect router and the customer edge to have access to the virtual data center.
* You can order only one private network endpoint per virtual data center.
* If you want to change the device type of your private network endpoint, you must first delete the existing private network endpoint. Then, create a new private network endpoint with the new device type.
* You can simultaneously make resource updates to your virtual data center while you create or delete a private network endpoint.

## System settings
{: #shared_creatingendpoints-sys-settings}

When you create a private network endpoint, you must specify the following settings.

### Device type
{: #shared_creatingendpoints-sys-settings-device}

Select from the following device type options:

* Multi-tenant
* Dedicated with 1 Gbps uplinks
* Dedicated with 10 Gbps uplinks

You are not charged for the multi-tenant option.
{:note}

### Allowlisted IP addresses and subnets
{: #shared_creatingendpoints-sys-settings-ip-subnet}

Add the IP addresses or subnets you want to have access to the private network endpoint.

## Monthly cost
{: #shared_creatingendpoints-cost}

Based on your selected configuration for the private network endpoint, the estimated monthly cost is instantly generated and displayed.

You can also add the provisioned resources to the {{site.data.keyword.cloud_notm}} estimate tool, by clicking **Add to estimate**. The tool is useful if you want to estimate the price of the selected VMware Solutions Shared resources together with other {{site.data.keyword.cloud_notm}} resources that you might consider purchasing.

## Procedure to create a private network endpoint for virtual data centers
{: #shared_creatingendpoints-add-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **VMware Solutions Shared** table, click the virtual data center where you want to create a private network endpoint.
3. Under **Private network endpoint** on the virtual data center details page, click **Create a private network endpoint**.
4. Complete the following configuration in the **Create new private network endpoint** pane.
  1. Select the device type.
  2. Provide the IP addresses or subnets to allowlist.
  3. Click **Create**.

For more information about creating a private network endpoint and to review an example of a successful configuration, see [Order a Private Network Endpoint (PNE) to connect your IBM account to your IBM VMWare Solutions Shared virtual datacenter](https://mlwiles.github.io/vmwaresolutions/vcd/order-pne/){:external}.

### Results after you create a private network endpoint for virtual data centers
{: #shared_creatingendpoints-add-procedure-results}

1. The status of the private network endpoint is changed to **Creating**.
2. When the private network endpoint is created, the status changes to **ReadyToUse**.

## Procedure to create and connect an IPsec tunnel over a private network endpoint
{: #shared_creatingendpoints-ipsec-tunnel}

After you create a private network endpoint for your virtual data center, you can use the private network endpoint to create an IPsec tunnel between your IBM account and the virtual data center. For more information, see [IPsec Tunnel over IBM Private Network Endpoint (PNE)](https://mlwiles.github.io/vmwaresolutions/vcd/ipsec-pne/){:external}.

## Procedure to view a private network endpoint for virtual data centers
{: #shared_creatingendpoints-view-procedure}

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **VMware Solutions Shared** table, click an virtual data center name.
3. View the **Private network endpoint** details. Expand **Allow listed IPs and subnets** to view the list of IP addresses and subnets that you added when you ordered the private network endpoint.

| Item          | Description   |
|:------------- |:------------- |
| Device type | The multi-tenant or dedicated device and size. |
| Service network IP | The IP address for the service network. |
| Private network IP | The IP address for the private network. |
| Service address | The IP address that your virtual data center is allocated for {{site.data.keyword.cloud_notm}} access. |
| Allow listed IPs and subnets | The list of all allow listed IP addresses and subnets for the virtual data center. |
{: caption="Table 1. Private network endpoint items" caption-side="top"}

The **Service address** is available only when you select the *Dedicated 1 Gbps uplinks* or *Dedicated 10 Gbps uplinks* **Device type** when you order the private network endpoint.
{:note}

The private network endpoint can have different statuses.

| Status        | Description   |
|:------------- |:------------- |
| Creating | The private network endpoint is being created. |
| Ready to use | The private network endpoint is operating. |
| Deleting | The private network endpoint is being deleted. |
| Deleted | The private network endpoint is deleted. |
{: caption="Table 2. Status descriptions for a private network endpoint" caption-side="top"}

## Procedure to modify a private network endpoint for virtual data centers
{: #shared_creatingendpoints-modify}

You must open an IBM Support ticket to modify or adjust allow listed IP addresses or subnets. Provide the following details when you contact IBM Support:
* The IP addresses and subnets that you want to add or delete
* The virtual data center ID

For more information about submitting an IBM Support ticket, see [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support).

## Procedure to delete a private network endpoint from a virtual data centers
{: #shared_creatingendpoints-delete}
{: help}
{: support}

You might want to delete a private network endpoint from a virtual data center when it's no longer needed.

1. From the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. In the **VMware Solutions Shared** table, click the virtual data center that you want to delete the private network endpoint from.
3. In the **Private network endpoint** section, click **Delete**.
4. Confirm that you want to delete the private network endpoint.

## Related links
{: #shared_creatingendpoints-related}

* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide)
* [VMware Solutions Shared pricing](/docs/vmwaresolutions?topic=vmwaresolutions-shared_pricing)
