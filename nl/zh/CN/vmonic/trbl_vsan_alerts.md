---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, SAN health, virtual SAN issue

subcollection: vmware-solutions


---

# 虚拟 SAN 运行状况警报和警告
{: #trbl_vsan_alerts}

## 问题
{: #trbl_vsan_alerts-problem}

在 VMware vSphere Web Client 的**监视**页面上，可能会看到与虚拟 SAN 运行状况问题相关的警报和警告。

## 解决方法
{: #trbl_vsan_alerts-resolution}

这些警告并不是问题，也并不指示功能性问题。但是，如果要清除 vSphere Web Client 发出的警告，请使用以下过程。

1. 转至 http://partnerweb.vmware.com/service/vsan/all.json，并将名为 `all.json` 的 JSON 文件保存在本地系统上。
2. 确保完成 [vCenter 控制台超时](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console)中的步骤。
3. 在实例的详细信息页面上，单击 **vCenter 控制台**，然后使用 {{site.data.keyword.vmwaresolutions_full}} 控制台上显示的凭证登录到 vSphere Web Client。
4. 在 vSphere Web Client 上，转至**管理 > 设置**，然后打开**虚拟 SAN > 运行状况 > HCL 数据库**部分。单击**通过文件更新**，然后上传先前保存的 `all.json` 文件。
5. 要清除警告，请转至 vSphere Web Client 右上角的**警报**窗格。右键单击每个警报，并选择**重置为绿色**。

有关更多信息，请参阅 [How to download offline vSAN HCL file for vSAN Health Check Plugin](https://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window}。
