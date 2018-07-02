---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# 문제점 해결 지원

## 문제점

일부 상황에서 더 복잡한 문제가 발생할 수 있고, 루트 원인 분석을 완료하고 솔루션을 제공하기 위한 로그 파일이 부족합니다.

## 해결

문제점을 해결하고 이 문제의 유형을 해결하려면 {{site.data.keyword.vmwaresolutions_full}} 지원 팀이 {{site.data.keyword.cloud_notm}} 관리 가상 머신(VM)에 액세스해야 합니다. IBM CloudDriver라고 하는 이 관리 VM은 배치된 VMware Cloud Foundation 인스턴스 및 VMware vCenter Server 인스턴스를 관리하는 데 사용되는 기본 인터페이스입니다.

보안상의 이유로, IBM CloudDriver에 대한 액세스가 제한됩니다. {{site.data.keyword.vmwaresolutions_short}} 지원 팀이 고객 승인을 요청하고 승인을 받은 후 팀은 {{site.data.keyword.cloud_notm}} 인프라 가상 서버를 사용하여 CloudDriver 컴포넌트에 액세스할 수 있습니다. 이 서버는 {{site.data.keyword.cloud_notm}} 인프라 FCR(Frontend Customer Router) 공용 네트워크를 통해 환경에 연결합니다.

그런 다음, {{site.data.keyword.vmwaresolutions_short}} 지원 팀은 매시간 {{site.data.keyword.cloud_notm}} 인프라 가상 서버를 배치하기 위해 인스턴스의 주문 및 구성을 위해 제공된 {{site.data.keyword.cloud_notm}} 인프라 {{site.data.keyword.slapi_short}} 키(또는, 필요한 경우 고객이 제공하는 업데이트된 키)를 사용합니다.

문제점 해결을 위한 IBM CloudBuilder 도구 사용 비용이 고객 계정에 청구됩니다. 디버그 및 조치 방안이 완료된 후 IBM CloudBuilder 컴포넌트가 릴리스됩니다.

문제점 해결을 위해 사용되는 {{site.data.keyword.cloud_notm}} 인프라 가상 서버가 다음 스펙과 함께 전개됩니다.

* 1개의 CPU, 1GB RAM이 탑재된 CentOS 7 공용 노드 VSI(Virtual Service Instance)가 사용됩니다.
* VSI는 인스턴스가 있는 동일한 기본 공인 및 사설 VLAN의 동일한 데이터 센터에 배치됩니다.
* 사후 설치 스크립트는 {{site.data.keyword.vmwaresolutions_short}} 지원 팀에서 소유하고 사용하는 특정 IP 주소 세트에서 수신되는 SSH 연결만 허용하는 방화벽 규칙을 설정하도록 VSI 배치와 함께 사용됩니다.
* 해당 IP 주소를 사용하는 지원 시작 시스템은 사설 {{site.data.keyword.cloud_notm}} 인프라 네트워크를 통해서만 액세스되고 HA(High Availability)쌍 {{site.data.keyword.cloud_notm}} 인프라 Vyatta 시스템으로 보호되는 {{site.data.keyword.cloud_notm}} 인프라에서 실행됩니다.
* IBM Security 도구(예: QRadar®, Nessus 및 IBM BigFix®)는 보안 위협으로부터 지원 시작 시스템을 모니터하는 데 사용됩니다.
