---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 将 WebSphere Application Server 中的 Stock Trader 转换为容器中的 Stock Trader

在 Stock Trader 现代化之旅中，下一步是将工作负载从在虚拟机 (VM) 中运行转换为在容器中运行。

接着，Todd 和 Jane 运行了 Transformation Advisor 来分析 Stock Trader 工作负载，识别任何迁移复杂性并建议更改。准备就绪后，他们使用 Transformation Advisor 将 Stock Trader 部署到在 {{site.data.keyword.icpfull_notm}} 中运行的 Liberty 容器中。

## 准备 IBM Cloud Private

Todd 首先需要安装 {{site.data.keyword.icpfull_notm}}。Todd 在 {{site.data.keyword.cloud_notm}} 环境中有 VMware，因此他决定使用 {{site.data.keyword.cloud_notm}} Private Hosted 产品来获得在 {{site.data.keyword.cloud_notm}} 中的 VMware VM 上运行的完整 {{site.data.keyword.icpfull_notm}} 实例。

缺省仪表板提供了一个综合用户界面，用于通过目录来管理 Kubernetes 集群、安全性、存储和部署。

### 准备存储器

{{site.data.keyword.cloud_notm}} Private Hosted 现成配置为使用 GlusterFS，并提供了跨 VM（作为专用 GlusterFS 节点）的文件存储器。GlusterFS 的价值在于它支持动态供应。Todd 可以根据需要将额外的 VM 设置为 NFS 服务器。

由于 Todd 需要 NFS 服务器可供自己使用，因此他确定了一个名为“toddnfs”的 VM，并运行了这些[步骤](https://help.ubuntu.com/community/SettingUpNFSHowTo)。

Todd 运行了以下命令来创建新的 NFS 服务器：

`ssh root@toodnfs.acme.com`

`apt-get install nfs-kernel-server`

`mkdir -p /shared`

`chown nobody:nogroup /shared`

`vi /etc/exports`

接下来，Todd 添加了以下行：

`/shared \*(rw,no_subtree_check,async,insecure,no_root_squash)`

`systemctl restart nfs-kernel-server`

然后，Todd 在每个 VM 上运行了以下命令，以将 NFS 安装到每个 {{site.data.keyword.icpfull_notm}} 工作程序 VM 上：

`sudo apt-get update`

`sudo apt-get install nfs-common`

Todd 运行了以下命令以确认安装的版本：

`apt-cache policy nfs-common`

每当需要新的 NFS 卷时，Todd 都会在需要时运行以下命令来创建新的 NFS 卷：

`cd /shared`

`mkdir -p <foldername>`

`chmod 777 <foldername>`

### 准备映像安全性

在 {{site.data.keyword.icpfull_notm}} V3.1 中，通过要求在任何映像拉取到 {{site.data.keyword.icpfull_notm}} 实例之前落实映像策略，从而增强了安全性。此增强功能需要为 IBM 映像所在的位置 *dockerhub/ibmcom* 以及在 Docker 存储中添加映像策略。

缺省情况下已提供 ibmcloud-default-cluster-image-policy，该策略涵盖 docker.io/ibmcom/\* 中的所有 IBM 映像，但由于 Db2 和其他 IBM 内容位于 Docker 存储中，因此需要用于 Docker 存储的另一个映像策略 *docker.io/store/ibmcorp/*。

此外，某些内容需要设置 pod 安全策略，以允许对 pod 进行特定访问。例如，Db2 需要一个策略用于要在非“default”名称空间中运行 Db2 的客户机。

请在 [IBM Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.1.0/manage_cluster/enable_pod_security.html) 中了解更多信息。

## 部署 Transformation Advisor 和 Microclimate

Todd 在 {{site.data.keyword.icpfull_notm}} 开始运行后，安装了 Transformation Advisor 以及 Microclimate。Todd 打开[目录](https://www.ibm.com/cloud/private/developer)并查看了所有可用内容。

Todd 单击 Helm Chart 后，搜索 Transformation Advisor 和 Microclimate，并使用提供的自述文件指示信息安装了这两项。

### 运行 Transformation Advisor

为了运行 Transformation Advisor，Jane 在 WebSphere 中运行 Stock Trader 的 VM 中添加了数据收集器，然后打开 [Transformation
Advisor](https://developer.ibm.com/recipes/tutorials/using-the-transformation-advisor-on-ibm-cloud-private/) 用户界面以查看结果。

Jane 单击 Stock Trader，并查看了在 Liberty 中运行每个 WAR 文件的建议，其中大部分迁移十分简单，只需一次中等规模的迁移就可完成。Jane 单击了“迁移详细信息”，然后看到 Transformation Advisor 提供了可用于完成迁移的部署文件。Jane 将二进制文件上传到 Transformation Advisor 后，Advisor 使用 Microclimate 提供的 API 来部署 Liberty 容器。

最后，生成的 Stock Trader 布局选项如下：
* 单个 Liberty 容器 - 如果 Jane 部署了 Liberty 运行时，并将其 Stock Trader 应用程序添加到这一单个容器中。
* 多个 Liberty 容器 - 根据 Transformation Advisor 对 Stock Trader 的建议，每个 .war 文件一个 Liberty 容器。

Todd 在转换步骤期间未变更数据源。Transformation Advisor 获取了 WebSphere Application Server Network Deployment 数据源配置，并将其添加到 Liberty 容器的 server.xml。
{:important}

### 相关链接

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
