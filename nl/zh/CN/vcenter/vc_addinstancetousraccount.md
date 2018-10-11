---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# 将 V2.5 之前的 vCenter Server 实例迁移到 IBM Cloud 帐户

在 {{site.data.keyword.cloud}} 帐户中 V2.5 和更高发行版中部署的 VMware vCenter Server 实例会自动添加到帐户，并由 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 进行管理。

对于部署在 V2.4 和更低发行版中的实例，可以将其迁移到指定的 {{site.data.keyword.cloud_notm}} 帐户，以进行支持 IAM 的用户管理。

## 开始之前

确保要将实例迁移到的 {{site.data.keyword.cloud_notm}} 帐户不是仅 IaaS 帐户。仅 IaaS 帐户是未链接到 {{site.data.keyword.cloud_notm}} 帐户的 {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) 帐户。

有关如何将仅 IaaS 帐户链接到 PaaS 帐户的更多信息，请参阅[执行以下步骤来链接 IaaS 和 PaaS 帐户](https://www.ibm.com/blogs/bluemix/2018/03/follow-steps-link-iaas-paas-accounts/)。

## 迁移实例的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在控制台条幅中，单击您的用户帐户图标，然后单击**帐户**字段以选择要将实例迁移到的用户帐户。
3. 在 **vCenter Server 实例**表中，找到 V2.5 之前的实例。
4. 在**操作**列中，单击溢出菜单图标，然后单击**将实例迁移到帐户**。
5. 在**将实例迁移到帐户**窗口中，确认要将实例迁移到的帐户，然后单击**迁移**。

### 结果

1. 您将收到控制台通知，指示已接受您要将实例迁移到指定 {{site.data.keyword.cloud_notm}} 帐户的请求。
2. 实例迁移完成后，实例将显示在**部署的实例**页面上它所迁移到的帐户下。迁移的实例不会再显示在从中迁移该实例的原始帐户中。

### 相关链接

* [使用 IAM 管理用户访问权](../vmonic/iam.html)
* [邀请用户访问服务和资源](../vmonic/iamuserinvite.html)
* [什么是 IBM Cloud IAM](../../../iam/index.html)
