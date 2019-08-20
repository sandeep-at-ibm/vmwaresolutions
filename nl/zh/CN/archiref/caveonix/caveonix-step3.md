---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# 步骤 3 - 应用程序配置
{: #caveonix-step3}

此步骤使用 Caveonix RiskForesight 配置脚本。对于“一体化”部署，此脚本通过 IBM Cloud for VMware Solutions 自动化来启动。

要进行缩放，客户机需要调用该脚本，以供应部分或完全分布式拓扑。此脚本会配置 RiskForesight 服务：
- Caveonix 应用程序（API 和中央收集器）
- Elastic Search
- PostgresSQL
- 远程收集器
- UI
- Kafka
- Kibana
- 所有服务的证书

在此步骤结束时，应用程序组件会安装在必需的虚拟机 (VM) 上。
