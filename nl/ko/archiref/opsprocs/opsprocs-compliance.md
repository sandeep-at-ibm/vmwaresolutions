---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

---

# 규제 준수
{: #opsprocs-compliance}

규제 준수는 규제 기관 또는 산업 우수 사례로 확립된 최소한의 제어를 충족하는 데 필요한 요구사항 세트입니다. 규제 준수 프레임워크는 일반적으로 다양한 기술에 대한 지침을 제공하는 광범위한 프레임워크이지만, 공급 업체의 산업 우수 사례는 일반적으로 기술상의 위험을 해결하는 데 특정한 기술입니다.

vCenter Server 인스턴스의 경우 보안은 전담 팀의 배치 후 작업을 사용하여 관리되는 것이 좋습니다. 이러한 업무 분리에는 인스턴스의 보안 상태에 대한 기능 보강과 모니터가 필요합니다. HyTrust CloudControl은 역할 기반 분리를 통해 팀을 지원할 수 있다.

HyTrust DataControl 및 KeyControl은 저장 중 암호화 및 지오펜싱(geo-fencing)과 같은 워크로드 보호를 제공하여 도움을 제공할 수 있습니다. 사용자는 정부 규제 준수뿐만 아니라 사이버 위험 및 포렌식 관리에 대한 도움을 제공하기 위해 Caveonix RiskForesight 서비스를 배치하는 데 관심이 있을 수 있습니다.

VMware Security Hardening 안내서는 안전한 방식으로 VMware 제품을 배치하고 운영하는 방법을 제공합니다. vSphere의 안내서는 가이드라인 분류 및 위험 평가를 허용하도록 사용하기 쉬운 스프레드시트 형식(다양한 메타데이터 포함)으로 제공됩니다. 보안 자동화를 사용으로 설정하기 위한 스크립트 예제도 포함됩니다. 연속되는 버전의 안내서에서 변경사항을 나열하는 비교 문서가 제공됩니다.

VMware Security Hardening 안내서에 설명된 많은 제어가 {{site.data.keyword.vmwaresolutions_full}} 참조 아키텍처에 포함됨에 따라 자동으로 배치되는 동안 플랫폼의 보안 상태를 고유한 요구사항 및 엔터프라이즈 정책에 맞게 사용자 조정해야 합니다. VMware Security Hardening 안내서는 이 검토를 수행하는 데 필요한 기술별 제어를 제공합니다. Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}는 이 규제 준수 태스크를 자동화하고 추가 규제 기관 안내서를 제공합니다.

vRealize Operations Manager를 사용하면 VMware 오브젝트가 vSphere Security Configuration 안내서의 규제 준수 규칙 위반 여부를 모니터할 수 있습니다. 규제 준수 경보는 vCenter Server 인스턴스, 호스트, 가상 머신, 분배 포트 그룹, 분배 스위치를 트리거하며, 규제 준수 위반에 대한 조사를 허용합니다. HIPAA(Health Insurance Portability and Accountability Act) 및 PCI DSS(Payment Card Industry Data Security Standard) 규제 준수에 관심이 있는 클라이언트는 VMWare Solutions Exchange 웹 사이트에서 vRealize Operations Manager Compliance Packs를 다운로드하고, 라이센스를 부여하고 설치할 수 있습니다. 이 규제 준수 팩은 HIPAA 및 PCI 강화 안내서에 대해 vSphere 리소스를 유효성 검증하도록 경보, 정책 및 보고서를 제공합니다.


## 관련 링크
{: #opsprocs-compliance-links}

* [VMware 보안 강화 안내서](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [vSphere 보안 안내서](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
