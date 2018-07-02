---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-19"

---

# 删除多站点配置中的 vCenter Server 实例

计划删除属于多站点配置的 vCenter Server 实例之前，有一些特殊注意事项需要留意。

删除 vCenter Server 实例时，会按顺序释放以下组件：
1. 所有部署的服务
2. 支持和服务费用
3. VMware 产品许可证
4. ESXi 服务器
5. 子网
6. VLAN

由于资源依赖关系，删除实例后，不会立即释放该实例中的组件。例如，在 {{site.data.keyword.cloud}} 基础架构完全回收 ESXi 服务器（在 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束时发生）后，才能删除子网和 VLAN。在 {{site.data.keyword.cloud_notm}} 基础架构计费周期（通常为 30 天）结束时，将删除子网和 VLAN，此时实例删除操作完成。

**注意**：在所删除实例的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。

## 过程

1. 从辅助 vCenter Server 实例中除去所有服务。
2. 确保没有任何 NSX 对象扩展到要删除的辅助实例中。
3. 从主 SSO (Single Sign-On) 域中删除辅助 vCenter 和 PSC (Platform Services Controller)。有关更多信息，请参阅[从 Single Sign-On 取消注册 vCenter Server](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}。
4. 降级本地域控制器 VSI（虚拟服务实例）。有关更多信息，请参阅[降级域控制器和域](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}。
5. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中删除辅助 vCenter Server 实例。
6. 对于多站点配置中的所有辅助 vCenter Server 实例，重复步骤 1 到 5。
7. 删除所有辅助实例后，还可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台中删除主实例。

## 相关链接

* [删除 vCenter Server 实例](vc_deletinginstance.html)
* [订购、查看和除去 vCenter Server 实例中的服务](vc_addingremovingservices.html)
