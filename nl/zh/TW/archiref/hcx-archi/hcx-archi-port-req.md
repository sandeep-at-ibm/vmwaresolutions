---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# VMware HCX on IBM Cloud 埠存取需求

HCX 必須遍訪公用網際網路及專用線路，並連接至資料中心元件（例如網路、交換器及埠群組）。

下表列出的埠必須開啟，才能順利安裝 Hybrid Cloud Services 虛擬應用裝置。vSphere 環境及 IBM Cloud 環境都必須允許 vSphere 內部部署裝置及 IBM Cloud 裝置中的「網路時間通訊協定 (NTP)」時鐘同步化。Hybrid Cloud Services 虛擬應用裝置及網路必須可存取 UDP 埠 123。安裝「Hybrid Cloud Services 應用裝置」時，可以指定已安裝的「NTP 伺服器」。

表 1. 埠存取需求

| 來源 | 目標 | 埠 | 通訊協定 | 用途 |服務|
|--------|--------------|------|----------|-----------------|----------|
|HCX| 客戶 DNS | 53 | TCP/UDP | 名稱解析 |DNS|
|HCX| IBM Cloud 中的 NSX LB | 443 | TCP | 登錄服務 | HTTPS |
|HCX| IBM Cloud 中的 vCenter | 443 | TCP | HCX REST 服務 | HTTPS |
|HCX| IBM Cloud 中的 PSC | 443 | TCP | HCX REST 服務 | HTTPS |
|HCX| connect.hcx.vmware.com | 443 | TCP | 登錄服務 | HTTPS |
|Web 瀏覽器|HCX| 9443 | TCP | 進行 HCX 系統配置的 HCX 虛擬應用裝置管理介面 | HTTPS |
|Admin 網路|HCX| 22 | SSH | 對 Hybrid Cloud Services 的管理者 SSH 存取 | SSH |
|HCX| ESXi 主機 | 902 | TCP | 將管理及佈建指示從 HCX 傳送至 IBM Cloud 中的「ESXi 主機」。| 內部 |
|HCX| vCenter SSO Server | 7444 | TCP | vSphere 查閱服務 |  |
|HCX| NTP 伺服器 | 123 | UDP | 時間同步化             | |
|HCX| Syslog |   | 由使用者所配置 | HCX（用戶端）與 Syslog 伺服器之間的連線。Syslog 埠及通訊協定的值指定於 vSphere Web Client 中。例如，埠 514 適用於 UDP 通訊協定。| |
|HCX| 雲端閘道 | 8123 | TCP | 將主機型抄寫服務指示傳送至「混合式雲端閘道」。| HTTP |
|HCX| 雲端閘道 | 9443 | TCP | 使用 REST API，將管理指示傳送至本端「混合式雲端閘道」。| HTTP</br>HTTPS |
| 雲端閘道 | L2C | 443 | TCP | L2C 使用與「混合式雲端閘道」相同的路徑時，將管理指示從「雲端閘道」傳送至 L2C。| HTTP</br>HTTPS |
| 雲端閘道 | L2C | 8443 | TCP | L2C 使用替代資料路徑時，為從「雲端閘道」至 L2C 的雙向管理指示。| HTTP</br>HTTPS |
| L2C | L2C（遠端）| 443 | TCP | L2C 使用替代資料路徑時，為從「雲端閘道」至 L2C 的雙向管理指示。| HTTP</br>HTTPS |
| 雲端閘道 | ESXi 主機 | 80、902 | TCP | 管理及 OVF 部署 | 內部 |
| ESXi 主機 | 雲端閘道 | 31031、44046 | TCP | 內部主機型抄寫資料流量 | 內部 |
| 雲端閘道 | ESXi 主機 | 8000 | TCP | vMotion（零關閉時間移轉）|  |
| 雲端閘道（本端）| 雲端閘道</br>（遠端）| 4500 | UDP | 網際網路金鑰交換 (IKEv2) 以封裝雙向通道的工作負載 | IPSEC |
| 雲端閘道（本端）| 雲端閘道</br>（遠端）| 500 | UDP | 用於雙向通道的網際網路金鑰交換 (ISAKMP) | IPSEC |

### 相關鏈結

* [在來源上安裝及配置 HCX](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-install-cfg-src.html)
