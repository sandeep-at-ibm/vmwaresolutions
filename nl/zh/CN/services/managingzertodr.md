---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 Zerto on IBM Cloud

Zerto on {{site.data.keyword.cloud}} 服务部署到实例后，可以配置或更新 Zerto Virtual Replication，并将更多的 Virtual Replication 设备部署到新添加的 ESXi 服务器。

## 使用您自己的 Zerto 证书

作为最佳实践，请对 Zerto Virtual Manager (ZVM) 使用您自己的 SSL 证书。部署了 Zerto on {{site.data.keyword.cloud_notm}} 后，请将 ZVM 的 SSL 证书替换为您自己的证书。有关更多信息，请参阅[如何使用 CER SSL 证书来替换 ZVM、ZSSP 或 ZCM 的自签名证书](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}。

## 管理 Zerto 复制的配置

要管理 Zerto 复制的配置，请使用具有管理员许可权的 vCenter 凭证登录到 Zerto Virtual Replication 控制台。例如，重新配对 Zerto 实例或配置虚拟保护组以复制虚拟机。

要在不同的 {{site.data.keyword.cloud_notm}} Zerto 实例之间进行复制时，可以直接在 Zerto 实例之间配置复制。如果要在 {{site.data.keyword.cloud_notm}} Zerto 实例与您自己的数据中心之间进行复制，那么您必须自行在自己的数据中心内安装 Zerto。此实例与 {{site.data.keyword.cloud_notm}} Zerto 实例配对时，可以自动对自身进行许可。

Zerto 复制不支持网络地址转换 (NAT) 遍历。在 {{site.data.keyword.cloud_notm}} Zerto 实例与您自己的数据中心之间建立连接可能需要对任一端的 Zerto Virtual Manager (ZVM) 设备或 Zerto Virtual Replication 设备 (VRA) 上的路由进行定制。建立连接还可能需要在站点之间进行安全隧道连接。在 ZVM 设备上配置或重新配置路由时，必须确保所有 ZVM 设备都可以成功连接到 `zerto.com` 以进行使用情况报告。可以通过从 ZVM 设备建立到 `https://www.zerto.com` 的浏览器会话，以验证此连接。

{{site.data.keyword.cloud_notm}} 上的 Cloud Foundation 实例和 vCenter Server 实例的“管理 VMware NSX Edge 服务网关 (ESG)”已预配置为允许源自 ZVM 的出站 HTTPS（TCP 端口 443）通信。
{:note}

## 更新 Zerto Virtual Replication

要更新 Zerto Virtual Replication，请登录到 Zerto Virtual Replication 控制台。

## 将 VRA 部署到新添加的 ESXi 服务器

为实例的主集群添加或除去 ESXi 服务器时，将自动部署或除去 VRA。VRA 不会自动部署到实例的辅助集群中的 ESXi 服务器。您可以自行在 Zerto Virtual Replication 控制台中部署这些 VRA。

### 相关链接

* [Zerto on {{site.data.keyword.cloud_notm}} 概述](addingzertodr.html)
* [请求 Zerto on {{site.data.keyword.cloud_notm}} 的受管服务](managing_zerto_services.html)
* [zerto.com Web 站点](https://www.zerto.com){:new_window}
* [Zerto 技术文档](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Zerto 灾难恢复](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Zerto Virtual Replication 警报的说明](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
