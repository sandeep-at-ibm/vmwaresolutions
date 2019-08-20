---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# 准备安装环境
{: #hcxclient-planning-prep-install}

安装 VMware HCX on IBM Cloud 具有以下软件需求：
* vSphere 5.5 U3 或者 vSphere 6.0u2 或更高版本。
* 如果使用了 NSX，版本须为 V6.2.2 或更高版本。策略迁移需要 NSX。
* 要使用跨云 vMotion，适用于内部部署的相同亲缘关系限制也适用于跨云的情况。有关更多信息，请参阅 [VMware EVC 和 CPU 兼容性常见问题](https://kb.vmware.com/s/article/1005764)。

## 配置网络连接
{: #hcxclient-planning-config-net}

HCX 必须遍历公用因特网和专用线路，并连接到数据中心组件，例如网络、交换机和端口组。
* 有关为了成功安装 HCX 虚拟设备而必须打开的端口的信息，请参阅[端口访问需求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)。
* 内部部署 vSphere 环境和 VCS HCX 云环境都必须允许 vSphere 内部部署设备和 VCS HCX 设备之间进行网络时间协议 (NTP) 时钟同步。UDP 端口 123 必须可由 HCX 虚拟设备和网络访问。

## 内部部署环境
{: #hcxclient-planning-on-prem-env}

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
{: #hcxclient-planning-verify-layer-2-inst}

第 2 层网络延伸具有以下需求：
* vSphere Enterprise Plus Edition。
* vSphere vCenter 必须满足以下需求才能支持第 2 层扩展：
  * vSphere Enterprise Plus 许可证
  * 必须具有 vSphere 分布式交换机 (vDS)。分布式交换机可与 vSphere Enterprise Plus Edition 一起使用。
  * 安装后，内部部署第 2 层集中器服务设备必须有权访问 vNIC 端口和要延伸的任何 VLAN。
  * 如果要通过公用因特网或 VPN（在备用路径上）延伸网络，那么 VCS 中的 L2C 虚拟机需要 IP 地址。配置第 2 层集中器需要该远程 IP 地址。
  * 如果需要多个第 2 层集中器，那么每个集中器都必须具有内部部署和云中的 IP 地址。

## 部署前规划
{: #hcxclient-planning-predepl}

部署 HCX 时，大部分时间是用在部署前阶段。虽然信息系统迁移项目通常需要几个月甚至几年时间才能完成，但 HCX 支持在短时间内完成迁移，并且允许在部署后立即启动与云的网络连接。

由于企业级客户的 HCX 部署通常涉及安全性、网络、存储和 vSphere 基础架构团队，因此如果可能，使这些团队参与到 POC 中是合理的。有效的项目管理和利益相关方的早期参与至关重要，可确保快速部署和运行 HCX。

## 避免分析瘫痪
{: #hcxclient-planning-avoiding}

在迁移一个虚拟机 (VM) 或一组 VM 时，由于需要修改应用程序环境的各部分，设计这些更改以及安排进行这些更改所需的停机时间，因此存在许多障碍，需要较长时间。在进行这些更改后，迁移会变得难以还原，进一步增加了分析瘫痪的可能性。尝试捕获迁移的所有方面，在团队之间进行协调，以及不断变化的关键利益相关方，都可能导致项目延迟。

HCX 支持跨 vSphere 实例迁移代表部分或整个复合应用程序的一个 VM 或一组 VM，而无需对应用程序进行任何修改。因此，退出迁移意味着将 VM 移回原位或重新延伸网络。这样就否定了迁移规划中很大一部分的必要性，但支持规划过程中的一些并行性。在选择要移动的应用程序并创建高级别网络设计之后，应用程序可以在云实例上以最少配置开始迁移，同时最终网络连接和设计可顺利进行。

## 延伸网络
{: #hcxclient-planning-stretched-net}

HCX 系列的网络延伸组件非常稳定。如果一个特定客户拥有 20 个以上的 VLAN，这些 VLAN 延伸到 {{site.data.keyword.cloud}} 与其他流量和 HCX 迁移隧道共享的 1 Gbps WAN 中，那么不会因该网络而导致任何应用程序问题。网络链路能以此方式正常运行 6 个月以上。

添加和除去更多延伸网络时不会发生任何问题。选取离得很近的 {{site.data.keyword.CloudDataCent_notm}}（对于此特定客户，等待时间小于 6 毫秒）也会提高延伸联网的网络稳定性。在设计中，使延伸网络长时间运行不应该是负面因素，但条件是应用程序具有足够的带宽和足够短的等待时间。

## 迁移生命周期
{: #hcxclient-planning-mig-lifecycle}

以下各部分描述了典型 HCX 迁移生命周期内的不同阶段，指示工作流在哪里可以并行执行。

## vSphere 清单
{: #hcxclient-planning-vsphere-planning}

- 对应用程序中要迁移的 VM 进行粗颗粒度评估。粗颗粒意味着了解参与应用程序的 VM，但不深入了解详细信息。
- 如果计划迁移多个 VM，而源站点和云站点之间的网络带宽有限，那么在源站点中应用 NSX 后，请按 VLAN 或 VXLAN 进一步对 VM 分组。这将支持级联 HCX 迁移计划，其中将迁移按 VLAN 划分的 VM 组，而它们所在的 L2 网络仅会延伸到释放 VLAN 的那一刻。

这意味着仅当云端网络设计最终完成并部署后，才能对相关 L2 延伸网络的初始组取消延伸。取消延伸意味着对特定 VXLAN 流量执行摆动操作，以便现在通过云实例 NSX 基础架构进行路由。

## 基线网络配置
{: #hcxclient-planning-baseline-net-config}

在云端 vSphere 实例中创建安全的外围网络。这通常由 NSX DLR 或 Edge 设备组成。如果使用 HCX 邻近路由，那么无需创建任何防火墙规则或上行链路拓扑，因为这可以在日后或同时完成，而不影响 L2 延伸流量。

## 网络扩展
{: #hcxclient-planning-net-extension}

扩展网络仅仅意味着从源 vSphere 环境中获取现有 VLAN 或 VXLAN（由虚拟分布式交换机 (vDS) 端口组表示），并将其扩展到 HCX 云端的 NSX VXLAN。

## 预检
{: #hcxclient-planning-preflight-tests}

预检涉及通过 vMotion 和批量迁移功能执行 HCX 迁移，以确定基线传输速率。

## 迁移非生产应用程序
{: #hcxclient-planning-mig-non-prod-apps}

VM 的迁移将从不太关键的 VM 的计划阶段开始。开发和测试团队会使用因特网连接进行迁移和处理 L2 延伸流量。

## 云网络设计和实施开始
{: #hcxclient-planning-cloud-net-begins}

在迁移继续时，云端网络设计会在云端 vSphere 实例中最终完成并实施。

## 更多网络连接注意事项
{: #hcxclient-planning-connect-considerations}

在迁移继续时，会订购专用 WAN 网络连接，因为这通常需要几周到几个月时间才能与云提供者建立连接。完成专用网络连接后，可以将 HCX 配置为同时使用专用私有网络链路和因特网来进行迁移和处理 L2 延伸流量。

## 物理服务器
{: #hcxclient-planning-physical-servers}

目标是从数据中心迁移到云中时，对于与要迁移的 VM 交互的任何物理服务器，可以评估是作为 VM (P2V) 或裸机迁移到 {{site.data.keyword.cloud_notm}} 中，还是保留在源中。如果物理服务器要保留在源中，并且 HCX 在迁移期间仅会使用到建立专用网络时，那么务必了解该物理服务器是否位于已使用 HCX 延伸到云中的任何网络上。在此场景中，HCX 不仅允许 VM 迁移到云中，还允许整个子网迁移到云中。

要在迁移结束时除去 HCX，如果要保持物理设备与已迁移 VM 之间的连接，那么子网不能存在于源和目标中。这意味着源站点中留下且在 L2 延伸网络上存在的任何物理设备都必须迁移到能够路由到云端的其他网络子网。但应用了其他某种 L2 延伸技术（如 NSX L2 VPN）来替换 HCX L2 延伸端点的情况例外。

## 迁移生产和复杂应用程序
{: #hcxclient-planning-mig-prod-complex-app}

有些 VM 在迁移之前需要给予额外考虑，例如，具有共享多写程序 VMDK（如 Oracle RAC 或 MS Exchange/SQL 集群）的 VM，或具有原始设备映射的 VM。

## 网络摆动
{: #hcxclient-planning-net-swing}

在源端网络上的 VM 转移完成，并且在云端完成网络设计/实现后，将执行网络摆动。将 HCX 配置为取消延伸与迁移批次内已完成 VM 相关的网络，即允许已迁移的 VM 使用云端 NSX 基础架构来路由网络流量。

## 支持的客户机平台
{: #hcxclient-planning-client-platforms}

对于网络扩展，仅支持 vSphere 虚拟分布式交换机 (vDS) 的端口组。这还意味着不支持独立 ESXi 主机，因为 ESXi 主机由 vCenter 进行管理时，只能有一个 vDS。
- vSphere 5.1（仅通过 API 用于 vCenter 5.1 的命令行）
- vSphere 5.5（vCenter 5.5u3 及更高版本上支持的 Web 客户机 UI）
- vSphere 6.0
- vSphere 6.5（vDS 必须为 6.0 级别）

## 支持的云平台
{: #hcxclient-planning-cloud-platforms}

HCX 云端通过 {{site.data.keyword.cloud_notm}} 自动化进行供应。

## 连接选项
{: #hcxclient-planning-connect-options}

### 标准 HCX 连接
{: #hcxclient-planning-standard-connect}

通过 {{site.data.keyword.vmwaresolutions_short}} 自动化部署 HCX 云端时，缺省情况下，HCX 云端安装配置为连接到公用因特网。

## 相关链接
{: #hcxclient-planning-related}

* [HCX 组件和术语的词汇表](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [HCX 客户机部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 内部部署服务网](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 混合云迁移](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [监视参数和组件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
