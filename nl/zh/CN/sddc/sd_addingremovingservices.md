---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# 订购、查看和除去 Cloud Foundation 实例的服务

可以为 VMware Cloud Foundation 实例订购服务，例如灾难恢复解决方案。不再需要这些服务时，可以将其从实例中除去。

## 可用于 Cloud Foundation 实例的服务

下表显示了可用于 Cloud Foundation 实例的服务以及已安装服务的版本。

表 1. 可用于 Cloud Foundation 实例的服务

|服务名称|当前服务版本|实例版本|
|----------------------------------------------------------------------------------------|------------------|
|[F5 on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services/f5_considerations.html)|BIG-IP VE V13.1.1.2| V1.9 和更高版本 |
|[FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fsa_considerations.html)|300 系列| V1.8 和更高版本 |
|[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_considerations.html)|6.0.3| V2.0 和更高版本 |
|[HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html)|5.4.0| V2.3 和更高版本 |
|[HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_considerations.html)|4.2.1| V2.3 和更高版本 |
|[HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_considerations.html)|4.2|V2.5 和更高版本|
|[IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/spp_considerations.html)|10.1.2| V2.2 和更高版本 |
|[KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html)|2.0|不适用|
|[Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/veeam_considerations.html)|9.5u3| V1.8 和更高版本 |
|[Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/addingzertodr.html)|6.0 Update 3| V1.2 和更高版本 |

## 向 Cloud Foundation 实例添加服务的过程

要向 Cloud Foundation 实例添加服务，请单击上表中的相应服务链接以查看服务的注意事项，并检查部署的组件。然后，按照相应的订购服务主题中的指示信息将服务添加到实例。

### 服务安装结果

安装服务成功完成后，系统将通过电子邮件通知您，并且该服务会显示在实例的**服务**页面上，状态为**已安装**。

## 查看 Cloud Foundation 实例的服务的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**已部署的实例**。
2. 在 **Cloud Foundation 实例**表中，单击要查看其服务的实例。
3. 在左侧导航窗格上，单击**服务**。
4. 在**服务**页面上，单击某个服务以查看相关信息，例如服务状态和其他详细信息。
5. 根据查看的服务，可以使用服务详细信息中提供的凭证来访问服务控制台，并可在其中管理该服务。

## 除去 Cloud Foundation 实例的服务的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**已部署的实例**。
2. 在 **Cloud Foundation 实例**表中，单击要除去其服务的实例。
3. 在左侧导航窗格上，单击**服务**。
4. 在**服务**页面上，找到要除去的服务实例，然后单击**删除**图标。
5. 在**删除服务**窗口中，查看注意事项或警告（如有）。选中**我了解**，然后单击**删除**。

### 服务除去结果

接受服务除去请求后，服务状态会更改为**正在除去**。

服务除去成功完成后，系统将通过电子邮件通知您，并且该服务会从实例的**服务**页面中除去。

在所除去服务的 {{site.data.keyword.cloud_notm}} 计费周期结束之前，仍然会对您计费。
{:note}

### 相关链接

* [常见问题](/docs/services/vmwaresolutions/vmonic/faq.html)
