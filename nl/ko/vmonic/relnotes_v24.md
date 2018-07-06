---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# V2.4 릴리스 정보

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 추가 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## 스펙터(Spectre) 및 멜트다운(Meltdown) 조치 방안

{{site.data.keyword.vmwaresolutions_short}}가 스펙터(Spectre) 및 멜트다운(Meltdown)(CVE-2017-5753, CVE-2017-5715 및 CVE-2017-5754)으로 알려진 취약점에 대한 응답으로 VMware에서 패치를 릴리스했습니다.

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

자세한 정보는 [스펙터(Spectre) 및 멜트다운(Meltdown) 취약점 해결](../vmonic/trbl_fix_spectre.html)을 참조하십시오.

## 자국어 지원

V2.4 릴리스부터는 자국어 지원(NLS)이 IBM Cloud for VMware Solutions에서 사용 가능합니다.
사용자 문서를 포함한 콘솔의 모든 기능은 여러 언어로 사용할 수 있습니다.

영어 외에 다음 언어가 지원됩니다.
* 독일어
* 스페인어
* 프랑스어
* 이탈리어어
* 일본어
* 한국어
* 브라질 포르투갈어
* 중국어
* 대만어

**참고**: 참조 아키텍처 문서는 영어로만 사용 가능합니다.

## Skylake Xeon CPU 지원

V2.4 릴리스부터는 다음 새 Bare Metal Server CPU 모델이 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}, VMware vSphere on {{site.data.keyword.cloud_notm}} 및 VMware Federal on {{site.data.keyword.cloud_notm}} 인스턴스 및 클러스터에서 배치에 사용 가능합니다.

* 듀얼 Intel Skylake Xeon Silver 4110 프로세서 / 총 16개의 코어, 2.1GHz
* 듀얼 Intel Skylake Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz
* 듀얼 Intel Skylake Xeon Gold 6140 프로세서 / 총 36개의 코어, 2.3GHz

자세한 정보는 *Bare Metal Server 설정* 절을 참조하십시오.

* [Cloud Foundation 인스턴스 주문](../sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [새 vSphere 클러스터 주문](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)
* [VMware Federal 인스턴스 주문](../vcenter/vc_fed_orderinginstance.html#bare-metal-server-settings)

## VMware vCenter Server 인스턴스에 대한 업데이트

### Network File System 성능 개선

가장 까다로운 워크로드 유형에 맞게 디자인된 10IOPS/GB의 성능 레벨은 더 이상 특정 {{site.data.keyword.CloudDataCent_notm}}로 제한되지 않으며 이제 어디서든 사용 가능합니다. 자세한 정보는 [vCenter Server 개요](../vcenter/vc_vcenterserveroverview.html#vcenter-server-technical-specifications)에서 *스토리지* 절을 참조하십시오.

## VMware Federal 인스턴스에 대한 업데이트

### 새 IBM Cloud Data Center 옵션

이제 VMware Federal 인스턴스를 DAL08 - Dallas, TX {{site.data.keyword.CloudDataCent_notm}}에 배치할 수 있습니다. 자세한 정보는 [VMware Federal 인스턴스에 대한 요구사항 및 계획](../vcenter/vc_fed_planning.html#ibm-cloud-data-center-availability)의 *IBM Cloud Data Center 가용성* 절을 참조하십시오.

## 추가 서비스에 대한 업데이트

### IBM Spectrum Protect Plus on IBM Cloud

현재 릴리스는 새로 배치된 모든 인스턴스에 IBM Spectrum Protect&trade; Plus V10.1.1 패치 1을 설치합니다. IBM Spectrum Protect Plus V10.1.1 패치 1의 새 기능에 대한 정보는 [IBM Spectrum Protect Plus 업데이트](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}를 참조하십시오.

### VMware HCX on IBM Cloud

새 옵션은 이 서비스를 주문할 때 HCX 상호연결을 위해 공용 네트워크와 사설 네트워크 중에서 선택하는 데 사용할 수 있습니다. 자세한 정보는 [VMware HCX on IBM Cloud 주문](../services/hcx_ordering.html)을 참조하십시오.

## 새로 작성되고 업데이트된 문서

### 참조 아키텍처 문서

{{site.data.keyword.vmwaresolutions_short}} 아키텍처 문서는 이제 사용자 문서의 *참조* 절에서 사용할 수 있습니다. 참조 아키텍처는 문서는 영어로만 사용 가능합니다. 자세한 정보는 [솔루션 개요](../archiref/solution/solution_overview.html)를 참조하십시오.

### 서비스 문서

서비스 주문 시 관련 정보를 쉽게 찾을 수 있도록 서비스 정보가 재구조화되고 탐색이 개선되었습니다.

자세한 정보는 다음을 참조하십시오.

* [F5 on IBM Cloud 주문](../services/f5_ordering.html)
* [FortiGate Security Appliance on IBM Cloud 주문](../services/fsa_ordering.html)
* [FortiGate Virtual Appliance on IBM Cloud 주문](../services/fortinetvm_ordering.html)
* [Hytrust CloudControl on IBM Cloud 주문](../services/htcc_ordering.html)
* [Hytrust DataControl on IBM Cloud 주문](../services/htdc_ordering.html)
* [IBM Spectrum Protect Plus on IBM Cloud 주문](../services/spp_ordering.html)
* [KMIP for VMware on IBM Cloud 주문](../services/kmip_ordering.html)
* [Veeam on IBM Cloud 주문](../services/veeam_ordering.html)
* [Zerto on IBM Cloud 주문](../services/zerto_ordering.html)

## 사용자 인터페이스 업데이트 및 개선사항

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.

* 클러스터 추가 및 서비스 추가 분할창에서는 이제 레이아웃이 잘 구성된 페이지 형식을 사용하므로 태스크를 보다 효율적으로 완료할 수 있습니다.
* **배치된 인스턴스** 페이지의 기능은 검색, 페이지 매김 및 정렬 기능으로 개선되었습니다. 이러한 개선사항을 통해 매우 빠르게 인스턴스를 찾을 수 있습니다.
* 인스턴스 세부사항 페이지에서는 왼쪽 탐색 메뉴를 사용하므로 인스턴스 정보에 쉽고 빠르게 액세스할 수 있습니다.
* 다양한 오류 메시지 및 도구 팁 개선사항은 사용자 인터페이스의 설정을 적절하게 선택하는 데 도움이 됩니다.
