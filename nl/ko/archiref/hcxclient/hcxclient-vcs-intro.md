---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# VMware HCX on IBM Cloud 소개
{: #hcxclient-vcs-intro}

VMware HCX on IBM Cloud 서비스를 사용하면 IBM Cloud for VMware Solutions와 온프레미스 VMware 가상화 데이터 센터 간에 원활한 연결을 작성할 수 있습니다.

IBM Cloud for VMware Solutions를 통해 IBM Cloud에 VMware vCenter Server(VCS)를 완전히 자동화하고 빠르게 배치할 수 있습니다. 이 오퍼링은 온프레미스 인프라를 보완하고, 온프레미스에서 사용하는 동일한 도구, 스킬 및 프로세스를 사용하여 변환 없이 IBM Cloud에서 기존 워크로드 및 이후의 워크로드가 실행될 수 있도록 합니다. 자세한 정보는 [가상화된 사설 클라우드를 확장하기 위한 가상화](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture)를 참조하십시오.

VMware HCX on IBM Cloud 서비스는 워크로드에 대한 원활한 네트워크 확장 및 양방향 마이그레이션을 작성하여 vCenter Server의 인스턴스를 기존의 온프레미스 가상화 데이터 센터와 결합시킴으로써 이 하이브리디티를 더욱 발전시킵니다.

IBM Cloud VMware 대상 사이트에서 가상 머신으로 배치된 VMware HCX on IBM Cloud 컴포넌트는 피어 온프레미스 소스 사이트에 설치된 VMware HCX on IBM Cloud 컴포넌트와 연결할 수 있도록 합니다.

![VMware vCenter Server – 하이브리드 클라우드 서비스](../../images/cloudfoundation_hybrid_cloud_services.svg "VMware vCenter Server – 하이브리드 클라우드 서비스")

이 연결을 통해 온프레미스와 IBM Cloud 간에 느슨하게 결합된 상호연결이 작성되며 다음과 같은 기능을 사용할 수 있습니다.
* 간단한 상호연결 – 실제 접속(예: 공용 인터넷, 사설 VPN 또는 직접 링크)에서 논리 네트워크 연결을 쉽게 설정할 수 있습니다.
* 계층 2 확장 – 온프레미스 네트워크가 클라우드로 확장됩니다. 이 네트워크에는 온프레미스 서브넷 및 IP 주소 지정이 포함됩니다.
* 암호화 – 네트워크 트래픽이 두 사이트 간에 안전하게 암호화됩니다.
* 최적화된 네트워크 – 네트워크 트래픽이 가능한 빠르게 이동할 수 있도록 최상의 연결을 선택하여 효율적으로 연결이 흐르게 합니다.
* 데이터 중복 제거 – 네트워크 트래픽의 50% 만큼 감소할 수 있습니다. 워크로드가 이동되는 경우 네트워크 트래픽이 대상 사이트 게이트웨이를 사용하고 원래 사이트로 다시 "헤어핀"하지 않도록 근접 라우팅에서 네트워크 경로 또는 게이트웨이를 변경할 수 있습니다.
* 무중단 마이그레이션 – vMotion을 사용하여 실행 중인 시스템을 클라우드로 이동하거나 클라우드에서 이동할 수 있습니다.
* 예정된 마이그레이션 – 임의의 가상 머신을 대상 사이트에 복제한 후 원래 사이트에서 실행 중인 시스템을 교체하는 지정된 시간에 해당 사이트에서 활성화할 수 있습니다.
* 보안 정책의 마이그레이션 – NSX가 온프레미스에 사용되는 경우 보안 정책 또는 방화벽은 워크로드와 함께 이동됩니다.

## 관련 링크
{: #hcxclient-vcs-intro-related}

* [HCX 컴포넌트 용어집](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [설치 환경 준비](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 클라이언트 배치](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 온프레미스 서비스 메시](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 하이브리드 클라우드 마이그레이션](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [매개변수 및 컴포넌트 모니터링](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
