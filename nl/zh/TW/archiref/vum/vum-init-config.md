---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

# 起始配置

IC4VS 自動化會配置將預設閘道設為「{{site.data.keyword.cloud}} 後端客戶路由器 (BCR)」的 VCSA。不過，沒有可透過 BCR 通往網際網路的路徑。從 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 實例通往網際網路的標準路徑是透過「管理 ESG」。因為不建議變更 VCSA 或「管理 ESG」的配置，所以建議在客戶子網路上實作 Proxy 伺服器，以啟用 VUM。

此方法表示不需要重新配置 VCSA 或「管理 ESG」，不過，需要安裝一個小型虛擬機器 (VM) 或應用裝置。Proxy 伺服器是位於兩個端點裝置之間的系統，用來作為中間裝置。在此情況下，它位在 VUM 與 VMware 的更新伺服器之間。

VUM 從 VMware 的更新伺服器要求資源時，會先將要求傳送至 Proxy 伺服器，而 Proxy 伺服器接著會將要求傳送至更新伺服器。在 Proxy 伺服器取得資源之後，會將資源傳送至 VUM。Proxy 伺服器可以用來協助安全、管理控制及快取服務。

本文件說明如何使用基於 CentOS 及 Squid 的 Proxy 伺服器。Squid Proxy 是 Web 的開放程式碼快取 Proxy，支援許多通訊協定（包括 HTTP 及 HTTPS）。有許多 VM 及應用裝置型 Proxy 可供使用，而您應該根據企業的需求來選取適當的 Proxy，並安裝及配置下列供應商指引。選擇使用 CentOS/Squid 實作的用戶端應該會繼續下面的處理程序。

* 將 CentOS ISO 下載至跳躍伺服器
* 建立 vCenter 程式庫
* 將 ISO 上傳至 vCenter 程式庫
* 建立 VM、安裝及配置 CentOS，並安裝 Squid

您需要收集資訊來移入表 1，才能開始此作業。請檢閱建議值，並確定它們適合您的企業。此配置僅根據使用 CentOS-Minimal 及 Squid 之 VUM 的小型 Proxy。

表 1. 部署值

| 參數               | 建議值 | 附註 |
|:--------- |:-------------- |:------ |
| Proxy CPU | 1 vCPU | Squid 沒有最低需求 |
| Proxy RAM | 2 GB | Squid 沒有最低需求 |
| Proxy 磁碟 |25 GB | Squid 沒有最低需求 |
| 主機名稱 | Proxy01 | |
| 位址 |proxy ip |應該從佈建處理程序期間指派的「客戶」專用可攜式子網路使用備用 IP 位址。此子網路上只保留兩個 IP 位址；一個適用於 BCR，另一個適用於 customer-esg
| 網路遮罩 |255.255.255.192 | |
| 閘道 |customer-nsx-edge 專用上行鏈路 IP | 這是 Proxy 伺服器的預設閘道設定，即 customer-nsx-edge 的專用上行鏈路 IP 位址。檢閱 **customer-nsx-edge** 的**設定**標籤，即可找到此 IP 位址。|
| DNS 伺服器 |AD/DNS IP | 在 {{site.data.keyword.vmwaresolutions_short}} 主控台的實例頁面（**已部署的實例**頁面）上，可以找到此 IP 位址。|
| BCR IP |bcr ip | 這是「{{site.data.keyword.cloud_notm}} 後端客戶路由器」的 IP 位址，並且是 10.0.0.0/8 和 161.26.0.0/16 的閘道。此位址用於 Proxy 伺服器的靜態路徑中，讓它能夠連接 VCSA 及 AD/DNS 伺服器。 |

## 配置 NSX

需要有「NSX 客戶 ESG」防火牆及 NAT 設定，才能啟用 Proxy 伺服器資料流量。

### 防火牆

1. 移至**首頁** > **網路與安全**。
2. 選取 **NSX Edge** (customer-nsx-edge)，然後選取**防火牆**。
3. 按一下 **+** 符號，然後新增防火牆規則。
4. 提供必要的參數，如下表所述。新的防火牆規則必須出現在最後一個規則（「預設拒絕規則」）前面。

表 2. 防火牆規則

