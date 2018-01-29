---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-25"

---

# Ordering, viewing, and removing services for Cloud Foundation instances

You can order services for your VMware Cloud Foundation instances, such as a disaster recovery solution. When you no longer need these services, you can remove them from your instances.

## Available services for Cloud Foundation instances

With the exception of managed services from IMI (Integrated Management Infrastructure), the service installation and removal process is automated. After you select to install or remove a service, all the procedures for the successful installation or removal of the service are completed automatically.

The following services are available to Cloud Foundation instances.

### Managed Services from IMI

These services enable IBM Integrated Managed Infrastructure (IMI) to deliver dynamic remote management services for a broad range of cloud infrastructures. For more information, see [Requesting managed services from IMI](../services/managing_imi.html).

### Veeam on IBM Cloud

This service integrates seamlessly with your VMware environment to help you manage the backup and restore of all the virtual machines (VMs) in your environment, including the backup and restore of the management components. It can help provide a recovery point objective (RPO) of less than 15 minutes upon configuration for your data.

This service is initially configured to back up the management VMs immediately upon deployment for your instance. If you do not order this service, there is no backup of the management VMs.

When you order this service, configure the following settings:
* **Number of VMs to License**: A minimum of 4 VMs for licenses is required for management.
* **Storage Size**: The capacity that meets your storage needs. A minimum of 2,000 GB of storage is required for management. For considerations when estimating storage size, see [Estimating Repository Capacity](https://bp.veeam.expert/resource_planning/repository_planning_sizing.html).
* **Storage Performance**: The IOPS (Input/output Operations Per Second) per GB based on your workload requirements.

For more information about Veeam on {{site.data.keyword.cloud_notm}}, see [Managing Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html).

### F5 on IBM Cloud

This service optimizes performance and ensures availability and security for applications with the F5 BIG-IP Virtual Edition (VE). You can now install multiple instances of this service as needed.

When you order this service, configure the following settings:
* **Name**: Specify a unique name for the service instance to distinguish it from the additional service instances that you might install later.
* **License Model**: Select **Good**, **Better**, or **Best** according to your requirements. For more information about what is provided for each license option, click **Learn More** on the **F5 on IBM Cloud** service card.
* **Maximum Bandwidth**: The maximum data transfer rate for the network connection.

For more information about F5 on {{site.data.keyword.cloud_notm}}, see [Managing F5 on {{site.data.keyword.cloud_notm}}](../services/managing_f5.html).

### FortiGate Security Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Security Appliance (FSA) 300 series devices that can provide firewall, routing, NAT, and VPN services to protect the public network connection to your environment. For more information, see [Managing FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html).

### FortiGate Virtual Appliance on IBM Cloud

This service deploys an HA-pair of FortiGate Virtual Appliances that can allow you to reduce risk by implementing critical security controls within your virtual infrastructure. You can now install multiple instances of this service as needed.

When you order this service, configure the following settings:
* **Name**: Specify a unique name for the service instance to distinguish it from the additional service instances that you might install later.
* **Deployment Size**: Select **Small**, **Medium**, or **Large** with different CPU and RAM specifications for the FortiGate Virtual Appliances.
* **Monthly Subscription License Model**: Select **Standard FW**, **Standard FW + UTM**, or **Standard FW + Enterprise** according to your requirements. For more information about what is provided in each license option, click **Learn More** on the **FortiGate Virtual Appliance on IBM Cloud** service card.

For more information, see [Managing FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html).

### HCX on IBM Cloud

This service can seamlessly extend the networks of on-premises data centers into {{site.data.keyword.cloud_notm}}, which allows virtual machines (VMs) to be migrated to and from the {{site.data.keyword.cloud_notm}} without any conversion or change.

When you order this service, select the **Public endpoint certificate type**. If you select **CA Certificate**, configure the following settings:
* **Certificate Contents**: Enter the contents of the CA certificate.
* **Private Key**: Enter the private key of the CA certificate.
* (Optional) **Password**: Enter the password for the private key if it is encrypted.
* (Optional) **Reenter Password**: Enter the password for the private key again.
* (Optional) **Hostname**: Enter the host name to be mapped to the common name (CN) of the CA certificate. HCX requires the CA certificate to be in a format that is accepted by NSX Edge. For more information about NSX Edge certificate formats, see [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).

### Zerto on IBM Cloud

This service provides replication and disaster recovery capabilities to help protect your workloads. For more information, see [Managing Zerto on {{site.data.keyword.cloud_notm}}](../services/managingzertodr.html).

## Procedure

1. Click **Deployed Instances** from the left navigation pane.
2. Click the instance for which you want to install or view services, or from which you want to remove services.
3. Click the **Services** tab.
4. To install services, complete the following steps:
   1. On the **Add Services** tab, find the services that you want to install and click **Select Service** on the service cards.
   2. If you want to install Veeam on {{site.data.keyword.cloud_notm}}, specify the required settings in the **Configure Veeam on IBM Cloud** area.
   3. If you want to install F5 on {{site.data.keyword.cloud_notm}}, specify the required settings in the **Configure F5 on IBM Cloud** area.
   4. If you want to install FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, specify the required settings in the **Configure FortiGate Virtual Appliance on IBM Cloud** area.
   5. If you want to install HCX on {{site.data.keyword.cloud_notm}}, specify the required settings in the **Configure HCX on IBM Cloud** area.
   6. After completing all selections for the services you want, scroll down on the **Add Services** page and click **Install**.
   7. In the **Order Summary** window, click the link or links of the terms that apply to the services, and ensure that you agree with the terms before you install the services.
   8. Review the estimated cost of the services by clicking the price link under **Estimated Cost**.
   9. Click **Place Order**. After your request to install the services is accepted, the status of the services is changed to **Installing**.
5. To install additional instances of a service, which is only applicable to the F5 on {{site.data.keyword.cloud_notm}} service and the FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} service, complete the following steps:
   1. Click the **Installed Services** tab. Ensure that the existing instances of the service are in the **Installed** status.
   2. Click the **Add Services** tab, find the service, and then click **Select Service** on the service card.
   3. If you want to install additional instances of F5 on {{site.data.keyword.cloud_notm}}, specify the required settings in the **Configure F5 on IBM Cloud** area.
   4. If you want to install additional instances of FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, specify the required settings in the **Configure FortiGate Virtual Appliance on IBM Cloud** area.
   5. Scroll down on the **Add Services** page and click **Install**.
   6. In the **Order Summary** window, click the link or links of the terms that apply to the service instance, and ensure that you agree with the terms before you install the service instance.
   7. Review the estimated cost of the services by clicking the price link under **Estimated Cost**.
   8. Click **Place Order**. After your request to install the service instance is accepted, the status of the service instance is changed to **Installing**.
   9. You can only add one instance for a service at a time. Repeat steps **5a** to **5h** to install all additional instances for a service.
