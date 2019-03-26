---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# 准备安装环境
{: #hcx-archi-prep-install}

安装 VMware HCX on IBM Cloud 具有以下软件需求：
* vSphere 5.5 U3 或者 vSphere 6.0u2 或更高版本。
* 如果使用了 NSX，版本须为 V6.2.2 或更高版本。策略迁移需要 NSX。
* 要使用跨云 vMotion，适用于内部部署的相同亲缘关系限制也适用于跨云的情况。有关更多信息，请参阅 [VMware EVC 和 CPU 兼容性常见问题](http://bit.ly/2vK6Sp5)。

## 配置网络连接
{: #hcx-archi-prep-install-config-net}

HCX 必须遍历公用因特网和专用线路，并连接到数据中心组件，例如网络、交换机和端口组。
* [端口访问需求](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-port-req)列出了必须打开的端口，只有打开这些端口，HCX 虚拟设备才能成功安装。
* 内部部署 vSphere 环境和 VCF/VCS HCX 云环境都必须允许 vSphere 内部部署设备和 VCF/VCS HCX 设备之间进行网络时间协议 (NTP) 时钟同步。UDP 端口 123 必须可由 HCX 虚拟设备和网络访问。

## 内部部署环境
{: #hcx-archi-prep-install-on-prem-env}

安装 HCX 之前，请验证环境是否可以支持要完成的任务。内部部署环境必须支持以下任务，才能安装 HCX。
* 具有 vSphere 5.5 Update 3 或 6.0 Update 2 的虚拟中心。
* vMotion 和策略迁移功能需要 NSX V6.2.2 或更高版本。
* 分配有“管理员”vCenter Server 系统角色的 vSphere 服务帐户。
* 在 vCenter 中，有足够的磁盘空间可用于安装 HCX 设备。
* 有足够的 IP 地址用于在安装期间供应的内部部署 VM。
* 如“端口访问需求”中所述，根据需要打开了端口和防火墙。
* 如果单点登录 (SSO) 服务器是远程服务器，那么必须识别运行外部查找服务的 vCenter、外部 SSO 服务器或 Platform Services Controller (PSC) 的 URL。向 vCenter 注册 HCX Manager 时，必须提供此 URL。
* 如果 vCenter 没有自己的内部查找服务实例，那么可能是出于下列其中一种原因：
  * vCenter 6.0u2 运行的是外部 Platform Services Controller。
  * vCenter 处于链接方式（其中，辅助 vCenter 使用主 vCenter 中的 SSO 服务或使用外部 SSO 服务）。

## 验证第 2 层安装环境
{: #hcx-archi-prep-install-verify-layer-2-inst}

第 2 层网络延伸具有以下需求：
* vSphere Enterprise Plus Edition。
* vSphere vCenter 必须满足以下需求才能支持第 2 层扩展：
  * vSphere Enterprise Plus 许可证
  * 必须具有 vSphere 分布式交换机 (vDS)。分布式交换机可与 vSphere Enterprise Plus Edition 一起使用。
  * 安装后，内部部署第 2 层集中器服务设备必须有权访问 vNIC 端口和要延伸的任何 VLAN。
  * 如果要通过公用因特网或 VPN（在备用路径上）延伸网络，那么 VCF/VCS 中的 L2C 虚拟机需要 IP 地址。配置第 2 层集中器需要该远程 IP 地址。
  * 如果需要多个第 2 层集中器，那么每个集中器都必须具有内部部署和云中的 IP 地址。

## 相关链接
{: #hcx-archi-prep-install-related}

* [在源上安装和配置 HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
* [VMware EVC 和 CPU 兼容性常见问题](http://bit.ly/2vK6Sp5)
