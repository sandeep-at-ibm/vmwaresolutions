---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# FortiGate Security Appliance on IBM Cloud 개요

FortiGate Security Appliance on {{site.data.keyword.cloud}} 서비스는 고가용성 모드에서 방화벽, 라우팅, NAT 및 VPN 서비스를 제공하도록 FSA(FortiGate Security Appliance) 300 시리즈 디바이스의 쌍을 배치하여 인스턴스의 공용 VLAN에서 모든 서버 및 가상 머신을 보호합니다.

SSH를 통해 FortiOS Web Client 또는 명령 인터페이스를 사용하여 이 서비스를 관리할 수 있습니다.

**가용성:** 이 서비스는 V1.8 이상 릴리스에 배치된 인스턴스에서만 사용 가능합니다.

## FortiGate Security Appliance on IBM Cloud의 기술 스펙

다음 컴포넌트가 주문되고 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

### 하드웨어

FortiGate 300 시리즈 Security Appliance.

### 고가용성

2개의 어플라이언스가 활성-수동 구성에 배치됩니다.

### 네트워킹

* 업스트림 및 다운스트림 네트워크 모두에 연결된 듀얼 1GbE
* 하나의 새 업스트림 {{site.data.keyword.cloud_notm}} 공용 VLAN
* 하나의 기존 다운스트림 {{site.data.keyword.cloud_notm}} 공용 VLAN

## FortiGate Security Appliance on IBM Cloud 설치 시 고려사항

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 설치하기 전에 다음 고려사항을 검토하십시오.
* 사용 중인 {{site.data.keyword.cloud_notm}} 계정에 **Hardware Firewall** 권한이 있는지 확인하십시오. 이 권한은 인스턴스의 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스에 대한 방화벽 로그 및 설정을 편집하거나 보는 데 필요합니다.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 배치된 인스턴스에 추가하려면 인스턴스의 공용 VLAN에 {{site.data.keyword.cloud_notm}} 인프라의 다른 방화벽이 이미 없는지 확인하십시오.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 설치하면 새 공용 VALN이 추가됩니다.
* 서비스 배치 중에 일시적으로 인스턴스가 인터넷에 액세스할 수 없습니다.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스가 설치된 후 FortiGate 콘솔에서 FSA의 방화벽 규칙을 관리하고 구성할 수 있습니다. FSA 방화벽 규칙이 인터넷을 통해 {{site.data.keyword.cloud_notm}}의 외부 관리 데이터베이스와 통신하기 위해 관리 컴포넌트(예: Zerto Virtual Manager)에서 시작되는 아웃바운드 HTTPS(TCP 포트 443) 통신을 허용하도록 정의되어 있는지 확인해야 합니다. 아웃바운드 HTTPS(TCP 포트 443) 통신은 인스턴스에 있는 관리 서비스 VMware NSX Edge Services Gateway(ESG)의 공인 IP 주소에서 시작됩니다.
* 필요한 통신만 허용하고 기타 모든 통신은 거부하도록 FortiGate Security Appliance 구성을 주의하여 관리해야 합니다.
* 추가 클러스터를 주문하는 경우, 이러한 새로 추가된 클러스터에 대한 공용 VLAN에는 Security Appliance의 HA 쌍이 없습니다.

## FortiGate Security Appliance on IBM Cloud 제거 시 고려사항

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 다음 고려사항을 검토하십시오.
* FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스를 제거하면 추가된 공용 VALN이 제거됩니다.
* 서비스 제거 중에 일시적으로 인스턴스가 인터넷에 액세스할 수 없습니다.
* NAT 트래픽을 허용, 검사, 차단 및 라우트할 모든 FortiGate 규칙이 Fortinet 서비스와 함께 제거됩니다. NAT 규칙이 있는 경우 다시 구성해야 합니다.

### 관련 링크

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 주문](fsa_ordering.html)
* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 관리](managingfsa.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet 웹 사이트](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
