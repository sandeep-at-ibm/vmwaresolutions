---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 HyTrust CloudControl on IBM Cloud
{: #managinghtcc}

要管理 HyTrust CloudControl on {{site.data.keyword.cloud}} 服务 (HTCC)，请通过 {{site.data.keyword.vmwaresolutions_short}} 控制台访问 HTCC WebGUI，或通过 vSphere Web Client 访问 HTCC 控制台。

## 通过 IBM Cloud for VMware Solutions 控制台访问 HyTrust CloudControl WebGUI
{: #managinghtcc-accessing-webgui}

要登录到主或辅助 HTCC 设备的 WebGUI，请使用在 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的 WebGUI 凭证。

## 通过 vSphere Web Client 访问 HyTrust CloudControl 控制台
{: #managinghtcc-accessing-console}

要通过 vSphere Web Client 访问 HTCC 控制台，请使用以下过程：
1. 在 vSphere Web Client 中，找到名为 **CC1** 和 **CC2** 的虚拟机。
2. 右键单击 **CC1** 或 **CC2**，并单击**打开控制台**。
3. 使用可在 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的控制台凭证，登录到控制台。

有关更多信息，请参阅[订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)。

## 为 HyTrust CloudControl VM 启用因特网访问
{: #managinghtcc-internet-access}

对于 HTCC 5.5.1 和更高版本，{{site.data.keyword.vmwaresolutions_short}} 为已启用“回拨”功能的 HyTrust 许可证提供自动更新支持。对于不是仅专用的 vCenter Server 实例，HTCC 使用防火墙和 SNAT（源网络地址转换）规则进行部署，这些规则是在管理服务 ESG **mgmt-nsx-edge** 上定义的。

这些规则允许您为 HyTrust 虚拟机 (VM) 启用因特网访问。如果未启用因特网访问，那么应用于 HTCC 安装的许可证将在一年后到期。

对于仅专用的 vCenter Server 环境，未添加 VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge**，因此未定义防火墙和 SNAT 规则。因此，无法为仅专用实例启用因特网连接，并且 HyTrust 许可证每年到期。{:note}

### 查找已定义的防火墙和 SNAT 规则的过程
{: #managinghtcc-proc-find-firewall}

1. 登录到 VMware vSphere Web Client (FLEX)，并找到 ESG **mgmt-nsx-edge**。
2. 单击**主页 > 联网和安全性 > NSX Edge**。
3. 双击 ESG **mgmt-nsx-edge**，然后单击**管理**选项卡。
4. 转至**防火墙**选项卡并查找 HyTrust 规则。记下源 IP 地址。这些是 HyTrust VM 的 IP 地址。
5. 转至 **NAT** 选项卡并查找为 HyTrust VM 创建的 SNAT 规则。源 IP 地址将与您在上一步中记录的 IP 地址相匹配。

### 启用 HTCC 因特网连接的过程
{: #managinghtcc-enable-internet}

以下步骤适用于更新用于许可证升级的主虚拟机 (VM) 上的 HTCC 网络设置。无需更新辅助 VM 的设置。{:note}

1. 完成上一个过程中的步骤 1-3。
2. 单击**设置**，然后单击**接口**。记下专用上行链路的 IP 地址，这将成为新的缺省网关。
3. 转至 HyTrust CloudControl on IBM Cloud 服务详细信息页面，单击**查看 HTCC Web UI**，然后使用服务详细信息页面中的凭证登录。
4. 记下现有缺省网关。例如，对于 HTCC 5.5.1，单击**配置 > 网络**。记下列出的网关 IP 地址，这将成为静态路由的网关。
5. 添加静态路由。例如，对于 HTCC 5.5.1，单击**配置 > 静态路由**。单击**添加**，输入以下信息，然后单击**确定**。

  ```
  网络地址：10.0.0.0
  掩码：255.0.0.0
  网关：步骤 4 中记下的 IP
  设备：网络 1
  ```

6. 更改缺省网关。例如，对于 HTCC 5.5.1，单击**配置 > 网络**，并将**网关**字段中的 IP 地址替换为您在步骤 3 中记下的地址，然后单击**保存**。

  请确保在更改缺省网关之前设置了静态路由，否则 Web 控制台可能变为不可访问。{:important}

  主 VM 现在就可以访问因特网了。

7. 要确认主 VM 是否具有因特网访问权，请对公共 IP 地址或 Web 站点运行 `ping` 命令。要执行此操作，请返回到 vCenter 并右键单击 **CC1 > 打开控制台**。使用 HyTrust CloudControl on IBM Cloud 服务详细信息页面的控制台凭证登录到控制台。运行 `ping` 命令，如 `ping www.ibm.com`，您应该会立即获得响应。按 `Ctrl + C` 以结束 ping，确保丢包率为 0%。

## 相关链接
{: #managinghtcc-related}

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Web 站点](https://www.hytrust.com/)
