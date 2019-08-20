---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Caveonix view license, Caveonix manage license, delete Caveonix license

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 Caveonix RiskForesight 许可证
{: #caveonix_license_managing}

您可以查看或删除为独立使用而订购的 Caveonix RiskFoesight 许可证，或者编辑这些许可证的注释。

## 查看 Caveonix RiskForesight 许可证的过程
{: #caveonix_license_managing_procedure-view}

1. 单击左侧导航窗格中的**资源**，然后向下滚动到 **Caveonix RiskForesight 许可证**表。

   |项|描述|
   |:-----|:------------|
   |名称|许可证的名称。|
   |创建时间|创建许可证的日期和时间。|
   |状态|许可证的状态：<br>正在修改：正在创建许可证。<br>已安装：许可证已准备就绪可供使用。<br>正在除去：正在删除许可证。|
   {: caption="表 1. Caveonix RiskForesight 许可证项的描述" caption-side="top"}

2. 要查看特定许可证的详细信息，请单击该许可证。

## 编辑 Caveonix RiskForesight 许可证的注释的过程
{: #caveonix_license_managing_procedure-edit}

1. 在左侧导航窗格中，单击**资源**。
2. 向下滚动到 **Caveonix RiskForesight 许可证**表，然后单击要编辑其注释的许可证。
3. 在许可证详细信息页面上，编辑许可证注释，然后单击**确认**。

## 有关许可证日期显示的已知问题
{: #caveonix_license_considerations-date}

如果您使用的是 Mozilla Firefox 浏览器，那么可能会在 Caveonix RiskForesight 控制台上显示没有值的许可证开始和结束日期。要解决此问题，请在其他浏览器（例如，Google Chrome）中查看许可证信息。

如果您遇到此问题，而您只能使用 Firefox 浏览器，请联系 [Caveonix Support](https://www.caveonix.com/support/){:external} 以获取帮助。
{:note}

## 删除 Caveonix RiskForesight 许可证的过程
{: #caveonix_license_managing_procedure-delete}

删除 Caveonix RiskForesight 许可证不会除去 vCenter Server 实例上安装的 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务。要除去该服务，必须在 {{site.data.keyword.vmwaresolutions_short}} 控制台中执行此操作。有关更多信息，请参阅[除去 vCenter Server 实例的服务的过程](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure)。
{:note:}

1. 在左侧导航窗格中，单击**资源**。
2. 向下滚动到 **Caveonix RiskForesight 许可证**表，并找到要删除的许可证。
3. 在**操作**列中，单击“删除”图标。
4. 在**删除许可证**窗口中，单击**确定**。许可证的状态会更改为**正在除去**。完成许可证删除后，该许可证在 **Caveonix RiskForesight 许可证**表中不再可用。

## 相关链接
{: #caveonix_license_managing-related}

* [Caveonix RiskForesight 概述]()
* [订购 Caveonix RiskForesight 许可证](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)
