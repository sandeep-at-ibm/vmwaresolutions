---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# vCenter Server의 연결된 스토리지 정보

연결된 스토리지는 VMware vCenter Server on {{site.data.keyword.cloud}} 오퍼링의 확장입니다. VMware vCenter Server on {{site.data.keyword.cloud_notm}}에 대한 연결된 스토리지 솔루션 아키텍처는 디자인에서 각 컴포넌트의 상위 레벨 구성 및 솔루션의 컴포넌트를 자세히 보여줍니다.

vCenter Server 디자인에 대한 자세한 정보는 [솔루션 개요](../solution/solution_overview.html)를 참조하십시오.

## vCenter Server에 대한 연결된 스토리지의 주요 이점

연결된 스토리지가 VMware 환경의 전제조건이 아닌 반면 공유 스토리지 디바이스로 사용 시 IT 오퍼레이션에 대해 사용자에게 많은 이점이 제공됩니다. 공유 스토리지 디바이스를 사용하면 고가용성, 분배된 리소스 스케줄러, 스토리지 용량의 효율적인 사용 및 다음 표에 설명된 vSphere 기능 사용을 통한 단순화된 관리가 가능합니다.

표 1. vCenter Server에 대한 연결된 스토리지의 기능 설명

|기능 |설명 |
|:------- |:----------- |
| vSphere Distributed Resource Scheduler and Resource Pools | 이 기능을 사용하면 로드 밸런싱 및 가상 머신(VM) 배치를 통해 리소스의 추출 및 유연한 관리가 가능합니다. 리소스 풀은 계층으로 그룹화할 수 있으며 사용 가능한 CPU 및 메모리 리소스를 계층적으로 파티셔닝하는 데 사용할 수 있습니다. |
|vSphere High Availability | 이 기능은 클러스터에 있는 호스트 및 VM(풀링하여)에 고가용성을 제공합니다. 클러스터의 호스트는 모니터됩니다. 장애가 발생하면 장애가 발생한 호스트의 VM이 대체 호스트에서 다시 시작됩니다. |
| vSphere Datastore Clusters | 이 기능은 데이터 저장소 콜렉션에 공유 리소스 및 공유 관리 인터페이스를 제공합니다. |
| vSphere Fault Tolerance | 이 기능은 전체 호스트에 장애가 발생한 경우에도 작동 중단을 없애 VM에 지속적 가용성을 제공합니다. |

### 관련 링크

* [솔루션 개요](../solution/solution_overview.html)
