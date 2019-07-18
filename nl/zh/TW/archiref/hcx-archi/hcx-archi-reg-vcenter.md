---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-27"

subcollection: vmware-solutions


---
# 向 vCenter 登錄 HCX Manager
{: #hcx-archi-reg-vcenter}

在 VMware vSphere Web Client 中登錄 Hybrid Cloud Services 外掛程式，並啟動 Hybrid Cloud Services 管理服務。

## 開始之前
{: #hcx-archi-reg-vcenter-prereq}

必須先開啟 Hybrid Cloud Services 虛擬應用裝置的電源，才能進行登錄。

## 向 vCenter 登錄 HCX Manager 的程序
{: #hcx-archi-reg-vcenter-proc-register}

1. 登入 Hybrid Cloud Services 服務虛擬應用裝置。例如，`https:My-HCX-Manager:9443/`。
2. 按一下**管理設定**磚。
  1. 在左窗格的**配置系統**下，選取 vCenter。
  2. 按一下右上方的**新增 vCenter**。
  3. 以 `https:vCenter-host-name` 或 `https:vCenter-IP-address` 形式，輸入 vCenter Server 的 IP 位址。例如，`https:My-vCenter` 或 `https:10.108.26.211`。
  4. 輸入 vCenter Server 使用者名稱及密碼。使用的帳戶必須有「vCenter 管理者」角色。
  5. 按一下**確定**。當顯示_您需要重新啟動應用程式_ 訊息時，請不要重新啟動。
3. 配置查閱服務。
  1. 按一下**管理**標籤。
  2. 按一下**查閱服務 URL** 文字框最右側的**編輯**按鈕。
  3. 以下列形式輸入查閱網路服務端點：
    * 對於 vCenter Server 5.5u3，輸入 `https://ssoip:/7444/lookupservice/sdk`
    * 對於 vCenter Server 6.0u2，輸入 `https://ssoip/lookupservice/sdk`
  4. 按一下**確定**。當顯示重新啟動 Web 引擎的訊息時，請不要重新啟動。
4. 按一下**摘要**標籤，並尋找**混合管理元件**區段。停止並啟動應用程式引擎和 Web 引擎。
5. 若要終結登錄，請登出 vSphere Web Client。重新登入，以驗證已進行畫面更新。

## 結果
{: #hcx-archi-reg-vcenter-results}

請注意現有 **Hybrid Cloud** 圖示及左側的 **Hybrid Cloud Services** 功能表項目。Hybrid Cloud Services 登錄會更新這些標籤。在庫存中，圖示標籤會變成 **Hybrid Cloud Services**。

## 相關鏈結
{: #hcx-archi-reg-vcenter-related}

* [安裝及配置混合式服務](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-hybrid)
