---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: notifications console, filter notifications, system notification

subcollection: vmware-solutions


---

# 管理系统通知
{: #notifications}

您可以检查系统或用户操作的状态的通知。还可以使用这些信息对可能发生的问题进行调查。

## 查看通知
{: #notifications-view}

1. 在 {{site.data.keyword.vmwaresolutions_full}} 控制台中，单击左侧导航窗格中的**通知**。
2. 查看有关所有通知的摘要。

|列|描述|
|:------ |:----------- |
|严重性|通知所报告的事件的严重性。<br>**严重**：严重事件可能会影响整个系统或服务。<br>**错误**：在操作期间发生错误事件，可能需要管理员或用户的干预。<br>**警告**：组件发生故障或未正常工作。但是，故障并未中断组件的持续处理。<br>**参考**：系统或用户操作已完成。通常，以下事件会报告参考通知：
       <br>服务已安装。<br>服务已升级。<br>服务已除去。<br>已针对添加的 ESXi 服务器重新配置所有服务。<br>已针对除去的 ESXi 服务器重新配置所有服务。|
|类型|报告的事件与之相关的组件类型：vCenter Server 实例、服务或系统|
|资源|发送通知的实例或服务的名称。|
|描述|通知的简短描述。|
|日期|发送通知的日期和时间。|
{: caption="表 1. 通知历史记录" caption-side="top"}

3. 单击通知所在行可查看该通知的详细信息。

## 过滤通知
{: #notifications-filter}

缺省情况下，将显示所有未读通知。可以按状态、严重性和类型来过滤通知。要过滤通知，请在**状态**、**严重性**或**类型**列表中仅选中要显示的项所对应的复选框。

## 相关链接
{: #notifications-related}

* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [用户帐户和设置](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
