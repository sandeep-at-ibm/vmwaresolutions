---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

# 連接至 VMware vSphere Web Client 時發生逾時
{: #trbl_timeout_vc_console}

## 問題
{: #trbl_timeout_vc_console-problem}

當您嘗試連接至 vSphere Web Client 時，可能發生下列逾時錯誤：

`<IP_address> 中的伺服器的回應時間過長。`

## 解決方法
{: #trbl_timeout_vc_console-resolution}

請使用下列步驟來調查及修正問題。

1. 確定您已完成當游標移至 **vCenter 主控台**按鈕時工具提示中所顯示的步驟。為方便起見，這些步驟也如下所示：   
   1. 安裝適用於您瀏覽器的 Adobe Flash Player 外掛程式。   
   2. 從 {{site.data.keyword.slportal_full}} 建立 VPN 密碼。    
   3. 使用 {{site.data.keyword.cloud_notm}} 基礎架構 VPN 認證來[登入資料中心 VPN](/docs/infrastructure/iaas-vpn?topic=VPN-gettingstarted-with-virtual-private-networking#login-to-the-vpn)。    
   4. 從本端電腦將 PSC (Platform Services Controller) 的 IP 位址和主機名稱對映新增至 `hosts` 檔。請使用下列格式：

      ```javascript
      IP_Address              Host_Name
      ```

2. 記下所顯示的 IP 位址，因為您在後續其中一個步驟中會需要它。
3. 請確定您有權存取 {{site.data.keyword.cloud_notm}} 基礎架構 VPN。在 {{site.data.keyword.slportal}} 上完成下列步驟：
   1. 按一下**帳戶 > VPN 存取**。
   2. 按一下 **VPN 存取**直欄中的 **SSL 鏈結**。
   3. 在**使用者名稱的 VPN 存取**頁面上，將**子網路存取**選項設為**手動**。
   4. 在相同頁面上，尋找 IP 位址/主機名稱配對的子網路。如需相關資訊，請參閱**步驟 2**。    

      比方說，如果實例的 IP 位址是 `xx.yyy.zz.15`，vCenter 的 IP 位址是 `xx.yyy.zz.10`，則您必須授與子網路 `xx.yyy.zz.0/26` 的存取權。

   5. 選取該子網路的**授與存取權**勾選框，然後按一下**儲存**。
