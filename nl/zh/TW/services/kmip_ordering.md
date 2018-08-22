---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# 訂購 KMIP for VMware on IBM Cloud

您可以在訂購包含服務的新實例時，同時訂購 KMIP for VMware on {{site.data.keyword.cloud}} 服務，或將服務新增至現有實例。

## 為新實例訂購 KMIP for VMware on IBM Cloud

您可以使用下列其中一種方法，訂購包含 KMIP for VMware on {{site.data.keyword.cloud_notm}} 的新實例：
* 當您從 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購新實例時，請選取**服務**區段中的 **KMIP for VMware on IBM Cloud**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，選取 **KMIP for VMware on IBM Cloud**，指定服務設定，然後選取**新增至新實例**。

## 為現有實例訂購 KMIP for VMware on IBM Cloud

您可以使用下列其中一種方法，將 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務新增至現有實例：
* 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，檢視您要為其新增服務的實例，按一下左導覽窗格上的**服務**，然後按一下**新增**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，選取 **KMIP for VMware on IBM Cloud**，指定服務設定，然後選取**新增至現有實例**。

## KMIP for VMware on IBM Cloud 服務配置

當您訂購此服務時，請提供下列設定：

### 服務地區

選取要在其中管理 KMIP for VMware {{site.data.keyword.cloud_notm}} 服務實例的 {{site.data.keyword.cloud_notm}} 地區。

{{site.data.keyword.cloud_notm}} 在服務可用的每一個地區中都會維護高度可用的 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務端點。

### 用戶端 SSL 憑證

對於 vCenter Server，您必須配置「金鑰管理伺服器 (KMS)」叢集。所選取地區中的端點會透過用戶端 SSL 憑證安全地連接至 KMS。請參閱下表以瞭解每一個地區中的端點。這些端點使用 {{site.data.keyword.vmwaresolutions_short}} 團隊所維護的自簽憑證。憑證的指模是 `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`。

表 1：KMIP for VMware on {{site.data.keyword.cloud_notm}} 服務端點地區

|地區           |端點                   |
|:---------------|:-----------------------|
|德國           |`161.156.68.107:5696` |
|雪梨           |`130.198.73.134:5696` |
|英國           |`158.175.93.122:5696` |
|美國南部       |`169.60.185.42:5696`  |

在起始配置時，此設定是選用的。此時您可以將此欄位保留空白，因為在部署實例之後，就會知道 vCenter Server 中 KMS 的用戶端憑證。但您必須在部署實例之後輸入憑證，才能順利完成與 KMS 的 vCenter Server 連線。

### 服務 ID 的 API 金鑰

輸入用來存取 IBM Key Protect Service 實例之「{{site.data.keyword.cloud_notm}} 服務 ID」的 API 金鑰。

### Key Protect 實例

按一下**擷取**，以取得可用 IBM Key Protect Service 實例的清單，然後選取用於金鑰管理的實例。

### 客戶主要金鑰

按一下**擷取**，以取得所選取 IBM Key Protect 實例中儲存的客戶主要金鑰。



### 相關鏈結

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 概觀](kmip_considerations.html)
* [訂購、檢視及移除 Cloud Foundation 實例的服務](../sddc/sd_addingremovingservices.html)
* [訂購、檢視及移除 vCenter Server 實例的服務](../vcenter/vc_addingremovingservices.html)
* [訂購、檢視及移除 vCenter Server with Hybridity Bundle 實例的服務](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [常見問題](../vmonic/faq.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
