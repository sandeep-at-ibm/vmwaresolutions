---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# 虛擬機器 vSAN 備援
{: #vum-vsan-redundancy}

當您讓 vSAN 叢集上的 vSphere ESXi 主機進入維護模式時，需要選取資料撤除模式。模式選擇可能會影響將使用 vSAN 資料儲存庫的虛擬機器 (VM) 及應用裝置：
* **完整資料移轉**會撤除主機中的所有資料，並將它移至 vSAN 叢集裡的其他 vSphere ESXi 主機。此撤除模式會導致最大資料傳送數量，並使用最多時間及資源。所選取主機之本端儲存空間上的所有元件都會移轉至叢集裡的其他位置。主機進入維護模式時，所有 VM 及應用裝置都可以存取其儲存空間元件，而且仍然遵循其指派的儲存空間原則。完整資料撤除可能需要很長的時間，而且可以讓升級的維護時間有較長的持續時間。
* **確保可存取性資料撤除**模式是預設選項，而且在 vSphere ESXi 主機進入維護模式時，vSAN 可確保主機上的所有可存取的 VM 或應用裝置仍可供存取。由於僅發生局部資料撤除，所以 VM 或應用裝置在撤除期間可能不再完全遵循 VM 儲存空間原則，而且可能無法存取其所有抄本。如果在主機處於維護模式時發生失敗，且要容忍的主要失敗層次設為 1，則會發生資料流失，而且 VM 或應用裝置可能無法使用。
* 在**無資料移轉**模式中，vSAN 在進入維護模式時不會撤除主機中的任何資料。雖然這樣會縮短進入維護模式的時間，因而縮減維護時間的持續時間，但部分 VM 或應用裝置可能會變成無法存取。

本節會建立新的 VM 儲存空間原則，容許選取**確保可存取性資料撤除**模式來縮減維護時間，但也降低當某部主機處於維護模式時另一部主機的失敗導致 VM 或應用裝置無法存取的風險。對於不接受 vSAN 主機進入維護模式而變成非備用的任何 VM 或應用裝置，在完成任何補救動作之前，請先完成下列處理程序。需要至少有 6 部主機的叢集。

1. 建立設定為 RAID 5/6 及 FTT =2 (RAID 6) 的新 vSAN 設定檔，然後針對必要的 VM 或應用裝置套用此原則。

2. 先等待 vSAN 完成同步，再起始所有補救動作。導覽至叢集的 **vSAN Virtual Objects 監視**頁面，並檢閱**完成狀態**，來檢查完成狀態。

## 相關鏈結
{: #vum-vsan-redundancy-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_full}} Demos](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/)（示範）
