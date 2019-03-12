---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# 次要 vCenter Server 系統未出現在 vSphere Web Client 庫存中
{: #trbl_sec_inst_not_visible}

## 問題
{: #trbl_sec_inst_not_visible-problem}

在多站台配置中，當您新增次要實例之後，並登入先前所訂購實例的 VMware vSphere Web Client 時，它的 vCenter Server 系統並未出現。

## 解決方法
{: #trbl_sec_inst_not_visible-resolution}

這是 VMware 6.5 已知問題。

若要解決此問題，您必須重新啟動 vSphere Web Client：

1. 使用 **root** 帳戶，透過 **ssh** 連接至先前訂購實例的 vCenter VM（虛擬機器）。
2. 鍵入 ``shell`` 以進入 bash shell。
3. 輸入 `service-control --stop vsphere-client` 以停止用戶端。
4. 輸入 `service-control --start vsphere-client`，以重新啟動用戶端。
5. 在重新啟動先前所訂購實例的 vSphere Web Client 之後，請確認新增的次要實例的 vCenter Server 系統出現在 vSphere Web Client 中。
