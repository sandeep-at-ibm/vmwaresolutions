---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# 套用原生 NIC 驅動程式
{: #vum-applying-nic}

ESXi 6.5 包含許多新的原生驅動程式，其為舊版 vmklinux 驅動程式的取代項目。在安裝或升級之後，依預設會啟用大部分的新原生驅動程式，但依預設會停用其中三個新的原生驅動程式，因為它們未完全支援對應 vmklinux 驅動程式的功能。

ixgben 是一種原生驅動程式，可取代 vmklinux net-ixgbe 驅動程式，但不支援 SR-IOV 及 SW FcOE。佈建您的 vSphere ESXi 主機時，ICVS 自動化不會啟用此驅動程式。建議啟用此驅動程式，以獲得它帶來的效能優勢。本附錄所述的下列程序顯示如何使用「vSphere 指令行 (vCLI)」來啟用及停用原生驅動程式。

開始進行這項作業之前，請從 [{{site.data.keyword.cloud}} 基礎架構入口網站](https://control.softlayer.com/devices)中擷取所有實體主機 IPMI IP 位址、登入 ID 及密碼。這在取消或檢查升級進度時是必要的，其中沒有主機的直接網路存取權。

對於每部主機，依序：
1. 使用 vSphere Web Client 讓 vSphere ESXi 主機進入維護模式，方法是選取**首頁** > **主機及叢集**。在「導覽器」窗格中，選取 vSphere ESXi 主機，在主機上按一下滑鼠右鍵，然後選取**維護模式** > **進入維護模式**。因為主機是自動化 DRS 叢集的一部分，所以會在主機進入維護模式時將虛擬機器移轉至不同的主機。
2. 使用「IC4VS 主控台」中的詳細資料，以 SSH 到 vSphere ESXi 主機。
3. 執行下列 vCLI 指令，以啟用 ixgben 原生驅動程式：
  `esxcli system module set --enabled=true --module=ixgben`
4. 執行下列 vCLI 指令，以重新啟動 vSphere ESXi 主機：
  `system shutdown reboot --reason “Install ixgben driver”`
5. 在使用 SSH 重新啟動 vSphere ESXI 主機之後，請重新登入主機，發出下列 vCLI 指令，然後確認 ixgben 驅動程式「已載入」（第一欄）且「已啟用」（第二欄）：
  `esxcli system module list |grep ixg`
6. 如果已啟用驅動程式，則使用 vSphere Web Client 在「導覽器」窗格中選取主機，按一下滑鼠右鍵，然後選取**維護模式** > **結束維護模式**。選取下一部主機，並啟用驅動程式，直到完成所有主機為止。
7. 如果變更未作用，而要回復，請執行下列指令：
  `esxcli system module set --enabled=false --module=ixgben`

8. 如果您無法透過網路連接至主機，請使用 {{site.data.keyword.cloud_notm}} 主控台視窗，從 IPMI 主控台執行前一個指令。
9. 重新啟動 vSphere ESXi 主機之後，您現在會觀察到已載入並已啟用預設 ixgbe 驅動程式。

如果您需要回復，而且無法 SSH 至 vSphere ESXi 主機，則需要透過 {{site.data.keyword.cloud_notm}} 主控台視窗登入需要回復之主機的 KVM 主控台。

使用 {{site.data.keyword.cloud_notm}} 控制視窗中列出的 ID 及密碼與 IPMI IP 位址，以登入 IPMI Web 介面。您需要透過 VPN 連接至主機所在的資料中心。如需相關資訊，請參閱[開始使用 VPN](/docs/infrastructure/iaas-vpn?topic=VPN-getting-started-with-virtual-private-networking-vpn-)。

1. 移至 vSphere ESXi 主機的「裝置詳細資料」、「遠端管理」頁面，然後選取**動作** > **KVM 主控台**。會開啟另一個視窗，供您輸入「IPMI 使用者」及「密碼」。
2. 選取**遠端控制** > **iKVM/HTML5**，然後按一下 **iKVM/HTML5** 以重新啟動。您現在可以存取 vSphere ESXi 主機的主控台。
3. 如果主機正在回應指令，請在主控台中使用 **ALT-F1** 來存取 ESXi 主機主控台。請使用主機的認證來登入。
4. 如果主機沒有回應，請使用 IPMI 功能表啟動主機電源。
5. 在主機重新啟動時，請仔細監看 HTML5 主控台。當 ESXi 重新啟動時，您只有數秒鐘的時間可以進入回復模式。
6. 同時按 **CMD + R** 鍵，以進入回復模式。
7. 鍵入 **"Y"** 以進入回復模式，並使用舊版本啟動 ESXi 伺服器。
8. 透過主控台監視其進度。開機可能需要 10 - 20 分鐘。

## 相關鏈結
{: #vum-applying-nic-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware)（示範）
