---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

# 使用 VMware vSphere Web Client 部署 OVF 文件
{: #trbl_deploy_ovf}

## 解决方法
{: #trbl_deploy_ovf-resolution}

要使用 vSphere Web Client 部署 OVF（开放式虚拟化格式）文件，请使用以下过程：
1. 在尝试部署 OVF 文件之前，请将以下主机信息添加到 `/etc/hosts` 文件：

   * Platform Services Controller (PSC) 的主机信息
   * VMware ESXi 服务器的主机信息
   * vCenter 的主机信息
2. 检查 `/etc/hosts` 文件以确保成功添加了这些信息。hosts 文件的示例可能类似于以下列表：

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. 确保您有权访问 {{site.data.keyword.slportal_full}} 中所有必需的 VPN（虚拟专用网）。在此示例中，VPN 为 `10.131.7.xx` 和 `10.131.9.xxx`。
4. 登录数据中心的 VPN。
5. 单击 **vCenter** 以访问 vSphere Web Client。
6. 右键单击主机并部署 `.ovf` 文件。
