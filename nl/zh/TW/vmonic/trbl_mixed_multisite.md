---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-05"

---

# 無法將 1.7 版次要實例新增至 1.5 版主要實例

## 問題
在多站台 Cloud Foundation 配置中，由於 Microsoft Active Directory (AD) 伺服器上的作業系統版本不相符，您無法將 1.7 版次要實例新增至 1.5 版的主要實例。

## 解決方法
請在 1.5 版主要實例上完成下列步驟，為要成為 **Enterprise Admins** 和 **Schema Admins** 群組一部分的主要自動化使用者新增許可權。

1. 使用**管理者**密碼登入 Windows AD 伺服器。
2. 開啟**伺服器管理程式**，並按一下**工具 -> Active Directory 使用者和電腦**。
4. 在 **Active Directory 使用者和電腦**視窗上，按一下根網域下的**使用者**區段。
5. 用滑鼠右鍵按一下自動化使用者，以開啟**內容**視窗。
6. 按一下**成員隸屬**標籤。
7. 按一下**新增**，並輸入 **Enterprise Admins** 和 **Schema Admins** 群組，作為清單的物件名稱。  

完成這些步驟之後，您可以將 1.7 版次要實例新增至 1.5 版主要實例。
