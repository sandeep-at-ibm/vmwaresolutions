---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 对 Cloud Foundation 实例应用更新
{: #sd_applyingupdates}

{{site.data.keyword.vmwaresolutions_full}} 控制台会定期检测并列出可应用于 VMware 虚拟环境的可用软件更新。

可用更新是实例软件更新列表中的一个记录，可以立即应用，也可以安排在日后应用。更新是一个捆绑软件，包含一个或多个用于更新 IBM 管理组件和 VMware 组件的软件包。

将不再列出 IBM CloudDriver 更新，因为已启用自动更新。添加 ESXi 服务器、添加集群和订购服务等操作会自动将实例更新到最新版本。有关自动更新的更多信息，请参阅 [V2.5 发行说明](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-relnotes_v25)中的 *IBM CloudDriver 弹性*部分。
{:note}

## 开始之前
{: #sd_applyingupdates-prereq}

尝试应用更新之前，请通过单击向下箭头来展开更新条目，然后验证以下信息：
* 更新的版本。必须按时间顺序应用更新，从最早的更新开始一直应用到最新的更新。在应用最新的更新之前，请确保应用了所有先前的更新。例如，在尝试应用 V2.5 更新之前，必须先应用 V2.4 更新。
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

## 对 Cloud Foundation 实例应用更新的过程
{: #sd_applyingupdates-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **Cloud Foundation 实例**表中，单击要更新的实例。
3. 在**摘要**页面上，验证是否所有实例详细信息都正确显示。然后在左侧导航窗格上，单击**基础架构**以验证**基础架构**页面上的详细信息。
   如果未显示详细信息，这可能指示由于防火墙规则或其他网络问题而导致 IBM CloudDriver 虚拟服务器实例 (VSI) 发生连接问题。请解决该问题后，再继续下一步，否则更新可能会失败。
4. 在左侧导航窗格上，单击**更新和补丁**。
5. 单击向下箭头以展开要应用的更新，然后完成下列其中一个步骤：
   *  要立即启动更新，请单击更新条目的**操作**列中的溢出菜单图标，然后单击**立即更新**。
   *  要安排未来更新，请单击更新条目的**操作**列中的溢出菜单图标，然后单击**安排更新**。选择要启动更新的日期、时间和时区。单击**确定**。
6. 如果要在多站点部署配置中将更新应用于 Cloud Foundation 实例，那么会显示标题为**更新所需的步骤**的部分，其中列出多站点部署中所有实例所需的更新操作。必须通过对每个步骤单击**应用更新**来按顺序完成这些步骤。必须等待上一步完成后，才能开始下一步。

## 结果
{: #sd_applyingupdates-results}

1. 启动更新操作之前，会完成实例的运行状况检查。如果运行状况检查失败，那么系统会通知您，以便您可以在应用更新之前解决问题。
2. 在包含 VMware 组件更新的更新期间，可能需要从 ESXi 服务器迁移 VM 以使其进入维护模式。如果 VM 安装了本地数据存储或 CD-ROM，那么可能会阻止 VM 迁移。
3. 在供应新环境期间，{{site.data.keyword.vmwaresolutions_short}} 将创建用于实例管理（包括应用更新）的 **automationuser** 标识。不要更改此用户标识的密码。更改密码可能会导致更新失败。

4. 应用更新后，会在软件更新状态列表中显示一条记录，在其中可以查看更新的详细进度和状态。成功完成更新后，会在安装的软件更新列表中显示一条记录。

  要检索更新作业的最新状态，请单击页面右上角的“刷新”图标。
  {:tip}

5. 有关更新状态的更多信息，请参阅下表。

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

6. 如果更新过程在特定步骤失败，请[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)以获取帮助。IBM 支持人员将向您提供如何解决问题的建议，并指导您从失败的步骤重新启动升级。

## 相关链接
{: #sd_applyingupdates-related}

* [Cloud Foundation 概述](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)
* [Veeam on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
