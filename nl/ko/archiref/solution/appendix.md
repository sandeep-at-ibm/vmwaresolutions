---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmware-solutions


---

# VMware 컴포넌트 에디션의 비교 차트
{: #solution-appendix}

## VMware NSX 에디션 비교
{: #solution-appendix-nsx-editions}

이 디자인 내에는 라이센스가 필요한 여러 컴포넌트가 있습니다. 이 정보는 환경이 올바르게 작동하는 데 필요한 최소 라이센스를 캡처합니다.

표 1. 라이센스 요구사항

컴포넌트 | 용도 |라이센스
----------|---------|-------------
**vSphere** | 컴퓨팅 가상화 | vSphere 6.7 Enterprise Plus
**vCenter Server** |인프라 관리 | vCenter Server 6.7 Standard
**NSX** | 네트워크 가상화 | NSX Base for Service Providers 6.4
**vSAN** | 스토리지 가상화 | vSAN 6.6 Advanced  

NSX Base for Service Providers 에디션은 VMware vCloud Air Network(vCAN)를 통해 서비스 제공자만 사용할 수 있습니다. 이 에디션의 기능은 다음 표에서 찾을 수 있습니다.
{:note}

표 2. VMware NSX 에디션 비교 차트

| NSX 기능                                   | Base | Advanced |Enterprise |
|-----------------------------------------------|------|----------|------------|
| 분배 스위칭 및 라우팅             | •    | •        | •          |
| NSX Edge 방화벽                             | •    | •        | •          |
| NAT                                           | •    | •        | •          |
| NSX Edge 로드 밸런싱                       | •    | •        | •          |
| VPN(IPsec)                                   | •    | •        | •          |
| VPN(SSL)                                     | •    | •        | •          |
| API 구동 자동화                         | •    | •        | •          |
| vRealize 및 OpenStack과 통합\*     | •    | •        | •          |
| vRealize의 보안 정책 자동화 |      | •        | •          |
| 실제 환경에 대한 SW L2 브릿징        |      | •        | •          |
| ECMP와 동적 라우팅(활성-활성)     |      | •        | •          |
| 분배 방화벽                       |      | •        | •          |
| Active Directory와 통합             |      | •        | •          |
| 서버 활동 모니터링                    |      | •        | •          |
| 서비스 삽입(서드파티 통합)     |      | •        | •          |
| 분배 로드 밸런싱                    |      |          | •          |
| 교차 vCenter NSX                             |      |          | •          |
| 다중 사이트 NSX 최적화                  |      |          | •          |
| 원격 게이트웨이                                |      |          | •          |
| HW VTEP와 통합                     |      |          | •          |
\*L2, L3 & NSX Edge 통합에만 해당됩니다. 보안 그룹의 이용은 없습니다.

## VMware vSAN 에디션 비교
{: #solution-appendix-vsan-editions}

다음 표에는 솔루션이 지원하는 VMware vSAN의 **Advanced** 및 **Enterprise** 에디션의 사용 가능한 기능이 나열되어 있습니다.

표 3. VMware vSAN 에디션 비교 차트

| vSAN 기능                                    | Advanced |Enterprise |
|-------------------------------------------------|----------|------------|
| 스토리지 정책 기반 관리                 | •        | •          |
| 플래시 읽기/쓰기 캐싱                        | •        | •          |
| 분배 RAID                                | •        | •          |
| 가상 분배 스위치                      | •        | •          |
| 랙 감지                                  | •        | •          |
| vSphere 복제                             | •        | •          |
| 소프트웨어 체크섬                               | •        | •          |
| 올플래시(All-Flash) 하드웨어                              | •        | •          |
| iSCSI 대상 서비스                            | •        | •          |
| IOPS 한계                                      | •        | •          |
| 중복 제거 및 압축                   | •        | •          |
| RAID-5/6 삭제 코딩                         | •        | •          |
| 저장 데이터 암호화                         |          | •          |
| 로컬 장애 보호의 확장 클러스터 |          | •          |

## 관련 링크
{: #solution-appendix-related}

* [솔루션 개요](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [디자인 개요](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [컴포넌트 백업](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
