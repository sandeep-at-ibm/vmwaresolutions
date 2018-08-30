---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# FortiGate Virtual Appliance on IBM Cloud 주문

서비스가 포함된 새 인스턴스를 주문할 때 또는 기존 인스턴스에 서비스를 추가하여 FortiGate Virtual Appliance on {{site.data.keyword.cloud}} 서비스를 주문할 수 있습니다.

## 새 인스턴스에 대한 FortiGate Virtual Appliance on IBM Cloud 주문

다음 방법 중 하나를 사용하여 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}와 함께 새 인스턴스를 주문할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 인스턴스를 주문할 때 **서비스** 섹션에서 **FortiGate Virtual Appliance on IBM Cloud**를 선택하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **FortiGate Virtual Appliance on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **새 인스턴스에 추가**를 선택하십시오.

## 기존 인스턴스에 대한 FortiGate Virtual Appliance on IBM Cloud 주문

다음 방법 중 하나를 사용하여 기존 인스턴스에 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스를 추가할 수 있습니다.
* {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 해당 서비스를 추가할 인스턴스를 보고 왼쪽 탐색 분할창에서 **서비스**를 클릭한 후에 **추가**를 클릭하십시오.
* {{site.data.keyword.cloud_notm}} 카탈로그에서 **FortiGate Virtual Appliance on IBM Cloud**를 선택하고 서비스 설정을 지정한 후에 **기존 인스턴스에 추가**를 선택하십시오.

## FortiGate Virtual Appliance on IBM Cloud 서비스 구성

서비스를 주문할 때 다음 설정을 제공하십시오.

### 이름

서비스 이름을 입력하십시오.

### 배치 크기

{{site.data.keyword.cloud_notm}}에서는 다음의 배치 크기 옵션을 제공합니다.
* 소형(2개의 vCPU / 4GB RAM)
* 중형(4개의 vCPU / 6GB RAM)
* 대형(8개의 vCPU / 12GB RAM)

### 라이센스 모델

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}에 대한 라이센스 모델은 다음 옵션을 제공합니다.
<dl class="dl">
        <dt class="dt dlterm">표준 FW</dt>
        <dd class="dd">이 번들에는 상태 기반 패킷 검사, VLAN 보호 및 고급 로깅, 유입/유출 방화벽 규칙, SSL/IPSec VPN 종료 및 지속적 지원이 포함됩니다.</dd>
        <dt class="dt dlterm">표준 FW + UTM</dt>
        <dd class="dd">이 번들에는 NGFW IPS 및 웹 필터링, 안티바이러스 및 안티스팸, IP 및 도메인 평판, 코어 FortiCare 보안 서비스 외에도 모든 표준 방화벽 서비스가 포함됩니다.</dd>
        <dt class="dt dlterm">표준 FW + 엔터프라이즈</dt>
        <dd class="dd">이 번들에는 FortiSandbox 클라우드 및 모바일 보안 외에도 모든 표준 방화벽 및 UTM 서비스가 포함됩니다.</dd>
</dl>

**중요**: 서비스 설치 후 라이센스 모델을 변경할 수 없습니다. 라이센스 모델을 변경하려면 기존 서비스를 제거하고 다른 라이센스 옵션을 선택하여 서비스를 다시 설치해야 합니다.

### 관련 링크

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 개요](fortinetvm_considerations.html)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 관리](managingfortinetvm.html)
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](../sddc/sd_addingremovingservices.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_addingremovingservices.html)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet 웹 사이트](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
