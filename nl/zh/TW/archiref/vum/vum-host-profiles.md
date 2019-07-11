---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

#	 主機設定檔 
{: #vum-host-profiles}

vCenter 具有稱為「主機設定檔」的特性。此特性會建立設定檔來擷取預先配置及已驗證的參照主機配置，並協助系統管理者管理叢集裡的主機配置。「主機設定檔」提供自動化且集中管理的機制，用於主機配置及配置法規遵循。「主機設定檔」可將配置視為受管理物件，其中具有要配置的參數型錄：網路、儲存空間、安全及其他主機層次參數。這些「主機設定檔」可以套用至個別主機、叢集，或與主機設定檔關聯的所有主機及叢集。

由於部署原始叢集的 IBM Cloud for VMware Solutions 自動化已部署其他 VMware vCenter Server on {{site.data.keyword.cloud}} vSphere ESXi 主機越來越多，因此配置偏移會少於手動新增主機的方法。不過，自動化以外的系統管理者動作會讓主機配置不同。例如，新增了更多 NFS 儲存空間，或新增額外的 VLAN。使用「主機設定檔」根據現有主機來檢查此主機的法規遵循以驗證新主機的配置，是 {{site.data.keyword.cloud_notm}} 內此工具的有效使用案例。

若要將更多主機新增至 vCenter Server 叢集，請參閱[擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)。

附註：
*	對於已部署或升級至 2.1 版或更新版本的實例，新部署的 ESXi 伺服器和叢集會以 VMware 的最近但未必最新的 ESXi 更新進行修補。
*	您必須負責處理 VMware 元件的所有其他更新，包括確保新部署的 ESXi 伺服器和叢集具有您需要的所有最近更新。

建議在將新主機新增至叢集之後，讓它進入「維護模式」，以在管理任何工作負載之前，檢閱其法規遵循偏移並重新修補。

檢查法規遵循要求以下順序：
1.	從現有主機建立「主機設定檔」。
2.	將新主機連接至「主機設定檔」。
3.	使用「主機設定檔」來檢查新主機的法規遵循。
4.	檢閱法規遵循失敗，並重新修補。

##	從現有主機建立主機設定檔
{: #vum-host-profiles-create-host-profile}

1.	從 vSphere Web Client 的「首頁」中，按一下**原則及設定檔**。
2.	按一下**主機設定檔**，然後導覽至「主機設定檔」視圖。
3.	按一下**擷取主機的設定檔**圖示。
4.	選取用來作為參照主機的現有主機，然後按**下一步**。
5.	輸入名稱，輸入新設定檔的說明，然後按**下一步**。
6.	檢閱新設定檔的摘要資訊，然後按一下**完成**。
7.	新設定檔即會出現在設定檔清單中。

##	將新主機連接至主機設定檔
{: #vum-host-profiles-attach-to-profile}

1.	從「主機設定檔」主視圖的**設定檔清單**中，選取先前建立要套用至新主機的「主機設定檔」。
2.	按一下**將主機設定檔連接至主機及叢集/分離主機設定檔與主機及叢集**圖示。
3.	從展開的清單中選取新的主機，然後按一下**連接**。
4.	新主機即會新增至「連接的實體」清單。
5.	按**下一步**，然後按一下**完成**。

##	使用主機設定檔來檢查新主機的法規遵循
{: #vum-host-profiles-check-compliance}

1.	導覽至先前已完成的「主機設定檔」。
2.	按一下**檢查主機設定檔法規遵循**圖示。
3.	在**物件**標籤上，法規遵循狀態會更新為：_Compliant、Unknown 或 Non-compliant__。non-compliant 狀態指出設定檔與新主機之間發生探索到且特定的不一致。

##	檢閱法規遵循失敗及補救
{: #vum-host-profiles-review-compliance}

1. 若要查看法規遵循失敗的其他詳細資料，請從法規遵循檢查所使用的**物件**標籤中選取**主機設定檔**。
2. 若要查看法規遵循失敗之主機與「主機設定檔」間之不同參數的特定詳細資料，請按一下**監視**標籤，然後選取**法規遵循**視圖。
3. 展開物件階層，並選取失敗的主機。
4. 不同的參數即會顯示在「法規遵循」視窗的階層下方。
5. 檢閱參數，並瞭解新主機可能與參照主機不同的原因。對於不接受法規遵循的參數，請在新主機移出維護模式之前重新修補。例如，系統管理者動作導致配置變化。

## 相關鏈結
{: #vum-host-profiles-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware)（示範）
