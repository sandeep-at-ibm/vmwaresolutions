---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# F5 on IBM Cloud 주문

BIG-IP VE(Virtual Edition)가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 BIG-IP VE를 추가하여 F5 on {{site.data.keyword.cloud_notm}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 F5 on IBM Cloud 주문

다음 방법 중 하나를 사용하여 F5 on {{site.data.keyword.cloud_notm}}와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_full}} 콘솔에서 새 인스턴스를 주문할 때 **서비스** 섹션에서 **F5 on IBM Cloud**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **F5 on {{site.data.keyword.cloud_notm}} 서비스**를 선택하고 서비스 설정을 지정하고 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 F5 on IBM Cloud 주문

다음 방법 중 하나를 사용하여 기존 인스턴스에 F5 on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭하고 **서비스 추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **F5 on IBM Cloud 서비스**를 선택하고 서비스 설정을 지정하고 **기존 인스턴스에 추가**를 선택하십시오.

## F5 on IBM Cloud 서비스 구성

서비스를 주문할 때 다음 설정을 제공하십시오.

### 이름

서비스 이름을 입력하십시오.

### 라이센스 모델

F5 on {{site.data.keyword.cloud_notm}} 서비스에 대한 라이센스 모델은 다음 옵션을 제공합니다.
<dl class="dl">
        <dt class="dt dlterm">양호</dt>
        <dd class="dd">이 오퍼링은 전체 프록시 아키텍처로 작동하는 BIG-IP LTM(Local Traffic Manager™) VE를 활용하여 사용자가 항상 애플리케이션 서버를 사용할 수 있도록 인텔리전트 로컬 트래픽 관리, 완전한 SSL 트래픽 가시성, 분석 및 상태 모니터링을 제공합니다.</dd>
        <dt class="dt dlterm">우수</dt>
        <dd class="dd">이 오퍼링은 BIG-IP DNS™, BIG-IP AFM(Advanced Firewall Manager™) 및 BIG-IP Application AAM(Acceleration Manager™) 모듈을 추가하여 **양호** 옵션을 활용합니다. 이는 글로벌 트래픽 관리 서비스, 애플리케이션 성능 최적화, 고급 네트워크 방화벽 및 분산 서비스 거부(DDoS) 마이그레이션 기능을 제공합니다.</dd>
        <dt class="dt dlterm">최상</dt>
        <dd class="dd">**양호** 및 **우수** 오퍼링 외에도 BIG-IP ASM(Application Security Manager™)은 L7 DDoS, OWASP(Open Web Application Security Project) 상위 10개의 위협 및 공통 애플리케이션 취약점에 대한 포괄적인 애플리케이션 보호를 제공합니다. BIG-IP APM(Access Policy Manager™)은 다중 클라우드 환경 내에 있는 애플리케이션에 대한 안전하고 간소화된 액세스, SSO(Single Sign-On) 및 MFA(Multi-Factor Authentication)와 같은 통합 기능을 사용자에게 제공합니다.</dd>
</dl>

**중요**: 서비스 설치 후 라이센스 모델을 변경할 수 없습니다. 라이센스 모델을 변경하려면 기존 서비스를 제거하고 다른 라이센스 모델을 사용하여 서비스를 다시 설치해야 합니다.

### 최대 대역폭

F5 BIG-IP 어플라이언스의 최대 처리량을 지정하십시오.

## 관련 링크

* [F5 on {{site.data.keyword.cloud_notm}} 개요](f5_considerations.html)
* [F5 on {{site.data.keyword.cloud_notm}} 관리](managing_f5.html)
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](../sddc/sd_addingremovingservices.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [F5 Deployment Guides](https://f5.com/solutions/deployment-guides){:new_window}
