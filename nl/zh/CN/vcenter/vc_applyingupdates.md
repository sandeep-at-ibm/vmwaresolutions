---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: vCenter Server update, patch vCenter Server, IBM component update

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 对 vCenter Server 实例应用 IBM 管理组件更新
{: #vc_applyingupdates}

此部分中的过程适用于更新部署在 V2.1 到 V2.4 发行版中的实例的 IBM 管理组件。

对于部署在（或已升级到）V2.5 或更高版本的实例，会根据需要自动应用 IBM 管理组件的更新和补丁。

对于在 V2.0 和更低版本中部署的实例，必须手动应用更新。

此外，请注意在实例上完成特定操作时会有以下行为：
* 订购新服务时，实例会更新为最新版本。
* 添加新集群时，将向这些集群供应最新的 VMware 组件，但对于现有集群不是如此。
* 添加新 ESXi 服务器时，将向这些 ESXi 服务器供应最新的 VMware 组件，但对于现有 ESXi 服务器不是如此。

{{site.data.keyword.vmwaresolutions_short}} 不支持应用 VMware 组件的更新和补丁。您必须自行监视并应用这些更新。
{:important}

## 在应用 IBM 管理组件更新之前
{: #vc_applyingupdates-prereq}

通过单击向下箭头并验证以下信息来展开更新条目：
* 更新的版本。必须按时间顺序应用更新，从最早的更新开始一直应用到最新的更新。在应用最新的更新之前，请确保应用了所有先前的更新。例如，在尝试应用 V2.4 更新之前，必须先应用 V2.3 更新。
* 是否需要停机时间。
* 完成更新的估计总时间。
* 更新对 VMware 虚拟环境的影响。表 1 显示不同的更新级别对系统产生的影响。
* 更新详细信息。

表 1. 更新级别和影响

<table>
  <tr>
    <th>更新级别</th>
    <th>影响</th>
  </tr>
  <tr>
    <td>低</td>
    <td>此更新不会影响任何系统。不必在安排的停机时间内应用更新。</td>
  </tr>
  <tr>
    <td>中</td>
  <td>此更新可能会影响某些系统。建议在安排的停机时间内应用更新。</td>
  </tr>
    <tr>
    <td>重大</td>
  <td>此更新会影响部分系统或所有系统。必须在安排的停机时间内应用更新。</td>
  </tr>
</table>

## 应用 IBM 管理组件更新的过程（实例 V2.1 到 V2.4）
{: #vc_applyingupdates-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要更新的实例。
3. 在**摘要**页面上，验证是否所有实例详细信息都正确显示。然后在左侧导航窗格上，单击**基础架构**以验证**基础架构**页面上的详细信息。
   

   如果未显示详细信息，这可能指示由于防火墙规则或网络问题而导致 IBM CloudDriver 虚拟服务器实例 (VSI) 发生连接问题。请解决该问题后，再继续下一步，否则更新可能会失败。

4. 单击左侧导航窗格上的**更新和补丁**，单击向下箭头以展开要应用的 IBM 管理更新，然后完成下列其中一个步骤：
   * 要立即启动更新，请单击更新条目的**操作**列中的溢出菜单图标，然后单击**立即更新**。
   * 要安排未来更新，请单击更新条目的**操作**列中的溢出菜单图标，然后单击**安排更新**。选择要启动更新的日期、时间和时区。单击**确定**。
5. 如果要在多站点部署配置中将更新应用于实例，那么会显示标题为**更新所需的步骤**的部分。此部分列出多站点部署中所有实例所需的更新操作。必须通过对每个步骤单击**应用更新**来按顺序完成这些步骤。必须等待上一步完成后，才能开始下一步。

## 应用 IBM 管理组件更新后的结果
{: #vc_applyingupdates-results}

1. 应用更新后，会在软件更新状态列表中显示一条记录，在其中可以查看更新的详细进度和状态。成功完成更新后，会在安装的软件更新列表中显示一条记录。

  要检索更新作业的最新状态，请单击页面右上角的“刷新”图标。
  {:tip}

2. 有关更新状态的详细信息，请参阅下表。

   表 2. 更新状态的详细信息

    <table>
      <tr>
        <th>状态</th>
        <th>详细信息</th>
      </tr>
      <tr>
        <td>可用</td>
        <td>更新可供应用。在应用所有先前更新之后，才能选择可用更新。</td>
      </tr>
      <tr>
        <td>进行中</td>
      <td>更新作业已启动，但尚未完成。在当前更新作业完成之前，不能应用其他任何更新。</td>
      </tr>
        <tr>
        <td>已安装</td>
      <td>更新作业已完成。将更新 VMware 平台的相应组件。</td>
      </tr>
        <tr>
        <td>失败</td>
      <td>更新作业失败。控制台报告有关更新失败的错误。请复查错误并修正报告的问题，然后重新应用更新。</td>
      </tr>
          <tr>
        <td>已安排</td>
      <td>更新作业已安排为日后执行。更新作业会在安排的时间自动启动。</td>
      </tr>
          <tr>
        <td>未知</td>
      <td>无法获取更新作业的状态。请联系 IBM 支持人员以获取帮助。</td>
      </tr>
    </table>

3. 如果更新过程在特定步骤失败，请[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)以获取帮助。IBM 支持人员将向您提供如何解决问题的建议，并指导您从失败的步骤应用更新和补丁。

## 相关链接
{: #vc_applyingupdates-related}

* [vCenter Server 概述](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [升级 vCenter Server 实例的许可证](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
