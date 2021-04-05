---

copyright:

  years:  2016, 2021

lastupdated: "2021-03-17"

keywords: troubleshooting, Windows automatic installation, Windows updates

subcollection: vmwaresolutions


---

{:faq: data-hd-content-type='faq'}

# More limitations and considerations
{: #trbl_limitations}

Review the following considerations and limitations when you work with {{site.data.keyword.vmwaresolutions_full}}.

## Automatic installation of updates from Windows Update
{: #trbl_limitations-windows-update}
{: faq}

The Microsoft® Active Directory™ (AD) Domain Services server is automatically set up to download the updates only. It does not install these updates or restart automatically. You must install the updates manually and restart at a scheduled time that avoids any interruptions of the ongoing AD server configuration and other backup jobs. To apply Windows® updates, install the updates manually.
