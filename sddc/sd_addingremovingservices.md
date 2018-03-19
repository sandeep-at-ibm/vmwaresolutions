---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-17"

---

# Ordering, viewing, and removing services for Cloud Foundation instances

You can order services for your VMware Cloud Foundation instances, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instances.

## Available services for Cloud Foundation instances

With the exception of managed services from IMI (Integrated Management Infrastructure), the service installation and removal process is automated. After you select to install or remove a service, all the procedures for the successful installation or removal of the service are completed automatically.

The following services are available to Cloud Foundation instances.

### FortiGate Security Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Security Appliance (FSA) 300 series devices that can provide firewall, routing, NAT, and VPN services to protect the public network connection to your environment. For more information, see [Managing FortiGate Security Appliance on {{site.data.keyword.cloud}}](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Virtual Appliances that can allow you to reduce risk by implementing critical security controls within your virtual infrastructure. You can now install multiple instances of this service as needed.

When you order this service, configure the following settings:
* **Name**: Specify a unique name for the service instance to distinguish it from the additional service instances that you might install later.
* **Deployment Size**: Select **Small**, **Medium**, or **Large** with different CPU and RAM specifications for the FortiGate Virtual Appliances.
* **Monthly Subscription License Model**: Select **Standard FW**, **Standard FW + UTM**, or **Standard FW + Enterprise** according to your requirements. For more information about what is provided in each license option, click **Learn More** on the **FortiGate Virtual Appliance on IBM Cloud** service card.

For more information, see [Managing FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html).

### F5 on IBM Cloud

This service optimizes performance and ensures availability and security for applications with the F5 BIG-IP Virtual Edition (VE). You can now install multiple instances of this service as needed.

When you order this service, configure the following settings:
* **Name**: Specify a unique name for the service instance to distinguish it from the additional service instances that you might install later.
* **License Model**: Select **Good**, **Better**, or **Best** according to your requirements. For more information about what is provided for each license option, click **Learn More** on the **F5 on IBM Cloud** service card.
* **Maximum Bandwidth**: The maximum data transfer rate for the network connection.

For more information about F5 on {{site.data.keyword.cloud_notm}}, see [Managing F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html).

### HCX on IBM Cloud

This service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

When you order this service, select the **Public endpoint certificate type**. If you select **CA Certificate**, configure the following settings:
* **Certificate Contents**: Enter the contents of the CA certificate.
* **Private Key**: Enter the private key of the CA certificate.
* (Optional) **Password**: Enter the password for the private key if it is encrypted.
* (Optional) **Reenter Password**: Enter the password for the private key again.
* (Optional) **Hostname**: Enter the host name to be mapped to the common name (CN) of the CA certificate. HCX requires the CA certificate to be in a format that is accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).

### KMIP for VMware on IBM Cloud

This service provides lifecycle management for encryption keys that are used by {{site.data.keyword.cloud_notm}} services or customer built-in applications.

When you order this service, configure the following settings:
* **Service Region**: Select the {{site.data.keyword.cloud_notm}} region where your KMIP for VMware {{site.data.keyword.cloud_notm}} service instance is to be hosted.
* **Client SSL Certificate**: This field is optional at the time of initial configuration. You can leave this field blank at this time because the client certificate of the Key Management Server (KMS) in vCenter Server is known after your instance is deployed. But you must enter the cerficate after your instance is deployed, so that your vCenter Server connection to the KMS can be completed successfully.
* **API Key for Service ID**: Enter the API key for the {{site.data.keyword.cloud_notm}} Service ID that is used to access the IBM Key Protect Service instances.
* **Key Protect Instance**: Click **Retrieve** to get a list of all available IBM Key Protect Service instances and then select the one that is used for key management.
* **Customer Root Key**: Click **Retrieve** to get the customer root key that is stored in the IBM Key Protect instance selected above.

### Managed Services from IMI

These services enable IBM Integrated Managed Infrastructure (IMI) to deliver dynamic remote management services for a broad range of cloud infrastructures. For more information, see [Requesting managed services from IMI](../services/managing_imi.html).

### IBM Spectrum Protect Plus on IBM Cloud

This service provides data protection, data reuse, and recovery tools for virtual environments. It can be implemented as a stand-alone solution or integrated with your IBM Spectrum Protect&trade; Plus environment to offload copies for long-term storage and data governance with scale and efficiency.

This service provides data protection for the workload VMs only.

