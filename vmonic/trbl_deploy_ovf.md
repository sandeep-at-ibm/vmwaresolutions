---

copyright:

  years:  2016, 2020

lastupdated: "2020-03-18"

keywords: troubleshooting, OVF deploy, how to deploy OVF file

subcollection: vmwaresolutions

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Deploying an OVF file using the VMware vSphere Web Client
{: #trbl_deploy_ovf}
{: troubleshoot}
{: support}

## Resolution
{: #trbl_deploy_ovf-resolution}

To deploy an OVF (Open Virtualization Format) file by using the vSphere Web Client, use the following procedure:
{: tsResolve}

1. Before you attempt to deploy an OVF file, add the following host information to the `/etc/hosts` file:

   * Host information for Platform Services Controller (PSC)
   * Host information for VMware ESXi server
   * Host information for vCenter
2. Check your `/etc/hosts` file to ensure that this information is successfully added. An example of a hosts file might look like the following list:

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. Ensure that you have access to all the necessary VPNs (Virtual Private Networks) in the {{site.data.keyword.slportal_full}}. In this example, it would be `10.131.7.xx` and `10.131.9.xxx`.
4. Sign in the VPN for your data center.
5. Click **vCenter** to access the vSphere Web Client.
6. Right-click on a host and deploy an `.ovf` file.