| 參數               | 建議值 |
|:--------- |:-------------- |
|名稱 | 出埠 Proxy01 |
|類型      | User |
| 來源 | Proxy 伺服器 IP |
| 目的地 | any |
| 服務 | HTTP/HTTPS/ICMP Echo |
| 動作 | Accept |

提供參數之後，請按一下**發佈變更**。

### 安裝及配置 Proxy 伺服器

下列處理程序會從「內容程式庫」部署 VM 以管理 CentOS 及 Squid，以及包含下列步驟。假設您已佈建 Windows VSI 作為 jumpbox，而且您使用「遠端桌面通訊協定」連接至 VSI 的公用介面：

* 下載 CentOS-Minimal ISO 檔案
* 配置「vCenter 內容程式庫」，並在其中移入 CentOS ISO 檔案
* 配置 Proxy VM，並安裝 CentOS 及 Squid

### 下載 CentOS-Minimal ISO 檔案

在跳躍伺服器上，使用瀏覽器從 [CentOS](https://www.centos.org/download/) 下載 CentOS-Minimal ISO 檔案。請注意，{{site.data.keyword.cloud_notm}} 維護許多熱門 Linux 發行套件的鏡映。此鏡映僅適用於專用網路，且 CentOS ISO 位於下列位址：`http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`

### 配置內容程式庫，並在其中移入 CentOS ISO 檔案

建立本端 vCenter 內容程式庫。只有在建立程式庫的 vCenter Server 實例中，才能存取程式庫。請將部署 VM 所需的範本及 ISO 移入程式庫。

1. 透過 vSphere Web Client，導覽至**首頁** > **內容程式庫** > **物件** > **建立新的內容程式庫** > **在 vCenter 上建立訂閱的程式庫**。
2. 輸入內容程式庫的名稱（例如 ISO），然後在「附註」文字框中輸入程式庫的說明，然後按**下一步**。
3. 選取**本端內容程式庫**，然後按**下一步**。
4. 選取資料儲存庫，然後按一下適合的資料儲存庫（例如，vsanDatastore）。
5. 檢閱「準備完成」頁面上的資訊，然後按一下**完成**。

### 配置 Proxy VM，並安裝 CentOS 及 Squid

此活動具有下列作業：

*	建立新的 VM
*	安裝 CentOS
*	安裝 Squid

#### 建立新的 VM

此作業會建立新的 VM 以用來作為 Proxy 伺服器。應該使用「表 1 部署值」中的設定來移入配置。

1.	透過 vSphere Web Client，導覽至**首頁** > **VM 及範本**。
2.	在「導覽器」窗格中，按一下 **datacenter1**，然後按一下滑鼠右鍵選取**新建虛擬機器** > **新建虛擬機器**。
3.	選取**建立新的虛擬機器**，然後按**下一步**。
4.	輸入 VM 的「名稱」（例如 Proxy01），選取 **datacenter1**，然後按**下一步**。
5.	選取 **cluster1**，然後按**下一步**。
6.	選取適當的資料儲存庫（例如 vsanDatastore），按**下一步**，然後再按一次**下一步**。
7.	在**來賓作業系統系列**中選取 **Linux**，並在**來賓作業系統版本**中選取 **CentOS 7（64 位元）**，然後按**下一步**。
8.	將 **CPU** 設為 1，並將**記憶體**設為 2048 MB，然後將**新建硬碟**設為 25 GB。選取**內容程式庫 ISO 檔案**，並選取 **CentOS-7-x86_64-Minimal**，然後按一下**確定**，再勾選**已連接**方框。
9.	在「新建裝置」方框中，選取**網路**，然後按一下**新增**。
10.	選取 **SDDC-DPortGroup-Mgmt** 網路，並確定已勾選「連接」勾選框，然後按**下一步**。
11.	檢閱後按一下**完成**。

#### 安裝 CentOS

此作業會安裝及配置新建立的 VM 以進行 Squid 安裝

1.	在 vSphere Web Client 的「導覽器」窗格中，選取剛才建立的 **VM** (Proxy01)，然後選取**摘要**標籤。
2.	按**播放**按鈕，以開啟 VM 的電源。
3.	VM 現在將開機，並從 CentOS 7 ISO 啟動。請對 VM 啟動**遠端主控台或 Web 主控台**。請注意，必須安裝「遠端主控台」，而且執行 Web 瀏覽器的系統必須依名稱解析 vSphere ESXi 主機。
4.	在「歡迎使用 CentOS 7」畫面，選取您需要的語言，然後按一下**繼續**。
5.	在**本地化**畫面，按一下**日期及時間**，選取時區，然後按一下**完成**。
6.	在**本地化**畫面，按一下**鍵盤**以變更預設值（如有必要），然後按**完成**。
7.	在**本地化**畫面，按一下**安裝目的地**，按一下 **VMware 虛擬磁碟**圖示，然後按一下**完成**。
8.	在**本地化**畫面，按一下**網路及主機名稱**，將「主機名稱」變更為您選擇的主機名稱（例如 Proxy01）。
9.	按一下**配置**按鈕，然後按一下 **IPv4 設定**，在**方法**方框中選取**手動**。
10.	使用**新增**按鈕，在_表 1. 部署值_ 中插入_位址網路遮罩_ 和_閘道_。
11.	在「表 1. 部署值」中，輸入 _DNS 伺服器 IP 位址_。
12.	按一下**路徑**按鈕，然後新增下列具有「表 1 部署值」中閘道 IP 位址 _BCR IP 位址_ 的靜態路徑：_10.0.0.0/8 及 161.26.0.0/16_，以作為閘道。此靜態路徑容許 Proxy 伺服器連接到 DNS 伺服器。
13.	按一下**儲存**，然後確定乙太網路介面已開啟並顯示為已連接。按一下**完成**和**開始安裝**。
14.	繼續安裝時，請設定 root 密碼並設定使用者。
15.	安裝完成時，請以使用者身分登入，然後輸入 _ping vmware.com_ 指令。名稱應該解析為 IP 位址，而且您應該會取得回應。如果您未取得回應，請檢查：IP 位址、防火牆規則及 NAT 設定。

#### 安裝及配置 Squid

Squid 沒有任何最低硬體需求，但根據透過 Proxy 存取網際網路的使用者以及快取中所儲存的物件，RAM 的數量可能會不同。因為只有 VUM 才能存取 Proxy 伺服器，而且未啟用快取，所以只會配置小型 VM。

1. 使用 vSphere Web Client 中的「Web 主控台」或「遠端主控台」，以使用者身分登入 Proxy 伺服器，然後 `su` 到 root。
2. 安裝任何套件之前，建議您使用下列指令來更新系統及套件：
  `yum -y update`

3. 若要安裝 Squid，您需要將 EPEL 儲存庫安裝至系統，因為預設 Yum 儲存庫中沒有 Squid。請執行下列指令來安裝 EPEL 儲存庫：
  `yum -y install epel-release`

4. 使用下列指令來更新及清除：

  `yum -y update`
  `yum clean all`

5. 使用下列指令來安裝 Squid：`yum -y install squid`。
6. 安裝之後，使用下列指令立即啟動 Squid：`systemctl start squid`。
7. 若要在開機時自動啟動 Squid，請執行下列指令：`systemctl enable squid`。
8. 執行下列指令，以確保 Squid 執行中：`systemctl status squid`。
9. CentOS 防火牆需要使用下列指令來容許存取 Squid 埠 (TCP 3128)：`firewall-cmd -add-port=3128/tcp -permanent`。
10.	若要儲存規則並重新啟動此服務，請使用下列指令：`firewall-cmd -reload`。

## VUM 的起始設定

配置 VUM，以使用 Proxy 伺服器來存取網際網路上的儲存庫。
1. 使用 vSphere Web Client，導覽至**首頁** > **Update Manager**。按一下 vCenter Server。
2. 選取**管理**標籤，然後按一下**設定**按鈕。
3. 選取**下載設定**，然後按一下 _Proxy 設定_ 下的**編輯**。
4. 勾選**使用 Proxy** 方框，輸入 _Proxy 伺服器 IP 位址_ 和_埠 3128_，然後按一下**確定**。「連線功能狀態」會變更為_驗證中_，然後變更為_已連接_。
5. 按一下**立即下載**。在_最近作業_ 窗格中，您應該會看到此活動已完成。

### 相關鏈結

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) 上的 VMware 解決方案（示範）
