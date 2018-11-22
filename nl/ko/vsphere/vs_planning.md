---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-31"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware vSphere on IBM Cloud에 대한 요구사항 및 계획

VMware vSphere on {{site.data.keyword.cloud}}를 주문하기 전에 다음 요구사항을 검토하십시오. {{site.data.keyword.CloudDataCent_notm}} 위치와 워크로드 성능 및 용량 요구사항에 따라 VMware vSphere 클러스터를 계획하십시오.

환경을 설정하고, ESXi 서버가 배치된 후 여러 VMware 컴포넌트를 설치하고 구성할 책임이 있습니다. 다음 예는 VMware 컴포넌트입니다. VMware vCenter Server, VMware NSX, 및 VMware vSAN.
{:note}

## IBM Cloud 계정 요구사항

사용 중인 {{site.data.keyword.cloud_notm}} 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 계정에 대한 요구사항](../vmonic/slaccountrequirement.html)을 참조하십시오.

## IBM Cloud Data Center 가용성

vSphere 배치에는 실제 인프라에 대한 엄격한 요구사항이 있습니다. 그러므로, 요구사항을 충족하는 {{site.data.keyword.CloudDataCents_notm}}에만 클러스터를 배치할 수 있습니다. 다음 {{site.data.keyword.CloudDataCent_notm}}는 vSphere 배치에 사용 가능합니다.

vSAN 컴포넌트를 선택하면 위치 목록이 SSD(Solid-State Disk) 가용성을 기준으로 필터링됩니다.
{:note}

표 1. vSphere 클러스터에 사용 가능한 {{site.data.keyword.CloudDataCents_notm}}

| {{site.data.keyword.CloudDataCent_notm}} |위치 |지역 |
|:----------------------|:---------|:-------|
|AMS03 |암스테르담 |유럽 |
|CHE01 |첸나이 |아시아 태평양 |
|DAL09 |댈러스 |북미 남부 |
|DAL10 |댈러스 |북미 남부 |
|DAL12 |댈러스 |북미 남부 |
|DAL13 |댈러스 |북미 남부 |
|FRA02 |프랑크푸르트 |유럽 |
| FRA04 |프랑크푸르트 |유럽 |
|FRA05 |프랑크푸르트 |유럽 |
|HKG02 |홍콩 |아시아 태평양 |
|LON02 |런던 |유럽 |
|LON04 |런던 |유럽 |
|LON05 |런던 |유럽 |
|LON06 |런던 |유럽 |
|MEL01 |멜버른 |아시아 태평양 |
|MEX01 |케레타로 |북미 남부 |
|MIL01 |밀라노 |유럽 |
|MON01 |몬트리올 |북미 동부 |
|OSL01 |오슬로 |유럽 |
|PAR01 |파리 |유럽 |
|SAO01 |상파울루 |남미 |
|SEO01 |서울 |아시아 태평양 |
|SJC03 |산호세 |북미 서부 |
|SJC04 |산호세 |북미 서부 |
|SNG01 |싱가포르 |아시아 태평양 |
|SYD01 |시드니 |아시아 태평양 |
|SYD04 |시드니 |아시아 태평양 |
|TOK02 |도쿄 |아시아 태평양 |
|TOR01 |토론토 |북미 동부 |
|WDC04 |워싱턴, DC |북미 동부 |
|WDC06 |워싱턴, DC |북미 동부 |
|WDC07 |워싱턴, DC |북미 동부 |

### 관련 링크

* [새 vSphere 클러스터 주문](vs_orderinginstances.html)
* [기존 클러스터 스케일링](vs_scalingexistingclusters.html)
* [콘솔 외부에서 작성된 기존 클러스터 스케일링](vs_orderingforclustersoutside.html)
