---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-30"

---

# 운영 프로시저 소개
{: #opsprocs-intro}

많은 IT 조직은 Runbook에서 운영 프로시저를 문서화합니다. Runbook은 공통적으로 발생하는 IT 태스크를 설명하는 표준화된 문서, 참조 및 프로시저의 세트입니다. IT 직원은 업무를 수행하는 데 최적의 방식을 찾기 위해 Runbook을 참조합니다. Runbook은 표준화를 통해 조직의 효율성을 높이고 온보딩 직원을 더욱 효율적으로 지원합니다. 일반적으로 Runbook에는 다음 두 가지 유형이 있습니다.

1. 프로시저, 안내서 및 태스크를 캡처하는 데 사용되는 일반 문서입니다. 일반적인 특성이 있으며 공급업체에서 제공하는 기존의 문서를 참조합니다.
2. 엔터프라이즈를 위해 작성된 특수 문서입니다. 이 문서는 시스템에 특정하며, 공급업체 문서에서는 애플리케이션 또는 애플리케이션 스위트를 다루지 않습니다. 특수 문서를 문서화할 때 다음 구조를 사용하는 것이 좋습니다. 

 * 개요 - 다음에 대해 설명하는 섹션이 포함된 서비스의 개요입니다.
    * 서비스의 개념은 무엇이며, 서비스가 엔터프라이즈에 필요한 이유는 무엇입니까?
    * 서비스의 기본 담당자는 무엇입니까?
    * 서비스와 관련된 문제는 어떻게 보고합니까?
 * 빌드 - 이 섹션은 개발 팀과 서비스의 기본 소프트웨어 컴포넌트 및 서비스 구성 방법에 중점을 두고 있습니다. 소프트웨어 제품, OVA 위치, 배포 매체 또는 소스 코드 위치에 대한 정보입니다. 릴리스를 패키징하거나 분배하는 데 필요한 단계입니다. 여기에는 새 개발자가 시작하는 방법에 대한 필수 지시사항이 포함되어 있습니다.
 * 배치 - 이 섹션은 운영 팀과 소프트웨어 배치 방법에 중점을 두고 있습니다. 여기에는 하드웨어 및 가상화된 인프라의 세부사항과 vCPU, RAM 및 디스크 요구사항, OS 버전 및 구성, 설치할 미들웨어 또는 패키지를 포함한 가상 머신(VM) 빌드 방법이 포함되어 있습니다. 
 * 프로시저 - 추가, 변경 및 삭제, 공통 문제 및 솔루션, 문제점 해결 조언과 같은 공통 태스크에 대한 단계별 지시사항입니다. 
 * 문제점 해결 - 서비스 문제점 해결을 위한 일반적인 지침을 비롯하여 이 경보에 대한 단계별 태스크를 포함한 모니터링 시스템의 공통 경보 목록입니다.
 * 재해 복구 플랜 및 프로시저 - 기본 위치의 재해로 인해 다른 위치에서 서비스를 복구하는 방법에 대한 세부사항입니다.
 * 서비스 레벨 계약(SLA) - 계약된 서비스 매개변수(예: 운영 레벨 계약, 핵심 지표, 가용성 목표, 복구 지점 목표, 복구 시간 목표)입니다.

대부분의 IT 조직에는 참조 매뉴얼의 역할을 하는 여러 Runbook이 있습니다. 이 일련의 문서는 vCenter Server 인스턴스를 이용하는 사용자 조직이 일반적인 Runbook으로 사용할 수 있도록 설계되었습니다. 모든 Runbook의 컨텐츠가 조직의 요구사항에 따라 달라지지만, Runbook 작성의 방법은 다음 두 단계를 사용하여 상당히 표준화되어 있습니다.

1. 첫 번째 단계는 문서화되어야 하는 프로시저를 결정하고 나열되면 충분한 세부사항을 포함하여 각 프로시저를 문서화하는 것입니다.
2. 두 번째 단계는 지속적이며 이 프로시저의 유지보수, 업데이트 및 정정, 새 프로시저의 추가 및 더 이상 필요하지 않은 프로시저의 폐기로 구성됩니다. 

{{site.data.keyword.vmwaresolutions_full}}를 통해 온프레미스에서 {{site.data.keyword.cloud_notm}}의 인스턴스를 관리하도록 팀의 기존 스킬, 도구 세트 및 Runbook을 사용할 수 있습니다. 다음 일반 문서에는 공통 프로시저, 안내서 및 태스크가 포함되는 것이 좋습니다. 

* 구성 태스크 - 이 태스크는 시스템 관리자가 엔터프라이즈의 요구를 충족시키고 새 VM 추가 및 용량 증가와 같은 서비스 요청에 응답하도록 환경을 사용자 조정해야 하는 일반적인 활동입니다. 이 태스크는 다음 구조로 그룹화되어 있습니다.
 * 일반 안내서
 * VM 프로시저
 * vCenter 프로시저
 * vSphere ESXi 호스트 프로시저
 * 스토리지 프로시저
 * 네트워크 프로시저
* 알람 - vSphere에는 vSphere 환경에서 발생하는 이벤트를 추적하고 이 정보를 사용할 수 있도록 하는 이벤트 및 알람 서브시스템이 포함됩니다. 이 절에서는 이 서브시스템과 엔터프라이즈에서 알람을 활성화하고 사용하는 방법에 대해 설명합니다.
* 일일 사전 예방적 점검 - 이 점검을 통해 시스템 관리자는 환경을 정상 상태로 유지할 수 있습니다. 매일 수행하는 경우 용량 및 성능이 워크로드에 영향을 주지 않도록 해야 합니다. 
* 문제점 해결 - 일일 사전 예방적 점검을 수행하는 경우에도 워크로드에 영향을 주는 문제가 발생합니다. 그러므로 가능한 빨리 기본 문제를 수정해야 합니다. 이 문제점 해결 안내서와 일부 공통 문제점 해결 시나리오는 시스템 관리자가 이 문제를 빨리 식별하고 수정할 수 있도록 지원합니다.
* 규제 준수 - 규제 준수 안내서는 규정 준수 계획 또는 산업 우수 사례에 대한 환경의 규제 준수를 유지보수하는 데 필요한 몇 가지 통찰을 제공합니다. 이 안내서의 초점은 VMware 강화 안내서에 있으며, 여기에는 VMware 환경에 적합한 많은 우수 사례의 목록이 문서화되어 있습니다.

다수의 이전 태스크는 Operations Management on {{site.data.keyword.cloud_notm}}에서 자동화되며, 자동화되지 않은 태스크의 경우에는 이 도구를 통해 시스템 관리자가 수동 프로세스를 더욱 쉽게 처리할 수 있습니다. VMware 환경의 코어 컴포넌트가 Operations Management on {{site.data.keyword.cloud_notm}}에서 모니터되어야 합니다. 다음과 같이 수행됩니다.

## Operations Management on IBM Cloud
{: #opsprocs-intro-ops-mgmt}

vCenter Server 인스턴스를 모니터하고 관리하기 위해 사용할 수 있는 위치에서 엔터프라이즈 도구가 제공될 수 있습니다. 표 1에서는 vCenter Server 환경의 코어 컴포넌트, 모니터되어야 하는 이유, Operations Management on {{site.data.keyword.cloud_notm}}를 사용하여 모니터되는 방법에 대해 설명합니다. 자세한 정보는 참조 아키텍처 문서를 참조하십시오.

표 1. vCenter Server 환경 코어 컴포넌트

| 컴포넌트 | 목적 | 모니터 수행자  |
|---|---|---|
|vCenter | vCente는 vSphere 호스트를 관리하고 클러스터와 같은 가상화된 구조를 관리하는 인프라 관리 컴포넌트입니다. vSAN은 vCente를 통해 모니터됩니다. 분배 스위치와 같은 vSphere 네트워킹 및 포트 그룹은 vCenter를 통해 모니터됩니다. | vROps(vRealize Operations Manager) 및 VMware SDDC Health Management Pack. vRLI(vRealize Log Insights)는 vCenter에서 로그 데이터를 수집하고 Content Pack for vSphere는 특정 이해를 로그에 추가하고 다시 경보를 vROPs에 전송합니다. |
| vSphere 호스트 | vSphere 호스트는 가상화된 CPU, RAM 및 네트워크를 컴퓨팅 VM에 제공합니다. | vCenter를 통한 vROps입니다. vRLI는 로그 데이터를 수집합니다. |
|vSAN | vSAN은 VM에서 사용할 수 있도록 호스트에서 스토리지를 통합하여 데이터 저장소를 제공합니다. 성능 및 용량에 관한 문제는 이 VM에서 실행되는 애플리케이션에 영향을 줍니다. |vROps 및 Management Pack for vSAN은 vSAN의 모니터링에 도움이 되는 추가 대시보드를 제공합니다. vCenter vSAN 상태 검사는 vROps를 통해 수집됩니다. vRLI는 vCenter에서 로그 데이터를 수집합니다. |
|NSX | NSX는 컴퓨팅 VM으로 사용되는 가상화된 네트워크 컴포넌트를 제공하고 네트워크 장애는 이 VM에서 실행되는 애플리케이션에 영향을 줄 수 있습니다. | vROps 및 vROps Management Pack for VMware NSX는 네트워크 토폴로지에 대한 가시성을 제공합니다. vRLI는 제어기, ESG 및 논리 스위치와 같은 NSX 컴포넌트에서 로그 데이터를 수집합니다. vRNI(vRealize Network Insight)를 통해 심층적인 네트워크 문제를 해결할 수 있습니다. |

모니터링 외에도 Operations Management on {{site.data.keyword.cloud_notm}}는 구성, 규제 준수 및 이 문서에서 자세하게 설명된 사전 예방적 태스크에 도움을 줍니다. 


## 관련 링크
{: #opsprocs-intro-links}

* [vSphere Monitoring](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-A8B06BE0-E5FC-435C-B12F-A31618B21E2C.html){:new_window}
* [VMware 보안 강화 안내서](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro){:new_window}
* [vCenter Server 아티팩트 변경에 대한 고려사항](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
