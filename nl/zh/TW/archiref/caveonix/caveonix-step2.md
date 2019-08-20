---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# 步驟 2 - 虛擬機器部署
{: #caveonix-step2}

{{site.data.keyword.vmwaresolutions_full}} 自動化會要求一個額外的可攜式專用 IP 子網路，且「全功能」虛擬機器 (VM) 會以這個子網路的 IP 位址進行配置，因此，Caveonix RiskForesight 元件可以：

- 透過 BCR 連接至 vCenter 及 NSX Manager。
- 連接至「遠端收集器」，可在 VXLAN 上進行或由遠端部署管理。
- 容許在擴充時由用戶端管理 IP 位址空間。