6. To view details about a service, complete the following steps:
   1. On the **Installed Services** tab, find the service that you want to view details for and click **View Details** on the service card.
   2. Review the information about the selected service, such as the service status and so on.
   3. For Veeam on {{site.data.keyword.cloud_notm}}, you can access the Veeam console with the credentials provided on this page by using Remote Desktop Protocol (RDP). For more information, see [Accessing the Veeam console by using RDP](../services/managingveeam.html#accessing-the-veeam-console-by-using-rdp).
   4. For F5 on {{site.data.keyword.cloud_notm}}, you can log in to the primary or secondary console with the credentials provided on this page to manage the service by clicking **View BIG-IP Primary Web UI** or **View BIG-IP Secondary Web UI**.
   5. For FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, you can log in to the FortiGate 300 series console with the credentials provided on this page to manage the service by clicking **View FortiGate Console**.
   6. For FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, you can log in to the FortiGate console of the primary or secondary FortiGate VM with the credentials provided on this page to manage the service by clicking **View Primary Web UI** or **View Secondary Web UI**.
   7. For HCX on {{site.data.keyword.cloud_notm}}, you can log in to the HCX management consoles with your vCenter credentials or with the credentials provided on this page to manage the service by clicking **View HCX Cloud Console** or **View HCX Manager Admin Console**.
   8. For Zerto on {{site.data.keyword.cloud_notm}}, you can log in to the Zerto console with your vCenter credentials to manage the service by clicking **View Zerto Console**.
7. To remove a service or an instance of a service, complete the following steps:
   1. On the **Installed Services** tab, find the service or the specific instance of a service that you want to remove.
   2. Click the overflow menu icon in the upper right of the service card, and then click **Remove Service**.
   3. In the **Remove Service** window, review the considerations or warnings if there are any. Click **I Understand**. After your request for service removal is accepted, the service status is changed to **Removing**.

## Results

When the installation of the service is completed successfully, you are notified by email, and the service is displayed on the **Installed Services** tab with the **Installed** status.

**Important**: After the FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} service is installed successfully, you can manage and configure firewall rules for the FSA from the FortiGate console. You must ensure that the FSA firewall rules are defined to allow outbound HTTPS (TCP port 443) communications that are initiated by management components such as the IBM CloudDriver virtual machine or Zerto Virtual Manager to communicate with the external management database on {{site.data.keyword.cloud}} over the internet. The outbound HTTPS (TCP port 443) communications originate from the public IP address of the management services VMware NSX Edge Services Gateway (ESG) in your instance.

When the removal of the service is completed successfully, you are notified by email, and the service is removed from the **Installed Services** tab.

**Attention**: You are billed until the end of the {{site.data.keyword.cloud_notm}} billing cycle for the removed services.

## Related links

* [Ordering Cloud Foundation instances](sd_orderinginstance.html)
* [FAQ](../vmonic/faq.html)
