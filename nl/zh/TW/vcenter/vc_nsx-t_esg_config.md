---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 配置網路以使用客戶管理的 NSX-T ESG 來搭配您的 VM
{: #vc_nsx-t_esg_config}

配置虛擬機器的網路，以便利用 VMware vCenter Server 實例中所部署的 VMware NSX-T Edge Services Gateway (ESG)。如需為協助降低安全風險而設的安全措施相關資訊，請參閱[管理服務 NSX Edge 是否造成安全風險？](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX-T 是一種網路虛擬化平台，可將隔離的網路虛擬化，並提供數個網路服務，例如交換器、路由及防火牆。如需 NSX 的相關資訊，請參閱 [Overview of NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}。

在訂購 vCenter Server with NSX-T 實例程序的過程中，將代表您完成下列動作：
* 訂購專用客戶子網路，供您的 VM（虛擬機器）用來存取 {{site.data.keyword.cloud}} 基礎架構專用網路。
* 訂購公用客戶子網路，讓您的 VM 存取網際網路。
* NSX-T 在您的 vCenter Server with NSX-T 實例中進行部署和配置。
* 部署一個範例 NSX-T 邏輯交換器，供客戶工作負載 VM 使用。
* 部署一個範例「NSX-T 分散式邏輯路由器 (DLR)」，以因應連接至第 2 層 (L2) 網路之間的潛在東西向通訊。
* 部署並配置一個 NSX-T Edge 應用裝置，以執行從工作負載邏輯交換器的 IP 位址範圍到 NAT 規則上的公用 IP 位址的網址轉換 (NAT)。

  對於僅限專用的實例不會部署 NSX-T Edge。{:note}

## 配置 VM 網路設定的程序
{: #vc_nsx-t_esg_config-procedure-config-networking}

若要為工作負載 VM 利用 NSX-T，您必須在建立 VM 時完成下列步驟來配置一些設定：

1. 將 VM 的網路配接卡設為工作負載邏輯交換器：
   1. 在**新虛擬機器**對話框中，按一下**自訂硬體**標籤。
   2. 在**新裝置**功能表上，選取**網路**，然後按一下**新增**。
   3. 在新增的網路配接卡上，從功能表中選取工作負載邏輯交換器。**vxw-dvs-17-virtualwire-1-sid-6000-Workload** 為工作負載邏輯交換器的名稱範例。

   請確定您未選取**工作負載傳輸**交換器。{:important}

2. 識別 VM 的可用 IP 位址：
   *  IP 位址的範圍必須是 `192.168.10.0/24`。請注意，已保留 IP 位址 `192.168.10.1`（請參閱**步驟 3**）。
   *  當您配置在 VM 上執行之作業系統的網路時，請使用所選取的 IP 位址及網路遮罩 `255.255.255.0`。

   您要負責管理您為 VM 所指派的 IP 位址範圍。
   {:note}

3. 將 VM 的預設閘道指派為 `192.168.10.1`。此位址是 NSX DLR 的 IP 位址，它與工作負載 VM 位於相同的邏輯交換器上。

## 啟用 SNAT 規則的程序
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

如果您要讓工作負載 VM 具有對網際網路的出埠存取，則必須啟用相關聯的 SNAT（來源網址轉換）規則。啟用 SNAT 規則可讓您 VM 的網際網路存取轉換為單一公用 IP 位址。在 VMware vSphere Web Client 完成下列步驟：

1. 按一下**首頁 > 網路與安全**。
2. 在導覽窗格上，按一下 **NSX Edge**，然後按兩下名稱為 **customer-nsx-edge** 的 Edge。
3. 按一下**管理 > NAT**，以開啟 **NAT** 標籤。
4. 選取表格中的預設 SNAT 規則，然後按一下表格上方的綠色勾號，以啟用規則。

如需 NSX-T Edge NAT 規則的相關資訊，請參閱[管理 NAT 規則](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}。

## 識別客戶子網路詳細資料的程序
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

Edge **customer-nsx-edge** 是要給您自己使用的，因此您可以修改它，為入埠或出埠資料流量定義更多 NAT 規則。這些規則只能使用公用或專用客戶子網路上代表您訂購的 IP 位址。

若要識別客戶子網路的詳細資料，以便您可以使用已訂購的 IP 位址，請在 VMware vSphere Web Client 完成下列步驟：

1. 按一下**首頁 > 網路與安全**。
2. 在導覽窗格上，按一下 **NSX Edge**，然後在右窗格的 Edge 清單中找出 **customer-nsx-edge edge**。
3. 在**說明**直欄中，將游標移至 **customer-nsx-edge** 的 Edge 說明，來查看專用和公用客戶子網路的子網路 ID。

此外，您也可以在 {{site.data.keyword.slportal}} 中完成下列步驟，來尋找有關客戶子網路的更多詳細資料：

1. 按一下**網路 > IP 管理 > 子網路**。
2. 按一下過濾器功能表，然後在「子網路」欄位中輸入您在 VMware vSphere Web Client 的**摘要**標籤上的 **customer-nsx-edge**  Edge 的說明中所看到的 ID。
3. 檢閱針對 IP 位址所顯示的附註。這些附註可識別在起始設定期間所訂購及使用的子網路和 IP 位址。

   請勿使用在起始設定期間所訂購及使用的 IP 位址。不過，您可以根據自己的需求使用這些子網路上的其他 IP 位址。若要設定其他網址轉換規則，請參閱 [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}。
   {:important}

## 相關鏈結
{: #vc_nsx-t_esg_config-related}

* [變更 vCenter Server 構件的考量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
