---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# vCenter Server 인스턴스 요구사항 및 계획

VMware vCenter Server 인스턴스를 주문하기 전에 다음 요구사항을 검토하십시오. {{site.data.keyword.CloudDataCent}} 위치, 워크로드 용량 요구사항 및 추가 기능 서비스 요구사항에 따라 인스턴스를 계획하십시오.

## IBM Cloud 계정 요구사항

사용 중인 {{site.data.keyword.cloud_notm}} 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 계정에 대한 요구사항](../vmonic/slaccountrequirement.html)을 참조하십시오.

## IBM Cloud Data Center 가용성

vCenter Server 배치에는 실제 인프라에 대한 엄격한 요구사항이 있습니다. 그러므로, 요구사항을 충족하는 {{site.data.keyword.CloudDataCents_notm}}에만 인스턴스를 배치할 수 있습니다. 다음 {{site.data.keyword.CloudDataCents_notm}}는 vCenter Server 배치에 사용 가능합니다.

표 1. vCenter Server 인스턴스에 사용 가능한 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |위치 |지역 |서버 옵션 |
|:----------------------|:---------|:-------|:---------------|
|AMS03 |암스테르담 |유럽 |사용자 정의됨 |
|CHE01 |첸나이 |아시아 태평양 |사용자 정의됨 |
|DAL09 |댈러스 |북미 남부 |사용자 정의됨 |
|DAL10 |댈러스 |북미 남부 |사용자 정의됨, 소형, 중형, 대형 |
|DAL12 |댈러스 |북미 남부 |사용자 정의됨 |
|DAL13 |댈러스 |북미 남부 |사용자 정의됨 |
|FRA02 |프랑크푸르트 |유럽 |사용자 정의됨, 소형, 중형, 대형 |
| FRA04 |프랑크푸르트 |유럽 |사용자 정의됨 |
|HKG02 |홍콩 |아시아 태평양 |사용자 정의됨 |
|LON02 |런던 |유럽 |사용자 정의됨 |
|LON04 |런던 |유럽 |사용자 정의됨 |
|LON06 |런던 |유럽 |사용자 정의됨, 소형, 중형, 대형 |
|MEL01 |멜버른 |아시아 태평양 |사용자 정의됨 |
|MEX01 |케레타로 |북미 남부 |사용자 정의됨 |
|MIL01 |밀라노 |유럽 |사용자 정의됨 |
|MON01 |몬트리올 |북미 동부 |사용자 정의됨 |
|OSL01 |오슬로 |유럽 |사용자 정의됨 |
|PAR01 |파리 |유럽 |사용자 정의됨 |
|SAO01 |상파울루 |남미 |사용자 정의됨 |
|SEO01 |서울 |아시아 태평양 |사용자 정의됨 |
|SJC03 |산호세 |북미 서부 |사용자 정의됨, 소형, 중형, 대형 |
|SJC04 |산호세 |북미 서부 |사용자 정의됨 |
|SNG01 |싱가포르 |아시아 태평양 |사용자 정의됨 |
|SYD01 |시드니 |아시아 태평양 |사용자 정의됨 |
|SYD04 |시드니 |아시아 태평양 |사용자 정의됨 |
|TOK02 |도쿄 |아시아 태평양 |사용자 정의됨 |
|TOR01 |토론토 |북미 동부 |사용자 정의됨, 소형, 중형, 대형 |
|WDC04 |워싱턴, DC |북미 동부 |사용자 정의됨, 소형, 중형, 대형 |
|WDC06 |워싱턴, DC |북미 동부 |사용자 정의됨 |
|WDC07 |워싱턴, DC |북미 동부 |사용자 정의됨 |

{{site.data.keyword.CloudDataCents_notm}}의 소형 서브세트는 사전 구성된 **소형**, **중형** 및 **대형** Bare Metal Server 옵션을 제공합니다. 가용성 및 자원 명세 제공에 따라 {{site.data.keyword.CloudDataCents_notm}}는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 상태 표시기를 표시하여 배치를 계획할 수 있습니다.

표 2. vCenter Server 인스턴스 주문 시 {{site.data.keyword.CloudDataCents_notm}}에 대한 상태 표시기

|상태 |상태 세부사항 |
|:------------------------------|:--------------------------------------------------|
|서비스 예정                   |{{site.data.keyword.CloudDataCent_notm}}는 현재 사용할 수 없습니다. |
|임시적으로 사용 불가능  |{{site.data.keyword.CloudDataCent_notm}}는 현재 사용 가능하지 않습니다. |
|제한된 자원 명세             |{{site.data.keyword.CloudDataCent_notm}}에는 제한된 가용성이 있으며 주문이 완료되지 않을 수 있습니다. |

## 관리 컴포넌트의 백업

사용자는 모든 인스턴스 컴포넌트의 가용성을 유지보수하고 보장할 책임이 있습니다. 모든 관리 컴포넌트의 백업 또는 고가용성에 대해 계획하도록 적극 권장합니다. 자세한 정보는 [컴포넌트 백업](../archiref/solution/solution_backingup.html)을 참조하십시오.

## vCenter Server 인스턴스에 대한 서비스

사용자의 요구(재해 복구)에 따라 인스턴스에 추가 기능 서비스를 주문할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](vc_addingremovingservices.html)를 참조하십시오.

## 용량 고려사항

용량 고려사항에 대한 자세한 정보는 [용량 스케일링](../archiref/solution/solution_scaling.html)을 참조하십시오.

### 관련 링크

* [vCenter Server 개요](vc_vcenterserveroverview.html)
* [vCenter Server 인스턴스 주문](vc_orderinginstance.html)
* [vCenter Server 인스턴스에 대한 용량 확장 및 축소](vc_addingremovingservers.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](vc_addingremovingservices.html)
