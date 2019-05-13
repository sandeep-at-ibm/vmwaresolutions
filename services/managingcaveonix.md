---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix}

## Accessing the Caveonix RiskForesight console
{: #managingcaveonix-access-console}

To manage the Caveonix RiskForesight on {{site.data.keyword.cloud}} service, you must access the Caveonix RiskForesight console by completing the following steps:

1. Use the IBM Cloud infrastructure VPN or a jump server to allow access to the IP address of the Caveonix RiskForesight virtual machine (VM). You can find the IP address on the service details page for Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} in the {{site.data.keyword.vmwaresolutions_short}} console. To be specific:
   1. Create a VPN password from the {{site.data.keyword.cloud_notm}} infrastructure customer portal.
   2. Log in to the data center VPN portal by using the {{site.data.keyword.cloud_notm}} infrastructure VPN credentials.
   3. Add the IP address and the host name mapping into the `hosts` file from your local computer. Use the following format:

      ```javascript
      RiskForesight_VM_IP_Address      RiskForesight_FQDN
      ```
2. To access the Caveonix RiskForesight console, click **View RiskForesight Console** on the service details page for Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, and then log in by using the credentials listed on the same service details page.

## Applying updates to Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix-update}

You are responsible for maintaining Caveonix RiskForesight to keep it updated to the most recent version. You can download the required updates from the [Caveonix Service Provider Portal](https://support.caveonix.com).

## Updating Caveonix RiskForesight licenses

The Caveonix RiskForesight license is valid for one year. You can update the Caveonix RiskForesight license when it expires by using the following procedure:
1. Order a new Caveonix RiskForesight license and copy it to the Caveonix RiskForesight console. For more information, see [Procedure to order Caveonix RiskForesight licenses](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure).
2. Delete the expired license from the **Caveonix RiskForesight Licenses** table in the {{site.data.keyword.vmwaresolutions_short}} console. For more information, see [Procedure to delete Caveonix RiskForesight licenses](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete).

## Related links
{: #managingcaveonix-related}

* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Ordering Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
