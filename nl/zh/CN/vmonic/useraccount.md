---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-03"

---

# 管理用户帐户和设置

{{site.data.keyword.vmwaresolutions_full}} 通过 {{site.data.keyword.slapi_short}} 调用与 {{site.data.keyword.cloud_notm}} 基础架构进行通信。要安全地访问 {{site.data.keyword.slapi_short}}，必须将您的 {{site.data.keyword.cloud_notm}} 帐户的凭证与 {{site.data.keyword.vmwaresolutions_short}} 用户帐户相关联。

**注**：{{site.data.keyword.cloud_notm}} 帐户先前称为 IBM SoftLayer 帐户。

在 {{site.data.keyword.vmwaresolutions_short}} 控制台上，还可以指定是否要针对各种事件接收电子邮件通知。

## 开始之前

* 只能将一个 {{site.data.keyword.cloud_notm}} 帐户与您的 {{site.data.keyword.vmwaresolutions_short}} 用户帐户相关联。
* 要使用的 {{site.data.keyword.cloud_notm}} 帐户必须满足特定需求。有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} 帐户需求](slaccountrequirement.html)。
* 如果 {{site.data.keyword.cloud_notm}} 帐户中的 API 密钥发生更改，那么必须更新 {{site.data.keyword.vmwaresolutions_short}} 用户帐户中的密钥。

   **重要信息**：您负责确保**设置**页面上保存的 API 密钥正确且最新。
   否则，需要 API 密钥验证的操作可能会失败。

要将 {{site.data.keyword.vmwaresolutions_short}} 帐户与 {{site.data.keyword.cloud_notm}} 帐户相关联，请在 {{site.data.keyword.vmwaresolutions_short}} 控制台的**设置**页面上输入 {{site.data.keyword.cloud_notm}} 帐户凭证。

在关联 {{site.data.keyword.cloud_notm}} 帐户之后，控制台会自动检索 {{site.data.keyword.cloud_notm}} 帐户凭证，以与 {{site.data.keyword.cloud_notm}} 上的 VMware 环境进行通信。

## 过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**设置**。
2. 如果希望发生新事件时获得电子邮件通知，请选中**启用电子邮件通知**复选框。
3. 如果希望发生新事件时在控制台上获得通知，请选中**启用控制台通知**复选框。
4. 在 **IBM Cloud 基础架构凭证**区域中，输入 {{site.data.keyword.cloud_notm}} 帐户的用户名，然后按照控制台上的指示信息输入 {{site.data.keyword.slapi_short}} 密钥。
5. 单击**保存凭证**。

## 结果

存储的 {{site.data.keyword.cloud_notm}} 帐户凭证将用于未来需要与 {{site.data.keyword.cloud_notm}} 基础架构进行交互的操作。如果针对某些实例事件启用了电子邮件通知或控制台通知，那么在发生这些事件时，将通过电子邮件或控制台消息通知您。

## 相关链接

* [常见问题](faq.html)
* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)
* [订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)
* [通知](notifications.html)
* [SoftLayer API](../../../customer-portal/cpapi.html){:new_window}