When you order this service, configure the following settings:
* **Number of Storage Volumes**: The number of volumes that meet your storage needs.
* **Storage Size per Volume**: The storage capacity per volume. A minimum of 500 GB per volume is required for management.
* **Storage Performance**: The IOPS (Input/output Operations Per Second) per GB based on your workload requirements.
* If you want to order licenses for IBM Spectrum Protect Plus, specify the **Number of VMs to License** on the **Order Licenses** tab. A minimum of 10 VMs is required for license management.
* If you want to Bring Your Own License (BYOL), click the **IBM Spectrum Protect Plus licenses** tab, and then click **Add files** to upload the IBM Spectrum Protect Plus license files that you own.

For more information, see [Managing IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/managingspp.html).

### Veeam on IBM Cloud

This service integrates seamlessly with your VMware environment to help you manage the backup and restore of all the virtual machines (VMs) in your environment, including the backup and restore of the management components. It can help provide a recovery point objective (RPO) of less than 15 minutes upon configuration for your data.

When you order this service, configure the following settings:
* **Number of VMs to License**: A minimum of 4 VMs is required for license management.
* **Storage Size**: The capacity that meets your storage needs. A minimum of 2,000 GB of storage is required for management. For considerations when estimating storage size, see [Estimating Repository Capacity](https://bp.veeam.expert/resource_planning/repository_planning_sizing.html).
* **Storage Performance**: The IOPS (Input/output Operations Per Second) per GB based on your workload requirements.

For more information, see [Managing Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html).

### Zerto on IBM Cloud

This service provides replication and disaster recovery capabilities to help protect your workloads. For more information, see [Managing Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html).

## Ordering services for Cloud Foundation instances

1. Click **Deployed Instances** from the left navigation pane.
2. Find and click the instance for which you want to install services.
3. Click the **Services** tab and then click the **Add Services** tab.
4. Find the service that you want to install and click **Select Service** on the service card.
5. For each service that you want to install, scroll down and specify the required settings in the corresponding configuration section of the page.
6. After completing all selections and configuration settings for the services that you want, scroll down and click **Install**.
7. In the **Order Summary** window, click the link or links of the terms that apply to the services, and ensure that you agree with the terms before you install the services.
8. Review the estimated cost of the services by clicking the price link under **Estimated Cost**.
9. Click **Place Order**. After your request to install services is accepted, the status of the services is changed to **Installing**.
10. (Supported for F5 on {{site.data.keyword.cloud_notm}} and FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} only) To install additional instances of a service, repeat **Step 4** to **Step 9** for the services that you want. You can only add one service instance at a time.

### Service installation results

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Installed Services** tab with the **Installed** status.

**Important**: After the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service is installed successfully, you can manage and configure firewall rules for the FSA from the FortiGate console. You must ensure that the FSA firewall rules are defined to allow outbound HTTPS (TCP port 443) communications that are initiated by management components such as the IBM CloudDriver virtual machine or Zerto Virtual Manager to communicate with the external management database on {{site.data.keyword.cloud_notm}} over the internet. The outbound HTTPS (TCP port 443) communications originate from the public IP address of the management services VMware NSX Edge Services Gateway (ESG) in your instance.

## Viewing services for Cloud Foundation instances

1. Click **Deployed Instances** from the left navigation pane.
2. Find and click the instance for which you want to view services.
3. Click the **Services** tab.
4. On the **Installed Services** page, find the service that you want to view details for and click **View Details** on the service card.
5. Review the information about the selected service, such as the service status and other details.
6. Depending on the viewed service, you can access the service consoles using the credentials provided on the service page and manage the service from here.

## Removing services for Cloud Foundation instances

1. Click **Deployed Instances** from the left navigation pane.
2. Find and click the instance for which you want to remove services.
3. Click the **Services** tab.
4. On the **Installed Services** page, find the service or the specific instance of a service that you want to remove.
5. Click the overflow menu icon in the upper right of the service card, and then click **Remove Service**.
6. In the **Remove Service** window, review the considerations or warnings if there are any. Click **I Understand**. After your request for service removal is accepted, the service status is changed to **Removing**.

### Service removal results

When the removal of the service is completed successfully, you are notified by email, and the service is removed from the **Installed Services** tab.

**Attention**: You are billed until the end of the {{site.data.keyword.cloud_notm}} billing cycle for the removed services.

## Related links

* [Ordering Cloud Foundation instances](sd_orderinginstance.html)
* [FAQ](../vmonic/faq.html)
