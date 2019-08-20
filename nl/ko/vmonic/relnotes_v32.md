---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: release notes, what's new, version 3.2

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V3.2 릴리스 정보
{: #relnotes_v32}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함되어 있습니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}를 참조하십시오.

## VMware HCX for IBM Cloud 가용성
{: #relnotes_v32-HCX}

3.2 릴리스부터 VMware vCenter Server 인스턴스와 함께 VMware HCX on {{site.data.keyword.cloud_notm}} 서비스를 주문하는 옵션이 있습니다. 이전에는 VMware vCenter Server with Hybridity Bundle 인스턴스를 통해서만 HCX on {{site.data.keyword.cloud_notm}} 서비스를 주문할 수 있었습니다. vCenter Server with Hybridity Bundle 인스턴스는 더 이상 사용 가능하지 않습니다.

HCX on {{site.data.keyword.cloud_notm}} 서비스를 주문할 때 12개월 약정이 필요합니다. 12개월 약정이 만료된 후 HCX on {{site.data.keyword.cloud_notm}} 서비스를 설치하고 설치 제거할 수 있으며 제한사항 없이 호스트 및 클러스터를 추가하고 제거할 수 있습니다. 그런 다음 사용자 계정에 월별로 비용이 청구되며 언제든지 취소할 수 있습니다.

자세한 정보는 [VMware HCX on IBM Cloud 개요](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations)를 참조하십시오.

## VMware vSphere 6.7 Update 2 지원
{: #relnotes_v32-vsphere-v67}

이제 VMware vCenter Server, VMware vCenter Server with NSX-T 및 VMware vSphere on IBM Cloud 인스턴스와 함께 Mware vSphere 버전 6.7 Update 2를 주문하는 옵션이 있습니다. vSphere Enterprise Plus 6.7u2가 vSphere Enterprise Plus 6.7u1을 새 인스턴스와 함께 주문하는 옵션을 대체합니다. 또한 이제 마이그레이션 및 앱 현대화를 위한 단일 노드 평가판과 데이터 보호 및 재해 복구를 위한 단일 노드 평가판 인스턴스를 vSphere Enterprise Plus 6.7u2와 함께 주문합니다.

vSphere Enterprise Plus 6.7u2는 Skylake, Cascade Lake 및 Broadwell {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}에 사용할 수 있습니다.

vSphere Enterprise Plus 6.7u1을 사용하는 기존 인스턴스가 있는 경우 vSphere Enterprise Plus 6.7u1 또는 vSphere Enterprise Plus 6.7u2와 함께 새 호스트를 추가하는 옵션이 있습니다. 그러나 새 6.7u1 호스트를 추가하는 것은 안전하지 않습니다. 가능한 빨리 호스트를 최신 ESXi 서버 버전으로 업데이트하는 것이 좋습니다.
{:note}

## Cascade Lake 지원
{: #relnotes_v32-cascade}

V3.2 릴리스부터 다음의 새 {{site.data.keyword.baremetal_short_sing}} CPU 모델을 VMware vSphere 6.7 Update 2가 있는 인스턴스 및 클러스터의 배치에 사용할 수 있습니다. 이는 vCenter Server, vCenter Server with NSX-T 및 VMware vSphere에 적용됩니다.

* 듀얼 Intel Xeon Gold 4210 프로세서 / 총 20개의 코어, 2.3GHz 
* 듀얼 Intel Xeon Gold 5218 프로세서 / 총 32개의 코어, 2.3GHz 
* 듀얼 Intel Xeon Gold 6248 프로세서 / 총 40개의 코어, 2.5GHz 

Cascade Lake {{site.data.keyword.baremetal_short}}는 다중 구역 지역(MZR) {{site.data.keyword.CloudDataCents_notm}}에서 사용 가능합니다. 자세한 정보는 [다중 구역 지역(MZR) 개요](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview)를 참조하십시오.

{{site.data.keyword.baremetal_short_sing}} 설정에 대한 자세한 정보는 다음을 참조하십시오.

* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-cascade)
* [VMware vCenter Server with NSX-T 주문](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-cascade)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstance-cascade)

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v32-vcs}

이 릴리스는 새로 배치된 인스턴스, 클러스터 및 호스트에 대한 다음 업그레이드 및 개선사항을 적용합니다.

* VMware NSX for vSphere 6.4.5(빌드 13282012)
* vSphere ESXi 6.7 EP 10(빌드 6.7.0-13981272)
* vCenter Server Appliance 6.7 Update 2b(6.7.0.-13843469)
* Platform Services Controller 6.7 Update 2b(6.7.0.-13843469)

자세한 정보는 [vCenter Server 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)를 참조하십시오.

### 초기 클러스터 이름 지정
{: #relnotes_v32-vcs-initial-cluster}

이제 인스턴스를 주문하는 동시에 작성될 초기 클러스터의 이름을 지정할 수 있습니다. 자세한 정보는 다음을 참조하십시오.

* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [VMware vCenter Server with NSX-T 주문](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## VMware vSphere 인스턴스에 대한 업데이트
{: #relnotes_v32-vss}

사설 네트워크만 있는 새 vSphere 클러스터를 주문하는 경우 공용 VLAN이 더 이상 필요하지 않습니다.

자세한 정보는 [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-network-interface-settings)의 *네트워크 인터페이스 설정* 섹션을 참조하십시오.

## 추가 서비스에 대한 업데이트
{: #relnotes_v32-services}

이 릴리스는 새로 배치된 인스턴스에 다음 서비스 버전을 설치합니다.

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Update 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Update 4

### VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

이제 vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} 서비스를 V3.2 이상 릴리스에 배치되거나 업그레이드된 VMware vCenter Server 인스턴스에 사용할 수 있습니다. 

이 서비스는 vROps(vRealize Operations Manager)와 통합된 VMware vRLI(vRealize Log Insight)를 제공하여 가상화된 환경의 상태 및 성능을 모니터하고 사전 예방적으로 관리하며 로그를 통해 필터링하고 검색하여 문제의 근본 원인 분석을 수행하는 데 도움이 됩니다.

포함된 vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}와 함께 vCenter Server 인스턴스를 주문하거나 나중에 인스턴스 세부사항 페이지의 서비스 탭에서 이 서비스를 기존 인스턴스에 추가할 수 있습니다.

또한 엔터프라이즈 vRealize Operations and vRealize Log Insight 라이센스를 클라우드로 가져오거나(CPU 또는 OSI별) IBM Cloud에서 라이센스를 임대할 수 있습니다.

자세한 정보는 [VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vrops_overview)를 참조하십시오.

## 새로 작성되고 업데이트된 문서
{: #relnotes_v32-updated-doc}

* Activity Tracker 문서가 업데이트되었습니다. 자세한 정보는 [활동 트래커 이벤트](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events)를 참조하십시오.

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v32-ui}

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.

* 인스턴스 이름 요구사항이 변경되었습니다. 자세한 정보는 주문 중인 인스턴스 유형에 해당되는 주제를 참조하십시오.
* 완전한 ESXi 서버의 형식이 변경되었습니다. 자세한 정보는 주문 중인 인스턴스 유형에 해당되는 주제를 참조하십시오.
* 적절한 정렬을 허용하기 위해 선행 제로가 호스트 및 클러스터 이름에 추가되었습니다.
* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.
