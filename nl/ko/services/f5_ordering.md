---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: F5 license activation, F5 configuration, order F5

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# F5 on IBM Cloud 주문
{: #f5_ordering}

서비스가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 서비스를 추가하여 F5 on {{site.data.keyword.cloud}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 F5 on IBM Cloud 주문
{: #f5_ordering-new}

다음 방법 중 하나를 사용하여 F5 on {{site.data.keyword.cloud_notm}}와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 인스턴스를 주문할 때 **서비스** 섹션에서 **F5 on IBM Cloud**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **F5 on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 F5 on IBM Cloud 주문
{: #f5_ordering-existing}

다음 방법 중 하나를 사용하여 기존 인스턴스에 F5 on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 해당 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **F5 on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **기존 인스턴스에 추가**를 선택하십시오.

## 개인용 인스턴스에 대한 F5 on IBM Cloud 주문
{: #f5_ordering-private}

공용 인터페이스로 구성되지 않은 인스턴스에 대한 F5 on {{site.data.keyword.cloud_notm}}를 주문하는 경우 설치를 완료하려면 프록시 서버를 제공해야 합니다. F5 on {{site.data.keyword.cloud_notm}} 설치가 시작되기 전에 VRF(Virtual Routing and Forwarding)를 통해 HTTP 프록시 서버를 구성하고 사용할 수 있어야 합니다.

BigIP VE(Virtual Edition) 엔드포인트가 작동 가능하게 되기 전에 해당 라이센스를 활성화할 수 있어야 합니다. BigIP VE 엔드포인트가 설치된 후에는 더 이상 프록시 서버를 사용할 필요가 없습니다.

서비스 설치 시 작동 중인 프록시 서버 없이 F5 on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 없습니다.
{:note}

## F5 on IBM Cloud 서비스 구성
{: #f5_ordering-config}

서비스를 주문할 때 다음 설정을 제공하십시오.

### F5 라이센스 활성화 연결
{: #f5_ordering-config-license}

라이센스 활성화에 대한 **공용 네트워크** 또는 **사설 네트워크**를 선택하십시오. 대상 클러스터가 사설 전용 네트워크 인터페이스로 구성되는 경우 **사설 네트워크** 옵션만 사용할 수 있습니다. 이 선택사항은 F5 가상 서버가 F5 라이센스 서버에 접속하는 방법을 결정하며, 워크로드 데이터 플레인에는 영향을 주지 않습니다.

**사설 네트워크**를 선택하는 경우 다음 설정을 지정하십시오.
* **프록시 IP 주소**: 프록시 서버의 IPv4 주소입니다.
* **프록시 포트 번호**: 프록시 서버의 포트 번호이며 일반적으로 8080 또는 3128입니다.

인증 프록시는 지원되지 않습니다.
{:note}

### 이름
{: #f5_ordering-config-name}

서비스 이름을 입력하십시오.

### 최대 대역폭
{: #f5_ordering-config-bandwidth}

F5 BIG-IP 어플라이언스의 최대 처리량을 지정하십시오.

### 라이센스 모델
{: #f5_ordering-config-license-model}

F5 on {{site.data.keyword.cloud_notm}} 서비스에 대한 라이센스 모델은 다음 옵션을 제공합니다.
<dl class="dl">
        <dt class="dt dlterm">양호</dt>
        <dd class="dd">이 오퍼링은 전체 프록시 아키텍처로 작동하는 BIG-IP LTM(Local Traffic Manager™) VE를 사용하여 사용자가 항상 애플리케이션 서버를 사용할 수 있도록 인텔리전트 로컬 트래픽 관리, 완전한 SSL 트래픽 가시성, 분석 및 상태 모니터링을 제공합니다.</dd>
        <dt class="dt dlterm">우수</dt>
        <dd class="dd">이 오퍼링은 BIG-IP DNS™, BIG-IP AFM(Advanced Firewall Manager™) 및 BIG-IP Application AAM(Acceleration Manager™) 모듈을 추가하여 **양호** 옵션을 활용합니다. 이는 글로벌 트래픽 관리 서비스, 애플리케이션 성능 최적화, 고급 네트워크 방화벽 및 분산 서비스 거부(DDoS) 마이그레이션 기능을 제공합니다.</dd>
        <dt class="dt dlterm">최상</dt>
        <dd class="dd">**양호** 및 **우수** 오퍼링 외에도 BIG-IP ASM(Application Security Manager™)은 L7 DDoS, OWASP(Open Web Application Security Project) 상위 10개의 위협 및 공통 애플리케이션 취약점에 대한 포괄적인 애플리케이션 보호를 제공합니다. BIG-IP APM(Access Policy Manager™)은 다중 클라우드 환경 내에 있는 애플리케이션에 대한 안전하고 간소화된 액세스, SSO(Single Sign-On) 및 MFA(Multi-Factor Authentication)와 같은 통합 기능을 사용자에게 제공합니다.</dd>
</dl>

서비스 설치 후에는 라이센스 모델을 변경할 수 없습니다. 라이센스 모델을 변경하려면 기존 서비스를 제거하고 다른 라이센스 모델을 선택하여 서비스를 다시 설치해야 합니다.
{:important}

## 관련 링크
{: #f5_ordering-releated}

* [F5 on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [F5 on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [F5 Deployment Guides](https://www.f5.com/services/resources/deployment-guides){:new_window}
