---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# 升级 HCX 组件
{: #hcxclient-vcs-upgrade}

升级 HCX 是一个简单的过程：使用客户机 Web 用户界面 (UI) 更新客户机端 HCX Manager，以及使用云 Web UI 更新云端 HCX Manager。

必须升级这两端，因为任何系列组件更新都会导致这两端在 HCX Manager 上所安装代码的级别重新部署系列组件。

如果 VMware 支持人员要求提供系统标识，请同时提供客户机端和云端的标识。使用 SSH 登录到 HCX Manager（客户机或云），然后运行 `cat /common/location` 来查找系统标识。

## 相关链接
{: #hcxclient-vcs-upgrade-related}

* [HCX 组件和术语的词汇表](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [准备安装环境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 客户机部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 内部部署服务网](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 混合云迁移](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [监视参数和组件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
