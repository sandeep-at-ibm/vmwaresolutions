---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: IAM user, user role, user permission

subcollection: vmware-solutions


---

# IAM에서 사용자 액세스 관리
{: #iam}

계정의 사용자와 관련한 {{site.data.keyword.vmwaresolutions_full}} 서비스 인스턴스에 대한 액세스는 {{site.data.keyword.cloud_notm}} IAM(Identity and Access Management)에 의해 제어됩니다. 계정에서 {{site.data.keyword.vmwaresolutions_short}} 서비스에 액세스하는 모든 사용자에게는 IAM 사용자 역할이 정의된 액세스 정책이 지정되어야 합니다.

액세스 정책은 선택된 서비스 또는 인스턴스의 컨텍스트 내에서 사용자가 수행할 수 있는 조치를 결정합니다. 허용되는 조치는 서비스에서 수행 가능한 오퍼레이션으로서 {{site.data.keyword.cloud_notm}} 서비스에 의해 사용자 정의되고 정의됩니다. 그리고 이 조치는 IAM 사용자 역할에 맵핑됩니다.

정책은 액세스 권한이 서로 다른 레벨에서 부여될 수 있도록 합니다. 일부 옵션에는 다음 액세스 권한이 포함됩니다.

* 계정의 모든 서비스 인스턴스 간의 액세스
* 계정의 개별 서비스 인스턴스에 대한 액세스
* 인스턴스 내의 특정 리소스에 대한 액세스
* 계정의 모든 IAM 사용 서비스에 대한 액세스

액세스 정책의 범위를 정의한 후에는 역할을 지정합니다.

{{site.data.keyword.vmwaresolutions_short}} 서비스 내에서 각 역할이 허용하는 조치가 개략적으로 설명된 다음 정보를 검토하십시오.

## 플랫폼 관리 역할 및 권한
{: #iam-roles}

플랫폼 관리 역할을 사용하여 사용자는 플랫폼 레벨에서 서비스 리소스에 대한 태스크를 수행할 수 있습니다. 예: 서비스에 대한 사용자 액세스 지정, 서비스 ID 작성 또는 삭제, 인스턴스 작성, 그리고 애플리케이션에 인스턴스 바인드.

다음 표에서는 플랫폼 관리 역할에 맵핑된 조치에 대한 정보를 제공합니다.

|플랫폼 관리 역할 |조치 | 예제 조치 |
|:----------------- |:----------------- |:----------------- |
| 뷰어 | 읽기 전용 조치 |인스턴스 요약 보기<br>인스턴스 세부사항 보기 |
| 편집자 | 특정 인스턴스 업데이트 |ESXi 서버 추가 또는 제거<br>클러스터 추가 또는 제거<br>서비스 추가 또는 제거<br>상위 버전으로 인스턴스 업그레이드 |
| 운영자 | 읽기 전용 조치 |인스턴스 나열<br>인스턴스 세부사항 보기 |
| 관리자 | 전체 관리 액세스 |새 인스턴스 작성<br>인스턴스 삭제<br>기타 사용자에 대한 플랫폼 액세스 권한 부여|
{: caption="표 1. 플랫폼 관리 역할 및 허용된 조치" caption-side="top"}

{{site.data.keyword.vmwaresolutions_short}}의 경우에는 다음 조치가 존재합니다.

| 조치 |서비스에 대한 오퍼레이션 |역할 |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create |새 인스턴스 작성 | 관리자 |
| vmware-solutions.instances.delete |인스턴스 삭제 | 관리자 |
| vmware-solutions.instances.view |인스턴스 나열<br>인스턴스 세부사항 보기 |뷰어, 운영자, 편집자 및 관리자 |
| vmware-solutions.instances.update |ESXi 서버 추가 또는 제거<br>클러스터 추가 또는 제거<br>서비스 추가 또는 제거<br>상위 버전으로 인스턴스 업그레이드 |편집자 및 관리자 |
| vmware-solutions.account.update |계정 설정 업데이트 | 관리자 |
{: caption="표 2. 조치 설명 및 필수 역할" caption-side="top"}

## 사용자에 대한 액세스 관리
{: #iam-users}

해당 사용자가 계정에 대해 프로비저닝된 서비스와 리소스를 공유할 수 있도록 {{site.data.keyword.cloud_notm}} 계정에 새 사용자를 추가할 수 있습니다. 자세한 정보는 [서비스 및 리소스에 액세스하기 위한 사용자 초대](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)를 참조하십시오.

기존 액세스 수정, 새 액세스 지정 및 지정된 액세스 검토를 포함하여 기존 사용자에 대한 액세스를 관리할 수도 있습니다. 사용자에 대한 액세스를 관리하려면 계정 소유자이거나 **관리자** 플랫폼 관리 역할을 보유해야 합니다. 자세한 정보는 [리소스에 대한 액세스 관리](/docs/iam?topic=iam-iammanidaccser)를 참조하십시오.

## IBM Cloud 계정으로 기존 인스턴스 마이그레이션
{: #iam-migrate}

IAM과 {{site.data.keyword.vmwaresolutions_short}}의 통합으로 인해, {{site.data.keyword.cloud_notm}} 계정에서 V2.5 이상 릴리스에 배치된 인스턴스는 자동으로 계정에 추가되며 IAM에 의해 관리됩니다.

V2.4 이하 릴리스에서 배치된 기존 인스턴스의 경우에는 IAM-사용 관리를 위해 지정된 {{site.data.keyword.cloud_notm}} 계정으로 이를 마이그레이션할 수 있습니다. 자세한 정보는 다음 주제를 참조하십시오.
* [IBM Cloud 계정으로 V2.5 이전 vCenter Server 인스턴스 마이그레이션](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [IBM Cloud 계정으로 V2.5 이전 vCenter Server with Hybridity Bundle 인스턴스 마이그레이션](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [IBM Cloud 계정으로 V2.5 이전 NetApp ONTAP Select 인스턴스 마이그레이션](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

## 관련 링크
{: #iam-related}

* [ID 및 액세스 관리](/docs/iam?topic=iam-getstarted)
* [사용자 초대](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [IAM 개념](/docs/iam?topic=iam-iamoverview)
