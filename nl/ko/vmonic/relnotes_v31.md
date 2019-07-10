---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: release notes, what's new, version 3.1

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V3.1 릴리스 정보
{: #relnotes_v31}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함되어 있습니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## 데이터 보호 및 재해 복구를 위한 단일 노드 평가판 인스턴스
{: #relnotes_v31-dr-bundle}

데이터 보호 및 재해 복구를 위한 단일 노드 평가판은 {{site.data.keyword.cloud_notm}}를 시범 작동하여 VMware 워크로드를 {{site.data.keyword.cloud_notm}}에 마이그레이션하고 복구할 수 있는 가장 빠른 방법입니다. 이 팽가판은 온프레미스 환경과 동일한 익숙한 도구를 사용하여 관리될 수 있는 싱글 테넌트 VMware 플랫폼인 VMware vCenter Server on IBM Cloud 버전입니다. 이 평가판에는 Veeam on {{site.data.keyword.cloud_notm}}, VMware HCX on {{site.data.keyword.cloud_notm}} 및 Zerto on {{site.data.keyword.cloud_notm}} 서비스가 포함되어 있습니다. 

자세한 정보는 [재해 복구를 위한 단일 노드 평가판 개요](/docs/services/vmwaresolutions?topic=vmware-solutions-dr_backup_bundle_overview)를 참조하십시오.

## IBM Cloud Expert Services
{: #relnotes_v31-expert-services}

이제 IBM Expert Services에 참여하여 계획부터 현대화까지 또는 이 사이의 모든 단계에서 자체 {{site.data.keyword.cloud_notm}} 솔루션을 배치하고, 마이그레이션하고, 유지보수하도록 내부 팀과 함께 작업할 수 있습니다. 

**시작하기** 페이지에서 언제든지 상담을 요청하여 {{site.data.keyword.cloud_notm}} Expert Services를 인스턴스 주문에 추가할 수 있습니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} Expert Services 요청](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_ices)을 참조하십시오.

## IBM Cloud Cost Estimator와의 통합

이제 {{site.data.keyword.cloud_notm}} 프레임워크에서 제공하는 통합 예상 도구를 통해 {{site.data.keyword.vmwaresolutions_short}} 리소스의 비용을 예상할 수 있습니다. 이 기능을 사용하면 {{site.data.keyword.cloud_notm}} Catalog에서 리소스의 스냅샷을 저장하고 나중에 참조하기 위해 다운로드할 수 있는 단일 PDF 파일 아래에 보관할 수 있습니다. 비용 추정량은 계약이나 정확한 견적이 아닌 총 비용의 추정치일 뿐입니다. 

비용 추정량에 대한 자세한 정보는 [비용 예상](/docs/billing-usage?topic=billing-usage-cost)을 참조하십시오.

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v31-vcs}

이 릴리스는 새로 배치된 인스턴스, 클러스터 및 호스트에 대한 다음 업그레이드 및 개선사항을 적용합니다.

* vSphere ESXi 6.5 Update 2(빌드 6.5.0-13635690)
* vCenter Server Appliance 6.5 Update 2g(빌드 6.5.0-13638625)

자세한 정보는 [vCenter Server 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)를 참조하십시오.

