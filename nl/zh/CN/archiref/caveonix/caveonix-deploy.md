---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight 的部署模型
{: #caveonix-deploy}

此部分描述了 Caveonix RiskForesight 的部署模型以及安装解决方案的安装过程。

选择 {{site.data.keyword.vmwaresolutions_full}} RiskForesight 选项时，不必像自动执行的初始部署步骤那样，执行部署中的所有步骤。但是，要了解完整部署和体系结构，以及要在初始部署后横向扩展解决方案，就需要详细了解这些步骤。

RiskForesight 安装包含以下高级别步骤：

1. [初始规划和先决条件](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step1) - 了解和选择部署选项，配置 DNS 以便为应用程序组件提供 FQDN/IP 解析。
2. [虚拟机部署](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step2) - 通过 OVF 模板部署 VM。VM 已安装在所有应用程序组件上。
3. [应用程序配置](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step3) - 运行用于在每个 VM 上配置应用程序组件的 Caveonix 配置脚本。
4. [应用程序设置](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step4) - 设置服务提供者和租户或组织，以便用户可以访问应用程序。

自动执行的安装会供应一个 VM，并在该 VM 上配置所有应用程序组件。
{:note}

## 部署大小调整
{: #caveonix-deploy-sizing}

部署大小调整是使用以下卷进行计算的。

表 1. 卷

|数据类型|卷|
|---|---|
|每天扫描数|1|
|扫描数据 (MB)|20|
|日志数据 (MB)|500|
|流数据 (MB)|200|
|资产数据 (MB)|46|
|每天每个资产的总存储量 (MB)|766|
|数据复制乘数|2|
|每天每个资产的总索引存储量 (MB)|1532|

数据复制乘数设置为 2，因为缺省情况下，索引存储 (Elastic Search) 会对索引使用 n+1 复制。
{:note}

“缩放 VM 数”是通过“资产数”和“要建立索引的数据的天数”计算的。

表 2. 缩放 VM 参数

|资产数|100|500|5000|
|---|---|---|---|
|数据的天数|30|30|30|
|每天每个资产的总索引存储量 (MB)|1532|1532|1532|
|30 天每个资产的总索引存储量 (TB)|4|22|219|
|每个缩放节点支持的数据量 (TB)|0|8|8|
|需要的缩放 VM 数|0|3|27|

所需存储量的计算如下所示：

表 3. 存储量参数

|资产数|100|500|5000|
|---|---|---|---|
|长期数据保留时间（月）|8|8|8|
|每天每个资产的总存储量 (MB)|766|766|766|
|数据的天数|30|30|30|
|近期数据保留 (TB)|7|33|329|
|长期数据保留 (TB)|18|88|877|

从数据角度来看，数据用途如下所示：

-	扫描数据用于合规性管理
-	日志数据用于取证管理
-	策略和流数据用于风险管理，流数据仅可通过 NSX Manager 提供

数据存储包含三个层：

-	已复制
-	近期
-	长期

下表提供了部署的摘要：

表 4. 摘要

|部署模型|“一体化”|部分分布式|完全分布式|
|---|---|---|---|
|资产数|100|500|5000|
|30 天内生成的联机数据 (TB)|4|22|219|
|近线数据保留（90 天）(TB)|7|33|329|
|离线数据保留（8 个月）(TB)|18|88|877|
|总数据存储保留（1 年）(TB)|28|142|1425|
|基本 VM 数|1|1|20|
|缩放 VM 数|0|3|28|
|VM 总数|1|4|48|

**注：**
除去 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务时，{{site.data.keyword.vmwaresolutions_short}} 自动化仅删除已部署的单个“一体化”Caveonix VM 以及为其订购的专用子网。因此，
* 如果 Caveonix VM 已横向扩展为多个 VM，那么不会除去这些额外的 VM。 
* 如果在额外的 VM 上使用专用子网的 IP 地址，那么这些 VM 必须分配有新的 IP 地址才能继续正常运行。 
* 如果删除已安装了 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务的 vCenter Server 实例 A，并且您已使用在 vCenter Server 实例 B 中为该服务订购的专用子网的 IP 地址，那么在删除 vCenter Server 实例 A 时将取消该专用子网。

## 相关链接
{: #caveonix-deploy-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
