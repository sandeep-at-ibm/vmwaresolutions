---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# IBM Cloud for VMware Solutions의 개요
{: #solution_overview}

{{site.data.keyword.vmwaresolutions_full}} 오퍼링을 사용하면 기존의 VMware 가상화된 데이터 센터를 {{site.data.keyword.cloud_notm}}로 확장하거나 클라우드 고유 애플리케이션을 수용할 수 있습니다.

이 솔루션은 클라우드로 용량 확장(및 필요 없으면 축소), 클라우드로 마이그레이션, 클라우드로 재해 복구 및 클라우드로 백업 등과 같은 유스 케이스를 지원합니다. 이 솔루션을 사용하면 개발, 테스트, 트레이닝, 랩 또는 프로덕션 전용의 클라우드를 작성할 수 있습니다.

대상 워크로드가 상위 레벨의 가용성과 확장성을 요하는 VMware Cloud Foundation 및 VMware vCenter Server를 포함한 {{site.data.keyword.vmwaresolutions_short}} 오퍼링의 디자인인 경우에는 이 정보를 검토하십시오.

이 디자인은 특정 유스 케이스를 위해 추가될 기타 내부 또는 공급업체 특정 컴포넌트에 대한 기초를 제공하는 베이스 라인 아키텍처로서의 역할을 합니다.

그림 1. VMware on {{site.data.keyword.cloud_notm}} 개요
![VMware on {{site.data.keyword.cloud_notm}}](solution_overview.svg "솔루션은 애플리케이션이 실행될 수 있는 VM에서 사용할 컴퓨팅, 네트워크 및 선택적으로 스토리지 리소스를 가상화합니다.")

## IBM Cloud for VMware Solutions의 주요 이점
{: #solution_overview-benefits}

VMware Cloud Foundation 및 vCenter Server on {{site.data.keyword.cloud_notm}}는 기본 구성 요소를 제공하며, 여기에는 vSAN을 포함한 공유 스토리지 옵션과 VMware vSphere, vCenter Server, NSX가 있습니다. 이러한 컴포넌트는 워크로드에 가장 적합한 VMware 소프트웨어 정의 데이터 센터 솔루션을 유연하게 구축하는 데 필요합니다.

고급 자동화 및 싱글 테넌트 베어메탈 인프라를 적용함으로써 몇 시간 내에 전체 VMware 환경을 {{site.data.keyword.cloud_notm}}에 신속하게 배치할 수 있습니다. 그런 다음 고유 VMware 클라이언트, 명령행 인터페이스(CLI), 기존 스크립트 또는 기타 친숙한 vSphere API 호환 도구를 통해 IBM 호스팅 환경에 액세스하고 이를 관리할 수 있습니다.

배치 후에 ESXi 호스트 노드를 추가하고 일부 관리 컴포넌트에 대한 패치와 백업을 관리할 수 있습니다. {{site.data.keyword.cloud_notm}} Professional Services 및 Managed services를 활용하면 마이그레이션, 구현 및 온보딩 서비스 등의 오퍼링을 사용하여 클라우드로의 이동 속도를 높이는 데 도움이 됩니다.

VMware on {{site.data.keyword.cloud_notm}} 오퍼링은 다음과 같은 이점을 제공합니다.

* 리소스의 조달, 아키텍처, 구현 및 배치에 걸리는 시간을 몇 주나 심지어는 몇 달에서 몇 시간으로 줄임으로써 개발자 및 비즈니스 라인을 위한 IT 프로젝트의 **전달 가속화**.
* 저장 데이터의 암호화를 포함하여 호스팅되는 프라이빗 클라우드의 전용 Bare Metal Server를 사용하여 **보안 개선**.
* 가상화 관리에 대한 전체 관리 액세스를 제공하여 기존 VMware 도구, 스크립트 및 교육 투자를 그대로 유지함으로써 배치된 하이브리드 클라우드의 **지속적인 관리 및 통제 가능**.
* 전세계 30여개의 {{site.data.keyword.CloudDataCents_notm}}에 걸쳐 있는 IBM Professional 및 Managed Services를 사용하여 **글로벌 규모로 VMware 전문지식을 최대한 활용**.

## 관련 링크
{: #solution_overview-related}

* [디자인 개요](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [용량 스케일링](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling)
* [컴포넌트 백업](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
