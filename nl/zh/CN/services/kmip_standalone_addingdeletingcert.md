---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 添加、查看和删除 KMIP for VMware on IBM Cloud 实例的证书
{: #kmip_standalone_addingdeletingcert}

KMIP for VMware on {{site.data.keyword.cloud}} 实例准备就绪后，必须向其添加证书。不再需要证书时，可以将其从实例中删除。

## 向 KMIP for VMware on IBM Cloud 实例添加证书的过程
{: #kmip_standalone_addingdeletingcert-add}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 向下滚动到 **KMIP for VMware on IBM Cloud 实例**表，然后找到要为其添加证书的实例。
3. 单击**添加**。
4. 在**添加客户机 SSL 证书**窗口中，输入证书名称和内容。

   证书名称不能在所选实例中复用。证书内容必须有效且包含 BEGIN CERTIFICATE 和 END CERTIFICATE 标记，并且证书不能在部署了实例的所选区域中复用。
{:note}
5. 单击**添加**。

## 查看 KMIP for VMware on IBM Cloud 实例证书的过程
{: #kmip_standalone_addingdeletingcert-view}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 向下滚动到 **KMIP for VMware on IBM Cloud 实例**表，然后找到要查看其证书的实例。
3. 在**客户机 SSL 证书**部分下，查看已添加证书的列表。
4. 要查看特定证书的内容，请单击**下载**。

## 从 KMIP for VMware on IBM Cloud 实例中删除证书的过程
{: #kmip_standalone_addingdeletingcert-delete}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 向下滚动到 **KMIP for VMware on IBM Cloud 实例**表，然后单击要删除其证书的实例。
3. 在**客户机 SSL 证书**表中，找到要删除的证书，然后单击**删除**图标。

   对于加密和解密数据或备份数据的用途，客户机会立即失去对所有密钥的访问权。要使客户机重新获得访问权，您必须重新添加客户机 SSL 证书。
{:note}

## 相关链接
{: #kmip_standalone_addingdeletingcert-related}

* [查看 KMIP for VMware on IBM Cloud 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [订购 KMIP for VMware on IBM Cloud 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [删除 KMIP for VMware on IBM Cloud 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker 事件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
