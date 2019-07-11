---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-23"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 將 WebSphere Application Server 中的 Stock Trader 轉變成容器中的 Stock Trader
{: #vcscontent-stocktrmod}

Stock Trader 現代化旅程的下一步，是將要在虛擬機器 (VM) 中執行的工作負載轉變為在容器中執行。

若要繼續，Todd 及 Jane 會執行 Transformation Advisor 來分析 Stock Trader 工作負載、識別任何移轉複雜性，以及建議變更。就緒時，他們會使用 Transformation Advisor 將 Stock Trader 部署至在 {{site.data.keyword.icpfull_notm}} 中執行的 Liberty 容器。

## 準備 IBM Cloud Private
{: #vcscontent-stocktrmod-prep-icp}

Todd 需要先安裝 {{site.data.keyword.icpfull_notm}}。因為 Todd 在 {{site.data.keyword.cloud_notm}} 環境上有 VMware，所以他決定使用 {{site.data.keyword.cloud_notm}} Private Hosted 供應項目，以提供可在 {{site.data.keyword.cloud_notm}} 的 VMware VM 上執行的完整 {{site.data.keyword.icpfull_notm}} 實例。

預設儀表板提供綜合性的使用者介面，以管理 Kubernetes 叢集、安全、儲存空間，以及從型錄部署。

### 準備儲存空間
{: #vcscontent-stocktrmod-prep-storage}

{{site.data.keyword.cloud_notm}} Private Hosted 預設已配置 GlusterFS，並在作為專用 GlusterFS 節點的 VM 之間提供檔案儲存空間。GlusterFS 的價值在於它會啟用動態佈建。如果 Todd 想要的話，可以將額外的 VM 設定為 NFS 伺服器。

因為 Todd 想要他可用的 NFS 伺服器，所以識別稱為 'toddnfs' 的 VM，並執行這些[步驟](https://help.ubuntu.com/community/SettingUpNFSHowTo)。

Todd 執行下列指令，以建立新的 NFS 伺服器：

`ssh root@toodnfs.acme.com`

`apt-get install nfs-kernel-server`

`mkdir -p /shared`

`chown nobody:nogroup /shared`

`vi /etc/exports`

接下來，Todd 會新增下行：

`/shared \*(rw,no_subtree_check,async,insecure,no_root_squash)`

`systemctl restart nfs-kernel-server`

Todd 接著會在每部 VM 上執行下列指令，以將 NFS 安裝至每部 {{site.data.keyword.icpfull_notm}} 工作者節點 VM：

`sudo apt-get update`

`sudo apt-get install nfs-common`

Todd 會執行下列指令，以確認已安裝的版本：

`apt-cache policy nfs-common`

只要需要新的 NFS 磁區，Todd 就會執行下列指令，以在必要時建立新的 NFS 磁區：

`cd /shared`

`mkdir -p <foldername>`

`chmod 777 <foldername>`

### 準備映像檔安全
{: #vcscontent-stocktrmod-prep-img-sec}

在 {{site.data.keyword.icpfull_notm}} 3.1 版中，在將任何映像檔取回至 {{site.data.keyword.icpfull_notm}} 實例之前，需要先準備好映像檔原則以加強安全。加強功能需要您新增 IBM 映像檔所在位置 (*dockerhub/ibmcom*) 及 Docker 儲存庫中的映像檔原則。

依預設，會提供 ibmcloud-default-cluster-image-policy，並涵蓋 docker.io/ibmcom/\* 中的任何 IBM 映像檔，但因為 Db2 及其他 IBM 內容位在「Docker 儲存庫」中，所以需要 Docker 儲存庫 *docker.io/store/ibmcorp/* 的另一個映像檔原則。

此外，部分內容需要 Pod 安全原則集，以容許對 Pod 進行特定存取。例如，Db2 需要有一個原則，供想要在 'default' 以外的名稱空間中執行 Db2 的用戶端使用。

在 [IBM Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.1.0/manage_cluster/enable_pod_security.html) 中進一步瞭解。

## 部署 Transformation Advisor 及 Microclimate
{: #vcscontent-stocktrmod-deploy-tam}

Todd 在執行 {{site.data.keyword.icpfull_notm}} 之後，會安裝 Transformation Advisor 及 Microclimate。Todd 會開啟[型錄](https://www.ibm.com/cloud/private/architecture)，並檢視所有可用的內容。

Todd 會搜尋 Transformation Advisor 及 Microclimate，並在他按一下 Helm 圖表時，使用提供的 Readme 檔指示來安裝它們。

### 執行 Transformation Advisor
{: #vcscontent-stocktrmod-run-trans-advisor}

若要執行 Transformation Advisor，Jane 已在 WebSphere 中於執行 Stock Trader 的 VM 中新增資料收集器，並開啟 [Transformation Advisor](https://developer.ibm.com/recipes/tutorials/using-the-transformation-advisor-on-ibm-cloud-private/) 使用者介面以檢視結果。

Jane 已按一下 Stock Trader，並看到建議以在 Liberty 中執行每個 war 檔，而且大部分移轉都具有一個受控管的移轉，因此十分簡單。Jane 按一下「移轉詳細資料」，並查看 Transformation Advisor 是否提供她可用來完成移轉的部署檔案。Jane 將二進位檔上傳至 Transformation Advisor 之後，它會使用 Microclimate 所提供的 API 來部署 Liberty 容器。

結束時，產生的 Stock Trader 佈置選項如下：
* 單一 Liberty 容器 - 如果 Jane 部署 Liberty 運行環境，並已將其 Stock Trader 應用程式新增至該單一容器。
* 多個 Liberty 容器 - 每個 .war 檔都有一個容器，如 Transformation Advisor 針對 Stock Trader 的建議。

Todd 在轉變步驟期間未變更資料來源。Transformation Advisor 採用 WebSphere Application Server Network Deployment 資料來源配置，並將它新增至 Liberty 容器的 server.xml。
{:important}

## 相關鏈結
{: #vcscontent-stocktrmod-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
