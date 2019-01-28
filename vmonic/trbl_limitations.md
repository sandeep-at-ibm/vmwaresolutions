---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-11"

---

{:faq: data-hd-content-type='faq'}

# More limitations and considerations

Review the following considerations and limitations when you work with {{site.data.keyword.vmwaresolutions_full}}.

## Windows automatic installation of updates
{: faq}

The Microsoft Active Directory (AD) / Domain Name Server (DNS) is automatically set up to download the updates only. It does not install these updates or restart automatically. You must install the updates manually and restart at a scheduled time that avoids any interruptions of the ongoing AD server configuration and other backup jobs. To apply Windows updates, install the updates manually.

## Considerations when you choose a root domain name for Cloud Foundation instances

When you choose a domain name during the deployment of a primary or secondary Cloud Foundation instance, you need to verify that the `sddcmanager.<subdomain>` host name does not resolve to an external domain by using the `ping` or `nslookup` commands.

The structure of the Cloud Foundation instance subdomain is `<VCF instance name>.<domain name>`. For example, if your `<domain name>` is `test.local`, and the Cloud Foundation instance name is `mytest`, then the `sddcmanager.mytest.test.local` host name does not resolve to an IP address before it deploys the Cloud Foundation instance. Otherwise, the instance deployment might fail.
