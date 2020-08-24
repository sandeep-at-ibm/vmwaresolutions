---

copyright:

  years:  2019, 2020

lastupdated: "2020-07-21"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Deployment
{: #htdc-hpcs-deployment}

At a high level, there are the following three activities to configure HyTrust DataControl to use Hyper Protect Crypto Services:

* Deploy and configure Hyper Protect Crypto Services.
* Create an IBM Cloud Service ID.
* Deploy and configure HyTrust DataControl.

Detailed instructions for each of these activities are contained within the product information websites. The following information gives an overview of the activities with links to the more detailed step-by-step instructions.

## Hyper Protect Crypto Services
{: #htdc-hpcs-deployment-hpcs}

* Provision an IBM HPCS instance - [Provisioning service instances](/docs/hs-crypto?topic=hs-crypto-provision)
* Set up the IBM HPCS environment:
  * Verify API endpoint.
  * Set up CLI - Install the IBM Cloud CLI, if not already installed. For more information, see [Getting started with the IBM Cloud CLI](/docs/cli?topic=cli-getting-started).
  * Install TKE plug-in - Using the CLI, log in and install the Trusted Key Entry plug-in, `ibmcloud plugin install tke`.
  * Set up local directory for key files - On your local workstation, create a directory, for the primary key part files and signature key part files, which will be named in the variable CLOUDTKEFILES.
* Manage crypto units in a service instance:
  * Display assigned crypto units.
  * Add crypto units - Using the CLI, select the crypto unit so that you can perform operations against it.
* Load primary key - To create and load a primary key into a primary key register, you need to create a signature key so that you can sign the operation of creating the primary key:
  * Create Signature keys - Using the CLI, create a signature key by using a username and password and select the signature key.
  * Manage administrators:
    * Add Administrators - Add an admin user, and signature key, to the crypto unit so it can perform operations.
    * Exit imprint mode - Exit imprint mode as the initial setup is complete.
  * Create primary key parts - It is good practice to create multiple parts of a primary key, split across different people in the enterprise, where these people would need to use their keys at the same time. Create a primary key part, choosing a highly secure password. At least two primary key parts are required, so repeat this process.
  * The two primary key parts and the signature key are on the workstation, in the directory CLOUDTKEFILES. They need to be on the same machine to add the primary key parts to an HSM crypto unit.
  * Load primary key:
    * Load new primary key - Passwords for all three keys will now be required, in practice these will be different passwords, known to different people, and stored on different systems.
    * Commit primary register key - Commit this primary key register. The CLI will prompt for the password for the signature key for the administrator with access to the crypto unit. You should now have a fully-committed primary key.
    * Activate primary key - There are two registers for primary keys in the crypto unit, one for a new key and one for the current key. To activate this primary key, it needs to become the current key. On the IBM Cloud Portal, the HPCS instance manage tab should confirm that the HSM primary key has been configured.
* Create a root key - IBM HPCS uses the recommended envelope encryption mechanism of taking a key that is used to encrypt data, the data encryption key or DEK, and encrypting the key itself with a root key. This root key never leaves the HSM.
  * Using the IBM Cloud Portal, view the IBM Cloud resources, and find your IBM HPCS instance.
  * Click the **Add Key** button and then generate a new root key.
  * Review [Creating root keys](https://cloud.ibm.com/docs/hs-crypto?topic=hs-crypto-create-root-keys) for more information of this step.
* Create a standard key - Perform this operation to [create a standard key](https://cloud.ibm.com/docs/hs-crypto?topic=hs-crypto-create-standard-keys).

## Service ID
{: #htdc-hpcs-deployment-serviceid}

* Create a Service ID. For more information, see [Creating and working with service IDs](/docs/account?topic=account-serviceids).

| Parameter                           | Example                          |
| ----------------------------------- | -------------------------------- |
| Name                                | HPCS01                           |
| Description                         | For HyTrust and HPCS             |
| Group                               | Public Access                    |
| Access policy - Services            | Hyper Protect Crypto Services    |
| Access policy - Region              | Frankfurt                        |
| Access policy - Service Instance ID | Hyper Protect Crypto Services-5c |
| Access policy - Platform access     | Viewer                           |
| Access policy - Service access      | Reader                           |
| API Key - Name                      | HPCSAPI01                        |
| API Key - Description               | For HyTrust and HPCS             |
{: caption="Table 1. Service ID example" caption-side="bottom"}

Copy the API key or click download to save it. You will not be able to view this API key again, and you cannot retrieve it.

## HyTrust DataControl
{: #htdc-hpcs-deployment-htdc}

* Order HyTrust DataControl - [Ordering HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_ordering)
* Update static routes on the HTDC VMs - Review [Managing HyTrust DataControl](/docs/vmwaresolutions?topic=vmwaresolutions-managinghtdc) for further details.
* Configure the Customer ESG to use SNAT to allow communication between VMs to be encrypted connected to the NSX overlay networks and the HyTrust DataControl virtual machines, which are connected to the IBM Cloud underlay network. Review [Add a SNAT rule](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-BEF4D960-5F8A-4DE5-84F6-0160DF916FDA.html){:external} and [Add a firewall rule](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-C7A0093A-4AFA-47EC-9187-778BDDAD1C65.html){:external}.
* Configure HTDC - [HyTrust DataControl Administration Guide](https://docs.hytrust.com/DataControl/Admin_Guide-4.0/Content/OLH-Files/Admin-Guide.htm){:external}
  * Initializing the KeyControl webGUI.
  * Authenticating New KeyControl Nodes.
  * Creating a Cloud Admin User Account.
  * Creating a Cloud VM Set by using an HPCS KEK. A VM must be part of a Cloud VM Set before it can be encrypted. For an HPCS KEK, you must specify the HPCS server information when you create the Cloud VM Set. Select **Use HPCS KEK** from the list and click Save to view the HPCS KEK properties. The following information is required:

| Parameter | Example |
| --------- | ------- |
| HPCS URL - The URL for the IBM HPCS server to be used by the Cloud VM Set. Available from the Manage Instance web page on the IBM Cloud portal. |  `https://api.private.eu-de.hs-crypto.cloud.ibm.com:9133` |
| HPCS API Key - The API key to be used to connect to the IBM HPCS server. The Service ID API Key.  | `rsC_SawDQ0GEOGSjsTXruArwQ9fC73WKv-87dVVTdf_i` |
| HPCS Instance ID - The instance ID for your IBM HPCS server. Available from the Manage Instance web page on the IBM Cloud portal. | `5e03d770-558d-4699-a7c6-8c98a17f5f5a` |
| HPCS Root Key - The Key ID in the IBM HPCS server to be used for generating a KEK. This value is optional. If you do not include the root key, then KeyControl will create one in HPCS. | `121b4f6c-8147-4194-b9c4-367f33fd8555` |
{: caption="Table 2. Cloud VM Set example" caption-side="bottom"}

  * Install the Policy Agent - The HyTrust DataControl Policy Agent is a software module that runs on Windows and Linux operating systems, and which provides encryption of virtual disks and individual files. When a user attempts to access an encrypted disk, the Policy Agent queries HTKC to validate the request, and returns the information to the user if HTKC authorizes the request. A Policy Agent must be installed in each VM, and on each disk, to be encrypted with HTDC.

## Related links
{: #htdc-hpcs-deployment-related}

*  [Getting started with IBM Cloud Hyper Protect Crypto Services](/docs/hs-crypto?topic=hs-crypto-get-started)
*  [HyTrust DataControl overview](/docs/vmwaresolutions?topic=vmwaresolutions-htdc_considerations)
