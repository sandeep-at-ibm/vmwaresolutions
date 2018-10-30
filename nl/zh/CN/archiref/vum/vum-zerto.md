---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-03"

---

# Zerto

如果发现 vSphere ESXi 主机无法在修复过程中进入维护模式，那么可能是因为 Zerto 正在停止该主机。如果自初始部署后已更新 Zerto，请执行以下步骤来更正此问题。如果尚未更新，请遵循[如何将具有关联的 VRA 的主机置于维护模式](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/)中的指示信息进行操作。

1. 登录到 Zerto Web UI。
2. 从下拉菜单中选择**站点设置**。
3. 选择**策略**选项卡，并确保选中**允许 Zerto 在修复过程中始终使主机进入维护模式**。
4. 从 Zerto 注销。

### 相关链接

* [VMware HCX on IBM Cloud 解决方案](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud 数字技术互动](https://ibm-dte.mybluemix.net/ibm-vmware)（演示）
