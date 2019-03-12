---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# vCenter Server on IBM Cloud with Hybridity Bundle 개요
{: #vcs-hybridity-intro}

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle은 호스팅되는 프라이빗 클라우드로 안전하고 원활한 인프라 하이브리디티 및 애플리케이션 이동성을 위해 온프레미스 인프라를 쉽고 빠르게 클라우드로 확장하도록 도와줍니다.

vCenter Server Hybridity Bundle은 최소 4개의 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}에 배치되고, 가상 스토리지 영역 네트워크(VSAN)를 통해 전용 스토리지를 제공하며, 관리하기 쉬운 소프트웨어 정의 네트워킹 인프라(NSX-V)의 자동 배치 및 구성이 포함되어 있습니다. vCenter Server Hybridity Bundle은 일관성, 성능 및 규제 준수를 보장하는 자동화를 통해 배치되는 참조 아키텍처입니다. 대부분의 경우 전체 환경은 하루 내에 프로비저닝할 수 있으며, 베어메탈 인프라는 필요에 따라 신속하고 탄력적으로 컴퓨팅 및 저장 용량을 늘리거나 줄이도록 스케일링할 수 있습니다.

vCenter Server Hybridity Bundle을 강화하고 확장하기 위한 여러 옵션을 사용할 수 있습니다. {{site.data.keyword.cloud_notm}} 서비스 오퍼링은 스토리지 옵션과 다양한 공용 및 사설 WAN 연결 옵션을 추가할 뿐만 아니라, 플랫폼 보안, 네트워크 보안, 트래픽 로드 밸런싱에서 백업 및 장애 복구 영역까지 포함합니다.

플랫폼 보안 서비스에는 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}가 포함되어 있으며 자동화된 보안 및 준수 지원을 제공하여 클라우드 환경 및 관리자에 대한 가시성과 제어를 향상시킬 수 있습니다. HyTrust DataControl on {{site.data.keyword.cloud_notm}}는 강력한 암호화 및 확장 가능한 키 관리를 사용하여 데이터 보호를 제공하여 라이프사이클 동안 워크로드를 보호합니다. {{site.data.keyword.cloud_notm}} Secure Virtualization은 규제 준수를 단순화하고 암호화, 지오펜싱(geo-fencing) 정책 및 역할 기반 액세스 제어를 통해 데이터를 보호하는 반면, KMIP for VMware on {{site.data.keyword.cloud_notm}}의 경우 암호화 키 라이프사이클 관리 오퍼링이 {{site.data.keyword.cloud_notm}} 서비스 또는 고객 기본 제공 애플리케이션에서 사용되는 암호화 키를 관리합니다.

네트워크 보안 옵션은 네트워크 트래픽을 분석하고 가상 인프라를 보호하기 위해 FortiGate Security Appliance 디바이스의 고가용성 이중화를 프로비저닝하는 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 및 가상 인프라 내에서 중요한 보안 제어를 구현하여 위험을 줄이기 위해 FortiGate VM on {{site.data.keyword.cloud_notm}}의 고가용성 이중화를 배치하는 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}입니다. 더 많은 네트워크 보안 오퍼링이 개발 중입니다.

F5 on {{site.data.keyword.cloud_notm}} 네트워크 로드 밸런서 서비스 오퍼링은 성능을 최적화하고, F5 BIG-IP 스위트를 사용하여 가장 중요한 애플리케이션의 가용성과 보안을 보장합니다.

IBM, Veeam 및 Zerto의 백업 및 재해 복구 오퍼링은 재해가 발생하는 경우 마음의 안정을 찾을 수 있게 도와주며 운영 지속성을 제공합니다. IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}는 가상 환경을 위한 데이터 보호 및 가용성 솔루션입니다. Veeam on {{site.data.keyword.cloud_notm}} 를 통해 {{site.data.keyword.cloud_notm}}의 통합된 백업, 복구 및 복제 기능으로 Always-On Enterprise™에 대한 가용성을 제공합니다. Zerto on {{site.data.keyword.cloud_notm}}는 온프레미스 및 {{site.data.keyword.cloud_notm}} 고객에게 안전하고 유연하며 확장 가능한 재해 복구 솔루션을 제공합니다.

vCenter Server Hybridity Bundle은 IBM 관리 서비스를 추가하여 일상적인 운영 및 가상화, 게스트 OS 또는 애플리케이션 계층의 유지보수를 오프로드할 수 있지만 관리 서비스는 아닙니다. 또한 {{site.data.keyword.cloud_notm}} Professional Services 팀을 활용하면 마이그레이션, 구현, 계획 및 온보딩 서비스를 사용하여 클라우드로의 이동 속도를 높이는 데 도움이 됩니다.

vCenter Server Hybridity Bundle의 플랫폼 통합 옵션은 vRealize Suite 또는 vSphere with Operations Management와 같이 VMware에서 사용 가능한 옵션으로 제한되지 않지만, 오픈 소스 Terraform을 사용하여 IaC(Infrastructure as Code)를 관리하고 제공하는 [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) 및 [{{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)과 같은 여러 {{site.data.keyword.cloud_notm}} 서비스 오퍼링으로 확장됩니다.

vCenter Server Hybridity Bundle에 사용 가능한 서비스 및 다중 오퍼링 통합 옵션의 광범위한 포트폴리오는 서비스로서의 하이브리드를 가능하게 하는 진정한 하이브리드 플랫폼을 제공합니다.

## 관련 링크
{: #vcs-hybridity-intro-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
