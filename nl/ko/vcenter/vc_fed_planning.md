---

copyright:

  years:  2016, 2019

lastupdated: "2018-07-19"

---

# VMware Federal 인스턴스에 대한 요구사항 및 계획

VMware Federal 인스턴스를 주문하기 전에 다음 요구사항을 검토하십시오. 워크로드 용량 요구사항에 따라 인스턴스를 계획하십시오.

## IBM Cloud 계정 요구사항

사용 중인 {{site.data.keyword.cloud}} 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 계정에 대한 요구사항](../vmonic/slaccountrequirement.html)을 참조하십시오.

## IBM Cloud Data Center 가용성

VMware Federal on {{site.data.keyword.cloud_notm}} 배치에는 실제 인프라에 대한 엄격한 요구사항이 있습니다. 다음 {{site.data.keyword.CloudDataCents_notm}}에만 VMware Federal 인스턴스를 배치할 수 있습니다.
- WDC03 - Washington, DC, POD2
- DAL08 - Dallas, TX, POD2

## 관리 컴포넌트의 백업

사용자는 선호하는 백업 솔루션을 사용하여 모든 인스턴스 컴포넌트의 가용성을 유지보수하고 보장할 책임이 있습니다. 모든 관리 컴포넌트의 백업 또는 고가용성에 대해 계획하도록 적극 권장합니다. 자세한 정보는 [컴포넌트 백업](../archiref/solution/solution_backingup.html)을 참조하십시오.

## VMware Federal 인스턴스에 대한 서비스

VMware Federal on {{site.data.keyword.cloud_notm}}는 추가 서비스를 주문하는 옵션을 제공하지 않습니다.

## 용량 고려사항

용량 정보 및 고려사항은 [용량 스케일링](../archiref/solution/solution_scaling.html)을 참조하십시오.

### 관련 링크

* [vCenter Server 소프트웨어 명세서](vc_bom.html)
* [VMware Federal on {{site.data.keyword.cloud_notm}} 개요](vc_fed_overview.html)
* [VMware Federal 인스턴스 주문](vc_fed_orderinginstance.html)
* [VMware Federal 인스턴스 보호](vc_fed_securinginstance.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
