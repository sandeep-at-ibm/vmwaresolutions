---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-03"

---

# Zerto

如果您發現 vSphere ESXi 主機無法在補救期間進入維護模式，則可能是 Zerto 正在停止它。如果您已在起始部署後更新 Zerto，則請執行下列步驟來更正此問題。如果您尚未更新，則請遵循[如何讓具有關聯 VRA 的主機進入維護模式](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/)的指示。

1. 登入 Zerto Web 使用者介面。
2. 從下拉功能表中選取**站台設定**。
3. 選取**原則標籤**，並確定已選取**容許 Zerto 在補救期間一律讓主機進入維護模式**。
4. 登出 Zerto。

### 相關鏈結

* [VMware HCX on IBM Cloud 解決方案](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware)（展示）
