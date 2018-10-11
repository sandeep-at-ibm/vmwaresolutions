---

copyright:

  years:  2016, 2018

lastupdated: "2016-11-04"

---

# 1.1 版的版本注意事項

此版本包括新增特性、可用性加強功能及錯誤修正程式。如需不同版本的已修正問題、產品的已知問題以及使用 {{site.data.keyword.vmwaresolutions_full}} 之要訣的清單，請參閱 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VLAN 跨越需求

如果您使用典型（非 VRF）SoftLayer® 帳戶，則必須啟用 VLAN 跨越。如果未對典型帳戶啟用 VLAN 跨越，則 VMware 虛擬化環境的各種元件可能無法彼此通訊。如果要在 SoftLayer 帳戶中啟用 VLAN 跨越，請參閱[啟用或停用 VLAN 跨越](../../../infrastructure/vlans/vlan-spanning.html){:new_window}。

## 電子郵件設定和通知

您可以在**設定**頁面上配置電子郵件通知。依預設，會啟用此設定，這表示當佈建了實例且備妥可供使用時，您會透過電子郵件收到任何新訂購實例的通知。您也可以在**設定**頁面上停用電子郵件通知。如需相關資訊，請參閱[使用者帳戶及設定](useraccount.html)。

## 詳細狀態資訊

現在，Cloud Foundation 實例有詳細狀態資訊可供使用。當您按一下實例名稱時，顯示的狀態資訊會提供部署進度的更多詳細資料。如果發生錯誤，則會顯示訊息以協助您處理問題。如需相關資訊，請參閱[檢視 Cloud Foundation 實例](../sddc/sd_viewinginstances.html)。
