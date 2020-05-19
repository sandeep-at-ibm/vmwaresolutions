---

copyright:

  years:  2016, 2020

lastupdated: "2020-03-30"

keywords: KMIP certificate, add certificate KMIP, delete certificate KMIP

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Adding, viewing, and deleting certificates for KMIP for VMware instances
{: #kmip_standalone_addingdeletingcert}

After your KMIP for VMware instance is ready, you must add certificates to it. When you no longer need a certificate, delete it from your instance.

## Procedure to add certificates to KMIP for VMware instances
{: #kmip_standalone_addingdeletingcert-add}

1. In the {{site.data.keyword.vmwaresolutions_full}} console, click **Resources** from the left navigation pane.
2. Scroll down to the **KMIP for VMware Instances** table, click the instance that you want to add certificates for.
3. Click **Add**.
4. In the **Add Client SSL Certificate** window, enter the certificate name and content.

   The certificate name cannot be reused within your selected instance. The certificate content must be valid and contain the BEGIN CERTIFICATE and END CERTIFICATE tags, and the certificate cannot be reused in the selected region where the instance is deployed.
   {:note}
5. Click **Add**.

## Procedure to view certificates for KMIP for VMware instances
{: #kmip_standalone_addingdeletingcert-view}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. Scroll down to the **KMIP for VMware Instances** table, click the instance to view the certificates for.
3. View the list of added certificates under the **Client SSL Certificates** section.
4. To view the content of a particular certificate, click **Download**.

## Procedure to delete certificates from KMIP for VMware instances
{: #kmip_standalone_addingdeletingcert-delete}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane.
2. Scroll down to the **KMIP for VMware Instances** table, click the instance that you want to delete certificates from.
3. In the **Client SSL Certificates** table, locate the certificate that you want to delete and click the **Delete** icon.

   The client immediately loses access to all keys for the purpose of encrypting and decrypting data or backup data. For the client to gain access again, you must add the client SSL certificate again.
   {:note}

## Related links
{: #kmip_standalone_addingdeletingcert-related}

* [Viewing KMIP for VMware instances](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_viewing)
* [Ordering KMIP for VMware instances](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_ordering)
* [Deleting KMIP for VMware instances](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_deleting)
* [Activity Tracker events](/docs/vmwaresolutions?topic=vmwaresolutions-at-events)
