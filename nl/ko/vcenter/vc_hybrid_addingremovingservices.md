---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-10"

keywords: vCenter Server Hybridity add service, view service vCenter Server Hybridity, remove service vCenter Server Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거
{: #vc_hybrid_addingremovingservices}

재해 복구 솔루션과 같은 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 인스턴스에 대한 서비스를 주문할 수 있습니다. 이 서비스가 더 이상 필요하지 않은 경우 인스턴스에서 이를 제거할 수 있습니다.

## vCenter Server with Hybridity Bundle 인스턴스에 사용 가능한 서비스
{: #vc_hybrid_addingremovingservices-available-services}

다음 서비스는 설치된 서비스 버전과 함께 vCenter Server with Hybridity Bundle 인스턴스에 사용 가능합니다.

표 1. vCenter Server with Hybridity Bundle 인스턴스에 사용 가능한 서비스

| 서비스 이름 | 현재 서비스 버전 | 인스턴스 버전 |
|----------------------------------------------------------------------------------------|------------------|
| [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations) | 2.2 | V2.9 이상 |
| [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | BIG-IP VE v14.1.0.2 | V1.9 이상 |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)       | 300 시리즈 | V1.8 이상 |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | V2.0 이상 |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)              | 5.5.1 | V2.3 이상 |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)              | 4.3.2 | V2.3 이상 |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)              | 4.3.2 | V2.5 이상 |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | 3.1.2 | V2.7 이상 |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)  | 10.1.3 | V2.2 이상 |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) | 2.0  |해당사항 없음 |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | 9.5u4 | V1.8 이상 |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations) | 3.5.1 | V2.3 이상 |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | 6.5 update 3 | V1.2 이상 |

## vCenter Server with Hybridity Bundle 인스턴스에 서비스를 추가하는 프로시저
{: #vc_hybrid_addingremovingservices-adding-procedure}

vCenter Server with Hybridity Bundle 인스턴스에 서비스를 적용하려면 표에 있는 링크를 클릭하여 서비스에 대한 고려사항을 검토하십시오. 그런 다음 배치되는 컴포넌트를 확인하고 주문 주제의 지시사항을 따라 주문하십시오.

### 서비스 설치 결과
{: #vc_hybrid_addingremovingservices-adding-results}

서비스 설치가 완료되면 이메일로 알림을 받고 서비스가 **설치됨** 상태로 인스턴스 세부사항의 **서비스** 탭에 표시됩니다.

## vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스를 보는 프로시저
{: #vc_hybrid_addingremovingservices-viewing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 서비스를 볼 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **서비스**를 클릭하십시오.
4. **서비스** 페이지에서 하나의 서비스를 클릭하여 서비스 상태 및 기타 세부사항과 같은 정보를 검토하십시오.
5. 확인한 서비스에 따라 서비스 세부사항에 제공된 인증 정보를 사용하여 서비스 콘솔에 액세스하고 여기에서 서비스를 관리할 수 있습니다.

## vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스를 제거하는 프로시저
{: #vc_hybrid_addingremovingservices-removing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 서비스를 제거할 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **서비스**를 클릭하십시오.
4. **서비스** 페이지에서 제거할 서비스 인스턴스를 찾고 **삭제** 아이콘을 클릭하십시오.
5. 해당되는 경우 **서비스 삭제** 창에서 고려사항 또는 경고를 검토하십시오. **이해함**을 선택하고 **삭제**를 클릭하십시오.

### 서비스 제거 결과
{: #vc_hybrid_addingremovingservices-removing-results}

서비스 제거 요청이 허용된 후 서비스 상태가 **제거 중**으로 변경됩니다.

서비스 제거가 완료되면 이메일로 알림을 받고 서비스가 인스턴스의 **서비스** 페이지에서 제거됩니다.

제거된 서비스에 대한 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시까지 비용이 청구됩니다.
{:note}

## 관련 링크
{: #vc_hybrid_addingremovingservices-related}

* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
