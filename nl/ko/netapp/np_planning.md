---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# NetApp ONTAP Select 인스턴스에 대한 요구사항 및 계획

NetApp ONTAP Select 인스턴스를 주문하기 전에 다음 요구사항을 검토하십시오. {{site.data.keyword.CloudDataCent}} 위치와 워크로드 성능 및 용량 요구사항에 따라 인스턴스를 계획하십시오.

## IBM Cloud 계정 요구사항

사용 중인 {{site.data.keyword.cloud_notm}} 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 계정에 대한 요구사항](/docs/services/vmwaresolutions/vmonic/slaccountrequirement.html)을 참조하십시오.

## IBM Cloud Data Center 가용성

NetApp ONTAP Select 배치에는 실제 인프라에 대한 엄격한 요구사항이 있습니다. 그러므로, 요구사항을 충족하는 {{site.data.keyword.CloudDataCents_notm}}에만 인스턴스를 배치할 수 있습니다. 다음 {{site.data.keyword.CloudDataCents_notm}}는 NetApp ONTAP Select 배치에 사용 가능합니다.

표 1. NetApp ONTAP Select 인스턴스에 사용 가능한 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |위치 |지역 |서버 옵션 |
|:------|:----------------|:----------------|:---------------------------|
|AMS03 |암스테르담 |유럽 |고성능(중형), 고성능(대형), 고용량
|CHE01 |첸나이 |아시아 태평양 |고용량
|DAL09 |댈러스 |북미 남부 |고성능(중형), 고성능(대형), 고용량
|DAL10 |댈러스 |북미 남부 |고성능(중형), 고성능(대형), 고용량
|DAL12 |댈러스 |북미 남부 |고성능(중형), 고성능(대형), 고용량
|DAL13 |댈러스 |북미 남부 |고성능(중형), 고성능(대형), 고용량
|FRA02 |프랑크푸르트 |유럽 |고성능(중형), 고성능(대형), 고용량
| FRA04 |프랑크푸르트 |유럽 |고성능(중형), 고성능(대형), 고용량
|HKG02 |홍콩 |아시아 태평양 |고성능(중형), 고성능(대형), 고용량
|LON02 |런던 |유럽 |고성능(중형), 고성능(대형), 고용량
|LON04 |런던 |유럽 |고성능(중형), 고성능(대형), 고용량
|LON06 |런던 |유럽 |고성능(중형), 고성능(대형), 고용량
|MEL01 |멜버른 |아시아 태평양 |고성능(중형), 고용량
|MEX01 |케레타로 |북미 남부 |고성능(중형), 고성능(대형), 고용량
|MIL01 |밀라노 |유럽 |고성능(중형), 고용량
|MON01 |몬트리올 |북미 동부 |고성능(중형), 고성능(대형), 고용량
|OSL01 |오슬로 |유럽 |고성능(중형), 고성능(대형), 고용량
|PAR01 |파리 |유럽 |고성능(중형), 고성능(대형), 고용량
|SAO01 |상파울루 |남미 |고성능(대형), 고용량
|SEO01 |서울 |아시아 태평양 |고성능(대형), 고용량
|SJC03 |산호세 |북미 서부 |고성능(중형), 고성능(대형), 고용량
|SJC04 |산호세 |북미 서부 |고성능(중형), 고성능(대형), 고용량
|SNG01 |싱가포르 |아시아 태평양 |고성능(중형), 고성능(대형), 고용량
|SYD01 |시드니 |아시아 태평양 |고성능(중형), 고성능(대형), 고용량
|SYD04 |시드니 |아시아 태평양 |고성능(중형), 고성능(대형), 고용량
|TOK02 |도쿄 |아시아 태평양 |고성능(대형), 고용량
|TOR01 |토론토 |북미 동부 |고성능(중형), 고성능(대형), 고용량
|WDC04 |워싱턴, DC |북미 동부 |고성능(중형), 고성능(대형), 고용량
|WDC06 |워싱턴, DC |북미 동부 |고성능(중형), 고성능(대형), 고용량
|WDC07 |워싱턴, DC |북미 동부 |고성능(중형), 고성능(대형), 고용량

### 관련 링크

* [NetApp ONTAP Select 개요](/docs/services/vmwaresolutions/netapp/np_netappoverview.html)
* [NetApp ONTAP Select 인스턴스 주문](/docs/services/vmwaresolutions/netapp/np_orderinginstances.html)
