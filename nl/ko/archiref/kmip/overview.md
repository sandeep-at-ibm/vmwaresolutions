---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware 개요
{: #kmip-overview}

아 솔루션 아키텍처에서는 VMware on {{site.data.keyword.cloud_notm}} 인스턴스를 보호하기 위한 KMIP on VMware 아키텍처에 대해 설명합니다. 다수의 스토리지 암호화 옵션은 VMware 워크로드를 보호하는 데 사용 가능합니다. KMIP for VMware는 {{site.data.keyword.cloud_notm}} Key Protect 또는 {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services 고객 관리 키의 보안 및 유연성을 갖춘 간소화된 스토리지 암호화 관리를 제공하도록 VMware 원시 vSphere 암호화 및 vSAN 암호화와 함께 작동합니다.

이 솔루션은 {{site.data.keyword.cloud_notm}}에서 vCenter Server 오퍼링의 추가 컴포넌트와 확장으로 간주됩니다. 결과적으로 이 문서에서는 {{site.data.keyword.cloud_notm}}의 기본 솔루션에 대한 기존의 구성을 다루지 않습니다. 기본 솔루션 아키텍처에 대해 좀 더 자세히 이해하려면 [VMware on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)를 참조하십시오.

## 주요 이점
{: #kmip-overview-benefits}

많은 스토리지 암호화 솔루션이 VMware 워크로드에서 사용 가능하며 KMIP for VMware는 다음 이점을 제공합니다.

* VMware vSAN 암호화 및 vSphere 암호화와 통합되며, 이들은 모두 스토리지 또는 가상 머신 계층이 아닌 하이퍼바이저 계층에서 구현됩니다. 이 접근 방식을 통해 스토리지 솔루션 및 애플리케이션의 관리와 투명성이 용이해집니다.
* 완전히 관리되는 키 관리 서버는 많은 {{site.data.keyword.cloud_notm}} 다중 영역 지역(MZR)에서 사용 가능합니다.
* VMware 클러스터가 {{site.data.keyword.cloud_notm}} Key Protect 또는 {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services와 통합하면 언제든지 취소할 수 있는 완전한 고객 관리 키가 제공됩니다.

## 관련 링크
{: #kmip-overview-related}

* [솔루션 디자인](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [구현 및 관리](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-implementation)
