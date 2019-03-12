---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# 安装和配置混合服务
{: #hcx-archi-install-cfg-hybrid}

安装程序会为每个服务虚拟设备供应和配置虚拟机。服务虚拟机同时部署在内部部署和云中。

## 先决条件
{: #hcx-archi-install-cfg-hybrid-prereq}

* HCX Manager 必须以内部部署方式安装，并向支持 VCF/VCS HCX 的云端点进行注册。
* 目标虚拟数据中心必须有足够的资源。

## 配置概述
{: #hcx-archi-install-cfg-hybrid-config-ovw}

配置过程假定将配置所有服务虚拟设备。但是，并非所有服务虚拟设备都需要配置。
* Hybrid Cloud Gateway 是必需的。
* 通过在安装期间选中“WAN 优化服务”框来完成 WAN 优化的安装。无需进一步配置。
* 要配置 Network Extension 服务，请参阅_配置 Network Extension 服务_部分。可选设备的部署可以通过返回到“混合服务”页面来延迟执行，日后再安装该设备。

## 开始混合服务虚拟设备的安装和配置
{: #hcx-archi-install-cfg-hybrid-start-hsva}

可使用简单的 Web 界面来安装服务虚拟设备，并配置更多第 2 层集中器。

HCX Manager 必须已安装，并向支持 VCF/VCS HCX 的云端点进行注册。

### 安装和配置混合服务虚拟设备的过程
{: #hcx-archi-install-cfg-hybrid-proc-install}

1. 登录到 vSphere Web Client。
2. 在**主页**选项卡上，单击 **Hybrid Cloud Services** 图标。
3. 单击**混合服务**选项卡。
4. 单击**安装服务**。
5. 在**选择混合服务**页面上，选择要安装的服务，然后单击**下一步**。

### 后续步骤
{: #hcx-archi-install-cfg-hybrid-start-hsva-next}

1. 下一步是根据需要配置 Hybrid Cloud Gateway。
2. 如果有足够的资源可用于支持扩展，那么可以随时向现有安装添加第 2 层集中器。

## 配置 Hybrid Cloud Gateway
{: #hcx-archi-install-cfg-hybrid-config-hcg}

配置 Hybrid Cloud Gateway 服务虚拟设备。开始之前，执行_开始混合服务虚拟设备的安装和配置_中的步骤，并选中 Hybrid Cloud Gateway。

### 配置 Hybrid Cloud Gateway 的过程
{: #hcx-archi-install-cfg-hybrid-proc-config-hcg}

在 **Hybrid Cloud Gateway** 页面上，提供以下值，然后单击**下一步**：
* **网络** - 用于连接 Hybrid Cloud Gateway 管理界面的交换机。在用例 1 和 2 中，此项可以是标准虚拟交换机或虚拟分布式交换机。对于使用第 2 层扩展的任何配置，此项必须是虚拟分布式交换机。
* **集群/主机** - 选择要部署云网关的集群或主机。
* **数据存储** - 选择要部署云网关的数据存储。
* **VM/主机名** - 此值是可选的。
* 提供要用于云网关管理界面的 IP 地址/CIDR、缺省网关和 DNS 服务器。
* 要为 DNS 服务器输入多个地址，请用逗号分隔各地址。
* 在**扩展（可选）**下，选择 vMotion 网络（如果适用），然后设置 **admin** 和 **root** 用户密码。这些密码专门用于 Hybrid Cloud Gateway 设备。该用户名和密码不必与为 Hybrid Cloud Services 设备配置的用户名和密码相匹配。

## 配置 Network Extension 服务
{: #hcx-archi-install-cfg-hybrid-config-nes}

针对单路径部署或针对备用路径上的独立网络扩展，配置 Network Extension 服务。开始之前，选择 Network Extension 服务。如果安装了单路径配置，那么 **Network Extension** 是您唯一的选择。

### 配置 Network Extension 服务的过程
{: #hcx-archi-install-cfg-hybrid-proc-config-nes}

1. 在 **Network Extension 服务**页面上，从**分布式交换机**菜单中选择虚拟分布式交换机。安装标准第 2 层集中器时，**通过 Hybrid Cloud Gateway 路由延伸网络**复选框将可用。对于高吞吐量 L2C，没有此复选框。
2. 如果选中**通过 Hybrid Cloud Gateway 路由延伸网络**，安装程序将确定第 2 层集中器的合理位置（根据交换机），并填充位置信息。否则，必须在下一步中手动输入位置信息。
3. 设置 L2 集中器位置的路径。如果选中**通过 Hybrid Cloud Gateway 路由延伸网络**，那么无法编辑这些值。
  * **网络** - 第 2 层集中器管理界面的部署网络。
  * **计算** - 第 2 层集中器的部署集群或主机。
  * **数据存储** - 第 2 层集中器的部署数据存储。
  * **VM/主机名** - 此值是可选的。
4. 指定本地第 2 层集中器的网络参数。
  * 如果禁用此选项，请使用安装程序提供的缺省参数。
  * 如果在 Hybrid Cloud Gateway 页面的**网络**菜单中选择的端口组不属于分布式交换机，请查看**指定本地第 2 层集中器的网络参数**，并编辑**扩展配置**文本框。
5. （可选）**扩展配置** - 设置此特定第 2 层集中器的 **admin** 和 **root** 用户密码。
6. 单击**下一步**。复查**即将完成**页面上的信息，然后单击**完成**。

## 监视服务设备部署
{: #hcx-archi-install-cfg-hybrid-monitor}

任务控制台可用于监视服务虚拟机的部署进度。

### 监视服务设备部署的过程
{: #hcx-archi-install-cfg-hybrid-monitor-proc}

1. 登录到 vSphere Web Client。在**主页**选项卡上，单击 **Hybrid Cloud Services** 图标。
2. 在 **Hybrid Cloud Services** 窗格上，单击**混合服务**选项卡。可以在任务控制台中监视虚拟设备部署。
3. 转至**最近任务**窗格，并查看**所有用户的任务**。
4. 单击**更多任务**以打开任务控制台。
5. 在任务控制台中，监视部署任务。
6. 完成所有任务后，转至清单列表，并单击 **Hybrid Cloud Services**。
7. 在中央窗格中，单击**混合服务**选项卡。
8. 复查混合服务虚拟设备的配置摘要。

## 查看隧道状态
{: #hcx-archi-install-cfg-hybrid-view-tunnel}

查看云网关隧道状态。Network Extension 服务必须正常运行后，才能延伸网络。

### 查看隧道状态的过程
{: #hcx-archi-install-cfg-hybrid-proc-view-tunnel}

1. 要在 Web Client 中检查隧道状态，请选择清单中的 **Hybrid Cloud Services**，然后单击**混合服务**选项卡。
2. 要确认 Hybrid Cloud Gateway 隧道是否成功，请查看 CGW（Hybrid Cloud Gateway 的首字母缩写）状态是否为**活动**，并且在最右侧，隧道的颜色编码为绿色。

## 将第 2 层联网延伸到 IBM Cloud

将第 2 层网络从内部部署数据中心扩展到支持 VCF/VCS HCX 的云。
{: #hcx-archi-install-cfg-hybrid-stretch-layer-2}

### 将第 2 层网络延伸到 IBM Cloud 的先决条件
{: #hcx-archi-install-cfg-hybrid-prereq-stretch-layer-2}

* 只能延伸 VLAN 标记的端口组（“VLAN 类型”不为“无”或“VLAN 标识”不为 0）。VXLAN 被视为 VLAN。
* 此过程使用**扩展网络**向导。此向导必须从 vSphere® Web Client 的“联网清单”视图运行。虽然此向导会在其他视图中显示，但必须从清单上下文运行才能获得正确的信息。

### 将第 2 层网络延伸到 IBM Cloud 的过程
{: #hcx-archi-install-cfg-hybrid-proc-stretch-layer-2}

1. 登录到 vSphere Web Client。在中央窗格的**主页**选项卡上，单击**清单**列表中的**联网**图标。
2. 在**联网**层次结构中，识别要扩展的网络的端口组。
3. 右键单击端口组，然后从菜单中选择**混合操作**，再选择**扩展网络**。
4. 在**选择源端口组**页面上，确认端口组信息并输入网络的**网关 IP 地址**和前缀。单击**下一步**。
5. 在**选择目标网关**页面上，完成以下步骤：
  1. 从**组织**菜单中，选择 VCF/VCS Hybrid Cloud Services Cloud 组织。
  2. 从菜单中，选择 VCF/VCS Hybrid Cloud Services Cloud 虚拟数据中心。
  3. 使**邻近路由**保持禁用状态，以强制支持 VCF/VCS Hybrid Cloud Services 的云中的 VM 始终使用内部部署网关来访问因特网。缺省情况下，源自支持 VCF/VCS Hybrid Cloud Services 的云中的 VM 的流量会沿第 2 层数据路径遍历回内部部署数据中心，然后流出至缺省网关。如果选中**邻近路由**，那么支持 VCF/VCS Hybrid Cloud Services 的云中的 VM 可以访问因特网，而无需遍历 vSphere 的第 2 层数据路径。
  4. 通过单击网关列表中远程目标网关所在的行以选择该网关。单击**下一步**。
6. 在**即将完成**页面上，复查提供的所有值。单击**完成**。
7. 要跟踪网络扩展的进度，请转至**最近任务**窗口，单击**所有**选项卡，然后查看**所有用户的任务**。
8. 要打开任务控制台，请单击**更多任务**。**扩展网络**任务的状态为**完成**时，说明网络扩展已完成。

## 相关链接
{: #hcx-archi-install-cfg-hybrid-related}

* [修改或卸载 HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
