---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-24"

---

# Managing Zerto on IBM Cloud

After the Zerto on {{site.data.keyword.cloud}} service is deployed into your instance, you can configure or update Zerto Virtual Replication, and deploy more Virtual Replication Appliances to newly added ESXi servers.

## Using your own certificate for Zerto

As a best practice, you should use your own SSL certificate for Zerto Virtual Manager (ZVM). After you deployed Zerto on {{site.data.keyword.cloud_notm}}, replace the SSL certificate for ZVM with your own certificate by following the instructions at [How to use a CER SSL Certificate to Replace the Self-Signed Certificate for the ZVM, ZSSP, or ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}.

## Managing the configuration of Zerto replications

To manage the configuration of Zerto replications (such as re-pairing Zerto instances or configuring virtual protection groups to replicate virtual machines), log in to the Zerto Virtual Replication console by using the vCenter credentials with administrator permissions.

If you are replicating between different {{site.data.keyword.cloud_notm}} Zerto instances, you can configure replication directly between the Zerto instances. If you are replicating between the {{site.data.keyword.cloud_notm}} Zerto instance and your own data center, you must install Zerto yourself in your own data center. This instance of Zerto that you install in your own data center can license itself automatically when you pair it with the {{site.data.keyword.cloud_notm}} Zerto instance.

Because Zerto replication does not support Network Address Translation (NAT) traversal, establishing connectivity between the {{site.data.keyword.cloud_notm}} Zerto instance and your own data center might require customization of routes on the Zerto Virtual Manager (ZVM) appliances or Zerto Virtual Replication Appliances (VRAs) on either side, and might also require secure tunneling between the sites. When you are configuring or reconfiguring routes on ZVM appliances, you must ensure that all ZVM appliances can connect successfully to `zerto.com` for usage reporting. You can verify this connection by opening a browser session to `https://www.zerto.com` from the ZVM appliance.

**Note**: The Management VMware NSX Edge Services Gateway (ESG) of Cloud Foundation instances and vCenter Server instances on {{site.data.keyword.cloud_notm}} is preconfigured to allow outbound HTTPS (TCP port 443) communications that originate from ZVM.

## Updating Zerto Virtual Replication

To update Zerto Virtual Replication, log in to the Zerto Virtual Replication console.

## Deploying VRAs to newly added ESXi servers

When you add or remove ESXi servers for the primary cluster of your instance, VRAs are automatically deployed or removed. VRAs are not automatically deployed to ESXi servers in the secondary clusters of your instance, but you can deploy them yourself from the Zerto Virtual Replication console.

### Related links

* [Zerto on {{site.data.keyword.cloud_notm}} overview](addingzertodr.html)
* [Requesting managed services for Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [zerto.com website](https://www.zerto.com){:new_window}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Zerto disaster recovery](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Explanation of Zerto Virtual Replication Alerts](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
