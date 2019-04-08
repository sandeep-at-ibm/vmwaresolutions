---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# 升级 HCX 组件
{: #vcshcx-upgrade}

升级 HCX 是一个简单的过程：使用客户机 Web 用户界面 (UI) 更新客户机端 HCX Manager，以及使用云 Web UI 更新云端 HCX Manager。必须升级这两端，因为任何系列组件更新都会导致这两端在 HCX Manager 安装的代码的级别重新部署系列组件。如果 VMware 支持人员要求提供系统标识，请同时提供客户机端和云端的标识。使用 SSH 登录到 HCX Manager（客户机或云），然后运行 `cat /common/location` 来查找系统标识。

## 相关链接
{: #vcshcx-upgrade-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
