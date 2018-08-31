---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# 邀請使用者存取服務及資源

{{site.data.keyword.vmwaresolutions_full}} 已與 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 整合，可在多位使用者之間協同作業。在您註冊 {{site.data.keyword.cloud_notm}} 帳戶並登入 {{site.data.keyword.vmwaresolutions_short}} 主控台之後，即可將使用者新增至 {{site.data.keyword.cloud_notm}} 帳戶。這些新增的使用者可以共用針對該帳戶所佈建的服務及資源。

## 開始之前

* 確定您是帳戶擁有者，或 **VMware 解決方案**服務的平台管理角色是**管理者**。
* 確定您已檢閱[利用 Identity and Access Management 管理使用者存取](iam.html)中的使用者角色及許可權。

## 程序

1. 在橫幅左側，按一下**管理 > 安全 > 身分及存取**。
2. 在**使用者**頁面上，按一下**邀請使用者**。
3. 在**邀請使用者**頁面的**使用者**區段中，於**電子郵件位址**欄位中輸入您要邀請之使用者的電子郵件位址。
4. 在**存取**區段中，展開**服務**，然後完成下列作業：
   1. 從**將存取權指派給**清單中，選取**資源**。
   2. 從**服務**清單中，選取 **VMware 解決方案**。
   3. 選取您要指派給使用者的平台存取角色。它可以是**管理者**、**編輯者**、**操作員**或**檢視者**。
5. 按一下**邀請使用者**。

## 結果

在新增的使用者接受您的邀請之後，他們即可登入 {{site.data.keyword.vmwaresolutions_short}} 主控台，並切換至您的帳戶。若要這樣做，在使用者的設定檔設定中，使用者按一下其在 {{site.data.keyword.vmwaresolutions_short}} 主控台右上角的虛擬人像。然後，新增的使用者即可協作與共用您指定帳戶中可用的服務及資源。

### 相關鏈結

* [邀請使用者及指派存取權](../../../iam/iamuserinv.html)
* [管理身分及存取](../../../iam/quickstart.html)
* [管理使用者及存取](../../../iam/iamusermanage.html)
* [何謂 IAM](../../../iam/index.html)
* [將 2.5 版之前的 vCenter Server 實例移轉至 IBM Cloud 帳戶](../vcenter/vc_addinstancetousraccount.html)
* [將 2.5 版之前的 vCenter Server with Hybridity Bundle 實例移轉至 IBM Cloud 帳戶](../vcenter/vc_hybrid_addinstancetousraccount.html)
* [將 2.5 版之前的 Cloud Foundation 實例移轉至 IBM Cloud 帳戶](../sddc/sd_addinstancetousraccount.html)
* [將 2.5 版之前的 NetApp ONTAP Select 實例移轉至 IBM Cloud 帳戶](../netapp/np_addinstancetousraccount.html)
* [將 2.5 版之前的 VMware Federal 實例移轉至 IBM Cloud 帳戶](../vcenter/vc_fed_addinstancetousraccount.html)
