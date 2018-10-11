---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# 确保 VMware Federal 实例安全

完成以下过程，以确保已部署 VMware Federal 实例的安全，即，除去用于持续访问实例的开放式管理连接。

## 开始之前

查看以下信息，以了解确保已部署 VMware Federal 实例安全的结果：

* 在完成此过程之前，记录并保存环境可能需要的任何凭证。启动安全操作后，环境的所有凭证都将从 {{site.data.keyword.vmwaresolutions_full}} 数据库中擦除，并且无法取回。
* 在启动安全操作之后，将禁用其他所有管理功能，但完全实例删除操作除外。

## 确保 VMware Federal 实例安全的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在 **vCenter Server 实例**表中，单击要确保安全的实例。
3. 单击 **vCenter 控制台**旁边的溢出菜单图标。
4. 单击**确保实例安全**。
5. 单击**确定**以确认要将实例与自动化断开连接。
   

  **注**：在完成此步骤之前，请确保查看**开始之前**部分中的信息。

6. 除去环境中面向公众的管理服务 VMware NSX Edge Services Gateway (ESG)，也可以选择除去在自动化期间部署的由客户机管理的 ESG。
7. 重置 IBM 自动化所使用的所有帐户的密码或密钥。有关更多信息，请参阅 [How can I secure my environment to remove access by IBM automation and support?](https://developer.ibm.com/answers/questions/452354/how-can-i-secure-my-environment-to-remove-access-b/)。

## 结果

实例的状态会更改为**正在修改**。

成功确保实例安全后，该实例的状态会更改为**已保护**，并且只有实例属性和部署历史记录可用。

### 相关链接

* [VMware Federal on {{site.data.keyword.cloud_notm}} 概述](vc_fed_overview.html)
* [订购 VMware Federal 实例](vc_fed_orderinginstance.html)
* [查看 VMware Federal 实例](vc_fed_viewinginstance.html)
* [删除 VMware Federal 实例](vc_fed_deletinginstance.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
