---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# IBM Cloud Private
{: #vcsnsxt-overview-icp}

{{site.data.keyword.icpfull_notm}}는 컨테이너화된 애플리케이션의 개발 및 관리를 위한 애플리케이션 플랫폼입니다. 컨테이너 오케스트레이터 Kubernetes, 개인용 이미지 저장소, 관리 콘솔, 모니터링 프레임워크 및 애플리케이션을 배치, 관리, 모니터 및 확장할 수 있는 중앙 위치를 제공하는 그래픽 사용자 인터페이스가 포함된 통합 환경입니다.

{{site.data.keyword.cloud_notm}} Private에는 다음 기능이 있습니다.
-	**Unified 설치 프로그램** – 이 설치 프로그램은 Ansible 기반 설치 프로그램을 사용하여 마스터, 작업자 및 프록시 노드가 있는 Kubernetes 기반 클러스터를 신속하게 설치합니다.
-	**{{site.data.keyword.cloud_notm}} Private 관리 콘솔** – 안전한 중앙 집중식의 단일 관리 콘솔에서 애플리케이션 및 클러스터를 관리, 모니터링하고 문제점을 해결합니다.
-	**Private Docker 이미지 레지스트리** - 이 로컬 레지스트리에는 Docker Hub와 동일한 모든 기능이 있지만 이미지를 보거나 가져올 수 있는 사용자를 제한할 수 있습니다.
-	**중앙 집중식 소프트웨어 및 서비스 카탈로그** - 이 카탈로그는 패키지를 찾아보고 클러스터에 설치할 수 있는 중앙 집중식 위치를 제공합니다. 추가 IBM 제품의 패키지는 기본 {{site.data.keyword.cloud_notm}} Private
저장소 목록에 포함된 큐레이트 저장소에서 사용할 수 있습니다.
-	**격리된 테넌트 네트워크** - Calico는 클러스터 내에서 향상된 성능과 네트워크 격리를 허용합니다. Calico를 사용하여 클러스터 내에서 각 프로젝트를 위한 격리된 서브넷을 작성할 수 있습니다. 이 네트워크 격리는 데이터 전송 중에 보안을 강화하고 애플리케이션과 해당 데이터가 손상될 수 있는 가능성을 줄입니다. 또한 Calico는 단일 네임스페이스 내의 오브젝트 공유에서 미세한 제어를 사용할 수 있는 새로운 네트워크 정책을 쉽게 만들 수 있도록 합니다.
-	**ELK 스택을 사용한 강력한 모니터링 및 로깅** - {{site.data.keyword.cloud_notm}} Private은 로그와 메트릭의 수집, 저장 및 조회에 Elasticsearch, Logstash, Filebeat 및 Heapster를 사용합니다. 이 모니터링 및 로깅 프로세스는 로그와 메트릭에 대한 액세스와 조회를 수행할 때 모든 로그와 메트릭을 위한 중앙 집중식 저장소와 더 나은 성능 및 향상된 안정성을 제공합니다.

## IBM Cloud Private 컴포넌트
{: #vcsnsxt-overview-icp-comp}

{{site.data.keyword.cloud_notm}} Private 클러스터에는 부트, 마스터, 작업자 및 프록시라는 4개의 노드 기본 클래스가 있습니다. 클러스터에서 관리, VA(Vulnerability Advisor) 및 etcd 노드를 선택적으로 지정할 수 있습니다.
-	**부트 노드** - 부트 노드는 설치, 구성, 노드 스케일링 및 클러스터 업데이트를 실행하는 데 사용됩니다.
-	**마스터 노드** - 마스터 노드는 관리 서비스를 제공하고 클러스터에서 작업자 노드를 제어합니다. 마스터 노드는 리소스 할당, 상태 유지보수, 스케줄링 및 모니터링을 담당하는 프로세스를 호스팅합니다.
-	**작업자 노드** - 작업자 노드는 태스크 실행을 위해 컨테이너화된 환경을 제공하는 노드입니다. 요구가 증가하면 클러스터에 더 많은 작업자 노드를 쉽게 추가하여 성능과 효율성을 향상시킬 수 있습니다.
-	**프록시 노드** - 프록시 노드는 클러스터 내에서 작성된 서비스에 외부 요청을 전송하는 노드입니다.
-	**관리 노드** - 관리 노드는 모니터링, 미터링 및 로깅과 같은 관리 서비스만 호스팅하는 선택적 노드입니다. 전용 관리 노드를 구성하면, 마스터 노드에 과부하가 발생하는 것을 방지할 수 있습니다.
-	**VA(Vulnerability Advisor) 노드** - VA 노드는 Vulnerability Advisor 서비스 실행에 사용되는 선택적 노드입니다.
-	**etcd 노드** - etcd 노드는 etcd 분배 키 값 저장소 실행에 사용되는 선택적 노드입니다.

## IBM Cloud Private 네트워킹
{: #vcsnsxt-overview-icp-networking}

Calico를 사용하면 {{site.data.keyword.icpfull_notm}} 네트워크 관리가 용이합니다.
Calico는 OSI(Open System Interconnection) 모델의 계층 3 네트워크 계층을 사용합니다. Calico는 BGP(Border Gateway Protocol)를 사용하여 에이전트 노드 간의 통신을 용이하게 하는 라우팅 테이블을 빌드합니다.

Calico 네트워킹에 대한 자세한 정보는 [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-overview-iks)의 내용을 참조하십시오.
