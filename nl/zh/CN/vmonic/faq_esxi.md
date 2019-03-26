---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# 关于 ESXi 服务器的常见问题
{: #faq_esxi}

查找有关 {{site.data.keyword.vmwaresolutions_full}} 控制台上管理的 ESXi 服务器的常见问题的答案。

## 可以向实例添加多少个 ESXi 服务器？
{: #faq_esxi-instance}
{: faq}

* 对于 vCenter Server 实例，可以将缺省集群扩展为最多具有 51 个 ESXi 服务器。每个非缺省集群可以扩展为最多具有 59 个 ESXi 服务器。由于您最多可以向一个实例添加 10 个集群，因此每个部署的实例在所有集群中最多可以有 51 + 9x59 = 582 个 ESXi 服务器。
* 对于 Cloud Foundation 实例，标准配置有 4 个 ESXi 服务器。最多可以添加 28 个服务器（总共 32 个服务器）。对于多站点配置中的 Cloud Foundation 实例，在所有实例中最多可以有 128 个 ESXi 服务器。

  如果 Cloud Foundation 配置需要具有超过 128 个 ESXi 服务器的多站点部署，请[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)以获取帮助。
  {:note}

## 可以向集群添加多少个 ESXi 服务器？
{: #faq_esxi-cluster}
{: faq}

对于 V2.2 和更高版本中部署的实例，最多可以向初始集群添加 51 个 ESXi 服务器，最多可以向添加的集群添加 59 个 ESXi 服务器。

对于 V2.1 或更低版本中部署的实例，必须启用必要的 vSAN 支持才能将集群大小增加到 32 以上。要启用必要的 vSAN 支持，请完成以下步骤：

1. 在每个部署的 ESXi 服务器上，运行以下命令：

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. 重新启动每个 ESXi 服务器。有关更多信息，请参阅[创建具有最多 64 个主机的 vSAN 6.x 集群](https://kb.vmware.com/s/article/2110081)。
3. 可能需要增大 vCenter Server 的大小以容纳添加的虚拟机和 ESXi 服务器。
4. 开具 IBM 支持凭单以表明您已通过完成步骤 1 - 3 手动应用了 vSAN 更改。在凭单中，请求为超过 32 个的 ESXi 服务器启用已升级的实例。

## 可以更改 ESXi 服务器名称和 IP 地址吗？
{: #faq_esxi-change-name-ip}
{: faq}

不能更改 ESXi 服务器名称和 IP 地址，因为这些名称和 IP 地址已注册用于 Windows DNS 解析。更改可能会导致部署期间发生故障或 vCenter Server 功能发生故障。

不要使用 {{site.data.keyword.cloud_notm}} 用户界面上的**重命名设备**功能来更改 ESXi 服务器名称。此功能会更改 ESXi 服务器的 FQDN，但配置的 vCenter Server 和 Windows VSI 主机注册将不正确，并可能导致故障。
{:note}

## 可以禁用 ESXi 服务器上的 root 用户访问权吗？
{: #faq_esxi-disable-root}
{: faq}

建议在 ESXi 服务器上保持启用 root 用户访问权，否则 {{site.data.keyword.vmwaresolutions_short}} 功能中可能会发生故障。

如果有必要，您可以在 ESXi 服务器的状态处于**可供使用**后，在 {{site.data.keyword.vmwaresolutions_short}} 控制台上禁用 root 用户访问权。

对于添加或除去文件共享，或者安装附加服务（例如，Zerto on {{site.data.keyword.cloud_notm}}）等后续自动化操作，必须重新启用 root 用户访问权。

## 可以在 ESXi 服务器上添加静态路由以从其他位置安装存储器吗？
{: #faq_esxi-static-routes}
{: faq}

可以添加存储器的静态路由，但执行此操作时必须格外小心。否则，可能会卸装现有共享。

不支持为 vMotion 添加静态路由。vMotion 子网配置中的更改可能会导致 {{site.data.keyword.vmwaresolutions_short}} 功能中出现故障。
{:note}

## 相关链接
{: #faq_esxi-related}

* [扩展和收缩 vCenter Server 实例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [添加、查看和删除 vCenter Server 实例的集群](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
