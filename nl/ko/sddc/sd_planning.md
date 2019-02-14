---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-13"

---

# Cloud Foundation 인스턴스에 대한 요구사항 및 계획

VMware Cloud Foundation 인스턴스를 주문하기 전에 다음 요구사항을 검토하십시오. {{site.data.keyword.CloudDataCent}} 위치, 워크로드 용량 요구사항 및 서비스 요구사항에 따라 인스턴스를 계획하십시오.

## IBM Cloud 계정 요구사항

사용 중인 {{site.data.keyword.cloud_notm}} 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 계정에 대한 요구사항](../vmonic/slaccountrequirement.html)을 참조하십시오.

## IBM Cloud Data Center 가용성

Cloud Foundation 배치에는 실제 인프라에 대한 엄격한 요구사항이 있습니다. 그러므로, 요구사항을 충족하는 {{site.data.keyword.CloudDataCents_notm}}에만 인스턴스를 배치할 수 있습니다. 다음 {{site.data.keyword.CloudDataCents_notm}}는 Cloud Foundation 배치에 사용 가능합니다.

표 1. Cloud Foundation 인스턴스에 사용 가능한 {{site.data.keyword.CloudDataCents_notm}} 및 {{site.data.keyword.cloud_notm}} Bare Metal Server 구성

| {{site.data.keyword.CloudDataCent_notm}} |위치 |지역 |서버 구성 |
|:----------------------|:---------|:-------|:----------------------|
|AMS03 |암스테르담 |유럽 | Skylake, Broadwell |
|CHE01 |첸나이 |아시아 태평양 | Skylake, Broadwell |
|DAL09 |댈러스 |북미 남부 | Skylake, Broadwell |
|DAL10 |댈러스 |북미 남부 | Skylake, Broadwell |
|DAL12 |댈러스 |북미 남부 | Skylake, Broadwell |
|DAL13 |댈러스 |북미 남부 | Skylake, Broadwell |
|FRA02 |프랑크푸르트 |유럽 | Skylake, Broadwell |
|FRA04 |프랑크푸르트 |유럽 | Skylake, Broadwell |
|HKG02 |홍콩 |아시아 태평양 | Skylake, Broadwell |
|LON02 |런던 |유럽 | Skylake, Broadwell |
|LON04 |런던 |유럽 | Skylake, Broadwell |
|LON06 |런던 |유럽 | Skylake, Broadwell |
|MEL01 |멜버른 |아시아 태평양 | Skylake, Broadwell |
|MEX01 |케레타로 |북미 남부 | Skylake, Broadwell |
|MIL01 |밀라노 |유럽 | Skylake, Broadwell |
|MON01 |몬트리올 |북미 동부 | Skylake, Broadwell |
|OSL01 |오슬로 |유럽 | Skylake, Broadwell |
|PAR01 |파리 |유럽 | Skylake, Broadwell |
|SAO01 |상파울루 |남미 | Skylake, Broadwell |
|SEO01 |서울 |아시아 태평양 | Skylake, Broadwell |
|SJC03 |산호세 |북미 서부 | Skylake, Broadwell |
|SJC04 |산호세 |북미 서부 | Skylake, Broadwell |
|SNG01 |싱가포르 |아시아 태평양 | Skylake, Broadwell |
|SYD01 |시드니 |아시아 태평양 | Skylake, Broadwell |
|SYD04 |시드니 |아시아 태평양 | Skylake, Broadwell |
|TOK02 |도쿄 |아시아 태평양 | Skylake, Broadwell |
|TOR01 |토론토 |북미 동부 | Skylake, Broadwell |
|WDC04 |워싱턴, DC |북미 동부 | Skylake, Broadwell |
|WDC06 |워싱턴, DC |북미 동부 | Skylake, Broadwell |
|WDC07 |워싱턴, DC |북미 동부 | Skylake, Broadwell |

가용성 및 자원 명세 제공에 따라 {{site.data.keyword.CloudDataCents_notm}}는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 상태 표시기를 표시하여 배치를 계획할 수 있습니다.

표 2. Cloud Foundation 인스턴스 주문 시 {{site.data.keyword.CloudDataCents_notm}}에 대한 상태 표시기

|상태 |상태 세부사항 |
|:------------------------------|:--------------------------------------------------|
|서비스 예정                   |{{site.data.keyword.CloudDataCent_notm}}는 현재 사용할 수 없습니다. |
|임시적으로 사용 불가능  |{{site.data.keyword.CloudDataCent_notm}}는 현재 사용 가능하지 않습니다. |
|제한된 자원 명세             |{{site.data.keyword.CloudDataCent_notm}}에는 제한된 가용성이 있으며 주문이 완료되지 않을 수 있습니다. |

## 관리 컴포넌트의 백업

사용자는 모든 인스턴스 컴포넌트의 가용성을 유지보수하고 보장할 책임이 있습니다. 모든 관리 컴포넌트의 백업 또는 고가용성에 대해 계획을 세우는 것이 좋습니다. 자세한 정보는 [컴포넌트 백업](../archiref/solution/solution_backingup.html)을 참조하십시오.

## Cloud Foundation 인스턴스에 대한 서비스

사용자의 요구(재해 복구)에 따라 인스턴스에 추가 기능 서비스를 주문할 수 있습니다. 자세한 정보는 [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](sd_addingremovingservices.html)를 참조하십시오.

## 용량 고려사항

용량에 대한 자세한 정보는 [용량 스케일링](../archiref/solution/solution_scaling.html)을 참조하십시오.

### 관련 링크

* [Cloud Foundation 개요](sd_cloudfoundationoverview.html)
* [Cloud Foundation 인스턴스 주문](sd_orderinginstance.html)
* [Cloud Foundation 인스턴스에 대한 용량 확장 및 축소](sd_addingremovingservers.html)
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](sd_addingremovingservices.html)