### 클러스터를 위한 대체 ESXi 서버 구성
{: #relnotes_v31-esxi-config}

이제 클러스터에서 기존 호스트가 아닌 기존 구성 또는 대체 구성을 선택하여 새 ESXi 서버를 기존 클러스터에 추가할 수 있습니다. **서버 추가** 창에서 새 서버를 주문하는 경우 클러스터에서 기존 구성을 즉시 선택하거나 새 {{site.data.keyword.baremetal_short_sing}} 구성을 선택할 수 있습니다. 이는 모든 vCenter Server, vCenter Server with Hybridity 및 vCenter Server with NSX-T 인스턴스에 적용됩니다.

성능 또는 안전성 문제를 방지하기 위해 클러스터가 CPU, RAM 및 스토리지와 관련하여 동일하거나 유사한 구성을 사용하는 것이 좋습니다. 이 기능은 동일한 클러스터 내의 하드웨어 업데이트에 유용합니다. 

자세한 정보는 [vCenter Server 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers)를 참조하십시오.

### 정책 구성에 대한 업데이트
{: #relnotes_v31-policy-config}

vCenter Server 기본 인스턴스에 대해 생성된 vCenter 비밀번호는 이제 15자이며 비밀번호 및 잠금 정책 구성은 다음과 같습니다. 

* 현재 vCenter 비밀번호 정책의 최소 길이는 15자입니다. 
* 현재 vCenter 짐금 정책에서는 최대 3회의 로그인 시도 실패가 허용합니다. 
* 현재 vCenter 잠금 정책에서는 실패 사이에 900초의 시간 가격이 허용됩니다. 

NSX Server 기본 인스턴스에 대해 생성된 NSX Manager 비밀번호는 이제 15자입니다. 이전에는 생성된 비밀번호가 8자였습니다. 

 자세한 정보는 [vCenter Server 인스턴스에 대한 규제 준수 정보](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-default-policy-config)를 참조하십시오.

## 추가 서비스에 대한 업데이트
{: #relnotes_v31-services}

### HyTrust 라이센스 자동 갱신
{: #relnotes_v31-services-ht}

{{site.data.keyword.vmwaresolutions_short}}는 이제 콜홈 기능이 사용으로 설정된 HyTrust 라이센스의 자동 갱신 기능을 제공합니다. 이 지원은 다음 버전부터 제공됩니다.

* HyTrust CloudControl 5.5.1 이상
* HyTrust DataControl 4.3.2 이상
* HyTrust KeyControl 4.3.2 이상

라이센스의 자동 갱신을 보장하도록 HyTrust 가상 머신(VM)에 대한 인터넷 액세스를 사용으로 설정하는 프로시저를 완료해야 합니다. 이 프로시저를 완료하지 않으면 라이센스가 매년 만료됩니다.
{:important}

자세한 정보는 다음을 참조하십시오.

* [HyTrust CloudControl VM에 대한 인터넷 액세스 사용](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc#managinghtcc-internet-access)
* [HyTrust DataControl VM에 대한 인터넷 액세스 사용](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc#managinghtdc-internet-access)
* [HyTrust KeyControl VM에 대한 인터넷 액세스 사용](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc#managinghtkc-internet-access)

### Veeam on IBM Cloud
{: #relnotes_v31-services-veeam}

현재 릴리스에서는 새로 배치된 모든 인스턴스에 Veeam Availability Suite 9.5가 설치되어 있습니다. 또한 Veeam VSI 및 Veeam 구성 저장소에 대한 많은 업데이트가 수행됩니다. 자세한 정보는 [Veeam on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)를 참조하십시오.

### Zerto on IBM Cloud
{: #relnotes_v31-services-zerto}

V3.1 이상에 배치된 새 인스턴스의 경우 Zerto on {{site.data.keyword.cloud_notm}}를 설치하려면 청구 가능 {{site.data.keyword.cloud_notm}} 계정이 필요합니다. 이제 VM 복제 비용에서는 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 대신 {{site.data.keyword.cloud_notm}} 비용 청구 플랜을 사용합니다. 

Zerto on {{site.data.keyword.cloud_notm}}를 주문하려면 {{site.data.keyword.cloud_notm}} 계정은 특정 요구사항을 충족해야 합니다. 기존에 Zerto on {{site.data.keyword.cloud_notm}}가 설치된 경우 Zerto VM 청구 유형을 청구 가능으로 변환할 수 있습니다. 자세한 정보는 [Zerto 복제 청구](/docs/services/vmwaresolutions?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing)를 참조하십시오.

## 새로 작성되고 업데이트된 문서
{: #relnotes_v31-updated-doc}

* 활동 트래커 인스턴스 관리 이벤트 및 KMIP for VMware on IBM Cloud 서비스에 대한 이벤트가 업데이트됩니다. 자세한 정보는 [활동 트래커 이벤트](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events)를 참조하십시오.
* 사용자 ID 참조 문서는 {{site.data.keyword.cloud_notm}} 서비스 자동화를 통해 서비스의 설치 및 구성에 사용된 사용자 ID로 업데이트됩니다. 자세한 정보는 [IBM 사용자 ID](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids)의 *서비스 사용자 ID* 섹션을 참조하십시오. 
* 참조 문서는 새 ``Retrieve the detailed network interface of a cluster`` API에서 사용 가능합니다. 자세한 정보는 [API 참조](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}를 참조하십시오.
* 이제 다음 기술 문서가 사용자 문서의 *참조서* 섹션에서 새로 작성됩니다. 
  * [오퍼레이션 관리](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)
  * [2일차 운영 프로시저](/docs/services/vmwaresolutions?topic=vmware-solutions-opsprocs-intro)

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v31-ui}

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.
* **클러스터** 세부사항 페이지에는 이제 클러스터에서 사용하는 스토리지 유형이 표시됩니다. 
* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.
