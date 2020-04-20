---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-14"

keywords: KMIP for VMware, order KMIP stand-alone, KMIP for VMware configuration

subcollection: vmware-solutions

---

# Ordering KMIP for VMware instances
{: #kmip_standalone_ordering}

You can order a KMIP for VMware instance without associating it to any VMware vCenter Server instance for flexible management of the service and instances.

## Before you begin
{: #kmip_standalone_ordering-req}

Ensure that you completed the following tasks:
* You configured the {{site.data.keyword.cloud}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](/docs/vmwaresolutions?topic=vmware-solutions-useraccount).
* You reviewed all the considerations in [Considerations when installing KMIP for VMware instances](/docs/vmwaresolutions?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations-install).

## Procedure to order KMIP for VMware instances
{: #kmip_standalone_ordering-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
2. Scroll down to the **Services** section, and then click **KMIP for VMware** on the **Security and Compliance** card.
3. On the **KMIP for VMware** page, configure the service settings as required.
4. Click **Provision**.

## KMIP for VMware service configuration
{: #kmip_standalone_ordering-config}

When you order this service, provide the following settings:

### Resource group
{: #kmip_standalone_ordering-resource-group}

Use resource groups to organize the resources in your account for access control and billing purposes. The default resource group in your account is selected by default. You can also select another resource group according to your needs. The resource group that you select cannot be changed after the instance is created.

If **No resource group available** is displayed in this field, contact the account owner to be assigned an Editor or Administrator role on a resource group in the account because you currently do not have the permission to add the instance to any resource group in this account. For more information, see [IAM access](/docs/iam?topic=iam-userroles#platformroles).

### Instance Name
{: #kmip_standalone_ordering-config-instance-name}

The instance name is set to **kmip-_xx_** by default, where _xx_ represents two randomly generated alphabetic characters.

You can also specify a name for your KMIP for VMware instance.

### Service Location
{: #kmip_standalone_ordering-config-service-region}

Select the {{site.data.keyword.cloud_notm}} location where your KMIP for VMware instance is to be hosted.

{{site.data.keyword.cloud_notm}} maintains a highly available KMIP for VMware network service endpoint in each location where the service is available.

| Location         | Endpoints               |
|:---------------|:-----------------------|
| Dallas | <<code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code><br>and<br><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code> |
| Frankfurt | <code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code><br>and<br><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code> |
| London | <code>kmip-1.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code><br>and<br><code>kmip-2.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code> |
| Sydney | <code>kmip-1.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code><br>and<br><code>kmip-2.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code> |
| Tokyo | <code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code><br>and<br><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code> |
| Washington DC | <code>kmip-1.private.us-east.vmware-solutions.cloud.ibm.com:5696</code><br>and<br><code>kmip-2.private.us-east.vmware-solutions.cloud.ibm.com:5696</code> |
{: caption="Table 1. KMIP for VMware network service endpoint locations" caption-side="top"}

### API Key for Service ID
{: #kmip_standalone_ordering-config-api-key}

Enter the API key for the {{site.data.keyword.cloud_notm}} Service ID that is used to access the service instance of Key Protect or Hyper Protect Crypto Services.

### Key Manager Instance
{: #kmip_standalone_ordering-config-key-protect}

Click **Retrieve** to get the list of available key manager instances and select the one to use for key management.

### Customer Root Key
{: #kmip_standalone_ordering-config-root-key}

Click **Retrieve** to get the customer root key that is stored in your selected key manager instance.

## Results
{: #kmip_standalone_ordering-results}

The ordering of the KMIP for VMware instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the order by viewing the instance details.

When the instance is ready to use, the status of the instance is changed to **Installed** and you receive a notification by email.

## What to do next
{: #kmip_standalone_ordering-next}

Add client certificates for the KMIP for VMware instance that you ordered. For more information, see [Adding, viewing, and deleting certificates for KMIP for VMware instances](/docs/vmwaresolutions?topic=vmware-solutions-kmip_standalone_addingdeletingcert).

## Related links
{: #kmip_standalone_ordering-related}

* [Viewing KMIP for VMware instances](/docs/vmwaresolutions?topic=vmware-solutions-kmip_standalone_viewing)
* [Deleting KMIP for VMware instances](/docs/vmwaresolutions?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker events](/docs/vmwaresolutions?topic=vmware-solutions-at-events)
