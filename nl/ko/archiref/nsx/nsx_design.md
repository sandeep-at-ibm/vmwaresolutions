---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# NSX Edge Services Gateway 디자인

NSX Edge Services Gateway on {{site.data.keyword.cloud}} 솔루션은 전세계 {{site.data.keyword.CloudDataCents_notm}} 내에 배치된 VMware 기술을 제공합니다. {{site.data.keyword.vmwaresolutions_short}}는 NSX Edge Services Gateway와 관련된 두 가지 솔루션 아키텍처를 제공합니다.

## 내부 아키텍처 디자인

내부 아키텍처는 VMware Cloud Foundation 통합 클러스터 또는 VMware vCenter Server 클러스터의 리소스 풀에서 필요한 NSX Edge 컴포넌트의 배치를 지정합니다.

다음 그림에서 VMware vSAN은 선택사항입니다.
{:note}

그림 1. {{site.data.keyword.cloud_notm}}의 클라우드 네트워킹 서비스

![클라우드 네트워킹 서비스 아키텍처](architecture.svg "클라우드 네트워킹 서비스 아키텍처")

## 전용 아키텍처 디자인

전용 아키텍처는 NSX Edge 전용으로 사용되는 별도의 2-노드 vSphere 클러스터에 필요한 NSX Edge 컴포넌트를 배치하고 실제 네트워크 인프라와의 중요한 상호작용을 제공합니다. 전용 아키텍처에는 다음과 같은 특성과 기능이 있습니다.

* 실제 네트워크에 대한 온램프(on-ramp) 및 오프램프(off-ramp) 연결을 제공합니다 (예: NSX Edge 가상 어플라이언스의 North-South L3 라우팅).
* NSX L2 브릿징을 통해 실제 네트워크의 VLAN에 연결된 실제 디바이스와의 통신을 허용하고 DLR(Distributed Logical Router) 라우팅을 위해 제어 가상 머신(VM)을 호스팅합니다.
* 중앙 집중식 논리 또는 실제 서비스가 있을 수 있습니다 (예: 방화벽, 로드 밸런서, 가상 사설망(VPN) 모니터링 컴포넌트 및 Log Insight VM).
* 전용 vCenter를 사용하여 컴퓨팅 및 에지 리소스를 관리하는 경우 에지 클러스터에서 NSX Controller를 호스팅할 수 있습니다.
* 에지 클러스터 리소스에는 활성 대기 구성을 보호하거나 장애 발생 시 대역폭 가용성을 유지보수하기 위한 비유사성 요구사항이 있습니다.

## IBM Cloud 사설 IP 주소 범위 및 BYOIP(Bring Your Own IP) 주소 범위

RFC1918 사설 IP 주소 범위는 인터넷이 아니라 조직 내부에서 사용하도록 네트워크 범위의 사용을 특별히 예약합니다. {{site.data.keyword.cloud_notm}} 실제 네트워크 인프라는 전세계 위치에서 특정 RFC1918 사설 주소 공간, 10.x.x.x/8을 사용합니다. 이러한 IP 주소 범위는 고객 계정 간에 또는 {{site.data.keyword.cloud_notm}} 고객 계정 내에서 겹치지 않습니다. 고객 계정 내에서 {{site.data.keyword.cloud_notm}}의 할당된 사설 IP 공간은 VLAN Spanning이 사용으로 설정된 경우 {{site.data.keyword.CloudDataCents_notm}}의 다른 {{site.data.keyword.cloud_notm}} 사설 IP 주소 공간으로 라우팅할 수 있습니다.

이렇게 하면 계정 내에서 전세계에 연결된 인프라를 쉽게 설정할 수 있지만 {{site.data.keyword.cloud_notm}}와 동일한 사설 주소 공간을 사용 중인 경우 라우팅을 통해 데이터 센터를 {{site.data.keyword.cloud_notm}}로 확장하려고 할 때 고정 IP 주소 공간에 문제가 발생할 수 있습니다. 솔루션은 NSX를 사용하여 Cloud Foundation 또는 vCenter Server 인프라에 오버레이 토폴로지를 작성하여 {{site.data.keyword.cloud_notm}}에 할당된 사설 IP 주소 공간과 상호작용하지 않도록 BYOIP(Bring Your Own IP) 주소 공간을 격리하는 것입니다. NSX는 터널 내의 내부 BYOIP 주소 공간이 중첩될 수 있는 외부 IP 주소 공간에 걸쳐 있도록 하는 L2 VPN을 제공할 수 있습니다.

### 관련 링크

* [솔루션 개요](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)
