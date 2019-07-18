---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: planning vCenter Server Hybridity, data center hybridity, vCenter Server Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# vCenter Server with Hybridity Bundle 인스턴스에 대한 요구사항 및 계획
{: #vc_hybrid_planning}

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 인스턴스를 주문하기 전에 다음 요구사항을 검토하십시오. {{site.data.keyword.CloudDataCent_notm}} 위치, 워크로드 용량 요구사항 및 추가 서비스 요구사항에 따라 인스턴스를 계획하십시오.

## IBM Cloud 계정 요구사항
{: #vc_hybrid_planning-account-req}

사용 중인 {{site.data.keyword.cloud_notm}} 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 계정에 대한 요구사항](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)을 참조하십시오.

## IBM Cloud Data Center 가용성
{: #vc_hybrid_planning-dc-availability}

vCenter Server with Hybridity Bundle 배치에는 실제 인프라에 대한 엄격한 요구사항이 있습니다. 그러므로, 요구사항을 충족하는 {{site.data.keyword.CloudDataCents_notm}}에만 인스턴스를 배치할 수 있습니다. 다음 {{site.data.keyword.CloudDataCents_notm}}는 vCenter Server with Hybridity Bundle 배치에 사용 가능합니다.

| {{site.data.keyword.CloudDataCent_notm}} |위치 |지역 |
|:----------------------|:---------|:---------------|
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
|TOK04 |도쿄 |아시아 태평양 |
|TOR01 |토론토 |북미 동부 |
|WDC04 |워싱턴, DC |북미 동부 |
|WDC06 |워싱턴, DC |북미 동부 |
|WDC07 |워싱턴, DC |북미 동부 |
{: caption="표 1. vCenter Server with Hybridity Bundle 인스턴스에 사용 가능한 {{site.data.keyword.CloudDataCents_notm}}" caption-side="top"}

가용성 및 인벤토리 제공에 따라 {{site.data.keyword.CloudDataCents_notm}}는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 상태 표시기를 표시하여 배치를 계획할 수 있습니다.

|상태 |상태 세부사항 |
|:------------------------------|:--------------------------------------------------|
|서비스 예정                   |{{site.data.keyword.CloudDataCent_notm}}는 현재 사용할 수 없습니다. |
|임시적으로 사용 불가능  |{{site.data.keyword.CloudDataCent_notm}}는 현재 사용 가능하지 않습니다. |
|제한된 인벤토리             |{{site.data.keyword.CloudDataCent_notm}}에는 제한된 가용성이 있으며 주문이 완료되지 않을 수 있습니다. |
{: caption="표 2. vCenter Server with Hybridity Bundle 인스턴스 주문 시 {{site.data.keyword.CloudDataCents_notm}}에 대한 상태 표시기" caption-side="top"}

## 관리 컴포넌트의 백업
{: #vc_hybrid_planning-backup-mgmt-components}

사용자는 모든 인스턴스 컴포넌트의 가용성을 유지보수하고 보장할 책임이 있습니다. 모든 관리 컴포넌트의 백업 또는 고가용성에 대해 계획하도록 적극 권장합니다. 자세한 정보는 [컴포넌트 백업](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)을 참조하십시오.

## vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스
{: #vc_hybrid_planning-addon-services}

vCenter Server with Hybridity Bundle 인스턴스에는 VMware HCX on {{site.data.keyword.cloud_notm}} 서비스의 이용을 허용하는 VMware Hybrid Cloud Extension(HCX) 라이센싱이 포함되어 있습니다. 이 서비스는 {{site.data.keyword.cloud_notm}}로 온프레미스 데이터 센터의 네트워크를 원활하게 확장할 수 있으며, 이를 통해 변환이나 변경 없이 {{site.data.keyword.cloud_notm}}에서 가상 머신(VM)을 마이그레이션할 수 있습니다.

이 서비스를 배치할 때 다음 설정을 완료하십시오.
* 다음 옵션 중 하나를 선택하여 **HCX 상호연결 유형**을 지정하십시오.
  * **공용 네트워크**: HCX는 공용 네트워크를 통해 사이트 간에 암호화된 연결을 작성합니다.
  * **사설 네트워크**: HCX는 사설 네트워크를 통해 사이트 간에 암호화된 연결을 작성합니다.
* **공용 엔드포인트 인증서 유형**을 지정하십시오. **CA 인증서**를 선택하는 경우 다음 설정을 구성하십시오.
  * **인증서 컨텐츠**: CA 인증서의 컨텐츠를 입력하십시오.
  * **개인 키**: CA 인증서의 개인 키를 입력하십시오.
  * (선택사항) **비밀번호**: 개인 키가 암호화된 경우 개인 키의 비밀번호를 입력하십시오.
  * (선택사항) **비밀번호 다시 입력**: 개인 키의 비밀번호를 한 번 더 입력하십시오.
  * (선택사항) **호스트 이름**: CA 인증서의 공통 이름(CN)에 맵핑될 호스트 이름을 입력하십시오. HCX on {{site.data.keyword.cloud_notm}}에서는 NSX Edge에서 허용하는 형식의 CA 인증서를 필요로 합니다. NSX Edge 인증서 형식에 대한 자세한 정보는 [SSL 인증서 가져오기](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}를 참조하십시오.

사용자의 요구에 따라 인스턴스에 대한 다른 추가 기능 서비스를 주문할 수 있습니다(예: 재해 복구). 자세한 정보는 [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)를 참조하십시오.

## 용량 고려사항
{: #vc_hybrid_planning-capacity-considerations}

용량 고려사항에 대한 자세한 정보는 [용량 스케일링](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling)을 참조하십시오.

## 관련 링크
{: #vc_hybrid_planning-related}

* [vCenter Server with Hybridity Bundle 개요](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
