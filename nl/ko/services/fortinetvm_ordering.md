---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Virtual Appliance on IBM Cloud 주문
{: #fortinetvm_ordering}

서비스가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 서비스를 추가하여 FortiGate Virtual Appliance on {{site.data.keyword.cloud}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 FortiGate Virtual Appliance on IBM Cloud 주문
{: #fortinetvm_ordering-new}

다음 방법 중 하나를 사용하여 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 인스턴스를 주문할 때 **서비스** 섹션에서 **FortiGate Virtual Appliance on IBM Cloud**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **FortiGate Virtual Appliance on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 FortiGate Virtual Appliance on IBM Cloud 주문
{: #fortinetvm_ordering-existing}

다음 방법 중 하나를 사용하여 기존 인스턴스에 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 해당 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **FortiGate Virtual Appliance on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **기존 인스턴스에 추가**를 선택하십시오.

## FortiGate Virtual Appliance on IBM Cloud 서비스 구성
{: #fortinetvm_ordering-config}

서비스를 주문할 때 다음 설정을 제공하십시오.

### FortiGuard 네트워크 연결
{: #fortinetvm_ordering-config-network-connect}

FortiGuard에 대한 **공용 네트워크** 또는 **사설 네트워크**를 선택하십시오. 대상 클러스터가 사설 전용 네트워크 인터페이스로 구성되는 경우 **사설 네트워크** 옵션만 사용할 수 있습니다. 이 선택사항은 라이센스를 활성화하고 보안 패치를 다운로드하기 위해 FortiGuard에서 Fortinet 라이센스 서버에 접속하는 방법을 결정하며, 워크로드 데이터 플레인에는 영향을 주지 않습니다.

**사설 네트워크**를 선택하는 경우 다음 설정을 지정하십시오.
* **프록시 IP 주소**: 프록시 서버의 IPv4 주소입니다.
* **프록시 포트 번호**: 프록시 서버의 포트 번호이며 일반적으로 8080 또는 3128입니다.
* **프록시 사용자 이름** 프록시 인증이 필요한 경우 프록시 서버의 사용자 이름을 입력하십시오.
* **프록시 비밀번호** 프록시 인증이 필요한 경우 프록시 서버의 비밀번호를 입력하십시오.

### 이름
{: #fortinetvm_ordering-config-name}

서비스 이름을 입력하십시오.

### 배치 크기
{: #fortinetvm_ordering-config-size}

{{site.data.keyword.cloud_notm}}에서는 다음의 배치 크기 옵션을 제공합니다.
* 소형(2개의 vCPU / 4GB RAM)
* 중형(4개의 vCPU / 6GB RAM)
* 대형(8개의 vCPU / 12GB RAM)

### 라이센스 모델
{: #fortinetvm_ordering-config-license}

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}에 대한 라이센스 모델은 다음 옵션을 제공합니다.
<dl class="dl">
        <dt class="dt dlterm">표준 FW</dt>
        <dd class="dd">이 번들에는 상태 기반 패킷 검사, VLAN 보호 및 고급 로깅, 유입 및 유출 방화벽 규칙, SSL/IPSec VPN 종료 및 연중무휴 지원이 포함됩니다.</dd>
        <dt class="dt dlterm">표준 FW + UTM</dt>
        <dd class="dd">이 번들에는 모든 표준 방화벽 서비스뿐만 아니라 AMP(Advanced Malware Protection) 서비스가 포함되어 있습니다. 여기에는 안티바이러스, 봇넷 IP/도메인 서비스, 모바일 악성 코드 보안, FortiSandbox Cloud, Virus Outbreak Protection 서비스 및 Content Disarm & Reconstruct가 포함되어 있습니다. 또한 웹 필터링, IPS, 안티스팸, 애플리케이션 제어, FortiCare 서비스도 포함되어 있습니다.</dd>
        <dt class="dt dlterm">표준 FW + 엔터프라이즈</dt>
        <dd class="dd">이 번들에는 모든 표준 방화벽 및 UTM 서비스는 물론 다음 서비스가 포함되어 있습니다.<ul><li>CASB(Cloud Access Security Broker) - 이 서비스는 클라우드 기반 서비스에 대한 가시성, 규제 준수, 데이터 보안 및 위협 보호 기능을 제공합니다.</li><li>산업 보안 - 이 서비스는 공통 ICS/SCADA 프로토콜에 대한 서명을 제공합니다.</li><li>보안 등급 - 이 서비스는 감사 기능을 제공하여 중요한 취약점 및 구성의 단점을 식별하고 우수 사례 권장사항을 구현합니다.</li></ul></dd>
</dl>

2018년 3분기에, Fortinet에서는 세 개의 새로운 서비스(CASB, 산업 보안 및 보안 등급)를 엔터프라이즈 번들에 추가했습니다. 이러한 서비스는 FortiGate 6.0에서만 사용할 수 있습니다.
{:note}

서비스 설치 후에는 라이센스 모델을 변경할 수 없습니다. 라이센스 모델을 변경하려면 기존 서비스를 제거하고 다른 라이센스 옵션을 선택하여 서비스를 다시 설치해야 합니다.
{:important}

## 관련 링크
{: #fortinetvm_ordering-related}

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Fortinet 웹 사이트](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](https://docs.fortinet.com/product/fortigate/6.2){:new_window}
