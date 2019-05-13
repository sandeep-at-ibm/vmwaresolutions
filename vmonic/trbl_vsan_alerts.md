---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

# Virtual SAN Health alerts and warnings
{: #trbl_vsan_alerts}

## Problem
{: #trbl_vsan_alerts-problem}

On the VMware vSphere Web Client **Monitor** page, you might see alerts and warnings that relate to Virtual SAN Health issues.

## Resolution
{: #trbl_vsan_alerts-resolution}

These warnings are non-issues and do not indicate functional problems. However, if you want to clear the warnings from the vSphere Web Client, use the following procedure.

1. Go to http://partnerweb.vmware.com/service/vsan/all.json and save the JSON file, with the name `all.json`, on your local system.
2. Ensure that you completed the steps in [vCenter console timeout](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console).
3. On the details page of the instance, click **vCenter console** and log in to the vSphere Web Client by using the credentials displayed on the {{site.data.keyword.vmwaresolutions_full}} console.
4. On the vSphere Web Client, go to **Manage > Settings** and open the **Virtual SAN > Health > HCL Database** section. Click **Update from file**, then upload the `all.json` file that you saved previously.
5. To clear the warnings, go to the **Alarms** pane on the upper right of the vSphere Web Client. Right-click each of the alarms and select **Reset to green**.

For more information, see [How to download offline vSAN HCL file for vSAN Health Check Plugin](https://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window}.
