---

copyright:

  years:  2016, 2019

lastupdated: "2018-08-16"

---

# 使用 VMware vSphere Web Client 部署 OVF 檔案

## 解決方法

若要使用 vSphere Web Client 部署 OVF（開放式虛擬化格式）檔案，請使用下列程序：
1. 在您嘗試部署 OVF 檔案之前，請將下列主機資訊新增至 `/etc/hosts` 檔案：

   * Platform Services Controller (PSC) 的主機資訊
   * VMware ESXi 伺服器的主機資訊
   * vCenter 的主機資訊
2. 請檢查您的 `/etc/hosts` 檔案，確定已順利新增這項資訊。例如，主機檔案可能類似下列清單：

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. 請確保您有權存取 {{site.data.keyword.slportal_full}} 中的所有必要 VPN（虛擬專用網路）。在此範例中，它是 `10.131.7.xx` 及 `10.131.9.xxx`。
4. 為您的資料中心登入 VPN。
5. 按一下 **vCenter**，以存取 vSphere Web Client。
6. 用滑鼠右鍵按一下主機，並部署 `.ovf` 檔案。
