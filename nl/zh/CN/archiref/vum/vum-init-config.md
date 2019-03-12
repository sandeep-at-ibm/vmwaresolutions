---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# 初始配置
{: #vum-init-config}

IC4VS 自动化配置了缺省网关设置为 {{site.data.keyword.cloud}} 后端客户路由器 (BCR) 的 VCSA。但是，没有通过 BCR 连到因特网的路由。从 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 实例到因特网的标准路由是通过管理 ESG 进行的。由于建议不要更改 VCSA 或管理 ESG 的配置，因此推荐在客户子网上实现代理服务器来启用 VUM。

此方法意味着不必重新配置 VCSA 或管理 ESG，但是必须安装小型虚拟机 (VM) 或设备。代理服务器是一个系统，位于两个端点设备之间，充当中间设备。在本例中，代理服务器位于 VUM 与 VMware 的更新服务器之间。

VUM 向 VMware 的更新服务器请求资源时，会先将请求发送到代理服务器，然后代理服务器再将请求发送到更新服务器。代理服务器获得资源后，会将该资源发送给 VUM。代理服务器的使用有利于安全性、管理控制和高速缓存服务。

本文档描述了如何使用基于 CentOS 和 Squid 的代理服务器。Squid 代理是用于 Web 的开放式源代码高速缓存代理，支持许多协议，包括 HTTP 和 HTTPS。有若干 VM 和基于设备的代理可用，您必须根据企业需求选择适当的代理，并遵循供应商的指导进行安装和配置。选择使用 CentOS/Squid 实现的客户应该继续执行以下过程。

* 将 CentOS ISO 下载到跳板机
* 创建 vCenter 库
* 将 ISO 上传到 vCenter 库
* 创建 VM，安装和配置 CentOS，并安装 Squid

开始此任务之前，您需要收集信息以填充表 1。请复查建议的值，并确保这些值适合您的企业。此配置仅基于使用 CentOS-Minimal 和 Squid 的 VUM 的小型代理。

表 1. 部署值

|参数|建议值|注释|
|:--------- |:-------------- |:------ |
|代理 CPU| 1 个 vCPU |Squid 没有最低需求|
|代理 RAM| 2 GB |Squid 没有最低需求|
|代理磁盘|25 GB |Squid 没有最低需求|
|主机名| Proxy01 | |
|地址|代理 IP |必须使用供应过程中分配的客户专用可移植子网中的备用 IP 地址。此子网上只保留有两个 IP 地址：一个用于 BCR，另一个用于客户 ESG
|网络掩码|255.255.255.192 | |
|网关|customer-nsx-edge private uplink ip |这是代理服务器的缺省网关设置，即 customer-nsx-edge 的专用上行链路 IP 地址。可通过查看 **customer-nsx-edge** 的**设置**选项卡来找到此 IP 地址。|
|DNS 服务器|AD/DNS IP |可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台中的**已部署的实例**页面上找到此 IP 地址。|
|BCR IP|BCR IP |这是 {{site.data.keyword.cloud_notm}} 后端客户路由器的 IP 地址，并且是 10.0.0.0/8 和 161.26.0.0/16 的网关。此地址在代理服务器的静态路由中使用，以便可以访问 VCSA 和 AD/DNS 服务器。|

## 配置 NSX
{: #vum-init-config-config-nsx}

需要 NSX 客户 ESG 防火墙和 NAT 设置才能启用代理服务器流量。

### 防火墙
{: #vum-init-config-firewall}

1. 转至**主页** > **联网和安全性**。
2. 选择名为 customer-nsx-edge 的 **NSX Edge**，然后选择**防火墙**。
3. 单击 **+** 号并添加防火墙规则。
4. 提供下表中说明的必需参数。新的防火墙规则必须出现在最后一个规则（即“缺省拒绝”规则）之前。

表 2. 防火墙规则

|参数|建议值|
|:--------- |:-------------- |
|名称| 出站 Proxy01 |
|类型| User |
|源| 代理服务器 IP |
|目标| any |
|服务| HTTP/HTTPS/ICMP Echo |
|操作| Accept |

提供参数后，单击**发布更改**。

### 安装和配置代理服务器
{: #vum-init-config-inst-cfg-proxy}

以下过程将 VM 从内容库部署到主机 CentOS 和 Squid，包含以下步骤。此过程假定您已供应 Windows VSI 以用作跳板机，并且是使用远程桌面协议连接到 VSI 的公共接口：

* 下载 CentOS-Minimal ISO 文件
* 配置 vCenter 内容库并使用 CentOS ISO 文件填充该内容库
* 配置代理 VM，并且安装 CentOS 和 Squid

### 下载 CentOS-Minimal ISO 文件
{: #vum-init-config-downloading-centos}

在跳板机上使用浏览器从 [CentOS](https://www.centos.org/download/) 下载 CentOS-Minimal ISO 文件。请注意，{{site.data.keyword.cloud_notm}} 维护许多常用 Linux 分发版的镜像。此镜像仅在专用网络上可用，并且 CentOS ISO 可从以下地址获取：`http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`

### 配置内容库并使用 CentOS ISO 文件填充该内容库
{: #vum-init-config-config-conent-library}

创建本地 vCenter 内容库。只能在创建该内容库的 vCenter Server 实例中访问该库。使用部署 VM 所需的模板和 ISO 来填充库。

1. 通过 vSphere Web Client，浏览至**主页** > **内容库** > **对象** > **创建新内容库** > **在 vCenter 上创建预订的库**。
2. 输入内容库的名称（例如 ISO），并在“注释”文本框中输入库的描述，然后单击**下一步**。
3. 选择**本地内容库**，然后单击**下一步**。
4. 选择数据存储，然后单击适用的数据存储，例如 vsanDatastore。
5. 复查**即将完成**页面上的信息，然后单击**完成**。

### 配置代理 VM，并且安装 CentOS 和 Squid
{: #vum-init-config-config-proxy}

此活动具有以下任务：

*	创建新的 VM
*	安装 CentOS
*	安装 Squid

#### 创建新的 VM
{: #vum-init-config-create-new-vm}

此任务将创建一个可用作代理服务器的新 VM。应该使用“表 1 部署值”中的设置来填充配置。

1.	通过 vSphere Web Client，浏览至**主页** > **VM 和模板**。
2.	在“导航器”窗格中，单击 **datacenter1**，然后右键单击并选择**新建虚拟机** > **新建虚拟机**。
3.	选择**创建新的虚拟机**，然后单击**下一步**。
4.	输入 VM 的名称（例如，Proxy01），并选择 **datacenter1**，然后单击**下一步**。
5.	选择 **cluster1**，然后单击**下一步**。
6.	选择适用的数据存储（例如 vsanDatastore），并单击**下一步**，然后再次单击**下一步**。
7.	在**访客操作系统系列**中，选择 **Linux**，在**访客操作系统版本**中，选择 **CentOS 7（64 位）**，然后单击**下一步**。
8.	将 **CPU 设置为 1**，将**内存设置为 2048 MB**，将**新硬盘设置为 25 GB**。选择**内容库 ISO 文件**，接着选择 **CentOS-7-x86_64-Minimal**，单击**确定**，然后勾选**已连接**框。
9.	在“新建设备”框中，选择**网络**，然后单击**添加**。
10.	选择 **SDDC-DPortGroup-Mgmt** 网络，并确保勾选“连接”复选框，然后单击**下一步**。
11.	复查并单击**完成**。

#### 安装 CentOS
{: #vum-init-config-install-centos}

此任务安装并配置新创建的 VM，为安装 Squid 做准备

1.	在 vSphere Web Client 的“导航器”窗格中，选择刚才创建的 **VM** Proxy01，然后选择**摘要**选项卡。
2.	单击**“开始”**以打开 VM 的电源。
3.	现在，VM 将打开电源并从 CentOS 7 ISO 进行引导。对 VM 启动**远程控制台或 Web 控制台**。您必须安装远程控制台，并且运行 Web 浏览器的系统必须按名称解析 vSphere ESXi 主机。
4.	在“欢迎使用 CentOS 7”屏幕上，选择您所需的语言，然后单击**继续**。
5.	在**本地化**屏幕上，单击**日期和时间**，选择您所在时区，然后单击**完成**。
6.	在**本地化**屏幕上，单击**键盘**以根据需要更改缺省值，然后按**完成**。
7.	在**本地化**屏幕上，单击**安装目标**，单击 **VMware 虚拟盘**图标，然后单击**完成**。
8.	在**本地化**屏幕上，单击**网络和主机名**，将主机名更改为您选择的主机名，例如 Proxy01。
9.	单击**配置**，然后单击 **IPv4 设置**。在**方法**框中，选择**手动**。
10.	使用**添加**按钮插入_表 1 - 部署值_中的_地址网络掩码_和_网关_。
11.	输入“表 1 - 部署值”中的 _DNS 服务器 IP 地址_。
12.	单击**路由**按钮，然后将静态路由 _10.0.0.0/8 和 161.26.0.0/16_ 与“表 1 部署值”中 _BCR IP 地址_的网关 IP 地址一起添加为网关。此静态路由允许代理服务器访问 DNS 服务器。
13.	单击**保存**，然后确保以太网接口已开启并显示为已连接。单击**完成**，然后单击**开始安装**。
14.	在安装继续时，设置 root 用户密码并设置用户。
15.	安装完成后，以该用户身份登录，然后输入 _ping vmware.com_ 命令。该名称会解析为 IP 地址，并且您会收到响应。如果未得到响应，请检查 IP 地址、防火墙规则和 NAT 设置。

#### 安装和配置 Squid
{: #vum-init-config-install-cfg-squid}

Squid 没有任何最低硬件需求，但根据通过代理访问因特网的用户数和存储在高速缓存中的对象数，RAM 量可能会变化。由于只有 VUM 会访问该代理服务器，并且未启用高速缓存，因此仅配置了小型 VM。

1. 通过在 vSphere Web Client 中使用 Web 控制台或远程控制台，以用户身份登录到代理服务器，然后使用 `su` 命令切换到根目录。
2. 在安装任何软件包之前，必须使用以下命令来更新系统和软件包：`yum -y update`

3. 要安装 Squid，您需要将 EPEL 存储库安装到系统，因为 Squid 在缺省 yum 存储库中不可用。运行以下命令来安装 EPEL 存储库：
  `yum -y install epel-release`

4. 使用以下命令进行更新和清除：

  `yum -y update`
  `yum clean all`

5. 使用以下命令安装 Squid：`yum -y install squid`。
6. 安装后，立即使用以下命令启动 Squid：`systemctl start squid`。
7. 要在引导时自动启动 Squid，请运行以下命令：`systemctl enable squid`。
8. 运行以下命令来确保 Squid 正在运行：`systemctl status squid`。
9. CentOS 防火墙需要使用以下命令来允许访问 Squid 端口 TCP 3128：`firewall-cmd –add-port=3128/tcp –permanent`。
10.	要保存规则并重新启动服务，请使用以下命令：`firewall-cmd –reload`。

## VUM 的初始设置
{: #vum-init-config-init-setup-vum}

配置 VUM 以使用代理服务器来访问因特网上的存储库。
1. 使用 vSphere Web Client 浏览至**主页** > **Update Manager**。单击 vCenter Server。
2. 选择**管理**选项卡，然后单击**设置**按钮。
3. 选择**下载设置**，然后在_代理设置_下，单击**编辑**。
4. 选中**使用代理**框，并输入_代理服务器 IP 地址_和_端口 3128_，然后单击**确定**。“连接状态”会更改为_正在验证_，然后更改为_已连接_。
5. 单击**立即下载**。在_最近任务_窗格中，您应该会看到此活动已完成。

## 相关链接
{: #vum-init-config-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解决方案体系结构](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 数字技术互动](https://ibm-dte.mybluemix.net/ibm-vmware)（演示）
