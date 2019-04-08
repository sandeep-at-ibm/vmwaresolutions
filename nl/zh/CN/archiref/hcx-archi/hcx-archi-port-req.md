---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---
# VMware HCX on IBM Cloud 端口访问需求
{: #hcx-archi-port-req}

HCX 必须遍历公用因特网和专用线路，并连接到数据中心组件，例如网络、交换机和端口组。

下表列出了必须打开的端口，只有打开这些端口，Hybrid Cloud Services 虚拟设备才能成功安装。vSphere 环境和 IBM Cloud 环境都必须允许 vSphere 内部部署设备和 IBM Cloud 设备之间进行网络时间协议 (NTP) 时钟同步。UDP 端口 123 必须可由 Hybrid Cloud Services 虚拟设备和网络访问。安装 Hybrid Cloud Services 设备时，可以指定已安装的 NTP 服务器。

表 1. 端口访问需求

|源|目标|端口|协议|用途|服务|
|--------|--------------|------|----------|-----------------|----------|
|HCX|客户 DNS|53|TCP/UDP|名称解析|DNS|
|HCX|IBM Cloud 中的 NSX LB|443|TCP|注册服务|HTTPS|
|HCX|IBM Cloud 中的 vCenter|443|TCP|HCX REST 服务|HTTPS|
|HCX|IBM Cloud 中的 PSC|443|TCP|HCX REST 服务|HTTPS|
|HCX|connect.hcx.vmware.com|443|TCP|注册服务|HTTPS|
|Web 浏览器|HCX|9443|TCP|用于 HCX 系统配置的 HCX 虚拟设备管理界面|HTTPS|
|管理员网络|HCX|22|SSH|管理员通过 SSH 访问 Hybrid Cloud Services|SSH|
|HCX|ESXi 主机|902|TCP|将管理和供应指令从 HCX 发送到 IBM Cloud 中的 ESXi 主机。|内部|
|HCX|vCenter SSO 服务器|7444|TCP|vSphere 查找服务|  |
|HCX|NTP 服务器|123|UDP|时间同步| |
|HCX|Syslog|   |由用户配置|HCX（客户机）和 Syslog 服务器之间的连接。Syslog 端口和协议的值在 vSphere Web Client 中指定。例如，端口 514 用于 UDP 协议。| |
|HCX|云网关|8123|TCP|将基于主机的复制服务指令发送到 Hybrid Cloud Gateway。|HTTP|
|HCX|云网关|9443|TCP|使用 REST API 将管理指令发送到本地 Hybrid Cloud Gateway。|HTTP</br>HTTPS|
|云网关|L2C|443|TCP|L2C 使用与 Hybrid Cloud Gateway 相同的路径时，从云网关向 L2C 发送管理指令。|HTTP</br>HTTPS|
|云网关|L2C|8443|TCP|L2C 使用备用数据路径时，发送从云网关到 L2C 的双向管理指令。|HTTP</br>HTTPS|
|L2C|L2C（远程）|443|TCP|L2C 使用备用数据路径时，发送从云网关到 L2C 的双向管理指令。|HTTP</br>HTTPS|
|云网关|ESXi 主机|80，902|TCP|管理和 OVF 部署|内部|
|ESXi 主机|云网关|31031，44046|TCP|基于主机的内部复制流量|内部|
|云网关|ESXi 主机|8000|TCP|vMotion（零停机时间迁移）|  |
|云网关（本地）|云网关</br>（远程）|4500|UDP|因特网密钥交换 (IKEv2)，用于封装双向隧道的工作负载|IPSEC|
|云网关（本地）|云网关</br>（远程）|500|UDP|用于双向隧道的因特网密钥交换 (ISAKMP)|IPSEC|

## 相关链接
{: #hcx-archi-port-req-related}

* [在源上安装和配置 HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
