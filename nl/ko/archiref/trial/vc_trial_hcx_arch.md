---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server on IBM Cloud에 대한 단일 노드 평가판의 HCX on IBM Cloud 아키텍처 디자인
{: #vc_trial_hcx_arch}

VMware vCenter Server on {{site.data.keyword.cloud_notm}}에 대한 단일 노드 평가판이 포함된 VMware HCX on {{site.data.keyword.cloud}}는 {{site.data.keyword.vmwaresolutions_short}} 인스턴스와 온프레미스 VMware 가상화 데이터 센터 간의 원활한 연결을 사용으로 설정하는 오퍼링입니다. vCenter Server의 경우 최소 세 개의 노드가 권장되지만, 이 단일 노드 평가판은 하이브리드 클라우드 구현의 이점을 테스트하고 경험할 수 있는 저비용 경로를 제공합니다.

{{site.data.keyword.vmwaresolutions_short}}를 통해 {{site.data.keyword.cloud_notm}}에 vCenter Server 구성을 완전히 자동화하고 빠르게 배치할 수 있습니다. vCenter Server 오퍼링의 단일 노드 평가판은 온프레미스 인프라를 보완하며, 변환 없이 {{site.data.keyword.cloud_notm}}에서 실행될 기존 및 이후 워크로드를 허용합니다. 오퍼링은 온프레미스에 사용되는 동일한 도구, 스킬 및 프로세스를 사용합니다. {{site.data.keyword.vmwaresolutions_short}} 오퍼링에 대한 자세한 정보는 [IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture)를 참조하십시오.

HCX on {{site.data.keyword.cloud_notm}} 서비스는 워크로드에 대한 원활한 네트워크 확장 및 양방향 마이그레이션을 작성하여 vCenter Server 인스턴스와 기존 온프레미스 가상화 데이터센터를 결합시킵니다. {{site.data.keyword.cloud_notm}} VMware 대상 사이트에서 가상 머신(VM)으로 배치된 HCX on IBM Cloud 컴포넌트를 사용하면 피어 온프레미스 소스 사이트에 설치된 HCX on {{site.data.keyword.cloud_notm}} 컴포넌트와 연결할 수 있습니다.

그림 1. HCX 아키텍처

![HCX 아키텍처](hcx-architecture.svg "HCX 아키텍처")

다음 정보는 HCX on {{site.data.keyword.cloud_notm}} 서비스 구현의 디자인을 제공합니다. 대상 측 {{site.data.keyword.vmwaresolutions_short}} 인스턴스의 컴포넌트와 소스, 온프레미스에 배치된 컴포넌트가 모두 포함됩니다.

## HCX on IBM Cloud 개요
{: #vc_trial_hcx_arch-ovw}

{{site.data.keyword.cloud_notm}}는 온프레미스 vSphere vCenter 네트워크를 {{site.data.keyword.vmwaresolutions_short}} 배치에 원활하게 통합합니다. 하이브리드 네트워킹은 온프레미스 vSphere vCenter 네트워크를 {{site.data.keyword.cloud_notm}}로 확장하며, 양방향 VM 이동성을 지원합니다.

HCX는 소스 및 대상 암호화와 복호화 프로세스를 소유하며, 일관성 있는 보안을 보장하고 VM 마이그레이션 및 네트워크 확장과 같은 하이브리드 워크플로우를 허용합니다. 이 오퍼링은 확장된 네트워크 성능을 향상시키도록 최적화된 소프트웨어 정의 광역 네트워크(WAN)를 작성하며, 근거리 통신망(LAN) 속도에 도달하는 성능을 사용할 수 있습니다. HCX는 양방향 워크로드와 {{site.data.keyword.cloud_notm}}로의 VMware NSX 보안 정책 마이그레이션을 사용으로 설정하고, vSphere vCenter와 통합하며, vSphere Web Client에서 관리됩니다.

### 계층 2 네트워크 확장
{: #vc_trial_hcx_arch-layer-2-extension}

HCX는 기존 온프레미스 vCenter에서 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 또는 vCenter Server를 실행하는 {{site.data.keyword.CloudDataCent_notm}}까지 네트워크를 안전하게 확장하도록 기존의 온프레미스 vSphere 자산을 허용합니다. 다음 항목으로 이 기능을 사용할 수 있습니다.

* HCX는 Layer 2 Concentrator(L2C)라고 하는 어플라이언스를 제공합니다.
* 확장된 네트워크는 vCenter Server에 배치된 {{site.data.keyword.cloud_notm}} NSX Edge 어플라이언스에 연결합니다.
* 확장성을 확보하고 온프레미스 vCenter에서 처리량을 늘리기 위해 둘 이상의 표준 Layer 2 Concentrator를 배치할 수 있는 기능입니다.
* 클라우드 게이트웨이와 확장된 계층 2를 통해 마이그레이션된 VM은 IP와 MAC 주소를 보유할 수 있습니다.

### 가상 머신 마이그레이션
{: #vc_trial_hcx_arch-vm-mig}

HCX는 다음과 같은 세 가지의 VM 이동 방법을 제공합니다.

* 짧은 작동 중단 마이그레이션
* vSphere vMotion 마이그레이션
* 콜드 마이그레이션

#### 짧은 작동 중단 마이그레이션
{: #vc_trial_hcx_arch-low-downtime-mig}

짧은 작동 중단 마이그레이션은 VMware ESX 또는 VMware ESXi 하이퍼바이저에서 구현되는 분배된 기술인 vSphere 복제에 의존합니다. 온프레미스 HCX 배치는 {{site.data.keyword.cloud_notm}}에서 라이브 VM의 복제본을 작성하고 IBM Cloud로 이동하며 소스 VM의 전원을 끄고 마이그레이션된 VM의 전원을 켜도록 전환을 수행합니다. 마이그레이션 경로는 항상 클라우드 게이트웨이를 통과합니다. 전송은 인터넷, 계층 2 확장 네트워크 또는 직접 연결 회선이 될 수 있습니다. 모든 방향에서 VM을 두 번 이상 마이그레이션할 수 있습니다.

#### vSphere vMotion 마이그레이션
{: #vc_trial_hcx_arch-vmotion-mig}

{{site.data.keyword.cloud_notm}}로 확장된 네트워크에서 vSphere vMotion 마이그레이션을 사용하여 라이브 VM을 전송할 수 있습니다. vMotion 마이그레이션은 무중단 마이그레이션 또는 교차 클라우드 vMotion이라고도 합니다.

#### 콜드 마이그레이션
{: #vc_trial_hcx_arch-cold-mig}

콜드 마이그레이션은 Layer 2 Concentrator를 사용하여 작성되는 확장된 네트워크를 통해 전원이 꺼진 VM을 {{site.data.keyword.cloud_notm}}로 전송할 수 있는 기능을 제공합니다.

#### 공통 마이그레이션 기능
{: #vc_trial_hcx_arch-common-feat}

다음 기능은 모든 세 가지 유형의 마이그레이션에 사용 가능합니다.

* 마이그레이션 처리량 및 속도를 향상시키는 소프트웨어 정의 WAN 최적화입니다.
* 지정된 시간에 마이그레이션을 스케줄합니다.
* 호스트 이름, VM 이름(또는 둘 다)를 유지합니다.

### 네트워킹
{: #vc_trial_hcx_arch-network}

다음 네트워킹 기능은 클라우드 게이트웨이 및 Layer 2 Concentrator로 빌드됩니다.

#### 인텔리전트 플로우 라우팅
{: #vc_trial_hcx_arch-intel-flow}

인텔리전트 플로우 라우팅은 워크로드가 가능한 빨리 이동되도록 인터넷 경로를 기반으로 최적의 연결을 자동으로 선택하고, 전체 연결을 효율적으로 분산시킵니다. 백업 또는 복제와 같이 대형 플로우로 인해 CPU 경합이 발생하는 경우 소형 플로우가 사용량이 적은 CPU로 라우트되어 대화식 트래픽의 성능이 향상됩니다.

#### 근접 라우팅
{: #vc_trial_hcx_arch-prox-routing}

근접 라우팅은 온프레미스와 클라우드 모두에서 확장되고 라우트되는 네트워크에 연결된 VM 간의 전달이 대칭적인지 확인합니다. 이 기능에는 고객 프레미스와 클라우드 간에 구성되어 있는 동적 라우팅이 포함된 고급 네트워크 서비스가 필요합니다.

사용자가 네트워크를 클라우드에 확장하는 경우 계층 2 연결이 {{site.data.keyword.cloud_notm}} 네트워크로 확장됩니다. 그러나 라우트 최적화가 없으면 계층 3 통신 요청은 라우트되도록 온프레미스 네트워크 원점으로 돌아가야 합니다. 이 돌아가기는 "트럼본" 또는 "헤어핀"이라고 합니다. 트럼본은 소스 및 대상 VM이 모두 클라우드에 상주하는 경우에도 패킷이 네트워크 원점과 클라우드 사이를 이동해야 하므로 비효율적입니다.

전달 경로에 상태 저장 방화벽 또는 연결의 양방향이 모두 표시되어야 하는 기타 인라인 장비가 포함되어야 하는 경우 통신에 실패할 수 있습니다. 클라우드를 종료하는 유출 경로가 확장된 계층 2 네트워크 또는 조직의 라우트된 네트워크인 경우 VM 통신(라우트 최적화 없이) 장애가 발생합니다. 온프레미스 네트워크는 확장된 네트워크 "바로 가기"에 대해 모르고 있습니다. 이 문제점을 비대칭 라우팅이라고 합니다. 솔루션은 온프레미스 네트워크가 {{site.data.keyword.cloud_notm}}를 통해 라우트에 대해 알아볼 수 있도록 근접 라우팅을 사용으로 설정하는 것입니다.

클라우드 게이트웨이는 클라우드에서 VM의 인벤토리를 유지보수합니다. 다음 VM 상태에 대해서도 이해하고 있습니다.

* vMotion을 사용하여 {{site.data.keyword.cloud_notm}}로 전송됨(무중단 마이그레이션)
* 호스트 기반 복제를 사용하여 클라우드로 마이그레이션됨(짧은 중단 마이그레이션)
* 클라우드에 작성됨(확장된 네트워크에서)

#### 보안
{: #vc_trial_hcx_arch-sec}

클라우드 게이트웨이는 스위트 B 호환 AES-GCM(IKEv2 사용), AES-NI 오프로드 및 플로우 기반 허가 제어를 제공합니다. HCX는 소스 및 대상 암호화와 복호화 프로세스를 소유하며, 일관성 있는 보안과 VM 마이그레이션 및 네트워크 확장과 같은 하이브리드 워크플로우에 대한 참여를 보장합니다. 정의되고 VM 온프레미스에 지정된 보안 정책을 VM을 사용하여 {{site.data.keyword.cloud_notm}}로 마이그레이션할 수 있습니다.

정책 마이그레이션 다음 조건이 필요합니다.

* 온프레미스 데이터 센터에는 NSX V6.2.2 이상이 실행되고 있습니다.
* vSphere에서 보안 정책은 많은 규칙을 포함할 수 있는 단일 NSX 섹션입니다.
* 정책에 참여하기 위해 IP 주소 또는 MAC 주소 세트의 이름을 지정할 수 있습니다.
* MAC 세트 또는 IP 세트 이름은 218자를 초과할 수 없습니다.
* 지원되는 규칙은 소스 또는 대상으로 계층 3 IP 주소 또는 IP 세트를 지정하거나 계층 2 MAC 주소 또는 MAC 세트를 지정합니다.

### HCX 컴포넌트
{: #vc_trial_hcx_arch-hcx-comp}

HCX on {{site.data.keyword.cloud_notm}} 서비스는 온프레미스 데이터 센터와 IBM Cloud 대상 모두에 설치되고 구성된 네 가지 가상 어플라이언스를 배치합니다. 다음 정보에서는 네 가지 필수 가상 어플라이언스에 대해 각각 설명합니다. 선택적으로 구현 디자인에 따라 에지 디바이스가 필요할 수 있습니다.

#### HCX Manager
{: #vc_trial_hcx_arch-hcx-manager}

HCX Manager 가상 어플라이언스는 온프레미스 vCenter에 대한 확장입니다. 어플라이언스는 VM으로 배치되고 파일 구조에는 다른 하이브리드 서비스 가상 어플라이언스가 포함됩니다. HCX Manager는 온프레미스 및 {{site.data.keyword.cloud_notm}} 내에서 클라우드 게이트웨이, Layer 2 Concentrator 및 WAN 최적화 가상 어플라이언스의 배치 및 구성을 관리합니다.

#### 하이브리드 클라우드 게이트웨이
{: #vc_trial_hcx_arch-hcg}

하이브리드 클라우드 게이트웨이(CGW)는 온프레미스 vSphere 자산과 {{site.data.keyword.cloud_notm}} 간에 보안 채널을 유지보수합니다. HCX는 {{site.data.keyword.cloud_notm}}에 대한 사이트 대 사이트 연결을 부트스트랩하도록 강력한 암호화를 사용합니다. vSphere와 {{site.data.keyword.cloud_notm}} 간의 보안 채널은 "중간 구간" 보안 문제점을 방지합니다. 클라우드 게이트웨이는 양방향 마이그레이션을 수행하도록 vSphere 복제 기술을 통합합니다.

#### WAN 최적화
{: #vc_trial_hcx_arch-wan-opt}

WAN 최적화 어플라이언스는 대기 시간의 영향을 줄이기 위해 WAN 조건 지정을 수행하는 컴포넌트입니다. 패킷 유실 시나리오 및 중복되는 트래픽 패턴의 중복 제거를 무효화하도록 순방향 오류 정정도 통합합니다. 이를 통해 대역폭 사용이 줄어들고 {{site.data.keyword.cloud_notm}}로(에서) 데이터 전송을 가속화할 수 있는 사용 가능한 네트워크 기능을 최대한 활용할 수 있습니다.

VM 마이그레이션은 vSphere 온프레미스와 {{site.data.keyword.cloud_notm}} 간의 뛰어난 이동성을 구현하도록 클라우드 게이트웨이 및 WAN 최적화 어플라이언스의 결합에 의존합니다. 또한 계층 2 확장은 데이터 경로가 클라우드 게이트웨이를 통해 라우트될 때 WAN 최적화로부터 이점을 얻습니다.
{:important}

#### Layer 2 Concentrator
{: #vc_trial_hcx_arch-layer-2-conc}

Layer 2 Concentrator(L2C) 어플라이언스는 온프레미스 vSphere 데이터 센터에서 {{site.data.keyword.cloud_notm}}까지 계층 2 네트워크의 확장을 허용합니다.

Layer 2 Concentrator에는 다음 인터페이스가 있습니다.

* **내부 트렁크 인터페이스** 이 인터페이스는 {{site.data.keyword.cloud_notm}}에서 확장된 해당 네트워크에 맵핑하는 트랜잭션 브릿지를 사용하여 확장된 네트워크를 위한 VM 트래픽 온프레미스를 처리합니다.
* **업링크 인터페이스**: HCX는 {{site.data.keyword.cloud_notm}}로(에서) 캡슐화된 오버레이 트래픽을 전송하도록 이 인터페이스를 사용합니다. 애플리케이션 데이터는 업링크 인터페이스를 통해 이동됩니다.

### 배치 아키텍처
{: #vc_trial_hcx_arch-deployment}

HCX on {{site.data.keyword.cloud_notm}} 배치에 대한 자세한 정보는 [VMware HCX on {{site.data.keyword.cloud_notm}}
배치 및 오퍼레이션](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf)을 참조하십시오.
