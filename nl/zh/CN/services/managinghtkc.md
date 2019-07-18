---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: HTKC WebGUI, HTKC console, enable internet HTKC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 HyTrust KeyControl on IBM Cloud
{: #managinghtkc}

要管理 HyTrust KeyControl on {{site.data.keyword.cloud}} 服务 (HTKC)，请通过 {{site.data.keyword.vmwaresolutions_short}} 控制台访问 HTKC Web GUI，或通过 vSphere Web Client 访问 HTKC 控制台。

## 通过 IBM Cloud for VMware Solutions 控制台访问 HyTrust KeyControl Web GUI
{: #managinghtkc-accessing-webgui}

要登录到主或辅助 HTKC 设备的 Web GUI，请使用在 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的 WebGUI 凭证。

## 通过 vSphere Web Client 访问 HyTrust KeyControl 控制台
{: #managinghtkc-accessing-console}

要通过 vSphere Web Client 访问 HTKC 控制台，请使用以下过程：
1. 在 vSphere Web Client 中，找到名称以 **KC1** 和 **KC2** 开头的虚拟机，其匹配的 IP 地址可在 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到。
2. 右键单击 **KC1** 或 **KC2**，并单击**打开控制台**。
3. 使用可在 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的控制台凭证，登录到控制台。

有关更多信息，请参阅[订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)。

## 为 HyTrust KeyControl VM 启用因特网访问
{: #managinghtkc-internet-access}

对于 HTKC 4.3.2 和更高版本，{{site.data.keyword.vmwaresolutions_short}} 为已启用“回拨”功能的 HyTrust 许可证提供自动更新支持。对于不是仅专用的 vCenter Server 实例，HTKC 使用防火墙和 SNAT（源网络地址转换）规则进行部署，这些规则是在管理服务 ESG **mgmt-nsx-edge** 上定义的。

这些规则允许您为 HyTrust 虚拟机 (VM) 启用因特网访问。如果未启用因特网访问，那么应用于 HTKC 安装的许可证将在一年后到期。

对于仅专用的 vCenter Server 环境，未添加 VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge**，因此未定义防火墙和 SNAT 规则。因此，无法为仅专用实例启用因特网连接，并且 HyTrust 许可证每年到期。
{:note}

### 查找已定义的防火墙和 SNAT 规则的过程
{: #managinghtkc-proc-find-firewall}

1. 登录到 VMware vSphere Web Client (FLEX)，并找到 ESG **mgmt-nsx-edge**。
2. 单击**主页 > 联网和安全性 > NSX Edge**。
3. 双击 ESG **mgmt-nsx-edge**，然后单击**管理**选项卡。
4. 转至**防火墙**选项卡并查找 HyTrust 规则。记下源 IP 地址。这些是 HyTrust VM 的 IP 地址。
5. 转至 **NAT** 选项卡并查找为 HyTrust VM 创建的 SNAT 规则。源 IP 地址将与您在上一步中记录的 IP 地址相匹配。

### 启用 HTKC 因特网连接的过程
{: #managinghtkc-proc-enable-internet}

1. 完成上一个过程中的步骤 1 - 3。
2. 单击**设置**，然后单击**接口**。记下专用上行链路的 IP 地址。此地址将成为新的缺省网关。
3. 单击**主页 > 主机和集群**，然后找到 HyTrust VM。右键单击其中一个 VM，然后单击**打开控制台**。
4. 使用可在 {{site.data.keyword.vmwaresolutions_short}} 控制台上的 HyTrust KeyControl on IBM Cloud 服务详细信息页面上找到的控制台凭证，登录到控制台。
5. 要从 VM 获取当前缺省网关 IP 地址，请单击**管理网络设置 > 显示当前网络配置**。记下为**网关**列出的 IP 地址。此地址将成为用于静态路由的网关。
6. 要为 VM 设置静态路由，请单击**管理网络设置 > 管理静态路由 > 添加静态路由**。将**网络地址**设置为 `10.0.0.0/8`，将**网关**设置为上一步中记录的 IP 地址。
7. 要设置 VM 的缺省网关 IP，请单击**管理网络设置 > 更改当前网络配置**。如果收到警告消息，请单击**确定**，然后单击**定制配置**。将**网关**字段设置为步骤 2 中记录的专用上行链路 IP 地址，然后单击**确定**。等待安装新的网络配置并重新启动网络服务。
8. 如果看到要求 HyTrust SecureOS 重新认证的消息，请单击**确定**，然后输入此安装的其他 HyTrust VM 的 IP 地址。如果要求您输入 16 个字符的口令，请按 Enter 键以返回到主菜单。验证当前网络配置以确保应用更改。
9. 要确认 VM 是否有权访问因特网，请对公共 IP 地址或 Web 站点执行 ping 操作。单击**管理网络设置 > 网络诊断工具 > 测试其他服务器的入站端口**。输入公共 Web 站点地址（例如，`www.ibm.com`），单击**确定**，输入 `80 443` 作为端口（或要测试的其他任何端口），您应该立即获得响应，其中显示入站端口以及类似于 `80 (OK) 443 (OK)` 的消息。
10. 对另一个 HyTrust VM 重复步骤 3 - 9。

## 相关链接
{: #managinghtkc-related}

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust Web 站点](https://www.hytrust.com/){:external}
