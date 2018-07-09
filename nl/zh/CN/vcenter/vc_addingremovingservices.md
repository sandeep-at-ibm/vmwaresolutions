---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-21"

---

# 订购、查看和除去 vCenter Server 实例的服务

可以为 VMware vCenter Server 实例订购服务，例如灾难恢复解决方案。不再需要这些服务时，可以将其从实例中除去。

## 可用于 vCenter Server 实例的服务

下表显示了可用于 vCenter Server 实例的服务。

表 1. 可用于 vCenter Server 实例的服务

|服务名称|可用性| 实例支持 |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on IBM Cloud](../services/f5_considerations.html)|是| V1.9 和更高版本 |
| [FortiGate Security Appliance on IBM Cloud](../services/fsa_considerations.html)|是| V1.8 和更高版本 |
| [FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_considerations.html)|是| V2.0 和更高版本 |
| [HyTrust CloudControl on IBM Cloud](../services/htcc_considerations.html)|是| V2.3 和更高版本 |
| [HyTrust DataControl on IBM Cloud](../services/htdc_considerations.html)|是| V2.3 和更高版本 |
| [IBM Spectrum Protect Plus on IBM Cloud](../services/spp_considerations.html)|是| V2.2 和更高版本 |
| [KMIP for VMware on IBM Cloud](../services/kmip_considerations.html)|是| V2.2 和更高版本 |
| [Veeam on IBM Cloud](../services/veeam_considerations.html)|是| V1.8 和更高版本 |
| [VMware HCX on IBM Cloud](../services/hcx_considerations.html)|否| 不适用 |
| [Zerto on IBM Cloud](../services/addingzertodr.html)|是| V1.2 和更高版本 |


## 向 vCenter Server 实例添加服务

要向 vCenter Server 实例添加服务，请单击上表中的相应服务链接以查看服务的注意事项，并检查部署的组件。然后遵循服务订购主题中的指示信息向实例添加服务。

### 服务安装结果

安装服务成功完成后，系统将通过电子邮件通知您，并且该服务会显示在实例的**服务**页面上，状态为**已安装**。

## 查看 vCenter Server 实例的服务

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**部署的实例**。
2. 在 **vCenter Server 实例**表中，单击要查看其服务的实例。
3. 在左侧导航窗格上，单击**服务**。
4. 在**服务**页面上，单击某个服务以查看相关信息，例如服务状态和其他详细信息。
5. 根据查看的服务，可以使用服务详细信息上提供的凭证来访问服务控制台，并在其中管理该服务。

## 除去 vCenter Server 实例的服务

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在 **vCenter Server 实例**表中，单击要除去其服务的实例。
3. 在左侧导航窗格上，单击**服务**。
4. 在**服务**页面上，找到要除去的服务实例，然后单击**删除**图标。
5. 在**删除服务**窗口中，查看注意事项或警告（如有）。选中**我了解**，然后单击**删除**。

### 服务除去结果

接受服务除去请求后，服务状态会更改为**正在除去**。

服务除去成功完成后，系统将通过电子邮件通知您，并且该服务会从实例的**服务**页面中除去。

**注意**：在所除去服务的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。

## 相关链接

* [常见问题](../vmonic/faq.html)
