---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-30"

---

# 1.5 版的版本注意事項
{: #relnotes_v15}

此版本包括新增特性、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之提示的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VRF 與典型 SoftLayer 帳戶需求

若為典型 SoftLayer® 帳戶，則 VLAN 跨越是可以在帳戶層次啟用的設定。{{site.data.keyword.vmwaresolutions_short}} 需要啟用 VLAN 跨越。

若為 VRA（虛擬遞送及轉遞）SoftLayer 帳戶，VLAN 跨越的同等項目是一種無法變更的永久設定。VRF 帳戶不需要使用者配置。

在訂購實例之前，請確保 SoftLayer 帳戶是已啟用 VLAN 跨越的 VRF 帳戶或典型（非 VRF）帳戶。否則，訂單可能會失敗。

若要確認 SoftLayer 帳戶是否為 VRF 帳戶，請向「IBM Bluemix 支援中心」確認。若為典型帳戶，您必須遵循[啟用或停用 VLAN 跨越](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}中的指示，來啟用 VLAN 跨越。

## 服務計費模型更新

若為 Cloud Foundation 實例，則引進了新的 _SDDC Manager_ 授權，這是每一個節點的月費。如需相關資訊，請參閱 [Cloud Foundation 實例的技術規格](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview#technical-specifications-for-cloud-foundation-instances)。

## 可用性加強功能

在整個使用者介面中進行了改善：

* 使用者介面上明確指出各種 {{site.data.keyword.CloudDataCents_notm}} 的可用性，以及它們是否具有足夠的庫存來履行訂單。使用這些詳細資料，做出關於 {{site.data.keyword.CloudDataCent_notm}} 的明智決策，以在訂購實例時選取。如需相關資訊，請參閱 [Cloud Foundation 實例的需求及規劃](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_planning)及 [vCenter Server 實例的需求及規劃](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)。
* 對於 Cloud Foundation 實例，當您在輸入欄位中輸入必要資訊時，會以圖形格式自動顯示實例名稱、網域和子網域名稱以及資料中心位置這類資訊。如需相關資訊，請參閱[訂購 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)。
