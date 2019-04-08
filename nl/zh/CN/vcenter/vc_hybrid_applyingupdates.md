---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 对 vCenter Server with Hybridity Bundle 实例应用更新
{: #vc_hybrid_applyingupdates}

对 vCenter Server with Hybridity Bundle 实例应用补丁和更新的过程仅对管理组件自动执行。必须手动应用 VMware 更新。

## 开始之前
{: #vc_hybrid_applyingupdates-prereq}

从 V2.5 开始，不会再列出 IBM CloudDriver 更新，因为已启用自动更新。添加主机、添加集群和订购服务等操作会自动将实例更新到最新版本。有关自动更新的更多信息，请参阅 [V2.5 发行说明](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-relnotes_v25)中的 *IBM CloudDriver 弹性*部分。
{:note}

尝试应用更新之前，请通过单击向下箭头来展开更新条目，然后验证以下信息：
* 更新的版本。必须按时间顺序应用更新，从最早的更新开始一直应用到最新的更新。在应用最新的更新之前，请确保应用了所有先前的更新。例如，在尝试应用 V2.4 更新之前，必须先应用 V2.3 更新。
* 是否需要停机时间。
* 完成更新的估计总时间。
* 更新对 VMware 虚拟环境的影响。
* 更新详细信息。

下表显示不同的更新级别对系统产生的影响。

表 1. 更新级别和影响

|更新级别|影响|  
|:------------- |:------------- |
|低|此更新不会影响任何系统。不必在安排的停机时间内应用更新。|  
|中|此更新可能会影响某些系统。建议在安排的停机时间内应用更新。|  
|重大|此更新会影响部分系统或所有系统。必须在安排的停机时间内应用更新。|  

## 对 vCenter Server with Hybridity Bundle 实例应用更新的过程
{: #vc_hybrid_applyingupdates-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_full}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要更新的实例。
3. 在**摘要**页面上，验证是否所有实例详细信息都正确显示。然后在左侧导航窗格上，单击**基础架构**以验证**基础架构**页面上的详细信息。
   如果未显示详细信息，这可能指示由于防火墙规则或其他网络问题而导致 IBM CloudDriver 虚拟服务器实例 (VSI) 发生连接问题。请解决该问题后，再继续下一步，否则更新可能会失败。
4. 在左侧导航窗格上，单击**更新和补丁**。

   **更新和补丁**页面仅包含用于更新 IBM 管理组件的软件包，而不包含 VMware 更新。执行以下操作时，{{site.data.keyword.vmwaresolutions_short}} 会应用 VMware 更新：
   * 部署新的 vCenter Server 实例时。
   * 添加新的 ESXi 服务器后，将使用 VMware 更新供应新的 ESXi 服务器，但不会更新现有 ESXi 服务器。
   * 添加新的集群后，将使用 VMware 更新供应新的集群，但不会更新现有集群。
   {:note}

5. 要升级许可证，请单击**升级**。从列表中选择要升级的版本，然后单击**升级**。许可证版本降级不可用。

   许可证升级将替换实例上的所有现有 NSX 许可证。如果在计费周期内进行升级，那么可能会因旧许可证与新许可证重叠而发生额外费用。为了避免发生额外费用，建议在计费周期结束时升级许可证。
   {:note}

6. 对于软件更新，单击向下箭头以展开要应用的更新，然后完成下列其中一个步骤：
   *  要立即启动更新，请单击更新条目的**操作**列中的溢出菜单图标，然后单击**立即更新**。
   *  要安排未来更新，请单击更新条目的**操作**列中的溢出菜单图标，然后单击**安排更新**。选择要启动更新的日期、时间和时区。单击**确定**。
7. 如果要在多站点部署配置中将更新应用于 vCenter Server 实例，那么会显示标题为**更新所需的步骤**的部分。此部分列出多站点部署中所有实例所需的更新操作。必须通过对每个步骤单击**应用更新**来按顺序完成这些步骤。必须等待上一步完成后，才能开始下一步。   

## 结果
{: #vc_hybrid_applyingupdates-results}

1. 应用更新后，会在软件更新状态列表中显示一条记录，在其中可以查看更新的详细进度和状态。成功完成更新后，会在安装的软件更新列表中显示一条记录。

  要检索更新作业的最新状态，请单击页面右上角的“刷新”图标。
  {:tip}

2. 有关更新状态的详细信息，请参阅以下列表：
<dl class="dl">
<dt class="dt dlterm">可用</dt>
<dd class="dd">更新可供应用。在应用所有先前更新之后，才能选择可用更新。</dd>
<dt class="dt dlterm">进行中</dt>
<dd class="dd">更新作业已启动，但尚未完成。在当前更新作业完成之前，不能应用其他任何更新。</dd>
<dt class="dt dlterm">已安装</dt>
<dd class="dd">更新作业已完成。将更新 VMware 平台的相应组件。</dd>
<dt class="dt dlterm">失败</dt>
<dd class="dd">更新作业失败。控制台报告有关更新失败的错误。请复查错误并修正报告的问题，然后重新应用更新。</dd>
<dt class="dt dlterm">已安排</dt>
<dd class="dd">更新作业已安排为日后执行。更新作业会在安排的时间自动启动。</dd>
<dt class="dt dlterm">未知</dt>
<dd class="dd">无法获取更新作业的状态。请联系 IBM 支持人员以获取帮助。</dd>
</dl>

3. 如果更新过程在特定步骤失败，请[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)以获取帮助。IBM 支持人员将向您提供如何解决问题的建议，并指导您从失败的步骤重试升级。

## 相关链接
{: #vc_hybrid_applyingupdates-related}

* [vCenter Server with Hybridity Bundle 概述](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
