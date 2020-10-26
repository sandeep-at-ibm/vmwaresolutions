---

copyright:

  years:  2016, 2020

lastupdated: "2020-09-28"

keywords: troubleshooting, SAN health, virtual SAN issue

subcollection: vmwaresolutions

---

{:external: target="_blank" .external}
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# How do I manage Virtual SAN Health alerts and warnings?
{: #trbl_vsan_alerts}
{: troubleshoot}
{: support}

You might see alerts and warnings that relate to Virtual SAN Health issues on the VMware vSphere® Web Client Monitor page.
{: tsSymptoms}

These warnings are non-issues and do not indicate functional problems.
{: tsCauses}

Use the following steps to clear the warnings from the vSphere Web Client:
{: tsResolve}

1. Go to http://partnerweb.vmware.com/service/vsan/all.json and save the JSON file, with the name `all.json`, on your local system.
2. Ensure that you completed the steps in [vCenter console timeout](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_timeout_vc_console).
3. On the details page of the instance, click **vCenter console** and log in to the vSphere Web Client by using the credentials displayed on the {{site.data.keyword.vmwaresolutions_full}} console.
4. On the vSphere web Client, go to **Manage > Settings** and open the **Virtual SAN > Health > HCL Database** section. Click **Update from file**, then upload the `all.json` file that you saved previously.
5. To clear the warnings, go to the **Alarms** pane on the upper right of the vSphere Web Client. Right-click each of the alarms and select **Reset to green**.

For more information, see [How to download offline vSAN HCL file for vSAN Health Check plug-in](https://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:external}.

On the vSAN health page, the following warning might display with the recommendation to Host restart:
{: tsSymptoms}

`vSAN extended configuration in sync.`

The warning is a non-issue and does not indicate functional problems.
{: tsCauses}

Restart the vSAN Health page to resolve the issue.
{: tsResolve}
