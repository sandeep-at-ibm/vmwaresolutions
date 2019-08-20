---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-08"

subcollection: vmware-solutions


---
# 向 vCenter 注册 HCX Manager
{: #hcx-archi-reg-vcenter}

在 VMware vSphere Web Client 中注册 Hybrid Cloud Services 插件，然后启动 Hybrid Cloud Services 管理服务。

## 开始之前
{: #hcx-archi-reg-vcenter-prereq}

Hybrid Cloud Services 虚拟设备的电源必须打开后才能进行注册。

## 向 vCenter 注册 HCX Manager 的过程
{: #hcx-archi-reg-vcenter-proc-register}

1. 登录到 Hybrid Cloud Services 服务虚拟设备。例如，`https:My-HCX-Manager:9443/`。
2. 在**仪表板**面板上，完成以下步骤：
  1. 在左侧窗格中的**配置系统**下，选择 vCenter。
  2. 单击右上方的**添加 vCenter**。
  3. 输入 vCenter Server 的 IP 地址，格式为 `https:vCenter-host-name` 或 `https:vCenter-IP-address`。例如，`https:My-vCenter` 或 `https:10.108.26.211`。
  4. 输入 vCenter Server 用户名和密码。使用的帐户必须具有 vCenter 管理员角色。
  5. 单击**确定**。显示_您需要重新启动应用程序_消息时，不要重新启动。
3. 配置查找服务。
  1. 单击**管理**选项卡。
  2. 单击**查找服务 URL** 文本框最右侧的**编辑**按钮。
  3. 输入以下格式的查找网络服务端点：
    * 对于 vCenter Server 5.5u3，输入 `https://ssoip:/7444/lookupservice/sdk`
    * 对于 vCenter Server 6.0u2，输入 `https://ssoip/lookupservice/sdk`
  4. 单击**确定**。显示重新启动 Web 引擎的消息时，不要重新启动。
4. 单击**摘要**选项卡，并找到**混合管理组件**部分。停止并启动应用程序引擎和 Web 引擎。
5. 要最终完成注册，请从 vSphere Web Client 注销。然后，重新登录以验证是否已执行屏幕更新。

## 结果
{: #hcx-archi-reg-vcenter-results}

请注意现有**混合云**图标和左侧的 **Hybrid Cloud Services** 菜单项。Hybrid Cloud Services 注册会更新这些标签。在清单中，图标标签会变为 **Hybrid Cloud Services**。

## 相关链接
{: #hcx-archi-reg-vcenter-related}

* [安装和配置混合服务](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-hybrid)
