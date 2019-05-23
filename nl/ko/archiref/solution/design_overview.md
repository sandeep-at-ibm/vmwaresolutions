---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-07"

subcollection: vmware-solutions


---
# IBM Cloud for VMware Solutions 컴포넌트
{: #design_overview}

{{site.data.keyword.vmwaresolutions_full}}에서는 전세계에서 {{site.data.keyword.CloudDataCents_notm}}에 VMware 기술 컴포넌트를 배치하기 위한 자동화를 제공합니다.

이 솔루션 포트폴리오의 오퍼링에는 자동으로 배치되고 구성된 클러스터 내에 VMware vSphere 제품 즉, VMware vSphere ESXi, 임베디드 PSC(Platform Services Controller)가 포함된 VMware vCenter Server Appliance, VMware NSX-V 또는 NSX-T 및 VMware vSAN(선택사항)이 포함되어 있습니다.

이 아키텍처는 단일 클라우드 지역으로 구성되며 동일한 데이터 센터 내의 다른 지역 및 다른 {{site.data.keyword.cloud_notm}} 팟(Pod)에 위치한 여러 클라우드 지역으로 확장하는 기능을 지원합니다. 지역은 고유한 vCenter Server 인스턴스로서 정의됩니다. 이 디자인은 vCenter Server 인스턴스 내에서 가상 용량의 자동화된 확장과 축소도 허용합니다.

![{{site.data.keyword.vmwaresolutions_short}}의 솔루션 컴포넌트](../../images/vcsv4radiagrams-ra-full.svg "이 솔루션은 실제 인프라, 가상 인프라, 인프라 관리 및 공통 서비스로 구성되어 있습니다.")

## 관련 링크
{: #design_overview-related}

* [실제 인프라 디자인](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_physicalinfrastructure)
* [가상 인프라 디자인](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure)
* [공통 서비스 디자인](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice)
* [인프라 관리 디자인](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_infrastructuremgmt)
